---
title: "Grub Gui1?1"
date: 2005-12-31
forum: Absolute Beginner Talk
---

### Post by Jaygo333 on 2005-12-31
How Do you make grub GUI. A gui taht there are only two sides. Windows and Ubuntu. 

Also, at startup, at the grub menu, How do I also limit it to two choices and make windows the default chosen OS.

How do I also reinstall GRUB. I get a funny message at startup and want it gone and I think reistalling grub will help.

:arrow:h34r: Jaygo333 :arrow:h34r:

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=Jaygo333]How Do you make grub GUI. A gui taht there are only two sides. Windows and Ubuntu. 

Also, at startup, at the grub menu, How do I also limit it to two choices and make windows the default chosen OS.

How do I also reinstall GRUB. I get a funny message at startup and want it gone and I think reistalling grub will help.

:arrow:h34r: Jaygo333 :arrow:h34r:[/QUOTE]
There is a file called /boot/grub/menu.lst that lets you change the options.  There should be an option called "default" that is normally 0.  If you count down to the "Windows" option, you can change the default to that.

Be careful about removing various kernels.  Try removing just one old entry first, and make sure you back up the file and have a LiveCD handy in case you need to recover.

You can probably get grub to reconfigure itself with
```

$ sudo dpkg-reconfigure grub

```

---

### Post by Jaygo333 on 2005-12-31
[QUOTE=cwaldbieser]There is a file called /boot/grub/menu.lst that lets you change the options.  There should be an option called "default" that is normally 0.  If you count down to the "Windows" option, you can change the default to that.

Be careful about removing various kernels.  Try removing just one old entry first, and make sure you back up the file and have a LiveCD handy in case you need to recover.

You can probably get grub to reconfigure itself with
```

$ sudo dpkg-reconfigure grub

```[/QUOTE]


What do you mean by getting Grub to reconfigure itself. I typed the command and nothing happened. A little more explanation plaes.

I also typed the commands above to enter Grub list and get
jaygo333@Ubuntu:~$ /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied
I then enter sudo and get:
jaygo333@Ubuntu:~$ sudo /boot/grub/menu.lst
Password:
sudo: /boot/grub/menu.lst: command not found
jaygo333@Ubuntu:~$ /boot/grub/menu.lst
Any help Please.

:arrow:h34r: Jaygo333 :arrow:h34r:

---

### Post by Bananas21ca on 2005-12-31
Try this to open the Grub list:

sudo gedit /boot/grub/menu.lst

That should work. Just always remember to use gedit when opening config files.

---

### Post by cwaldbieser on 2005-12-31
[QUOTE=Jaygo333]What do you mean by getting Grub to reconfigure itself. I typed the command and nothing happened. A little more explanation plaes.

I also typed the commands above to enter Grub list and get
jaygo333@Ubuntu:~$ /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied
I then enter sudo and get:
jaygo333@Ubuntu:~$ sudo /boot/grub/menu.lst
Password:
sudo: /boot/grub/menu.lst: command not found
jaygo333@Ubuntu:~$ /boot/grub/menu.lst
Any help Please.

:arrow:h34r: Jaygo333 :arrow:h34r:[/QUOTE]

Sorry, as Bananas21ca pointed out, you need to edit the config file.

The "dpkg-reconfigure" command re-runs the configuration scripts for a package that were run when the package was first installed.  For some packages, there might not be any initial configuration, so nothing will happen.  Others might prompt you for info, etc.  It seems that grub doesn't really have any special setup.

---

### Post by micjustmic on 2005-12-31
If I might interject . . .

Instead of totally editing out the choices you don't want to appear in the menu, simply make them remarks (add # to the front of the line).  

This way if you remove something you later want/need, you can simply remove the remark tag and all is back the way it was.

Mic

---

### Post by kingsidy on 2006-01-01
micjustmic gave a good advice. instead of deleting it just put the # sign in front of the line just in case. I did mine that way after i installed a new kernel. it is the best way to remove unwanted menu items

---

### Post by Jaygo333 on 2006-01-02
[QUOTE=kingsidy]micjustmic gave a good advice. instead of deleting it just put the # sign in front of the line just in case. I did mine that way after i installed a new kernel. it is the best way to remove unwanted menu items[/QUOTE]

Where do you add it, At the title entry or where. 
Here is an example of boot options, where do I add it:

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

