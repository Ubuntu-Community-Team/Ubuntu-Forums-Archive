---
title: "Ive never made it to the desktop"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by Laughed on 2008-03-06
After countless re-installs I have yet to make it to the desktop. After the initial install and reboot I see a line at the bottom left of the screen stating kernel loading or something to that effect, then the screen loses signal and the PC runs idle.

I've waited almost an hour and nothing.

Not to sound desperate, but I really need direction here.

Update:
Problem has been solved. It was suggested that this was in fact due to a known bug here [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910").

Which brought me here [http://ubuntuforums.org/showthread.php?t=454392](http://ubuntuforums.org/showthread.php?t=454392) and after reading the 2nd post and using some guesstimation I was able to successfully boot up ubuntu.

Here is a copy of that 2nd post:

Code:

kernel   /boot/vmlinuz-2.6.20-15-generic root=UUID=35606f29-4636-4a6e-89e2-e7db49e9317f ro vga=794
# quiet splash

Try to comment out quiet and splash commands.

Here is a table of VESA video modes (VGA codes):
Code:

         640x480   800x600   1024x768   1280x1024   1600x1200   Ask user at boot.
8 bits   vga=769   vga=771   vga=773    vga=775     vga=796     vga=ask
16 bits  vga=785   vga=788   vga=791    vga=794     vga=798     vga=ask
32 bits  vga=786   vga=789   vga=792    vga=795     vga=799     vga=ask

I used the ask user, after the reboot I picked scan and than mode (1).


Booted right up, so happy Yeahhahahhahhh!!!!!!

It took forever for me to get to that one page and its now closed, so I hope this helps other users who find themselves in this position.

Update: Well this fix didnt last a reboot. So am off to find a more permanent solution.

---

### Post by gigaferz on 2008-03-06
I am assuming (i know what they say) that you have installed ubuntu before, right? Or you have never been able to do it?

  either way, sounds like you have a bad cd.

  always check the md5sum ,and also, there was an option ..something like "check cd for defects)...

---

### Post by Laughed on 2008-03-06
I installed Ubuntu a year ago. I had issues with ATI drivers overheating my card and there were no fixes at the time so I gave up on Ubuntu. 

Your right about what they say. I have checked the integrity of each of the 7-10 various Ubuntu disks I created using both mg5sum before creating said disc, and I've also used the check cd option after they were created.

I've run: 
cd /etc/X11
cp xorg.conf xorg.conf_backup
nano xorg.conf 

and I changed ati to vesa. No success. Since it didn't work I changed it back.

I've tried some other things with no success. I am willing to try anything (but a re-install) again.

---

### Post by kellemes on 2008-03-06
Have you tried booting in safe-mode and typing the following?
```
sudo dpkg-reconfigure xserver-xorg
```

If it doesn't work please post the following..
What card do you have?
Post /etc/X11/xorg.conf
**and** /var/log/Xorg.0.log

---

### Post by Crafty Kisses on 2008-03-06
> **Laughed said:**
> After countless re-installs I have yet to make it to the desktop. After the initial install and reboot I see a line at the bottom left of the screen stating kernel loading or something to that effect, then the screen loses signal and the PC runs idle.

I've waited almost an hour and nothing.

Not to sound desperate, but I really need direction here.

You may want to try the alternate CD installer.

---

### Post by alqualond on 2008-03-06
If I understand correctly, you can see GRUB and then, when Ubuntu starts loading, your screen looks like it's turned off, right?
I had something like that using the LiveCD, I couldn't get past that blank screen. Maybe this'll help: When you see the GRUB screen (where you choose which Operating System to load), edit one of the choices (I think you need to press "e" to edit, then make any changes). What I did was remove the "splash" option.
Or, if you can somehow get to a terminal, try editing /boot/grub/menu.lst, and removing the word "splash" from there. I made a post a while back that's a little more detailed: [http://ubuntuforums.org/showthread.php?p=4063680#post4063680 ]("http://ubuntuforums.org/showthread.php?p=4063680#post4063680")
Sorry if I'm not very explicit, hope this helps!

---

### Post by gigaferz on 2008-03-06
so, when booting  ,what are the system messages?

---

### Post by Laughed on 2008-03-06
> **kellemes said:**
> Have you tried booting in safe-mode and typing the following?
```
sudo dpkg-reconfigure xserver-xorg
```

If it doesn't work please post the following..
What card do you have?
Post /etc/X11/xorg.conf
**and** /var/log/Xorg.0.log

Nice. I actually just tried that command line with no success (after running through more than enough options). I'm rebooting and will post what you asked for.


Update:

I ran: 
cd /etc/X11
nano xorg.conf

from here I can scroll down and see that my card is identified correctly. ATI Radeon x850xt platinum PCI-E
Driver is listed as "ati" (which I changed at one point to vesa and then back)
Bus ID is "PCI:1:0:0" 
Honeslty, I think the bus id is wrong but I don't know how to determine what the bus path is to cross check it with this xorg. 

I'm not sure how to execute /var/log/Xorg.0.log. I couldn't cd to it, and when I ran nano it didnt show me anything. Sorry, honestly, I am learning as I go along here. This is all completely new to me, well, at least Linux is.

Update:
I am currently trying some of these other suggestions. BRB.

---

### Post by Laughed on 2008-03-06
> **gigaferz said:**
> so, when booting  ,what are the system messages?

The only message I ever get is on the bottom left hand of the screen. It reads Kernel loading... then a new line reading kernel again with a string of parameters and then death. =)

> **Codename said:**
> You may want to try the alternate CD installer.

Sorry, my last install was using the alternate version. Same thing was happening there as well.

BRB.

---

### Post by Laughed on 2008-03-06
> **alqualond said:**
> If I understand correctly, you can see GRUB and then, when Ubuntu starts loading, your screen looks like it's turned off, right?
I had something like that using the LiveCD, I couldn't get past that blank screen. Maybe this'll help: When you see the GRUB screen (where you choose which Operating System to load), edit one of the choices (I think you need to press "e" to edit, then make any changes). What I did was remove the "splash" option.
Or, if you can somehow get to a terminal, try editing /boot/grub/menu.lst, and removing the word "splash" from there. I made a post a while back that's a little more detailed: [http://ubuntuforums.org/showthread.php?p=4063680#post4063680 ]("http://ubuntuforums.org/showthread.php?p=4063680#post4063680")

Sorry if I'm not very explicit, hope this helps! Hey man, every little bit is greatly appreciated. Ive been at this non-stop and I really just want to get past this so I can get to the real problems, if you get what I'm saying.

I'm not really sure how to get to a terminal and when I press "e" at the grub screen it brings me to another screen giving me 4 options.

1.) root (hd,0)
2.) Kernel /boot/vmlinuz....
3.) initrd /boot/initrd.img...
4.) quiet

its there that my eyes glaze over. I would image I need to edit option 2...

---

### Post by Laughed on 2008-03-06
Okay Ive removed the word splash and nada.

How do I check the bus path?
How do I use / execute lspci?
How do I view / execute var/log...?
How can I edit "/boot/grub/menu.lst" from the root command?
Can I gain access to the "terminal" from the root command?

---

### Post by kesman on 2008-03-06
So you can boot to desktop now? Or just text-mode? In desktop, you can go applications -> accessories -> terminal, or in text mode, you are in it already. Once in terminal, you can use several text-editors for editing files, such as nano or pico. To open up ie. grub menu.lst, type:
```

sudo nano /boot/grub/menu.lst

```
to open the file. Then edit it, and quit with ctrl+x and answer yes to save the file.
Sudo in front of a command makes the command to be ran as root or Super User. It prompts you for password, which usually isn't shown when you type it, this is normal, a security thing.

---

