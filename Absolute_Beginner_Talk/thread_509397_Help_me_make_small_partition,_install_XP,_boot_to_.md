---
title: "Help me: make small partition, install XP, boot to either, without ruining my system?"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by jfrancis on 2007-07-25
OK. Skip the text below if you don't have time, it just sets the scene :) 

I play Eve-Online via wine on my 100% Ubuntu system... well I did until the latest patch came out for the game and now I can not play it.  Now, I am sure that in time this problem will be solved and I will be able to jump back in and play again, but in the mean time... and what about future patches to the game?  So I thought that perhaps I could stick this copy of XP I have on my system in a really small partition JUST to play eve when ever I can not in Linux.

So... what help do I want?

I am noob OK so bare that in mind.  This is what I want to achieve:

1)  On my single hard drive I would like to safely create a small partition just for XP.  How best to do this?  Is it NTFS that I should use?  How much space would I need to run XP and Eve-online only? ....

2)  When the above is done - How do I install XP without messing up my current install of Ubuntu?  Is this possible for a noobish guy like me?  Is it safe?  

3)  When the above is done - How do I choose to boot in to XP for the (hopefully) rare occasions when I can not play eve in Linux?   

If anyone can help me with this then I will be sooooo happy!  Thanks for reading.

---

### Post by Orochi on 2007-07-25
Use gparted to resize your current partition to make room for XP. Use the XP cd to install Windows to that partition (make sure you choose the correct partition!) You can either format with gparted or let XP installer format. Once you're done, you'll need to boot into Ubuntu using the LiveCD and reinstall GRUB to be able to dual-boot.

You should probably back everything up first just in case, but it should be relatively safe.

---

### Post by wolfen69 on 2007-07-25
the safest method is to get a second drive and install xp on it. just unplug ubuntu while installing xp.

---

### Post by mlentink on 2007-07-25
If you follow that route, better make sure your system can set boot order for multiple harddisks in the BIOS setup.

But I'd like to ask another question first. What do you want to use XP for? 
If it is only for playing that game, making a partition and installing XP on it seems a bit like overkill. In that case, I'd take a look at using a VMWare Server first.

---

### Post by jfrancis on 2007-07-25
> **mlentink said:**
> But I'd like to ask another question first. What do you want to use XP for? 
If it is only for playing that game, making a partition and installing XP on it seems a bit like overkill. In that case, I'd take a look at using a VMWare Server first.

Well, it is an extreme game :)  

So, IF I do go the route I first outlined, I think I might be OK up until the point where I reinstall my GRUB.  This part I have no idea about.  But any more thoughts on this before I jump in and do it?

---

### Post by mlentink on 2007-07-25
> **jfrancis said:**
> Well, it is an extreme game :)

Oh, OK.
I'm really not that much into gaming myself, so I wouldn't know. 
But there are thousands of people running ubuntu in dual boot with XP, so it's entirely possible. On my notebook I run dual boot with XP. But that had XP installed when I installed Ubuntu on it. I have read a couple of threads here that point out that Windows likes to be first, so if it is installed later on, there are a couple of extra things you need to do. Don't remember which at present, I would need to look through those threads....

---

### Post by rookshop on 2007-07-25
Even I was thinking of using VMWare server for gaming purposes. But I read in one of the How-To's that VMWare does not support games with heavy graphics. Is it true?? I am particularly interested in Civilization 4.

---

### Post by jfrancis on 2007-07-25
> **mlentink said:**
> Oh, OK.
I'm really not that much into gaming myself, so I wouldn't know. 
But there are thousands of people running ubuntu in dual boot with XP, so it's entirely possible. On my notebook I run dual boot with XP. But that had XP installed when I installed Ubuntu on it. I have read a couple of threads here that point out that Windows likes to be first, so if it is installed later on, there are a couple of extra things you need to do. Don't remember which at present, I would need to look through those threads....

Yes, this is where my understanding lays right now.  I am guessing the instruction above about installing the GRUB is how to get the boot order resolved with option to boot to XP where required.

