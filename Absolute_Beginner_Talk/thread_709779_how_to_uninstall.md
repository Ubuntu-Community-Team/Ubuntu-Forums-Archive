---
title: "how to uninstall"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Nissa_M on 2008-02-27
Ubuntu?  I have decide that the operating system is just not for me there is too much that I do that it is incompatible with.  I am trying to go back to my old operating system.

Thanks!
Nissa

---

### Post by Dr Small on 2008-02-27
Pop in another distro or Windows and simply install over it.

---

### Post by Vadi on 2008-02-27
Well, what is your old operating system?

---

### Post by Duck2006 on 2008-02-27
This link has all the good oil on how to do that.

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)

---

### Post by LuisGMarine on 2008-02-27
Well I'm sorry to hear that Ubuntu wasn't for you.  As hard as these guys try, I guess you can't make everyone happy, but thanks for trying it.

First of all , what OS are you going back to?  If windows, what you need to do is grab the Windows CD and boot it up like the day you were going to install Ubuntu.  Once you get there hit "r" to enter recovery mode, once in there type in:

```
fixmbr
```

this will replace grub ( linux boot loader ) with the one windows uses.  Remove the CD, restart and you should be back to normal.  

for the partitions use gParted or some sort of live cd to remove the Linux partion, and merge it with your windows partition, or however you want to go about it.  Hope this helps!

---

### Post by Thief X on 2008-02-27
I am assuming that you mean Windows XP, but these instructions will work for any OS

This is actually a pretty simple problem to solve

1. Grab your Restore disk that came with your computer
2. Pop it in your CD/DVD Drive
3. Start your computer and go through the instillation

If it doesn't boot from CD (which it should considering you installed Ubuntu from CD) then...

4. Start up your computer and hold C

If this doesn't work then just post and i will put the instructions on how to change your BIOS

EDIT: lol guess i am just too slow at typing, i was beat to it :P

---

### Post by LuisGMarine on 2008-02-27
haha me too! :lolflag:

---

### Post by Nissa_M on 2008-02-27
Ok here is the deal. I got this great idea from a friend that I would just love Ubuntu.  I checked it out a bit and was like oh yeah I want that.  Well I didn't do enough howe work.  I don't have that knowledge or the time to learn what I need to know to get it off the ground and more importantly it's not compatible with my choice of web builder. I installed ubuntu over everything in my hard D!  All i have is a Back up disk that I created a year ago today when I bought my computer, which means I'm still going to be stuck with vista.  I tried to reinstall all my info from the back up by trying to write over ubuntu but it wouldn't let me.  I have nothing left on my computer to lose. I just woant to go back.

Nissa

---

### Post by Dr Small on 2008-02-27
Sleep on it for awhile... It may come to you that you are sitting an a gold mine.
Otherwise, that recovery cd most likely won't do squat.

---

### Post by LuisGMarine on 2008-02-27
Try runnin the ubuntu CD again, and just use gParted program to clean your HDD, like completely wipe the thing.  

Then try the back up disks again.  Keep a good live CD around, this way if you loose your Ubuntu, and can't get windows back up you can still get to the internet while we help you to figure this out.

anyhow else go some input?  I mean I  would recommend the magnet trick ... :lolflag:

---

### Post by Dr Small on 2008-02-27
The magnet trick would be my last thoughts. He has a perfectly good drive, so why ruin it?
If the recovery disc does not work, then you will have to either stay with Ubuntu or pay for Vista / XP.

---

### Post by LuisGMarine on 2008-02-27
I would recommend that you try going to the manufactures website of who made your computer and see if they have some recovery disks for you.  If not you might have to do an illegal thing to get windows back on there, but I don't condone it, that only comes if you are completely that desperate to get back ...

---

### Post by Nissa_M on 2008-02-27
it said there was an error because of Ox0000017.  Whatever the **** that is.  The back up won't install!:confused::mad::(

---

### Post by 3rdalbum on 2008-02-27
Your recovery disc (that came with the computer) probably depends on a recovery partition being present on your hard disk. If you told Ubuntu to erase your whole hard disk, then the recovery partition has been wiped as well.

You'll basically need a copy of Windows Vista and the license key for your original installation. A friend might have a copy of Vista that you can use, but just remember to put in YOUR license key, not theirs.

If Windows Vista's installer doesn't see the hard disk, you will need to use Gparted from the Ubuntu Desktop CD to erase the hard disk. When it asks you what filesystem format you want, select "NTFS". After that is done, Windows Vista's installer will see the hard disk.

---

### Post by matherians2 on 2008-02-27
Just install another OS using the whole partition, assuming Ubuntu is the only OS on your hard drive.

---

### Post by Nissa_M on 2008-02-27
I can order a recovery disk (my computer didn't come with one) or I can buy a new windows OS (Vista was on my computer when I bought it) and that should make everything work, right?

I am going to be removing ubuntu so how would I use Gparted?  Not that I know what that is.

---

### Post by Dr Small on 2008-02-27
Save yourself the money and learn Ubuntu, and earn expirence.

---

### Post by Nissa_M on 2008-02-27
What is the easiest way to wipe my hard drive, with out using a magnet?

---

### Post by bryncoles on 2008-03-10
im newish here too, but i think i can help. Gparted is a partition editor which runs from the live cd. i think its what you will have used to install ubuntu on your computer in the first place. 

in order to run it to wipe your hard disk back to ntfs, you'll need to boot from the live cd as Gparted cant work if you're booting from the computers hard disk. 

so: pop the live cd into the hard drive and boot. run ubuntu from the cd. when its loaded, click system -> administration -> Gparted (or partition manager, i forget what its called). 

when that loads, it will show you all your drives. right click the ones you want to change and select 'format' from the menu. then you should be able to format them to NTFS, so that windows can see the drives. 

hope that helps you!

---

