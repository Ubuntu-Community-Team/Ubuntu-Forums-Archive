---
title: "How To Uninstall GRUB?"
date: 2006-01-11
forum: Absolute Beginner Talk
---

### Post by eddyvlad on 2006-01-11
I've read some tutorial on how to uninstall GRUB. I don't have floppy disk drive on my laptop, so I can't boot to floppy. However I have a copy of my bootable Windows XP cd. Luckily I've made a copy coz my original WinXP cd is warped. Anyway, I did try to boot from WinXP cd but it says, "Boot CD-ROM Type: Non-Emulation Booting". And it doesn't boot. 

I wanted to hide my linux partition so that nobody knows I have linux on my laptop. Let's say I've manage to uninstall GRUB. How do I go about accessing linux then after that? 

But first and foremost, I need to uninstall GRUB... help...

---

### Post by jonathanm on 2006-01-11
if you just want to hide your linux partition then the best thing to do would be to hide grub instead of deleting it.  This is done by editing the menu.lst file (sometimes called grub.conf)  This can be found by typing into a terminal:

sudo gedit /boot/grub/menu.lst

Find the lines:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

They should be near the top, edit them so that they read:

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

(No #) Then save, exit and reboot

You may also want to change your default boot entry, if you want your xp to load then add savedefault into your xp entry, mine looks like this:

title		Windows XP bootloader (x3)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

then change the default num option, usually first option to 'saved'

This should automatically boot to windows, without showing any traces of linux and if you want to boot to linux tap ESC on boot

---

### Post by Thirsteh on 2006-01-11
You could also change the timeout to like 1 second so people won't even notice anything suspicious (even if it's a black screen!). "Yes hello? Is this Langley?". Sorry.

---

### Post by M3lted on 2006-01-11
why would u hide something as great as Ubuntu / linux :(

---

### Post by eddyvlad on 2006-01-11
[quote=M3lted]why would u hide something as great as Ubuntu / linux :([/quote]

I only use linux when I really need a more powerful OS to do something that Windows can't. Other than that, it's faster to work in Windows as I don't need to type command lines. :)

---

### Post by M3lted on 2006-01-11
aha oke , was just curious :)

---

### Post by manicka on 2006-01-11
[QUOTE=eddyvlad]I only use linux when I really need a more powerful OS to do something that Windows can't. Other than that, it's faster to work in Windows as I don't need to type command lines. :)[/QUOTE]

You don't really need command lines in Linux either. Most tasks can be done with GUI if desired.

---

### Post by rfruth on 2006-01-11
I like and use the (Gnome) GUI but every now & then use the CLI, sure glad both are  available !

---

### Post by JonSh on 2007-06-27
Unfortunately, no one actually answered the posted question.  I need a CLI command to remove GRUB, and as a *nix noob, hopefully someone here can tell me the command(s) I need.

It has to be CLI because Ubuntu really despises all my nvidea interfaces, no matter what changes I attempt.

Grub needs to be gone because I need to image the bootable windows image...(why the installer felt the need to write to the disk I told it to leave alone I will never understand, but that's a very different question:)).

Any help greatly appreciated...Yes, Ubuntu is better than Windows, yes, Grub is a wonderful thing, yes, I still need it gone.

Jon

---

### Post by louieb on 2007-07-03
You don't remove GRUB - you replace it. If all  you do is uninstall GRUB, you will be left with an unbootable doorstop. In you case I guess you want to replace it with NTLDR. 
[http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=uninstall+grub&btnG=Search](http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=uninstall+grub&btnG=Search)
[How to Remove Linux and Install Windows on Your Computer]("http://support.microsoft.com/kb/247804")
[Un-install Grub  Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by LaRoza on 2007-07-03
The Super Grub disk can do that if you want.

---

### Post by mobeus1 on 2008-05-07
I am a newb to Ubuntu but it seems pretty easy to work with. I had the same problem when installing alongside my Windows XP. I can now boot between both OS and it works great !!! Thanks for the tip...

"live long and prosper"

mobeus:guitar:

---

