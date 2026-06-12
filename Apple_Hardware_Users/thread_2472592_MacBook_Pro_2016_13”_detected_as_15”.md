---
title: "MacBook Pro 2016: 13” detected as 15”"
date: 2022-03-04
forum: Apple Hardware Users
---

### Post by corduroy2 on 2022-03-04
On a vanilla install of Ubuntu 21.10, boot is in a video mode with 2880 vertical pixels, not the real 2560x1600

Impact: at the bottom of the display are 6–12 invisible lines, and during boot and console work, the cursor is below the bottom of the screen

Root cause: the computer is detected as MacBookPro13,3 (2016 15” 2880x1800) when it is MacBookPro13,2 (2016 13” 2560x1600)

It appears impossible to change the video mode in grub, there is only one device and it only has one mode. edid seems to claim that the display supports both 2560x1400 and 2880x1800 which is false
The dumb thing of course picks 2880x1800

I have noticed that linux-hardware.org probes incorrectly lists the computer as MacBookPro13,3

Question:
Can the video mode be changed somehow?
Should some other reconfiguration take place to get to 2560x1600

after boot, one can find:
**get-edid | parse-edid**This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
No EDID on bus 5
No EDID on bus 6
1 potential busses found: 4
256-byte EDID successfully retrieved from i2c bus 4
Looks like i2c was successful. Have a good day.
Checksum Correct


Section "Monitor"
        Identifier "Color LCD"
        ModelName "Color LCD"
        VendorName "APP"
        # Monitor Manufactured week 37 of 2015
        # EDID version 1.4
        # Digital Display
        DisplaySize 290 180
        Gamma 2.20
        Option "DPMS" "false"
        Modeline        "Mode 0" 260.73 2560 2568 2600 2640 1600 1632 1640 1646 +hsync -vsync 
        Modeline        "Mode 1" 328.92 2880 2888 2920 2960 1800 1838 1846 1852 +hsync -vsync 
EndSection

[COLOR=#000000][FONT=Arial]**for p in /sys/class/drm/*/status; do con=${p%/status}; echo -n "${con#*/card?-}: "; cat $p; done**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]DP-1: disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]DP-2: disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]eDP-1: connected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]HDMI-A-1: disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]HDMI-A-2: disconnected[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
kernel command-line options tested:
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]video=eDP-1:[COLOR=#000080]_[EMAIL="2560x1600@60"]2560x1600@60[/EMAIL]_[/COLOR]
# does not work[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]video=eDP-1:640x480[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# works but number of rows still wrong[/FONT][/COLOR]


grub:
[COLOR=#000000][FONT=Arial]**videoinfo**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]List of supported video modes:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Legend: mask/position=red/green/blue/reserved[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Adapter ‘Bochs PCI Video Driver’:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]No info available[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Adapter ‘Cirrus CLGD 5446 PCI Video Driver’:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]No info available[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]Adapter ‘EFI GOP driver’:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]* 0x0000 2880 x 1800 x 32 (115200) Direct color, mask: 8/8/8/8 pos: 16/8/0/24[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]does not work:
**videotest 2560x1600**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**videotest 640x480**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**videotest 1280x900**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**vbetest 640-480**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]error: can’t find command ‘vbetest’.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**vbeinfo**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]error: can’t find command ‘vbeinfo’.[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]**hwinfo --framebuffer**[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# has no output[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR]

---

### Post by QIII on 2022-03-04
*Moved to **Apple Hardware Users***

---

