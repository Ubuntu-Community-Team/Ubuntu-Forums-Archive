---
title: "Ubuntu progress bar not showing up"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by fetisha on 2008-04-03
This might be a trivial problem which doesn't effect my computer whatsoever, but you know that Ubuntu progress bar that's supposed to show up after then grub loads? Well, It's not showing up on my laptop. I have a dell Inspiron 1521 laptop and It would be nice to get it to show up. Any ideas as to how to make it work?

---

### Post by AdrianStrays on 2008-04-03
I was just about to ask about that! I have an Inspiron as well.  I dual boot, grub loads, I select Ubuntu, and then there is a black screen until I get to the log in screen.

---

### Post by Shazaam on 2008-04-03
Just a guess so try this........
Edit grub and change this.....
```
kernel		/boot/vmlinuz-(your kernel) ro quiet
```
to this.......
```
kernel		/boot/vmlinuz-(your kernel) ro quiet splash
```
From what I have read on the forums here some pc's need the splash screen disabled to be able to boot Ubuntu so make sure you back up menu.lst first so if your pc won't boot you will be able to restore the original one with the live cd.

---

### Post by AdrianStrays on 2008-04-03
Whats the command to edit grub?

---

### Post by Shazaam on 2008-04-03
This one.....
```
gksudo gedit /boot/grub/menu.lst
```
(small L)
You will probably see some authentication errors in terminal; AFAIK it's ok to ignore them.

---

### Post by fiestytom on 2008-04-03
log in as root and go to /boot/grub and edit the menu.lst file to suit your needs...

USE CAUTION when editing this!!!!

---

### Post by Dazed_75 on 2008-04-03
> **Shazaam said:**
> Just a guess so try this........
Edit grub and change this.....
```
kernel		/boot/vmlinuz-(your kernel) ro quiet
```
to this.......
```
kernel		/boot/vmlinuz-(your kernel) ro quiet splash
```
From what I have read on the forums here some pc's need the splash screen disabled to be able to boot Ubuntu so make sure you back up menu.lst first so if your pc won't boot you will be able to restore the original one with the live cd.

1) Actually, I prefer to dump the "quiet" and leave the "splash" which gives sort of the best of both worlds by showing you enough to see that something is actually happening, WHAT is happening, and IF something goes wrong, may give you a clue what it was.  The only reason I leave the splash is that it does look a bit more friendly when a visitor sees my system boot.

2) One of the respondents showed the command for editing the menu.lst file but forgot to remind the user that they should also run "sudo grub-update" afterward for the change to be effective right away.

---

### Post by fetisha on 2008-04-03
> **Shazaam said:**
> Just a guess so try this........
Edit grub and change this.....
```
kernel		/boot/vmlinuz-(your kernel) ro quiet
```
to this.......
```
kernel		/boot/vmlinuz-(your kernel) ro quiet splash
```
From what I have read on the forums here some pc's need the splash screen disabled to be able to boot Ubuntu so make sure you back up menu.lst first so if your pc won't boot you will be able to restore the original one with the live cd.

How would I go about editing grub? Would I put kernel		/boot/vmlinuz-(your kernel) ro quiet splash in the terminal? And where it says (your kernel) how would I know what to put in? As for backing it up, I assume that opens up a file I can save a copy of on my computer, right?

---

### Post by fetisha on 2008-04-03
> **Dazed_75 said:**
> 1) Actually, I prefer to dump the "quiet" and leave the "splash" which gives sort of the best of both worlds by showing you enough to see that something is actually happening, WHAT is happening, and IF something goes wrong, may give you a clue what it was.  The only reason I leave the splash is that it does look a bit more friendly when a visitor sees my system boot.

2) One of the respondents showed the command for editing the menu.lst file but forgot to remind the user that they should also run "sudo grub-update" afterward for the change to be effective right away.

