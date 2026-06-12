---
title: "Windows Xp Partition Dead?"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by SWR on 2006-07-11
Ok, I installed Ubuntu on about 5 other machines before i tried my main computer, just to be safe.
So, I installed ubuntu, it works fine, but when i go to boot in windows xp, it says in DOS:

Booting 'Microsoft Windows XP Professional'

root (hd0,0)
 Filesystem type unknown, partition type 0x7
savedefault
makeactive
chainloader +1


Ok, please tell me how to fix this and boot back to xp..
I'd rather not have to re-install and lose all of my data, ty.

---

### Post by Average_Joe on 2006-07-11
Number One Rule is to backup all data before installing Ubuntu on any machine you intend to dual boot.

You need to edit GRUB.

1) go to Terminal
2) type there -->  sudo gedit /boot/grub/menu.lst  (that is lst as in 'list')
3) scroll down until you find that chainloader section - it will be near bottom of the text file
4) change the (hd0,0) to (hd0,1)
5) save and reboot

This is not a guaranteed fix, but will cause GRUB to refer to the second partition (hd0,1) instead of the first partition (hd0,0) to continue loading Windows.

---

### Post by SWR on 2006-07-11
Hehe, well, I have all my music backed up on my laptop, nothing else...
Now it says
Booting 'Microsoft Windows XP Professional'

root (hd0,1)
Filesystem type is ext2fs, partition type 0x83
savedefault
makeactive
chainloader +1

Error 13: Invalid or unsupported executable format


Now what?

---

### Post by Emceay on 2006-07-11
SWR, it's unfortunate, but if you're not careful from this point forward, you may lose your data. Yesterday I was staring at the same message until I just mounted and moved everything off my windows drive and reinstalled EVERYTHING.
Tell ya what, unless you're absolutely sure, don't get to the step where you fixmbr or fixboot until you've saved your data somewhere.

I don't want to scare you with gloom and doom, it's not over yet. If Average Joe's advice doesn't work the first time there's still a few options open to you. Just don't get ahead of yourself and wind up with a spanking new install like me.

BTW, it never killed the data, I was still able to mount the windows drive in ubuntu, so you might want to give that a try if you get to the point where all else seems lost.

Best of luck

---

### Post by SWR on 2006-07-11
Thanks for the support Emceay,
I'll mount the windows drive if Average Joe cant help me.
But, I'm sure he can.
Um, I get an error message whenI try to mount the Volume that has Xp on it..am I doing something wrong?

---

### Post by Emceay on 2006-07-11
what message? perhaps permissions?

---

### Post by SWR on 2006-07-11
Unable to mount the selected volume

error: device /dev/hda1 is not removable
error: could not execute pmount

---

