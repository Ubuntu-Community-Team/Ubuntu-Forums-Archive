---
title: "ubuntu CD won't install-[FIXED] now HD won't fully boot-[FIXED]"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by Sysco Kid on 2007-06-15
OK I had a problem installing from the liveCD. 

Every time I chose Start or Install ubuntu from the CD, it kept crashing out.
It was searching for the floppy disk, and bombed out to the following error.

> BusyBox v1.1.3(Debian 1:1.1.3-3ubuntu3) Built-inshell(ash)
enter 'help' for a list of built in commands.

/bin/sh:can't access tty; job control turned off


It drove me mad, till I found the solution. (thanks to this good ol' ubunbtu forum)

At the CD boot menu
Press the F6 key and type in 
```
live boot=break
```

This took me to the command line, where I typed in

```
modprobe piix
exit

```

Woohoo!! this booted the CD to the ubuntu desktop. It even found my network card, got itself an IP address from my router, and let me broswe the internet.

Now I chose install ubuntu, and answered all the questions and removed the CD, after what looked like a perfect install.

But my server kept stopping at the following prompt:-
> 
BusyBox v1.1.3(Debian 1:1.1.3-3ubuntu3) Built-inshell(ash)
enter 'help' for a list of built in commands.

/bin/sh:can't access tty; job control turned off


which is the exact same prompt I got when I used the F6 boot option live break=top. And the same cure makes my ubuntu server boot. ie type 

```
modprobe piix
exit

```

After hours, and I mean HOURS reading numerous posts and threads on here, and trying the various suggestions I eventually tried and succeeded in getting good ol' nobooto to ubuntu booto.

After realisng that my server was halting very early on in it's boot process, I looked at what grub was doing. I noticed a line in the grubs menu.lst that was halting the boot process. I have no idea if this is in there by default, or was inserted as part of the install process when I typed in live break=top at the F6 optoins when installing.

But in my menu.lst see the options after splash in the kernel startup line.

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=13c4c864-a37c-41b8-a7e
a-bc7aa1c01b6c ro quiet splash **live break=top**
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault


Anyway I decided to delete all mention of **live break=top**, so I made a backup of the file, and edited it out.

To do so, open up terminal and type

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

This will make a backup of the menu.lst file as used by grub when booting.

Now to edit the file, and replace the string that stops ubuntu fully booting.

```
sudo gedit /boot/grub/menu.lst
```

From the drop down menu, choose Search/Replace
and type in

```
live break=top
```

And do a Replace All

Save the file, exit and type in
```
reboot
```

And voila!!. 

My server now boots ubuntu hands free.

---

### Post by trinaryouroboros on 2007-06-28
Man, I'm so sorry you had so much trouble installing Ubuntu.

I haven't seen this much installation trouble since I installed Red Hat linux back in 1997!

If you don't mind me asking, what kinda hardware you got?

---

