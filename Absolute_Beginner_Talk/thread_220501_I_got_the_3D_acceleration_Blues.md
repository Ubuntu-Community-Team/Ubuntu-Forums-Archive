---
title: "I got the 3D acceleration Blues"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by rene100 on 2006-07-21
I have a mobility radeon 9000, and I downloaded the fglrx 8.26.18 drivers and followed all the steps in this thread: [http://ubuntuforums.org/showthread.php?t=204910](http://ubuntuforums.org/showthread.php?t=204910)

But when I run the fglrxinfo my output is :

OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

When I check my xorg.conf file, I noticed this:

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"

Should I attempt to set OpenGLOveray to "on" or is that dangerous?

I know my 3d acceleration isn't working because I tested it with glxgears -printfps command

Please help

---

### Post by Paerez on 2006-07-21
you need to patch your libGL.so.1.2

find the ati file, and do:
```
./ati-driver-installer-8.26.18-x86.run --extract ati_26
```
Then search in there for the file "libGL.so.1.2". Then copy that file into "/usr/lib". Make a backup of "/usr/lib/libGL.so.1.2" before you overwrite it!

---

### Post by rene100 on 2006-07-21
I did that, backed up the file and replaced it with the new one, and I'm still not getting 3d acceleration

rene@rene-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


and glxgears is still slow :(

Should I change the opengl flag in the xorg.conf file?

---

### Post by Paerez on 2006-07-21
no, you don't need to. Did you restart your x server? Log out and press CTRL+ALT+BACKSPACE then log back in and check. Also, what does this output:
```
lsmod | grep fglrx
```

---

### Post by rene100 on 2006-07-21
I rebooted my whole system after the change

lsmod | grep fglrx

The command produces no output

---

### Post by Paerez on 2006-07-21
bingo! that means that your fglrx module is not being loaded.

Add "fglrx" to the end of "/etc/modules" so that it is loaded on every boot. To load it now, just type "sudo modprobe fglrx" then restart your x server (don't need to restart the whole comp, just the backspace trick at login).

---

### Post by adam.tropics on 2006-07-21
> **rene100 said:**
> I rebooted my whole system after the change

lsmod | grep fglrx

The command produces no output

Have a read through [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_8.26.18_drivers_in_Ubuntu_Dapper_Manually) and see how it differs, as I know that guide actually works.

---

### Post by rene100 on 2006-07-21
"sudo modprobe fglrx" produces this output:

FATAL: Error inserting fglrx (/lib/modules/2.6.15-26-686/volatile/fglrx.ko): Operation not permitted

---

### Post by Paerez on 2006-07-21
That guide doesn't work for me. I also have a 9000 mobility. I had to patch over my libgl. Plus, he is having a module loading problem, which that guide does not address.

---

### Post by Paerez on 2006-07-21
OK, now you have to do something which is really gross, and you have to do it on every boot:
```
cd /lib/modules/2.6.15-26-686/volatile/
sudo ln -sf ../misc/fglrx.ko fglrx.ko
sudo modprobe fglrx
```
then restart your x server.

---

### Post by rene100 on 2006-07-21
the last command produces:

FATAL: Could not open '/lib/modules/2.6.15-26-686/volatile/fglrx.ko': No such file or directory

when I do a LS i see it listed in the output but it's in a black square with red text (as opposed to everything else which is on a white background in black text)

---

### Post by Paerez on 2006-07-21
ok can you give me a:
```
ls /lib/modules/2.6.15-26-686/
ls /lib/modules/2.6.15-26-686/misc
```

---

### Post by rene100 on 2006-07-21
rene@rene-laptop:~$ ls /lib/modules/2.6.15-26-686/
initrd      modules.alias        modules.inputmap   modules.seriomap
kernel      modules.ccwmap       modules.isapnpmap  modules.symbols
madwifi     modules.dep          modules.ofmap      modules.usbmap
madwifi-ng  modules.ieee1394map  modules.pcimap     volatile

rene@rene-laptop:~$ ls /lib/modules/2.6.15-26-686/misc
ls: /lib/modules/2.6.15-26-686/misc: No such file or directory

---

### Post by Paerez on 2006-07-21
hmm, you don't seem to have the fglrx module. Lets do a search:
```
sudo find /lib/modules/ -name 'fglrx.ko'
```

---

### Post by rene100 on 2006-07-21
/lib/modules/2.6.15-23-686/misc/fglrx.ko
/lib/modules/2.6.15-26-686/volatile/fglrx.ko

---

### Post by Paerez on 2006-07-21
ok so it installed the module to the wrong kernel. Try this:
```
cd /lib/modules/2.6.15-26-686/volatile/
ln -sf /lib/modules/2.6.15-23-686/misc/fglrx.ko fglrx.ko
sudo modprobe fglrx
```

---

### Post by rene100 on 2006-07-21
here are my outputs

rene@rene-laptop:/lib/modules/2.6.15-26-686/volatile$ ln -sf /lib/modules/2.6.15-23-686/misc/fglrx.ko fglrx.ko
ln: cannot remove `fglrx.ko': Permission denied
rene@rene-laptop:/lib/modules/2.6.15-26-686/volatile$ sudo ln -sf /lib/modules/2.6.15-23-686/misc/fglrx.ko fglrx.ko
rene@rene-laptop:/lib/modules/2.6.15-26-686/volatile$ sudo modprobe fglrx rene@rene-laptop:/lib/modules/2.6.15-26-686/volatile$

I didn't get any output from the commands

---

### Post by Paerez on 2006-07-21
ok good. I think its in. Try:
```
lsmod | grep fglrx
```
if you see fglrx, its in!
Then restart your xserver and check fglrxinfo and glxgears.

---

### Post by rene100 on 2006-07-21
rene@rene-laptop:/lib/modules/2.6.15-26-686/volatile$ lsmod | grep fglrx
fglrx                 391756  0
agpgart                36784  2 fglrx,intel_agp


looks promising :)  now i'll reboot gui

---

### Post by rene100 on 2006-07-21
logged out, hit control-alt-backspace and screen went black..... never came back :(

I think i need to do a hard-reboot but doesn't that mess up the file system?

---

### Post by rene100 on 2006-07-21
ps.  I'm on a windows computer the in other room now

---

### Post by Paerez on 2006-07-21
since you logged out and everything don't worry about the file system, it will do a scan and it will be fine. At this point, I don't know anything else you can do, sorry. What I have explained is my method for getting fglrx. I would suggest using the radeon driver from xorg to get dri working.

I am gonna be offline for the rest of the day starting in about 15 minutes, so I won't be able to respond to posts for a little while.

good luck

---

### Post by rene100 on 2006-07-21
Will do.  

Thanks for all your time and help with this, I really appreciate it :)

This community rocks

-Rene

---

### Post by rene100 on 2006-07-21
In case any one else out there thinks they can help, I get a new output from fglrxinfo:

Xlib:  extension "XFree86-DRI" missing on display ":0.0".
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

---