### Post by Emceay on 2006-07-11
[http://www.psychocats.net/ubuntu/mountwindows.php]("http://www.psychocats.net/ubuntu/mountwindows.php")
Maybe this could help a lil? *fingers crossed*

---

### Post by Average_Joe on 2006-07-11
ok, we've now confirmed that (hd0,1) is your Ubuntu install since it is ext3 file extension.

so (hd0,0) is definitely your windows install then

change the grub menu.lst back to (hd0,0) please.

Before you do anything else, I urge you to go burn GAG Boot Manager onto a CD.  Hollar back when you have done this.  (Use Ubuntu, Firefox)
[http://gag.sourceforge.net/download.html](http://gag.sourceforge.net/download.html)

---

### Post by SWR on 2006-07-11
Emceay, halfway through the guide, the terminal commands didnt match, i tried twice..
Average joe, I used my last blank CD for  my Ubuntu install, is it ok if i burn GAG to a blank DVD?

---

### Post by Average_Joe on 2006-07-11
DVDs are fine.  I use only DVDs for all my linux stuff.

---

### Post by SWR on 2006-07-11
Sorry to be such a noob, but what file(s) do I put on the DVD?
Like, the whole zip file?
All of it's contents?
The Iso file in the zip folder?

---

### Post by Average_Joe on 2006-07-11
download the .zip file

after d/l and saving it to desktop,
right click it and open it with Archive Manager

it will unpack an .iso image file

then right click on the .iso and burn/write to cd

---

### Post by SWR on 2006-07-11
Ok, done, now what?
(thanks for your help so far)

---

### Post by Average_Joe on 2006-07-11
OK.  Now, there is no getting past this statement: "Read the directions on the front page dialogue when you load up GAG".

It will explain to you how to use GAG, so that you can boot up into your Windows installation, and get the data.  Give it a shot, read the directions, do a dry run and see if you understand the directions.

Be sure to ask any questions before installing GAG to your MBR.

And try to boot into Windows without installing GAG.  That is, use the operating-on-CD to boot into Windows.  Have something ready to copy your data onto though.

If you choose ot install GAG on the MBR, It will replace GRUB (Ubuntu's loader), but this is OK.

---

### Post by SWR on 2006-07-11
Ugh, I tried it, and tried booting into windows, it just shows a flashing underscore thing on the top left of the screen

Jesus Christ, it killed Grub...and it GAG wont do anything, it's just frozen when my computer boots to it..how to i get grub back?

I cant boot to any operating system!!

Help...

---

### Post by Average_Joe on 2006-07-11
If I understand your last post correctly, you went ahead and installed GAG over GRUB to the MBR.

But are you also saying that when your turn on the computer, it goes into GAG, and then GAG freezes?  That doesn't sound right at all.  I've never seen GAG freeze for any reason.  Let me know if my reading is correct.

---

### Post by SWR on 2006-07-11
Ok, here's what happend..I installed gag..set each partition to what it was, then tried to boot into Xp, it didnt work.
So, I rebooted, and GAG wont respond to and comand, it just sits there, the GAG dvd doesnt do anything, but I am able to boot from my ubuntu live CD, that's it.

---

### Post by Average_Joe on 2006-07-11
I'm wondering if you meant "GAG" in two places of text in your last message.  Please clarify.  GAG should have overwritten Grub, but you mention Grub.  Please advise.

---

### Post by SWR on 2006-07-11
Yeah, sorry, I edited it, i'm just panicing right now, so my typing isnt quite as good as it should be.

---

### Post by Average_Joe on 2006-07-11
OK.  Time for a new thread created by you, so that you can get more attention.

First though let me say that I've never seen GAG behave in the manner you describe.  When GAG boots, it doesn't 'do' anything at all -- it waits on user interaction completely.  It also doesn't freeze, because it doesn't do anything until you tell it to do something.

Therefore, please reboot and observe for repeatable pattern before posting your new thread.  What you are saying is that you now have GAG on your MBR, and when you boot up, GAG screen comes up but freezes and does not let you interact with GAG.

If this is the case after checking one last time, start a new thread and describe this.

(I will be away for one hour, until 2:45 AM London time.)

---

### Post by SWR on 2006-07-11
Ok, i got GAG to respond, for some reason, it was taking about 5 mins to respond to a command, what I am going to do now is reinstall Ubuntu, and see if I can get back grub...GAG isnt wokring for me.

Sadly, I still have the same problem as I started out with... an XP partition that I cant boot into.

---

### Post by krazyd on 2006-07-12
Have a look at the windows partition in the disks menu of ubuntu. Does it recognise the ntfs file system? If it does, you can try to repair the windows installation by having a look here:
[http://www.michaelstevenstech.com/XPrepairinstall.htm#warning2](http://www.michaelstevenstech.com/XPrepairinstall.htm#warning2)

I had a similar problem of not being able to boot into windows when I recently installed Ubuntu onto a master hard drive (windows on the slave) not realizing that the system partition is always on the master for windows.

Managed to get a working system again by making the windows drive master, booting into the windows setup cd recovery console and running:

copy D:\i386\ntldr C:\
copy D:\i386\ntdetect.com C:\
bootcfg /Rebuild

And then reinstalling ubuntu.

---

### Post by Sale on 2006-07-12
> **SWR said:**
> Hehe, well, I have all my music backed up on my laptop, nothing else...
Now it says
Booting 'Microsoft Windows XP Professional'

root (hd0,1)
Filesystem type is ext2fs, partition type 0x83
savedefault
makeactive
chainloader +1

Error 13: Invalid or unsupported executable format


Now what?

I just found a solution for this proble (at least, it works for me, I had pretty much the same one after this mornings kernel 2.6.15-26-386 update)

Until this morning, my menu.lst (the part thet loads Windows) used to look like this:

> 
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


...and after updating to 2.6.15-26-386 I was recieving the same error message as in the quoted post.

Now, it looks like this:

> 
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
chainloader	+1


Note the change from hd1 to hd0 in the "root" line and "#" characters in front of the "map" lines.

In other words, you need to point Grub directly to the hd where Windows is installed, without any remaping :)

Good luck :)

BTW, my Ubuntu loading part of menu.lst looks like this:
> 
title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot


---

### Post by molly_001 on 2006-07-12
To Sale --
To krazyd --

You have no idea how helpful the solutions you posted above could be to others.  I've been watching about a half dozen people come into the forums EACH DAY with the "Help! I just installed Ubuntu and now I can't boot into Windows" problem.  The problem and description of problem is remarkably similar in each case.

Would you two consider posting these solutions at my web site -- [http://www.commonmancomputing.com](http://www.commonmancomputing.com) ?  You can have your own page for it, and take as much time as you wish to describe what you did, what problem presented itself, your hardware config, and most importantly, how you managed to fix the problem.

Thank you,
molly

---

### Post by umattu on 2006-07-12
I had a similar problem once uopon a time. I can't remember the specifics surrounding what was happening but I can tell you that I thought Win XP was dead. At this point I could of cared less if my linux install was intact I just wanted my Win XP back. What I wound up doing was booting to my XP cd, starting the recovery console and uasing the command "fixmbr" as soon as I did that I could boot into windows. You could then configure boot.ini to give you the option to boot linux. I can't remember exactly what to enter there (I only use win XP at work now)I know this isn't a very explainitory post but if you get to the end of the line try "fixmbr"

---