(btw it is a bit extreme to install XP just for a game, I can see that.  So if I do this it will be a pretty small partition and hopefully I will never have to use it (once the issue I have is resolved)

---

### Post by jfrancis on 2007-07-25
> **rookshop said:**
> Even I was thinking of using VMWare server for gaming purposes. But I read in one of the How-To's that VMWare does not support games with heavy graphics. Is it true?? I am particularly interested in Civilization 4.

You know, I have little to no idea.  As I understand it however, VMWARE route will be heavy on system resources as it is literally running the OS on top of your OS, which is not strictly the case with WINE (I think...).

---

### Post by Orochi on 2007-07-25
I believe VMWare can't do any 3d graphics, which most newer games use. I may be wrong though.

If you install XP after Ubuntu, it will erase GRUB and install its own bootloader to the MBR. That's why you need to then boot off the Ubuntu LiveCD and reinstall GRUB. If you do a quick google search on "installing XP after Ubuntu" you should get some pages telling you how to do this. If you can't find one, I can help walk you through it.

---

### Post by jfrancis on 2007-07-25
> **Orochi said:**
> I believe VMWare can't do any 3d graphics, which most newer games use. I may be wrong though.

If you install XP after Ubuntu, it will erase GRUB and install its own bootloader to the MBR. That's why you need to then boot off the Ubuntu LiveCD and reinstall GRUB. If you do a quick google search on "installing XP after Ubuntu" you should get some pages telling you how to do this. If you can't find one, I can help walk you through it.

Thanks very much!  I will do a search and see how I get on.  If I fall over expect a post here...

---

### Post by jfrancis on 2007-07-25
OK, been reading about the grub, and it looks way too complicated to me.  Think I may sit and think about this for a while.. darn ccp for breaking the game for linux users :shock:

---

### Post by jfrancis on 2007-07-25
Well, I decided to go a head with this after all.

Now I have XP installed and it looks like my ubuntu installation is uneffected which is great.  Now I am the part where I need to get the GRUB back up and running.  I have failed at this bit and would really appreciate some help here.

This is what I have done so far:

Booted up my livecd.

Opened terminal.

Typed > grub
Typed> root (hd0,1)

Then got error about no such device.

Then tried> root (hd0,0)

That was accepted.

Then typed > setup (hd0)

Then quit and still no GRUB.  I know why... it is because I have not a clue what I am doing!  lol  so here I seek those who do know.  

UPDATE:

When I went in to try different values with the command > root (hd0,x) and it now does not accept anything I put in.  So something is worse or eh.. dunno :/


I need sleep now.. I will keep my fingers crossed that a solution will be posted here by the time I awake :)

---

### Post by MQMike on 2007-07-25
Good Morning (or whatever is appropriate for people like us who sleep on any schedule . . .)
Did you have a nice nap Jfrancis?

Over in Kubuntu I wrote a How-To on GRUB that does exactly what you need to do – re-install GRUB to the MBR of that drive so it manages the booting of both OSs.

How To GRUB Methods - Toolkit

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)
(Documentation > How Tos, by Qqmike)

Windows DOES like to be on the first hard drive, the first partition.  (If it is put on a second HD, you need to use map commands in GRUB’s boot menu for Windows – that’s in a post down below the How-To.)
However, we just did a case where Windows was on the first HD but not on the first partition and it worked fine.

Re-installing GRUB involves
from Ubuntu Live CD
$ sudo grub
grub> root (hdx, y)     # that’s hard drive x, partition y
grub> setup (hd0)
grub> quit

where (hdx, y) is the partition you installed Ubuntu to.  GRUB notation:  hard drives and partitions are numbered starting from zero.  Example, if you put Ubuntu on the first hard drive x = 0, and if it is on the first partition, y = 0.  (hd0) refers to the MBR of hd0.

After you re-install GRUB, worst case, you might just have to check the boot menu for Windows.
That is also covered in the How-To (Editing the menu.lst or the /boot/grub/menu.lst in Ubuntu).

