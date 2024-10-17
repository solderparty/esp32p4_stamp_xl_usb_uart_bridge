# USB to UART Bridge - Modified for the ESP32-P4 Stamp XL

This program can be flashed on the ESP32-P4 Stamp XL to act as a passthrough to the ESP32-C6 module so that it can be easily flashed with the esptool.

Code modified from https://github.com/espressif/esp-iot-solution/tree/master/examples/usb/device/usb_uart_bridge

## Original Readme:

USB to serial bridge tool using the USB and UART capabilities of the ESP32-P4 microcontroller. This tool serves as a debugging and downloading utility with the following features:

1. Bidirectional transparent data communication between USB and UART.
2. Configurable serial port settings (supports baud rates up to 3000000 bps).
3. Compatibility with automatic firmware download functionality for `esptool`, enabling firmware updates for other ESP SoCs.

### Build and Flash

1. Make sure `ESP-IDF` is setup successfully

2. Set up the `ESP-IDF` environment variables, please refer [Set-up the environment variables](https://docs.espressif.com/projects/esp-idf/en/latest/esp32/get-started/index.html#step-4-set-up-the-environment-variables), Linux can use:

    ```bash
    . $HOME/esp/esp-idf/export.sh
    ```

3. Build, Flash, output log

    ```bash
    idf.py build flash monitor
    ```

### Automatic Firmware Download with esptool

* The automatic download feature is enabled by default. You can disable this option in `menuconfig → USB UART Bridge Demo → Enable auto download`.
* When using the automatic download feature, connect the development board's `AUTODLD_EN_PIN` and `AUTODLD_BOOT_PIN` pins to the target MCU's IO0 (Boot) and EN (RST) pins respectively.
* The automatic download feature may not function correctly on certain development boards (due to delays caused by RC circuits). In such cases, please fine-tune the code with gpio_set_level software delays.
