---
title: "Blank after installed"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by jaya28inside on 2008-02-20
i install it for the text mode....

as the normal one but then 
after all completed

looks like after boot logon
it's not appeared anything...!!

except it's blank!! help me :( :KS

i use alternative CD
but why it's different from the others tutorial 
giving the result at the end is OK

meanwhile me not? :(

---

### Post by Rocket2DMn on 2008-02-20
Sounds like your graphics card doesn't really like you yet, but that can be fixed.  They this: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you have more questions, post back with your video card make/model.

---

### Post by jaya28inside on 2008-02-21
i really confused
after installing the Linux Ubuntu
via CD alternatives


it's completed already
and then restarted

but then it appeared nothing
after it comes the boot loader...

dunno why...

some user told me 
it's graphic card problems
...

but the strange is
a few days after that
i trun it on
and i leave it,,, appeared OK suddenly!!!

why it happened like this?

is the last Ubuntu version isnt' stable at all??

coz i'm using normal 
onBoard VGA
it;s Intel Graphic Accelerator 
as usual PC...  :p

---

### Post by jaya28inside on 2008-02-21
> **Rocket2DMn said:**
> Sounds like your graphics card doesn't really like you yet, but that can be fixed.  They this: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
If you have more questions, post back with your video card make/model.

i'll try to finish it tonight... please pray for me... hiks...
why i'm as new - ubuntu user  get some problems like this?? :( sigh

---

### Post by Rocket2DMn on 2008-02-21
You should be selecting the Intel driver during the reconfiguration.  Do you have a second video card in your computer?  If you still can't get it, reconfigure and select the "vesa" driver to get a safe graphics mode login, then show me your xorg.conf file:
```
cat /etc/X11/xorg.conf
```

---

### Post by jaya28inside on 2008-02-22
i bored!!
i choose normal on bootscreen
then it still cant

then i do as they said
CTRL + ALT + F1

and reconfigure the dpkg-reconfigure xserver-xorg
then choose the Vesa graphic
then Ok finished it appeared bad i think!
so i repeat again reconfiguring... but this time i choose
intel
and then OK now!!

no more CANT INITIALIZE HAL!!
but I'm not sure after i restart this Linux Ubuntu

perhaps it doing the same thing again!
can't log into it!!

blank again!
is it BECOZ of MY HARDDISK using Ext3 as the type?
or perhaps it coz I'm using ONBOARD graphic card...??
coz on the BIOS list...it's stated graphic options : PCI, Onboard, and 
i forgot one more AGI or what i forgot...

so why it become like this? sometimes appeared sometimes not??

> 

Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "ctrl:nocaps"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation 82865G Integrated Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection



---

### Post by PmDematagoda on 2008-02-22
Don't try to reconfigure the X-Server over much, just find a good configuration and stick with it. Also the X-Server is not responsible for the HAL start-up failure, the filesystem on the hard drive is also not responsible. 

If you were able to get Ubuntu to boot properly did Ubuntu log in properly and bring you to a working desktop regardless of the HAL error?

---

### Post by jaya28inside on 2008-02-22
it working into the Desktop 
If ONLY AND IF
i using the Normal selection on boot screen 
but then I press
CTRL ALT F1
then Stopping the Xserver
then CONFIGURE again
and then STARTing again the 

sudo /etc/init.d/gdm start

but sometimes...it working 
and sometimes... it just stuck there... on the CLI only...

OMG!!!

---

### Post by PmDematagoda on 2008-02-22
So you mean that Ubuntu boots into the desktop properly if you select "Normal" and just leave it but it goes away when you kill the GUI and reconfigure the X-Server?

---

### Post by jaya28inside on 2008-02-22
yes!
if ONLY i press the CTRL ALT F1
and CONFIGURE it again and again!!

i bored with this!! plzzz give me the path to the truth!!!
i can't do it again2 and again2... just becoz i want to use Ubuntu
so i need to RECONFIGURE each time i turned on my PC!!

---

