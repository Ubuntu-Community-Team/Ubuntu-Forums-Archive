---
title: "Modify kernel to setserial"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-12-29
If you are knowledgeable about mknod, exec, and how to modify the kernel, read on. Others will be wasting their time. For nearly 6 months, I have had a problem with my controller-based hardware-based internal pci modem. It works fine in win98. It works only intermittently in Linux/Ubuntu.

After six months of almost daily struggles to learn what is wrong and fix it myself, I believe I may have come across the fix, which is below. Only problem now is that this article from sys-Linux.org isn't specifically for Debian/Ubuntu, and I'm a newbie, anyway. I probably need to do what the poster below specifies, only I haven't a clue as to how to go about doing it. My Dapper has no /usr/src/linux nor can I "make xconfig". (is that part of make/make install?) So the help I need is how to do what the post quoted below suggests, but in Ubuntu. And I no longer have a Windows partition as a backup. It went bye-bye, w/o a tear, but it is gone forever. So please be knowledgeable about these mods.

Last of the prelims: I have an ActionTec (Lucent Venus chipset) PM560LKi, controller based hardware internal modem. It has a 16550A UART. It is K56 and v.90. So it is fairly modern. WvDial (wvdialconf) sets the modem into the kernel as /dev/ttyS4. Because GnomePPP can only "see" ttyS0,1,2, and 3, GnomePPP won't call my modem. Because of no /dev/modem with appropriate links, I can't use X-isp (alternative to WvDial). So, if you are a skilled programmer, please, fire away at me:

[what follows is a post at another linux forum]


[COLOR="Blue"]Okay, the modem in question is the 3Com/USRobotics 3CP5610 PCI FaxModem.  It is one of the few PCI modems that is controller based, having an on-board 16550AF chip.  It is a K56 flex V.90 modem, which works very well for me.  The greatest problem that people have with this modem is that it installs on COM5 in Win9* and there is no com5 (by default) in linux.

This is where most people have trouble, and the way to get it to work is this:

1.  You need to configure your kernel to support more than 4 serial ports.  In /usr/src/linux, do a make xconfig and in the character devices setup, turn on (mark 'y') the "Extended dumb serial driver options" and turn on the "Support for more than 4 serial ports".  Then do a make bzImage and install the kernel (or whatever you do for the normal kernel make - if you have specific questions see the Kernel HOW-TO).
 
2.  Create the device file in /dev - namely /dev/ttyS4:  do this by

mknod -m 0640 /dev/ttyS4 c 4 68
ln -s /dev/ttyS4 /dev/modem

3.  In your /etc/rc.d/rc.local file, add the following line:

exec setserial /dev/ttyS4 irq ?? port 0x??? ^fourport
        ^auto_irq skip_test autoconfig spd_vhi

This sets up the device where you should replace the '?' with the correct values for your system.  These values can be found in the /proc/pci file, or you can get them from the windows system/hardware config info.

Reboot.  Point your kppp setup at /dev/modem, and everything should work.  It's important to include the ^fourport and skip_test in the setserial.  Otherwise, the kernel thinks that you have a serial expansion card installed, and the set-up will fail.
[/COLOR]

---

### Post by kinematic on 2006-12-29
seems pretty straitforward.
do a search for linux-source in synaptic and install the kernel source code for the kernel you want.
cd to the /usr/src/linux-whatever directory after installation and follow the instructions(you have to create the file in /dev as root,the make xconfig you can do as user but you have to build and install the kernel as root).
[http://www.ubuntuforums.org/showthread.php?t=56835&highlight=kernel+compilation+howto](http://www.ubuntuforums.org/showthread.php?t=56835&highlight=kernel+compilation+howto)

---

### Post by Mark_in_Hollywood on 2006-12-29
HuH?

I have a kernel, I think.

Please, I'm not computer literate. I can follow detailed instructions, but not what you are suggesting, because:

cd /usr/src

ls

returns:

RPM

---

### Post by tuxcantfly on 2006-12-29
You have a kernel, but not the source. Do this:

sudo apt-get update
sudo apt-get install linux-source

---

### Post by semetay on 2007-02-12
Hello,

I have a very similar problem on my ubuntu x86_64 edgy. I have a pci hardware modem which works fine under xp (irq 17). when I do lspci -vv I see that it is on irq 5. It has been months I have been trying to make this work. setserial seems to work but KPPP tells the modem is busy. I think this is because of the reason that you have mentioned as linux doesnt have irq devices more than 4.

so as you found somewhere else, this could be the solution. I am a newbie as well so I hope someone can translate this direcyions for ubuntu.

thanks...

semetay

---