It was already set to quiet splah, so i tried just splash and it started up with a bunch of text that quickly dissappeared but no progress bar :(

and the sudo grub-update command didn't work in the terminal

---

### Post by fetisha on 2008-04-03
I have now tried it as
```
kernel		/boot/vmlinuz-(your kernel) ro quiet splash
```
and
```
kernel		/boot/vmlinuz-(your kernel) ro quiet
```
and
```
kernel		/boot/vmlinuz-(your kernel) ro splash
```

with no success.

---

### Post by AdrianStrays on 2008-04-03
This what mine says:

title		Ubuntu 7.10, kernel 2.6.22-14-rt
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-rt root=UUID=7df400b0-818c-4331-a094-cfa4ab7e161d ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-rt
quiet

---

### Post by fetisha on 2008-04-04
*bump*

---

### Post by drascus on 2008-04-04
your problem seems to be related to this bug in launchpad. there are several solutions to the issue posted there one of them should work for you. [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/136582](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/136582)

---

### Post by drascus on 2008-04-04
I have solved a similar issue with a different computer using this method

1) Change the resolution in /etc/usplash.conf to 1024x768
in terminal type: sudo gedit /etc/usplash.conf     
2) Add vga=791 to the kernel line in /etc/boot/menu.lst "this step I find unnecessary at least in the case I worked on" 

3) sudo update-initramfs -u -k `uname -r`
After step three reboot and see if it helps.

---

### Post by AdrianStrays on 2008-04-04
drascus' solution worked for me, although I didn't need the vga line, and just updated the theme rather than that int whatever thing.

Actually, the splash screen seemed kind of....stretched to me.  What are the other screen sizes?

---

### Post by joshrobinson on 2008-04-04
```
sudo gedit /boot/grub/menu.lst
```

towards the bottom you will see a section that resembles the following, just note im running hardy with a different kernel, so just look for a similar section

```


title		Ubuntu hardy (development branch), kernel 2.6.24-12-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-12-generic root=UUID=af922c34-f5fe-41b4-a6c3-925b0b1fb558 ro quiet splash
initrd		/boot/initrd.img-2.6.24-12-generic
quiet

```
make sure it says splash like mine does
then

```


sudo gedit /etc/usplash.conf

```
and input your resolution
then run this command
```


sudo update-usplash-theme usplash-theme-ubuntu

```


> **AdrianStrays said:**
> drascus' solution worked for me, although I didn't need the vga line, and just updated the theme rather than that int whatever thing.

Actually, the splash screen seemed kind of....stretched to me.  What are the other screen sizes?

input your resolution, it should work fine

---

### Post by fetisha on 2008-04-04
> **drascus said:**
> I have solved a similar issue with a different computer using this method

1) Change the resolution in /etc/usplash.conf to 1024x768
in terminal type: sudo gedit /etc/usplash.conf     
2) Add vga=791 to the kernel line in /etc/boot/menu.lst "this step I find unnecessary at least in the case I worked on" 

3) sudo update-initramfs -u -k `uname -r`
After step three reboot and see if it helps.

Did that without adding vga=791 and when i shut down i saw the progress bar, but when my computer started up, after grub load, it says:
kernel panic - not synching: VFS: Unable to mount root fs on unknown-block(0,0)

---

### Post by fetisha on 2008-04-04
> **drascus said:**
> I have solved a similar issue with a different computer using this method

1) Change the resolution in /etc/usplash.conf to 1024x768
in terminal type: sudo gedit /etc/usplash.conf     
2) Add vga=791 to the kernel line in /etc/boot/menu.lst "this step I find unnecessary at least in the case I worked on" 

3) sudo update-initramfs -u -k `uname -r`
After step three reboot and see if it helps.

Should I try it and do the add vga=791 to see if it works? I'm a little hesitant because last time it messed up my computer and i had to reinstall everything...

---

### Post by bubba_169 on 2008-04-04
If you prefer a GUI to do this with install startup-manager from synaptic then you can use this to change the resolution to 1024x768. Once installed its under system->administration->startup-manager...

---

### Post by fetisha on 2008-04-04
> **bubba_169 said:**
> If you prefer a GUI to do this with install startup-manager from synaptic then you can use this to change the resolution to 1024x768. Once installed its under system->administration->startup-manager...

I'm going to try that now

---

### Post by fetisha on 2008-04-04
> **bubba_169 said:**
> If you prefer a GUI to do this with install startup-manager from synaptic then you can use this to change the resolution to 1024x768. Once installed its under system->administration->startup-manager...

Amazing. It looked funny in color, but that was because it was set to 6 bit, and i changed it to 16. Now it is perfect. Thank you.

---

### Post by NZJon on 2008-06-25
Hi there.
[URL="http://ubuntuforums.org/showpost.php?p=4649062&postcount=16"]
joshrobinson's solution[/URL] worked for me. Thanks Josh!

   Jon

---

