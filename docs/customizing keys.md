https://docs.moergo.com/glove80-user-guide/customizing-key-layout/

Customizing key layout and swapping keycaps¶
Customizing key layout¶
Each of us has a different hand size and shape, typing habits, and different application needs.

Glove80 and its open-source ZMK-based firmware make it easy for you to customize your Glove80 to have exactly the key layout you want.

There are a few ways to change the key layout. The easiest way is to use the layout editor. An alternative is to edit the keymap file and compile your own ZMK firmware For more information on this, please see Appendix: ZMK.

After you have built a new ZMK firmware with the new key layout using either approach, you will have to load the firmware onto Glove80. To do this, follow the instructions in the Loading new ZMK firmware onto your Glove80 section.

Glove80 Layout Editor¶
Glove80 Layout Editor is an optional MoErgo service designed to complement your Glove80. Glove80 Layout Editor is an on-line web app accessible on most modern browsers, including on desktops and mobile devices. With Glove80 Layout Editor you can graphically design your own layout, and generate the firmware without any application installation.

Glove80 Layout Editor

Glove80 Layout Editor
To use Glove80 Layout Editor, you will need to create an account, subject to its terms of use.

Glove80 Layout Editor is simple to use and learn. The Layout Editor Guide is here.

Loading new ZMK firmware onto your Glove80¶
The Glove80 Layout Editor generates a .uf2 file which is the new firmware containing the new key layout. This new firmware needs to be loaded onto both halves of your Glove80.

To do this safely, you will need:

A spare keyboard or on-screen keyboard (as safety insurance)
A USB-C cable to connect from your computer to Glove80
The steps to load the new firmware are:

First plug in the USB-C cable to the right half of your Glove80 and to the host computer.
Put the right half into bootloader mode. On the default key layout, this is done by pressing the keys Magic + '(note: single-quote). If this doesn’t work or if you have changed your layout, please see the section on Putting Glove80 into Bootloader for Firmware Loading.
If successful, the bootloader will present a USB Mass Storage Device. As an example, on Windows you will see a File Explorer window with the name GLV80RHBOOT.
GLV80RHBOOT

Tips

We have multiple reports from users that a faulty USB hub or a faulty USB cable causing issues for firmware flashing, despite the cable and USB hub being able to transmit keystrokes. Please refer to this Troubleshooting FAQ entry if you suspect such an issue.

Note

If you need to leave the bootloader without loading new firmware, simply power Glove80 off and on again using the power switch.

Copy the .UF2 file onto this Mass Storage Device. If successful the Mass Storage Device will disappear.
Note

There is no need to rename the UF2 file to CURRENT.UF2. Any filename with the extension of .UF2 suffices

Warning

Recent versions of macOS fails the file copy if the UF2 filename is too long. Please see this Troubeshooting FAQ entry for details.

Next plug in the USB-C cable to the left half of your Glove80 and to the host computer.
Put the left half into bootloader mode. On the default key layout, this is done by pressing the keys Magic + Esc. If this doesn’t work or if you have changed your layout, please see the section on Putting Glove80 into Bootloader for Firmware Loading.
If successful, the bootloader will present a USB Mass Storage Device. As an example, on Windows you will see a File Explorer window with the name GLV80LHBOOT
GLV80LHBOOT

Copy the .UF2 file into this Mass Storage Device. If successful the Mass Storage Device will disappear.

After a firmware version change or changes made to Advanced Configuration, it is generally recommended to perform a Configuration factory reset and re-pairing left and right halves procedure.

Putting Glove80 into Bootloader for firmware loading¶
The bootloader is the piece of software that runs immediately after you turn on a Glove80 half. Normally it will simply pass the control over to the ZMK firmware. However, it also has the ability to load new ZMK firmware by presenting a USB mass storage device.

There are two ways to put Glove80 into the bootloader mass storage device mode for firmware loading. The first way (Entering bootloader mass storage device mode on power-up) is more reliable as it does not require a working ZMK installation, nor a connection between the left half and the right half. It works even if the two halves have different ZMK firmware versions. This is the recommended method.

You can tell if a Glove80 half has successfully entered into bootloader mass storage device mode by the slow pulsing red LED next to the power switch. If the red LED is fast flashing, it indicates that the Glove80 half is in bootloader mode but there is no USB connection with the host. If the red LED is solid red or off, the Glove80 is not in bootloader mode.

Entering bootloader mass storage device mode on power-up¶
Bootloader on power-up method

To put the left half into the bootloader mass storage device mode:

Switch off the power switch of the left half
Connect a USB cable from the host to the left half
Referring to the row-column key above, hold C6R6 + C3R3 (Magic + E on the default layout)
While holding the two keys, switch on the power switch of the left half
To put the right half into the bootloader mass storage device mode:

Switch off the power switch of the right half
Connect a USB cable from the host to the right half
Referring to the row-column key above, hold C6R6 + C3R3 (I + PgDn on the default layout)
While holding the two keys, switch on the power switch of the right half
Entering bootloader mass storage device mode from ZMK¶
Bootloader using ZMK method

Another way is to use the key mapping on the ZMK key layout by activating the &bootloaderbehavior on the half of the Glove80 that you want to load new firmware.

On the default key layout, you can do so by

First connect a USB cable from the host to the half of Glove80 you want to load firmware
Pressing Magic + Esc for the left half
Pressing Magic + ' for the right half
Warning

This method does not work if the ZMK installation is corrupted, or the left half and the right half are not communicating, or the two halves have different ZMK firmware versions. If keystrokes from your right half are not getting through to the host, this method is not likely to work. Please use Putting Glove80 into Bootloader for firmware loading instead.
