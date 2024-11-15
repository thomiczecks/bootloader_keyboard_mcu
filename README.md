# bootloader_keyboard_mcu
Bootloader build with https://github.com/adafruit/Adafruit_nRF52_Bootloader/ with minor modifications (see booloader.h).

### Flash instructions
Build openocd from source with:
```
sudo apt install wget git autoconf libtool make pkg-config libusb-1.0-0 libusb-1.0-0-dev libhidapi-dev libftdi-dev libhidapi-dev telnet
git clone https://github.com/ntfreak/openocd
cd openocd
./bootstrap
./configure --enable-sysfsgpio --enable-bcm2835gpio --enable-cmsis-dap
make
make install
```

Start openocd with:
```
sudo openocd -s ./openocd/tcl -d4 -f openocd.cfg
```

In another terminal run:
```
telnet localhost 4444
nrf5 mass_erase
flash write_image <full_path_to_hex_file>
verify_image <full_path_to_hex_file>
```