---
title: "Failure to start the X server?"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-05
After installing Ubuntu on my Dell Inspiron E1505 using the text installer because I have an ATI X1400 the Unbuntu Screen came up after saying the computer needed to reboot. After going to the Unbuntu screen with the load bar it goes to a command line interface and then quickly to an error screen saying: 

Failed to start the X server (your graphical interface). It is likely that is it not set up correctly. Would you like to view the X server output to diagnose the problem? 

I checked all the resolutions below 1680 and the output says:

X Window System Version 1.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.1
Build Operating System: Linux Ubuntu
Current Operating System: Linux Mark 2.6.20-15-generic #2 SMP Sun Apr
15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
          Before reportingf problems, check [http://wiki.x.org](http://wiki.x.org)
          to make sure that you have the latest version.
Module Loader Present.
Markers: ( -- ) probed, ( ** ) from config file, (==) default setting,
              (++) from command line, (!!) notice, (II) informational,
              (WW) warning, (EE) error, (NI_ not implemented, (??) ubnknown.
(==) Log File: "/var/log/Xorg.0.log". Time: Thu Jul 5 11:29:57 2007
(==) Using config file: "/etc/X11/xorg.conf"
                                                                        .2
acktrace:                                           tu
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0X80c5d91]                           pr
e: [0xffffe420]                   86
2: /usr/X11R6/bin/X(InitOutput+0x9aa) [0x80a5b9a]
3: /usr/X11R6/bin/X[main+0x27b) [0x807456b]            rg
4: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7db3ebc]
5: /usr/X11R6/bin/X(FontFileCompleteXFLD+0x1e1) [0x8073ab1]
                                                                                                           g,
Fatal server error:                                                                         l,
Caught signal 11. Server Aborting                                                          n.
                                                                                                                07
Y                                                            f"


Then the advanced config file is:


X Window System Version 1.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.1
Build Operating System: Linux Ubuntu
Current Operating System: Linux Mark 2.6.20-15-generic #2 SMP Sun Apr
15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
          Before reportingf problems, check [http://wiki.x.org](http://wiki.x.org)
          to make sure that you have the latest version.
Module Loader Present.
Markers: ( -- ) probed, ( ** ) from config file, (==) default setting,
              (++) from command line, (!!) notice, (II) informational,
              (WW) warning, (EE) error, (NI_ not implemented, (??) ubnknown.
(==) Log File: "/var/log/Xorg.0.log". Time: Thu Jul 5 11:29:57 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen"  (0)
(**) |    |-->Monitor "Generic Monitor"
(**) |    |-->Device "Generic Video Card"         .2
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"                                               pr
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"                                             rg
(**) |-->Input Device "Synaptics Touchpad"                 n.
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
               Entry deleted from path.                                                 g,
(**) FontPath set to:                                                                   l,
             /usr/share/fonts/X11/misc                                                        n.
             /usr/share/fonts/X11/100dpi/ :unscaled                                 07
             /usr/share/fonts/X11/75dpi/ :unscaled,"
             /usr/share/fonts/X11/Type1,
             /usr/share/fonts/X11/100dpi,
             /usr/share/fonts/X11/75dpi,
             /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
             /usr/share/fonts/X11/misc,                                                     pr
             /usr/share/fonts/X11/cyrillic,
             /usr/share/fonts/X11/100dpi/ :unscaled,
             /usr/share/fonts/X11/75dpi/ :unscaled.                     rg
             /usr/share/fonts/X11/Type1,
             /usr/X11R6/lib/X11/fonts/Type1
             /usr/share/fonts/X11/100dpi                                            g,
             /usr/share/fonts/X11/75dpi                                           l,
             /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType                  n.
(==) RgbPath Set to "/etc/X11?rgb"                                                  07
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI Successful (/var/run/acpid.socket)
(II) Loader magic: 0881c92e0
(II) Module ABI Versions:
             X.Org ANSI C Emulation: 0.3
             X.Org Video Driver: 1.1
             X.Org Xinput driver : 0.7                                                        pr
             X.Org Server Extension : 0.3
             X. Org Font Renderer : 0.5
(II) Loader running on lnux                           rg
(II) LoadModule: "pcidata"                        n.
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: verndor= "X.Org Foundation"                    g,
             compiled for 7.2.0, module version = 1.0.0               l,
             ABI class: X.Org Video Driver, Version 1.1                           n.
(++_ Using VT number 7                                                                  07


theres a ton more...and i dont feel if i can type it right now. Down at the bottom though it does say 

(II) VESA(0) : Not unsin built-in mode "1400X1050: (no mode of this name)


Hopefully some of this helps....eagerly awaiting any help.

---

### Post by Happy_Man on 2007-07-05
Ok, keep pressing enter until it drops you to a fullscreen terminal login. Log in, and then enter this command: ```
sudo dpkg-reconfigure xserver-xorg
```

Keep pressing enter until you get to a screen full of drivers. Scroll to select "ati", spacebar to select, keep going until it exits. There will be a screen of resolutions too, select whichever ones that apply there also. After it exits, and you get a prompt, put the command```
sudo /etc/init.d/gdm start
``` in and hope for the best!

---

### Post by jackocleebrown on 2007-07-05
**EDIT: ignore me, either I'm gong mad or Happy_man just edited his post ;)**



Just to add to what Happy_man said, instead of running 

"dpkg-reconfigure xserver-xorg"

you'll need to put "sudo" at the front like this

"sudo dpkg-reconfigure xserver-xorg"

it'll then ask you for your password. If you don't have the sudo then it will tell you "/usr/sbin/dpkg-reconfigure must be run as root"



Jack.

---

### Post by snwbord2456 on 2007-07-05
After doing all that and restarting I still get the "Failed ti start the X server" issue...I looked at the simple server output and it said


(EE) No Devices detected

Fatal server error:
No screens found


What did I do wrong?

---

### Post by snwbord2456 on 2007-07-05
Anything?

---

### Post by jackocleebrown on 2007-07-06
Have a look through the detailed output and just pick out the lines starting with (EE) - I suspect that there is probably another error further up that is resulting in your no screens message. 

Assuming it is still your video card not loading (which does end up giving the error you've now got) try running these commands which should install the fglrx driver for your ati card and then setup your Xserver to use it.

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


After running this reboot and see if it is fixed.

Jack.

---

### Post by alienexplorers on 2007-07-06
How about listing your xorg.conf file.

---

### Post by snwbord2456 on 2007-07-06
Everything is all worked out, there I downloaded the drivers and everything is up and running as it should. Thanks for all your help.

---

### Post by FlowingSnake on 2007-08-21
> **jackocleebrown said:**
> Have a look through the detailed output and just pick out the lines starting with (EE) - I suspect that there is probably another error further up that is resulting in your no screens message. 

Assuming it is still your video card not loading (which does end up giving the error you've now got) try running these commands which should install the fglrx driver for your ati card and then setup your Xserver to use it.

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


After running this reboot and see if it is fixed.

Jack.

now i have the same problem as the OP. And when i run the above commands, at the second line "sudo aticonfig --initial" i get no such command aticonfig

---

### Post by FlowingSnake on 2007-08-23
any ideas

---

### Post by c3genesis on 2007-08-23
I dont know if it makes you feel any better but im having very similar problems. Im gonna see if its the same when i get home and try the friendly advice. Good lúck to you as well

---

### Post by FlowingSnake on 2007-08-23
just to aid any help i may get these are my current system specs:

Memory (RAM): 1023 MB
CPU: AMD Athlon(tm) 64 Processor 3200+
CPU Speed: 1996.8 MHz
Sound card: C-Media Wave Device
Display Adapters: RADEON X550XT | RADEON X550XT Secondary | UltraMon Display Mirror Driver | NetMeeting driver | RDPDD Chained DD
Screen Resolution: 1024 X 768 - 32 bit
: 
Network Adapters: ASUS 802.11b/g Wireless LAN Card - Packet Scheduler Miniport | Marvell Yukon 88E8053 PCI-E Gigabit Ethernet Controller - Packet Scheduler Miniport
CD / DVD Drives: D: TSSTcorpCD/DVDW SH-W162Z | E: SCSIVAX DVD/CD-ROM       | G: CF9535Q OJO400A
: 
COM Ports: 
LPT Ports: 
Mouse: 8 Button Wheel Mouse Present
Hard Disks: C:  74.5GB | F:  149.0GB
Hard Disks - Free: C:  14.4GB | F:  110.2GB
USB Controllers: 5 host controllers.
Firewire (1394): 1 host controllers.
: 
Manufacturer: Phoenix Technologies, LTD
Product Make: A8V-E DELUXE
: 
AC Power Status: OnLine
BIOS Info: ATAT COMPATIBLE  012506  K8T890  42302e31
Time Zone: AUS Eastern Standard Time
Battery: No Battery
Motherboard: ASUSTek Computer INC. A8V-E DELUXE

---

### Post by FlowingSnake on 2007-08-24
Hi still looking for a resolve for this problem.

---

### Post by smo0th on 2007-08-27
I run an old AMD K6-2 450 with a generic PCI trashy video card, my problem was that the card was not able to display the default 24-bit graphic mode LOL.... so here's a recreation of what I did... 

first get into command shell mode and do the "sudo dpkg-reconfigure xserver-xorg" thing...

now type "sudo nano /etc/X11/xorg.conf"

scroll way down to the line where says DefaultDepth      24

I changed it for 16... you may play along with the values there but always keep a backup file before modifying anything.... just in case ;)

c-ya.

---

### Post by comacozi on 2007-08-28
i have the same problem, but when i try to install the drivers, it look in the cd drive, how do i change that?

---

### Post by phoenix96 on 2007-08-29
Oh shits -

I had the same problem with the same computer and same specs. I did it a bit sloppily and now after the Ubuntu splash screen finishes loading it just goes black. I can't find any way to the terminal.

Could somebody possibly guide me through this? Or even more, would anyone like to be a linux sensei for a little while, haha?

---