Make sure the boot entry for Windows looks like:

title  Windows XP or any description can go here
rootnoverify (hdw, z)
makeactive
chainloader +1

where (hdw,z) is the hard drive w and partition z where you put XP (remember, GRUB starts counting from zero)..

So, follow the How-To, and basically you’ll be doing the following:

--  Using the Live Ubuntu CD, re-install GRUB to the MBR, (hd0)
--  Then try booting up and see if you can get into Ubuntu and into XP
--  If you have to edit the boot menu for XP, do so from Ubuntu, /boot/grub/menu.lst, and with root privileges and don’t forget to save your edits with File – Save, File – Quit (explained in How-To), and worst case, you always have the Ubuntu Live CD as a tool for accessing the command line in Ubuntu.
--  After you get it to work, the How-To (see the second Post) tells you how to change the default OS and the timeout.
--  And after you are successful here, come back and help us help others!

--Mike
who also should take a nap soon and who may be stuck doing some work tomorrow but will try to check back in, but other folks here know this stuff, too

---

### Post by jfrancis on 2007-07-26
Good morning Mike,

I had a pretty good sleep thanks.  I really needed it after staring at this screen for so long!

Thank you for providing me with your guide.  It worked!  I now boot in ubuntu as default which is what I wanted.  All I got to do now is make sure I add windows to the boot options.  I will try that later...

Thanks again!

---

### Post by MQMike on 2007-07-26
jfrancis, Great!  At least you have your old friend back and accessible again.

As for Windows, we know it is installed to the first hard drive, along with Ubuntu, and Ubuntu is on the first partition (so Ubuntu is at (hd0, 0)), and the swap got its partition, maybe a separate /home partition, too?
My point is that Windows must be there somewhere, on (hd0, z), where z > 0:

title Windows XP or any description can go here
rootnoverify (hdw, z)
makeactive
chainloader +1

The rootnoverify tell GRUB to make no attempt to mount that NTFS partition, and sometimes that helps, too.
Some people say “makeactive” is optional (I’m not sure).

Tidbit:  Fact is, you can quickly experiment:
When you see GRUB menu offering Ubuntu, press the “c” key instead, that gives you a grub> prompt.
Now go for it:
Type
rootnoverify (hd0, z)   # for some specific z>0
makeactive
chainloader +1
boot     # you need the “boot” command only at the GRUB command line here, not in menu.lst

See if it goes into XP, try different z’s.

Good Luck!  Let us know.


PS1:  You know the sudo fdisk –lu command at the Ubuntu Terminal prompt?  It gives you a list of your hard drives and filesystems.  (-lu is “l” as  in “list,” “u” as in “units.”)

Or, at a GRUB prompt, grub>, try geometry (hdz), for some specific z value, and see if you recognize what comes back for that drive.

PS2, Don’t know anything about VMware, except what it is, but a good tutorial site is Dedo’s at:
[http://www.dedoimedo.com/computers/vmware_player.html](http://www.dedoimedo.com/computers/vmware_player.html)
(He also has other good tutorials.)
But right now, let's keep this simple and see if you can get XP on the GRUB boot menu!

---

### Post by jfrancis on 2007-07-26
\o/

Job done!  :)  Thanks a bunch, Mike.  I did as you say and found the windows installation at the 3rd partition, so number '2' in the grub.   Now I can easily boot to windows should I need to while continuing to enjoy ubuntu as before.  

Just installed eve online to windows and now can use this until I (well, others actually!) can fix the problem in wine.    

And doing this task has enabled me to learn about the GRUB and so if nothing else I may be able to help others, if only by pointing them to your posts, Mike.  

Cheers!

---

### Post by MQMike on 2007-07-26
That's a great start to the day!

As you found out, for most issues, GRUB isn't difficult.  In fact, it's alarmingly simple, thanks to its power.  Just a few commands, a few principles, and a couple things like sudo fdisk -lu and geometry (hdx) gets you through most of it.

Congratulations on your persistence!

--Mike

---

