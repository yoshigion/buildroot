Intro
=====

This default configuration will allow you to start experimenting with the
buildroot environment for the Orangepi 3. With the current configuration
it will bring-up the board, and allow access through the serial console.

Orangepi 3 link:
http://www.orangepi.org/Orange%20Pi%203/

Wiki link:
https://linux-sunxi.org/Xunlong_Orange_Pi_3

How to build
============

    $ make orangepi_3_defconfig
    $ make

Note: you will need access to the internet to download the required
sources.

How to write the SD card
========================

Once the build process is finished you will have an image called "sdcard.img"
in the output/images/ directory.

Copy the bootable "sdcard.img" onto an SD card with "dd":

  $ sudo dd if=output/images/sdcard.img of=/dev/sdX
  $ sudo sync

Insert the micro SDcard in your Orangepi 3 and power it up. The console
is on the serial line, 115200 8N1.

WiFi
====

 # wpa_passphrase ACCESSPOINTNAME >> /etc/wpa_supplicant.conf
   (type password and enter)
 # wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -B
 # udhcpc -i wlan0
 # ping google.com
