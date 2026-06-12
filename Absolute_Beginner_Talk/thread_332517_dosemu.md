---
title: "dosemu"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2007-01-06
I have installed dosemu, and dosemu-freedos
```

sudo apt-get install dosemu
sudo apt-get install dosemu-freedos

```
I have configured my glx properly.

This is the error message i get when i try to run "xdosemu"
```

sasa@Kanta:~/Games$ xdosemu

   You do not have the DOSEMU vga font installed and are running
   remote X. You need to install the vga font on your _local_ Xserver.
   Look at the readme for details. For now we start with an fixed font,
   which does not display all national characters correctly.
   ... be warned

The Linux DOSEMU, Copyright (C) 2003 the 'DOSEMU-Development-Team'.
This program is  distributed  in  the  hope that it will be useful,
but  WITHOUT  ANY  WARRANTY;   without even the implied warranty of
MERCHANTABILITY  or  FITNESS FOR A PARTICULAR PURPOSE. See the file
/usr/share/doc/dosemu/copyright for more details.  Use this program
at your own risk!

By continuing execution of this program,  you  are stating that you
have read the file /usr/share/doc/dosemu/copyright and the above
liability disclaimer and that you accept these conditions.

Enter 'yes' to confirm/continue: yes
ERROR: Unable to open console to evaluate the keyboard map.
Please specify your keyboard map explicitly via the $_layout option
sasa@Kanta:~/Games$ sudo apt-get install dosemu-freedos
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  dosemu-freedos
0 upgraded, 1 newly installed, 0 to remove and 90 not upgraded.
Need to get 0B/777kB of archives.
After unpacking 2060kB of additional disk space will be used.
Selecting previously deselected package dosemu-freedos.
(Reading database ... 93326 files and directories currently installed.)
Unpacking dosemu-freedos (from .../dosemu-freedos_b8p-4_i386.deb) ...
Setting up dosemu-freedos (b8p-4) ...
sasa@Kanta:~/Games$ xdosemu

   You do not have the DOSEMU vga font installed and are running
   remote X. You need to install the vga font on your _local_ Xserver.
   Look at the readme for details. For now we start with an fixed font,
   which does not display all national characters correctly.
   ... be warned

ERROR: Unable to open console to evaluate the keyboard map.
Please specify your keyboard map explicitly via the $_layout option
ERROR: cpu exception in dosemu code outside of VM86()!
trapno: 0x0e  errorcode: 0x00000004  cr2: 0x468a5b2d
eip: 0x468a5b2d  esp: 0xbf7fffb5  eflags: 0x00010282
cs: 0x0073  ds: 0x007b  es: 0x007b  ss: 0x007b
Page fault: read instruction to linear address: 0x468a5b2d
CPU was in user mode
Exception was caused by non-available page
ERROR: Fault handler re-entered! signal=11 _trapno=0xE
ERROR: cpu exception in dosemu code outside of VM86()!
trapno: 0x0e  errorcode: 0x00000004  cr2: 0x468a5b23
eip: 0x0807d350  esp: 0x0840a2c0  eflags: 0x00010202
cs: 0x0073  ds: 0x007b  es: 0x007b  ss: 0x007b
Page fault: read instruction to linear address: 0x468a5b23
CPU was in user mode
Exception was caused by non-available page
sasa@Kanta:~/Games$ 

```

what am i doing wrong ? ](*,)

---

### Post by energiya on 2007-01-06
It's not you... it's the command.com used by dosemu. I replaced it with another (i have the archieve on my HDD), but I can't remeber where I got it from... I think  [http://freedos.sourceforge.net/freecom](http://freedos.sourceforge.net/freecom)

---

### Post by Majlo on 2007-01-06
Hi 

I don`t use dosemu but i think better choice is dosbox . Just type 

sudo apt-get install dosbox

And enjoy :-)

---

### Post by energiya on 2007-01-06
> **Majlo said:**
> Hi 

I don`t use dosemu but i think better choice is dosbox . Just type 

sudo apt-get install dosbox

And enjoy :-)

I used both... I like dosemu best becouse it uses less CPU power and can run in Ctrl+Alt+F1 terminal (dosbox can't).

Sasa_Ivanovic, I found it at [sourceforge]("http://freedos.sourceforge.net/freecom/packages/082pl3/xmsswap.zip"). Download it and replace /usr/lib/dosemu/commands/comcom.com with this one (rename command.com to comcom.com). That its what I did to get it working...

EDIT

And try installing the xfonts-dosemu package (if you don't have it)
```
sudo aptitude install xfonts-dosemu
```

---

### Post by Sasa_Ivanovic on 2007-01-06
thanks for the help energiya. i'll try that out now...

PS : i don't use DosBox 'cause it's slooooow.

---

### Post by Sasa_Ivanovic on 2007-01-06
it works, thanks!

---

### Post by Sasa_Ivanovic on 2007-01-06
the time is passing too fast, how can i fix that ?

---

### Post by energiya on 2007-01-06
Glad to help!

---

### Post by energiya on 2007-01-06
> **Sasa_Ivanovic said:**
> the time is passing too fast, how can i fix that ?

found these:
[http://www.mail-archive.com/linux-msdos@vger.kernel.org/msg04139.html]("http://www.mail-archive.com/linux-msdos@vger.kernel.org/msg04139.html")
[http://www.faqs.org/docs/Linux-HOWTO/DOSEMU-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/DOSEMU-HOWTO.html")
[http://dosemu.sourceforge.net/docs/README-tech/1.2/pentium.html]("http://dosemu.sourceforge.net/docs/README-tech/1.2/pentium.html")

but nothing about slowing down... sorry

---

### Post by derjames on 2007-01-06
just FYI
I have QEMU + FreeDOS and it is working just fine... I could also transfer my old DOS files, DOOM and DOOM2 included!!
(QEMU from Synaptic and FreeDOS from [www.freedos.org](www.freedos.org))
...

---

### Post by fakie_flip on 2007-05-02
> **Majlo said:**
> Hi 

I don`t use dosemu but i think better choice is dosbox . Just type 

sudo apt-get install dosbox

And enjoy :-)

Why do you believe dosbox is a better choice? What are the differences between dosbox and dosemu?

I just tried dosbox and was still unable to get my games to work. Before that, I had tried Cedega, Wine from the Ubuntu repos and the newest Wine from the official Wine repos.

---

