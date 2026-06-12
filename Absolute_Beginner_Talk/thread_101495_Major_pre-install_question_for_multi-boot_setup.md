---
title: "Major pre-install question for multi-boot setup"
date: 2005-12-09
forum: Absolute Beginner Talk
---

### Post by TofuTheGreat on 2005-12-09
I searched the forums for "multi boot" and didn't find my question asked anywhere else so I think I'm safe putting this out there.  If it's been answered elsewhere please point me to that thread.  Now the question.

I have an XP machine (Home edition, runs slower than my dead great grandmother).  I want to dual boot with Ubuntu (so I can still backup my Win Mobile PDA).  My machine has two drives.  The first drive (C:) is NTFS for the entire size of the drive (18.61 GB with 9.41 free).  Drive two is also NTFS (149.05GB with 92.82 free).

As you can see I've got TONS of space to play with.  Do I need to create a partition for Ubuntu BEFORE I attempt the install?  Or will it automatically resize and repartition the drive that I install to?

I'm not opposed to starting from scratch but I'd like to avoid it if possible (so that I don't have to reload my kids' programs and data).  

About the only thing I know is that I have to have XP loaded first so that the Linux boot manager can take over.

Any help is much appreciated.

---

### Post by matthew on 2005-12-10
This will help you out.

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by TofuTheGreat on 2005-12-10
Thanks again Matthew!  I was able to create my partitions just fine (I actually found the wiki entry right after my post and immediately started the install before editing my post).  

However my Ubuntu install failed.  It failed at the "copying remaining packages" step (or something like that).  I think my CD-R was bad.  The install let me continue on by skipping that step so I did.

After everything else finished, and the CD ejected, the reboot and continuation didn't finish.  It just sat there doing nothing for a good 15 minutes.  So I gave the three finger salute that all Windows users know so well and booted to XP to post my woes here.

Can I restart the install (with a new CD that is) and pickup at the step that failed previously?  Or should I go through the whole setup again since I never got into Ubuntu to begin with?

I'm going to go burn a new disk either way (the one I've got has suspicious scratches and possibly crazing that I didn't notice before).  The bummer part is that I can't change the burn speed to go lower than max.  It's not even an option.

---

### Post by TofuTheGreat on 2005-12-10
Followed my instincts and burned a new CD to re-run the install from.  Everything went smoothly after that.  To be safe I went ahead and re-ran the partitioning too.

I'm posting from my Ubuntu install!

Haven't tried to boot to XP again but at the moment I couldn't care less.  It's just nice to have a faster system.

Only question left is how to configure GRUB so that it boots to XP by default and not to Ubuntu?  That way my kids can get their stuff easier.  The concept of dual booting really through them when I tried Red Hat a couple years ago.

---

### Post by prizrak on 2005-12-10
What you need to do is go to your terminal Applications>Accessories>terminal 
Type in```
sudo gedit /boot/grub/menu.lst
``` It will ask you for the password so just type in your user password.
Find the line that says ```
default 0
``` it's at the very beginning of the file. Change it to ```
**default 4**
```
It should work.

---

