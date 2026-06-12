---
title: "Booting problem"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by vanSnow on 2008-01-14
Hello people, I am very new to Ubuntu and this is my first post here so please be patient if I am slow.

I installed Ubuntu 7.10 some months ago on my new IBM X60. Nice! But yesterday I installed some updates (I don't remember for what) and now my Ubuntu cannot start. I see GRUB, then the splash-screen and when that is finished loading I only see a black screen with the cursor in the upper left corner (it is not possible for me to type anything). I have tried the different kinds of Ubuntu upstarts in GRUB but all ends with the same result.

If I press the power button when I see the black screen with the cursor then I see the closing splash-screen. So it seems that Ubuntu was started but without any desktop.

Please help me. I would be glad for just a hint.

---

### Post by family on 2008-01-14
When you get to GRUB, press Esc IMMEDIATELY!
Then, pick the recovery mode kernel.
Once the shell is loaded, type;
apt-get -f install
dpkg-reconfigure xserver-xorg

and then reboot and try to get back into the normal kernel.

If this fails, try SuperGRUBDisk; [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)
Or perhaps; [http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure](http://www.freesoftwaremagazine.com/blogs/how_to_fix_your_computers_graphics_with_dpkg-reconfigure)

---

### Post by vanSnow on 2008-01-15
Thank you for the answer family, but I have changed the GRUB-menu so I only see this:

Ubuntu 7.10, kernel 2.6.22-14-generic
(-and my WinXP)

If I edit (pressing 'e') the Ubuntu line I have these 4 options:

root (hd0,2)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=cf469...
initrd /boot/initrd. img-2.6.22-generic
quiet

I have tried them all 4 but I don't get to any command line where I can type in what you suggested. Maybe I have erased the vital recovery mode, then what?

Thanks in advance.

---

### Post by Yoke &amp; Chung on 2008-01-15
Did you change any of your hardware?

---

### Post by vanSnow on 2008-01-15
No, only software updates.

---

### Post by family on 2008-01-15
By command-line I mean the rot shell;
root@something# 

If you still cant get there, try burning a LiveCD for yourself, and once you boot Live, type this in a terminal;
```

mkdir /mnt/restore
mount /dev/sda1 /mnt/restore
chroot /
apt-get -f install
dpkg-reconfigure -a --use-defaults
dpkg-reconfigure --all

```
wishing you luck

---

### Post by vanSnow on 2008-01-15
OK, I will try to get an external CD-drive (since I have an IBM X60 without). If you or somebody else has an other suggestion not involving a CD-drive I would much appreciate.

I just have a lot of info in there and no CD-drive and a deadline in 25 hours!

---

### Post by dstew on 2008-01-15
It is possible that the X-window server configuration was altered. You will need to enter dpkg-reconfigure xserver-xorg as the other posters have suggested. To get a command line, go ahead and let it boot. When you think it has stopped loading up, press ctrl-alt-F1 and you should get a command line. Enter commands on that.

---

### Post by vanSnow on 2008-01-16
Sorry, no. I still just see the blinking cursor in the upper left corner no matter what I press (ctrl+alt+F1 or ctrl+shift+F1 or shift+alt+F1). And I still cannot type in anything.

Other suggestions are welcome. Thanks for all the time you guys and girls spend on helping me.

---

### Post by vanSnow on 2008-02-04
I still can't get in to my Ubuntu. Doesn't somebody have a suggestion? See the earlier posts in this thread to see what I have tried so far.

//Thanks

---

### Post by bumanie on 2008-02-04
Have you tried super grub disc yet? If your ubuntu is bootable, super grub disc will boot it. If it is not bootable, you may need to reinstall, seeing you seem unable to get into console by pushing ctrl+alt+f1 - I guess you know that they are pushed at the one time, not separately.

---

### Post by vanSnow on 2008-02-10
I don't have a disk drive.

Yes, I know they should be pressed simultaneously.

Sorry for the late answer.

---

### Post by 1337455 10534 on 2008-02-10
Do you have a floppy drive? Try mininux :D. The Gentoo Handbook has excellent instrctions on how to get/use it (albeit to install Gentoo, here is a link to the Mininux page; [http://mininux.free.fr/uk/](http://mininux.free.fr/uk/)).

Mininux is great but pretty advanced; if you have an other computer, print out or browse to a shell commands help page. You'll need to be pretty familiar with a black box staring at you, but it should work!

---

### Post by vanSnow on 2008-02-20
No, I don't have a floppy drive!

I don't understand why it is so difficult to recover my Linux. What does other people do when this happens? I can't be the first this happens to.

---

### Post by vanSnow on 2008-02-20
Now I just typed ' (recovery mode)' after the second line in GRUB and the splash-screen is substituted with a lot of screen text during start up. After some seconds it hangs for several minutes and then it enters some kind of console named BusyBox. I have tried to see what I can do with this BusyBox but I can't get anything meaningful out of it, even when I read the help.

Does anybody know what to do from here?

---

### Post by vanSnow on 2008-02-20
OK, now I got further in to the console and tried to reconfigure the X-window server. But it still cannot boot in graphics mode.

Suggestions?

---

### Post by 1337455 10534 on 2008-02-20
How did you  install Linux with no Floppy or CD Drive? Wubi?
After you reconfigure with dpkg in the console, type;

startx

and post the outcome.
:D, hang tight

---

### Post by vanSnow on 2008-02-21
I borrowed an external CD-drive from my brother. He is now in Guatemala and I am in Denmark!

I have started my old Ubuntu with the startx command. Hurray.

Thank you.

It wasn't the default boot I used. That is still hanging when I try to boot from that. I used the 3. from the Grub list and erased 2 words in the end of the boot-line (splash and something else)

How can I make the original default boot work again? I have updated the whole system but it doesn't seem to change anything.

---

### Post by N1N31NCHN41L5 on 2008-02-21
I was adjusting screen resolution and graphics cards and ran into the problem where my Ubuntu wouldnt load at all. I just reinstalled off the disk and am working great

---

### Post by 1337455 10534 on 2008-02-21
Dont do a reinstall just yet.
You say that you can get back into your normal Desktop?
See if you can go to System-->Preferences-->Sessions and add the startx command to the boot process. Then try rebooting.
Failing this, try reinstalling X from Synaptic. [Last RESORT].

---

### Post by vanSnow on 2008-02-21
Hello 1337455 10534, who are you writing to? Me or N1N31NCHN41L5?

---

