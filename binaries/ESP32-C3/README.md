To update the firmware on the newer model you only need the ESP32-C3 binary file using the web interface on the current running software. I you might happen to brick the system, then please check the "flashing.png" to recover your module using https://espressif.github.io/esptool-js/

For the recovery the module must be in boot mode. Press the boot button and hold it while resetting. After reset, you can let go of the boot button. Now the module is in boot mode.

On a macbook you need to install esptool (https://github.com/RavenSystem/esp-homekit-devices/wiki/Install-ESPTool-on-macOS) and then run:
python3 -m esptool --chip esp32c3 --port /dev/cu.usbmodem101 --baud 921600  --before default_reset --after hard_reset write_flash  -z --flash_mode dio --flash_freq 80m --flash_size 4MB 0x0 Sofar2mqtt.ino.bootloader.bin 0x8000 Sofar2mqtt.ino.partitions.bin 0xe000 boot_app0.bin 0x10000 Sofar2mqtt.v3.6-ESP32-C3.bin 
