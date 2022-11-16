
# STM32_Si5352A
Si5351 C Library for STM32 HAL (Based on Adafruit's si5351 driver)
******************************************************************
Put all .h/c files into their respective folders
```
(si5351_asserts.h,si5351_errors.h,si5351)--->/inc   , (si5351.c)--->/src
```
Modify si5351.c according to your platform
```
#include "stm32h7xx_hal.h"
#include "stm32h7xx_hal_i2c.h"
```

Modify si5351.h xtal_speed
```
------->#define SI5351_XTAL_FREQ  25000000 or 27000000 <-------
```

On main.c file add...
```
/* USER CODE BEGIN Includes */
#include "si5351.h"
/* USER CODE END Includes */
```
STM32CubeIDE Generated I2C handle
```
--> I2C_HandleTypeDef hi2c1;
```

  /* USER CODE BEGIN 2 */
  ```
  Si5351_set_correction(0);
  Si5351_init(SI5351_CRYSTAL_LOAD_10PF, SI5351_XTAL_FREQ);
  Si5351_set_pll(SI5351_PLL_FIXED, SI5351_PLLA);
  Si5351_set_ms_source(SI5351_CLK0, SI5351_PLLA);
  //1_000_000_00 = 1MHZ
  //32_768_000_00 = 32.768M
  Si5351_set_freq(100000000, SI5351_PLL_FIXED, SI5351_CLK0);
  Si5351_drive_strength(SI5351_CLK0, SI5351_DRIVE_2MA);
  Si5351_set_state_out(SI5351_CLK1, SI5351_OUT_DISABLE);
  Si5351_set_state_out(SI5351_CLK2, SI5351_OUT_DISABLE);
  ```
  /* USER CODE END 2 */

