---
title: "How do I: Move Ubuntu onto the Slave HD and then make the Slave HD the master?"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by Raavea on 2006-05-01
Read below for a full explanation, but basically: I have switched my hard-drives over so that the big one (which was slave and empty) is now Mistress, with a fresh install of Ubuntu, and the small one (which was Mistress and had Ubuntu) is now slave.

 During the install, something called GRUB was installed also. I want to completely wipe the old Ubuntu installation (the one on the now-slave) and get rid of GRUB, so that my PC will simply boot from this Ubuntu installation. (This being the now-Mistress, new installation.)

 I'm a little lost here... I figure using the disk manager to format the old HD should be okay, it should wipe the old Ubuntu and the GRUB (as I think it installed to the old HD) but I don't want to risk killing my PC... Can anyone shed some light? :-k 

-------------------------------------Merely for integrity, my original message:
**How do I: Move Ubuntu onto the Slave HD and then make the Slave HD the master?**
Ok, the title pretty much sums it up, but here goes.

 Welcome to another (yes, ANOTHER) post by lil old me! Thanks for coming, there's popcorn for the regulars, do take a seat...

 Now that you're all comfy, I'll begin.

 I have two hard-drives in my little PC. One is a seven gigabyte hard drive, which is getting old and haggard - This is set as Mistress. The other is a twenty gigabyte hard drive, only about a year old - This is set as slave.

 I had my original 7GB HD as Mistress when I was running XP, as I didn't want to uninstall and re-install the damn thing. When I installed Ubuntu over my XP installation (complete wipe and over-write) I did so with the Mistress, obviously.

 However, I feel moving my Ubuntu installation to the 20GB HD will be a better deal all around, more space, more mem-swap room, etc, with the 7GB being changed to be slave.

 Thing is... I don't know how! My father's a technology whore, so he took over all aspects of upgrading when I lived with him, thus I have huge gaps in my knowledge. (I know how to rip a PC apart and give it new bits, what bits are what, but I don't know, for instance, what certain wires do.) Can anyone help? Do I need to switch anything over inside the PC (I think I remember something about a wire and a switch, but I could be wrong....) or is it merely an internal, electronic thing?

 Could anyone be so kind as to help me out with this?

---

### Post by htinn on 2006-05-01
Swapping master/slave will not likely improve the performance of your drives if that is what you're thinking. However, moving Ubuntu to the larger hard drive will possibly improve the performance of Ubuntu.

Unless you have a lot of unbacked-up data on the 20 GB drive, you should probably just install a fresh install of Ubuntu on the 20 GB drive. From there, you can simply copy your old data from the 7 GB drive that you want, then use the 7 GB drive as a kind of "backup" drive. This is how I would handle it, anyway. :)

---

### Post by skinnygmg on 2006-05-01
to change a hard drive from slave to master, from a hardware stand point, you need to change the jumper position.  a jumper is a little plug that completes a circuit on your HDD.  there should be a little diagram on your HDD that shows you the correct jumper position.

---

### Post by Raavea on 2006-05-01
Nah, I know full well it won't change the drivers, but the larger space means I don't have to worry if I'm gonna fill her up, and should mean faster specs due to the bigger cache space. I think. It's quite late for me now... *sleepy*

 A full install eh... And, the fact that I'm totally new to linux shouldn't cause me to rape my poor PC? I just... Install Ubuntu onto slave and move my other files across...? I guess I could... Hmmm... Yes.

 But first, I will want to sort out a few issues I am having, so that the new install gets set up perfectly smoothly instantly. ^_^
 Thanks for the idea, htinn.

---

### Post by Raavea on 2006-05-02
Okay, thanks Skinny. (For some reason, I only just saw your post...)

 I've copied my important crap to CD, and am now preparing to install Ubuntu on the slave. When that's done, I'll be clearing my desk off and struggling with my casing, and then taking a peek at all them little wires. o..o

 Everyone, please cross your fingers. It is 2.24am, and I'm tired! XD

 Oh, and before I do that, out comes the notebook for all them usefull little bits I'll be wanting sorted from the start! XD

---

### Post by Raavea on 2006-05-02
Ehh... *blinks*

 I think I did a boo boo...

---

### Post by confused57 on 2006-05-02
Here's another option, it's how I have my system set up, note the instructions posted by lha:

[http://www.ubuntuforums.org/showthread.php?t=120994](http://www.ubuntuforums.org/showthread.php?t=120994)

---

### Post by Raavea on 2006-05-02
I'm not trying to Dual boot. I just wanted to change my slave over with my Mistress, without having to re-install Ubuntu. It seemed a fresh install was the best bet, so that's what I did.

 Sadly, just as I booted the new master with the new install up, the up/down led on my new mouse gave out. I had to switch to my old, less sexy mouse. ;_;

 Now, I just need to figure out how to get rid of GRUB and wipe the old HD, without killing my PC..

---

### Post by Raavea on 2006-05-02
I updated this thread rather than make a new one... Hope that's okay, adminy types. *quakes in fear* :lol:

---

### Post by htinn on 2006-05-03
If you have Ubuntu installed on both drives, it's a pretty good bet you'll have grub installed on both as well. I would suggest you make sure the BIOS is configured to boot off the new hard drive, boot into that, then run something like gparted or qtparted to unmount and reformat the old hard drive (assuming you successfully made backups, that is).

---

### Post by Raavea on 2006-05-03
*blinks* Wow, 7.30am. Been years since I was up this early. However, in this case, I merely forgot to go to bed...

 How would I go about ensuring my BIOS will boot off the new HD? I'm not sure how to get into the boot menu, you see...

---

### Post by htinn on 2006-05-03
Most BIOSes use F2 or Del at boot time to get into the configuration menu. From there you can usually navigate using the arrow keys and change options using various other keys. There should be a small sub-window on the side or bottom that explains what keys do what.

Somewhere in your BIOS menu you should have a "Boot order" or something like that. You'll want to arrange the drives in the order that suits you best for booting (put the new drive at the top of the list, for example).

---

### Post by Raavea on 2006-05-03
Thanks. ^__^

---

