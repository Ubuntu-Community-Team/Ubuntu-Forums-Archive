---
title: "Asus U41Sx: Making it work!"
date: 2011-08-28
forum: Asus Ubuntu Support (CLOSED)
---

### Post by FirstByté on 2011-08-28
[SIZE="4"]A Support thread![/SIZE]

Through this thread, I look forward to combating issues hindering a smooth ride for all ASUS U41Sx families and cousins.

[SIZE="1"]*To Moderators: If this is a duplicate please feel free to truncate thread*[/SIZE]

**This support applies to laptops with the [Related Specs]("http://www.sbs-silver.ru/en/product/noutbuk-asus-u41su41sv/"):**
Computer Name: **Asus U41S**
Processor:	 **Intel Core i5**
Processor Model:	 **2410M**
Number of cores:	 **2**
Frequency:	 **2300 MHz**
RAM:	 **4096 MB**
hard drive:	 **640 GB**
Memory Type:	 **DDR3-1333 PC-10600**
Video:	 **GeForce GT540M, CUDA 1024 MB / Intel GPU**


Consistent with [Asus U36S Support thread]("http://ubuntuforums.org/showpost.php?p=11174240&postcount=1"), the following *worked out-of-the-box*.

**Worked Out-of-the-Box**
Consistent with [Olof_]("http://ubuntuforums.org/showpost.php?p=11183644&postcount=17")
> **olof_ said:**
> there are several fn-keys and quite alot of them are actually working.

[SIZE="2"]Working[/SIZE]
[LIST]
[*]&#8220;ZZ&#8221; Icon (F1): Places the Notebook PC in suspend mode
[*]Radio Tower (F2): Toggles theinternal wireless LAN on
[*]Sun Down Icon (F5): Decreases the display brightness
[*]Sun Up Icon (F6): Increases the display brightness
[*]LCD Icon (F7): Toggles the display panel on and off
[*]Num Lk (Ins): Toggles the numeric keypad on and off
[/LIST]


[SIZE="2"]Not Working[/SIZE]
[LIST]
[*]Crossed-out Touchpad (F9)
[*]Crossed Speaker Icons (F10)
[*]Speaker Down Icon (F11)
[*]Speaker Up Icon (F12)
[*]Stop (Up Arrow)
[*]Play/Pause (Down Arrow)
[*]Next (Right Arrow)
[*]Previous (Left Arrow)
[/LIST]

[SIZE="2"]Not Tested (yet)[/SIZE]
[LIST]
[*]LCD/Monitor Icons (F8 )
[*]Scr Lk (Del)
[/LIST]

observe that this is with an out of the box setup. Ubuntu 11.04, x86.
[SIZE="2"]Worked [Tested by me][/SIZE]
[LIST]
[*] Wifi 
[*] Sound
[*] Right-side-up webcam
[/LIST]

[SIZE="2"]Yet to work [Tested by me][/SIZE]
[LIST]
[*] LCD/Monitor Icons (F8 ) [Every monitor toggle results in faulty rendering (blank black screen)]
[*] Wifi LED never works (Fn - F2 toggles wifi though but LED stays off)(Miraculously works with LiveCD/USB )
[/LIST]

[SIZE="2"]**Attempts at fixes**[/SIZE]
[SIZE="2"]**Installed [bumblebee]("https://github.com/Bumblebee-Project/Bumblebee/blob/master/README")**[/SIZE]
*Result:*
* Compiz works with Unity Session.
* Compiz still fails utterly in Ubuntu classic

Temporary measure to enjoy both (Unity, Gnome 2.3x) desktop juices:
* Added 'gnome-panels' to Startup Applications,
* Removed top panel (I left the bottom panel because I NEED control of my open windows!!)


[SIZE="2"]**Constant fan spinning**[/SIZE]
[SIZE="2"]Installing Sensor Applets[/SIZE]
```

$ sudo apt-get install sensors-applet lm-sensors
$ sudo sensors-detect 
$ sudo service module-init-tools start

```
*Result:*
Quieter running smooth system. 


**Fix media FN issues**
Follow this [post]("http://ubuntuforums.org/showpost.php?p=10997488&postcount=9")
*Result:*
All media buttons working! :)


I'll update this as I unravel more fixes.

Enjoy Asus ;)

---

### Post by FirstByté on 2011-09-01
This helps to turn 'off | on' my GT540M CUDA

```

$ sudo modprobe acpi_call
$ sudo sh asusU41X.sh

```

content of my asusU41Xsh

```

#!/bin/sh
# Power control for Asus U41SV Optimus
# by Ashon iKON
if ! lsmod | grep -q acpi_call; then
    echo "Error: acpi_call module not loaded"
    exit
fi

acpi_call () {
    echo "$*" > /proc/acpi/call
    cat /proc/acpi/call
}


case "$1" in
off)
    echo _DSM $(acpi_call "\_SB.PCI0.PEG0.GFX0._DSM" \
	"{0xF8,0xD8,0x86,0xA4,0xDA,0x0B,0x1B,0x47," \
	 "0xA7,0x2B,0x60,0x42,0xA6,0xB5,0xBE,0xE0}" \
	 "0x100 0x1A {0x1,0x0,0x0,0x3}")
	# ok to turn off: Buffer {0x59 0x0 0x0 0x11}
	# is already off: Buffer {0x41 0x0 0x0 0x11}
    echo _PS3 P=$(acpi_call "\_SB.PCI0.PEG0.GFX0._PS3")
;;
on)
    echo _PS0 P=$(acpi_call "\_SB.PCI0.PEG0.GFX0._PS0")
;;
*)
    echo "Usage: $0 [on|off]"
esac

echo P ${P}
#echo P3MO $(acpi_call "\_SB.PCI0.PEG0.GFX0.P3MO")
#echo DGPS $(acpi_call "\_SB.PCI0.PEG0.GFX0.DGPS")
#PSC=$(acpi_call "\_SB.PCI0.PEG0.GFX0._PSC")
#echo _PSC ${PSC}

case "$P" in **[COLOR="Red"]# I need to fix this line[/COLOR]**
0x0)
    PXX="on"
;;
0x3)
    PXX="off"
;;
esac
echo "Asus U41SV Optimus appears to be ${PXX}"


```

This gives me 50% more time battery life.
**Resume [COLOR="green"]Fixed [/COLOR]**

```
gksu gedit /etc/pm/sleep.d/20_custom-asus-u36sd 
```

```

BUSES="0000:00:1a.0 0000:00:1d.0"
BUSES3="0000:07:00.0"

case "${1}" in
    hibernate|suspend)
        # Switch USB buses off
        for bus in $BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/unbind
        done
        # Switch USB 3.0 buses off
        for bus in $BUSES3; do
            echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/unbind
        done
        ;;
    resume|thaw)
        # Switch USB buses back on
        for bus in $BUSES; do
            echo -n $bus | tee /sys/bus/pci/drivers/ehci_hcd/bind
        done
        # Switch USB 3.0 buses back on
        for bus in $BUSES3; do
            echo -n $bus | tee /sys/bus/pci/drivers/xhci_hcd/bind
        done
        ;;
esac
```

Adding executable permission:
```

sudo chmod +x /etc/pm/sleep.d/20_custom-asus-u36sd

```

[I]TRIVIA ISSUE:
[LIST]
[*] Wifi LED never comes back on after resume from suspension or hibernatation
[*] Have to run acpi_call script every boot!
[/LIST][/I]

---