Show by adding it in the right place. I want to hide windows, some times. Where do I put it for the one in windows.

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Show also by putting it in the right place.

:confused:h34r: Jaygo333 :confused:h34r:

---

### Post by kingsidy on 2006-01-02
you add it at the beginning of a line like > # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
#title Microsoft Windows XP Professional
#root (hd0,0)
#savedefault
#makeactive
#chainloader +1 for example would hide windows xp from the grub menu

---

### Post by Jaygo333 on 2006-01-02
[QUOTE=kingsidy]you add it at the beginning of a line like  for example would hide windows xp from the grub menu[/QUOTE]

It Worked. Thanks.
Just one other thing. What's the difference between:
Ubuntu, kernel 2.6.12-10-386           and
Ubuntu, kernel 2.6.12-9-386

They are both on the boot menu and I don't see the difference. 
Also, What's 
Ubuntu, memtest86+

I see it on the boot menu and don't know what it is.

:\\:D/:h34r: Jaygo333 :\\:D/:h34r:

---

### Post by micjustmic on 2006-01-02
"memtest" is exactly what the name implies, it's a memory test program that runs on a limited kernel, giving a more complete test than you could normally.

The different kernels you see are the one that came with Ubuntu (kernel 2.6.12-9-386), and the latest upgrade kernel (2.6.12-10-386).

Each major revision of a kernel will go though a few, if not several minor revisions, mainly bug fixes and security fixes.  

You won't 'see' any differences, especially working in a GUI, just know that when you see a kernel update, download it, install it, then re-install whatever drivers you need to re-install.  Usually graphics drivers and the like.
Over all you'll be happier knowing that whatever leaks/bugs were there before, have been reduced thanks to the updated kernel.

Once you're sure everything is working with the new kernel, you can either keep or remove the older one.  I like to keep one older kernel installed, that way if something goes wrong with the one I'm currently working in I can simply load the older one, do what I have to do, and at my convience figure out what's wrong with the newer kernel.

Mic

---

### Post by Jaygo333 on 2006-01-02
[QUOTE=micjustmic]"memtest" is exactly what the name implies, it's a memory test program that runs on a limited kernel, giving a more complete test than you could normally.

The different kernels you see are the one that came with Ubuntu (kernel 2.6.12-9-386), and the latest upgrade kernel (2.6.12-10-386).

Each major revision of a kernel will go though a few, if not several minor revisions, mainly bug fixes and security fixes.  

You won't 'see' any differences, especially working in a GUI, just know that when you see a kernel update, download it, install it, then re-install whatever drivers you need to re-install.  Usually graphics drivers and the like.
Over all you'll be happier knowing that whatever leaks/bugs were there before, have been reduced thanks to the updated kernel.

Once you're sure everything is working with the new kernel, you can either keep or remove the older one.  I like to keep one older kernel installed, that way if something goes wrong with the one I'm currently working in I can simply load the older one, do what I have to do, and at my convience figure out what's wrong with the newer kernel.

Mic[/QUOTE]

Thanks Man.Explained a lot.
But I've never had any major upgrades. I just installed Ubuntu Breezy and they were there. Anyway Thanks for the explanation.

:D:h34r: Jaygo333 :D:h34r:

---

### Post by kingsidy on 2006-01-02
i think that linux kernel 2.6.12.10 is an update of 2.6.12.9, usually a higher number means that the kernel is newer and prolly supports more hardware

---

### Post by micjustmic on 2006-01-02
Kernel 2.6.12-9-386 is what comes on the Breezy CD.  I JUST downloaded and installed it a couple of days ago (the CD) and that's the kernel that was installed.  

I had to update via the Internet to kernel 2.6.12-10-386 (and then again to kernel 2.6.12-10-686-smp, my fault for not paying attention.  :rolleyes: )

If you let the Update Manager (that little icon in the notification area that lets you know when there are updates) do an update for you, that's where the new kernel came from.

Unless there are disks out there with the 2.6.12-10-386 kernel on it already (don't think so) you had to have let it update.  It sounds like a major update, (and it is) but it's pretty painless using apt or the Update Manager GUI (which is just a pretty face for apt anyway) since it handles everything for you, you just reboot when it's done.

They don't ship with two versions of the kernel, there's simply no reason too, and it wastes space on the CD.  If you look in /boot/grub/menu.list you'll see that even the "recovery mode" is simply the same as the kernel listed above it, it simply loads the same kernel image in single user mode.

Mic

---

