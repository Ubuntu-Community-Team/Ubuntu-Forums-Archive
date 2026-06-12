---
title: "GRUB not showing Windows XP..."
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by JoshCrumley100 on 2007-10-21
I have been dualbooting Windows XP and Ubuntu for a while now without any problems. Today, while in ubuntu, i decided to go ahead and upgrade to 7.01 or whatever from 6.2 or something...(noob here!). when it finished installing, and it restarted, GRUB no longer had my Windows XP entry. It only had a bunch of Ubuntu listings.  In addition, Ubuntu doesn't load either. It goes to a black screen with the busy mouse icon, and just does nothing.  I REALLY need to boot into Windows, but i have no idea how to add it back to the list without going into linux and editing the menu.lst file.  anyone have any suggestions?


**ADDED**

I just figured out how to boot to windows using the command-line, with root (hd0,0) and all that stuff. It wont boot windows in normal mode though, only safe mode (which might be windows, i've been having problems with it lately). but i still want to be able to just select it, not type it every single time i want to boot windows. thanks!

---

### Post by Pumalite on 2007-10-21
At the Blank screen:
Ctrl+Alt+F1 to get command line
sudo dpkg-reconfigure xserver-xorg, accept most defaults, choose 'vesa' as the driver, then: startx
Get back to me after you are IN the system and will fix your menu.lst

---

### Post by JoshCrumley100 on 2007-10-21
woah...lol, ok i did all that, and it says after i typed startx "fatal server error: Server is already active for display 0......If this server is no longer running, remove /tmp/.X0-lock and start again.

then it goes on and says 

Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key...giving up.
xinit: unable to connect to X server
xinit: No such process (errno 3): Server error.

then it goes back to the terminal prompt. i may have done something wrong...but all i did was press enter and stuff over and over, i assume i selected all the defaults...

---

### Post by Pumalite on 2007-10-21
Do the same, but first do this:
sudo /etc/init.d/gdm stop
Then continue with sudo dpkg...etc

---

### Post by JoshCrumley100 on 2007-10-21
well, idk what in the world i just did, but its in ubuntu now. should i open the menu.lst file and change it now? if so, what do i change?

---

### Post by Maestro23 on 2007-10-21
> **JoshCrumley100 said:**
> well, idk what in the world i just did, but its in ubuntu now. should i open the menu.lst file and change it now? if so, what do i change?

Post the contents of the following command:

> cat /boot/grub/menu.lst (lower case L)


---

### Post by JoshCrumley100 on 2007-10-21
> **Maestro23 said:**
> Post the contents of the following command:

umm....what? im in linux, i typed that in a terminal and it just displays the menu.lst file, i have it open already....**head hurts**

---

### Post by Maestro23 on 2007-10-21
> **JoshCrumley100 said:**
> umm....what? im in linux, i typed that in a terminal and it just displays the menu.lst file, i have it open already....**head hurts**

Copy and paste the file so we can see what it looks like.  Use your mouse to highlight the text.

To edit it, you are going to use gedit.

---

### Post by JoshCrumley100 on 2007-10-21
ok, here it is:


title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=370b5264-af48-4a0a-95b0-f57be1a11a5d ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=370b5264-af48-4a0a-95b0-f57be1a11a5d ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.17-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=370b5264-af48-4a0a-95b0-f57be1a11a5d ro quiet splash
initrd		/boot/initrd.img-2.6.17-12-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-12-generic root=UUID=370b5264-af48-4a0a-95b0-f57be1a11a5d ro single
initrd		/boot/initrd.img-2.6.17-12-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=370b5264-af48-4a0a-95b0-f57be1a11a5d ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=370b5264-af48-4a0a-95b0-f57be1a11a5d ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


I assume thats the only part of the file you need.

**ADDED**

HELLO?? is there anyone there? i need this soon please! thanks!

---

### Post by capo327 on 2007-10-21
Add this:

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

---

### Post by Maestro23 on 2007-10-21
> **capo327 said:**
> Add this:

title		Windows XP
root		(hd0,0)
makeactive
chainloader	+1

Beat me to it.

---

### Post by JoshCrumley100 on 2007-10-21
ok thanks alot. will linux load too?

---

### Post by JoshCrumley100 on 2007-10-21
> **Maestro23 said:**
> Beat me to it.

lol, yea. thanks to you too! :)

---

### Post by capo327 on 2007-10-21
> **JoshCrumley100 said:**
> ok thanks alot. will linux load too?

Yeah, when you add that line to the menu.lst file, grub allows you to choose to boot Windows or Ubuntu when you start up the computer.

---

