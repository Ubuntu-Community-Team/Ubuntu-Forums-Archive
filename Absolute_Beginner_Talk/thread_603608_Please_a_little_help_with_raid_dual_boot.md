---
title: "Please a little help with raid dual boot"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by Dudeman02379 on 2007-11-05
Just to get started I want to say that I have been reading tons of threads about my situations similar to mine.  I just want to make sure that I have a clear understanding of exactly what I should be doing before I go make my situation any worse.  
So I have two 74gb drives in a nvidia (fake) raid 0.  I have vista and xp loaded on that array and working fine.  I then install a third 80gb sata drive.  I did not add that drive to any array.  I tried to install ubnutu 7.10 onto the 3rd drive.  When the computer rebooted I get grub error 25.  So that's where I am at.  I think that the problem is that grub is loaded on drive 1 instead of drive 3.  I hope that didn't mess up my raid array.  From what I have read it seems like this is what I should do.

1.  Reinstall ubuntu to the third drive and tell it to install grub on the third drive also.
2.  Change my bios config to try to boot of the third drive instead of the aray.
3.  Use a vista cd to recover the windows boot loader on the raid.
4.  Install raid drivers to ubuntu to recognise the array.
5.  Add an entry to grub to add Vista to the boot menu.

Please let me know if I am on the right track.  I don't have access to my computer right now because I am at work.  I am going to attack this problem when I get home today.  Luckily I knew enough to do a full acronis backup of my whole system before I started any of this so I'm not too concerned about losing my data.  I would rather not have to restore from my backup though :( .

---

### Post by ByteJuggler on 2007-11-05
Yep, that's pretty much it.  I have a similar setup to you at the moment, have Vista currenntly on a RAID set (VIA fakeraid) and Ubuntu on another single drive.  At one point in the past I even had Ubuntu installed on the fakeraid array together with Windows (at the time XP), so even that's possible.  I know you can fix Windows booting with fixmbr and fixboot from the Windows XP recovery console so something similar should be possible with Vista.  That will of course nuke Grub though, so you'd need to redo grub again as well.  

As for recognizing the RAID array under Linux, you don't so much need drivers, as just the "dmraid" package which should allow you to see the array.

---

### Post by Dudeman02379 on 2007-11-05
Thanks.  I was going to try to install ubuntu on the raid in its own partition but after reading all of the tutorials it just seemed like more than I wanted to get into.  I really hope this goes smoothly.  Anyone with any tips please let me know.

---

### Post by Dudeman02379 on 2007-11-05
OK I made some real progress but now I really need help.  This is what I have done so far.

1.  Reinstalled ubuntu 7.1 on the third stand alone drive with grub on the same drive

2.  Repaired vistas mbr

Now I depending on what drive I choose in my bios I can boot either os.  My new question is how can I get grub to recognise my vista install that is on the nvidia fake raid 0?  Where/how can I get ubuntu to see the raid and partitions and how do I edit my grub menu?  I could really use help at this point.   Please any response would be really appreciated.  My biggest reason for using this build of linux is the great community and support!

**** EDIT ****

Well I've made more progress on my own but again have a new issue.  Here is what I've done now.

1.  I changed my "/boot/grub/menu.lst" to include my vista boot loader

So now when grub starts I can choose windows or linux.  If I choose linux I am in ubuntu no problem.  If I choose windows I get my vista boot loader.  Now comes the new problem.  My vista boot loader has two options.  One for vista and one for xp.  If I choose vista there is no problem.  If I choose xp the computer reboots.  If I choose xp and hit f8 realy fast I get the startup options but safe mode and last known good also cause the pc to reboot without ever seeing any hint of xp starting.  I know this is really more of a windows issue in a linux forum but you have all been so helpful in the past I would really appreciate any advise anyone can give me.  Also I still cannot see my ntfs partitions from ubuntu.  I know I need to use dmraid somehow to see the striped raid but I don't understand what to do.  Can anyone please help?

---

### Post by Dudeman02379 on 2007-11-05
Please bump?  I can use any advice.  I would really like to keep xp because the rest of my family isn't very computer savy and likes to stay with what they know how to use.

---

### Post by ByteJuggler on 2007-11-06
Hey dude, some of us sleep too you know.  :-)  

OK, basically you have to add the following to the end of your grub menu.lst file (/boot/grub/menu.lst):

```

title		Microsoft Windows
root		(hd0,0)
makeactive
chainloader	+1

```

This assumes that from Linux/grub's point of view the Windows partition is on hard drive 0, partition zero, so the first hard drive's first partition.  If you've booted Linux from your first drive, and Windows is therefore now on a secondary drive, then this will change accordingly (e.g. if it's the second drive then it'll be hd(1,0) )  Note, you can put these entries into the menu.lst file, then try boot and if one setting doesn't work, you can edit the command line used "on the fly" inside grub, while booting/trying to boot.  Just press the "e" key and pick the line to edit (which will be the "root (hd0,0)" line) and press "e" again etc.  Eventually press "b" again to try to boot with the modified settings.  This will allow you to find sort of experimentally which drive you should use. 

OK, I'm off to work now, I'll try to get back to this and give you some more detailed instructions later, if needed.

---

### Post by Dudeman02379 on 2007-11-06
Sorry but I don't think you understood the problem.  I must not have explained it clearly enough.  I have already added the line to grub to include my windows boot loader.  That is working now.  So when grub starts I have the options for ubuntu or vista.  If I choose ubuntu it boots fine.  If I choose Vista I get my vista boot menu which includes vista and xp.  If I choose vista it boots fine.  If I choose xp my computer restarts.

Before I started all of this both vista and xp were working fine.  

My second question is how do I see my vista and xp partitions (on fake raid 0) from within ubuntu.  I want to be able to get to my ntfs data from ubuntu.  Thanks again for all of the help.

---

### Post by pjman on 2007-11-06
> **Dudeman02379 said:**
> Sorry but I don't think you understood the problem.  I must not have explained it clearly enough.  I have already added the line to grub to include my windows boot loader.  That is working now.  So when grub starts I have the options for ubuntu or vista.  If I choose ubuntu it boots fine.  If I choose Vista I get my vista boot menu which includes vista and xp.  If I choose vista it boots fine.  If I choose xp my computer restarts.

Before I started all of this both vista and xp were working fine.  

My second question is how do I see my vista and xp partitions (on fake raid 0) from within ubuntu.  I want to be able to get to my ntfs data from ubuntu.  Thanks again for all of the help.

Nested dual-boots.. sweet! 

> If I choose Vista I get my vista boot menu which includes vista and xp.  If I choose vista it boots fine.  If I choose xp my computer restarts.

It sounds like somewhere along the line the Windows boot loader got messed up. I haven't played with Vista at all (trying my best to stay away from it :-) ) so I don't know if Microsoft has changed the boot loader since XP... Can you post your boot.ini file from Vista? At least that is where the information was in XP.

As for your second question, check out this post. I think it will help you.
[http://ubuntuforums.org/showpost.php?p=3704219&postcount=6](http://ubuntuforums.org/showpost.php?p=3704219&postcount=6)

---

### Post by Dudeman02379 on 2007-11-06
I would love to post my boot.ini file but vista doesn't work the way xp did.  From what I understand it uses some sort of database to manage boot records.  I have no idea how to work with it.  I know I am probably asking too much trying to get my windows problems fixed in a linux forum.

I'll check out that link later when I get home.  Thanks.

---

### Post by ByteJuggler on 2007-11-07
As for getting your raid partition visible, install the "dmraid" package, after which you should have a mountable raid set under "/dev/mapper"

---

### Post by Dudeman02379 on 2007-11-07
> **ByteJuggler said:**
> As for getting your raid partition visible, install the "dmraid" package, after which you should have a mountable raid set under "/dev/mapper"

I did install dmraid.  So now I should have a mountable raid set under /dev/mapper?  I'm not exactly sure what that means.  How would I mount it?  Should I just browse to that folder and I should see the partitions there?

---

### Post by pjman on 2007-11-07
> **Dudeman02379 said:**
> I did install dmraid.  So now I should have a mountable raid set under /dev/mapper?  I'm not exactly sure what that means.  How would I mount it?  Should I just browse to that folder and I should see the partitions there?


Nope, you need to mount it: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_NTFS_Partitions](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Mount_NTFS_Partitions)

---

### Post by Dudeman02379 on 2007-11-08
Well after playing around trying to get xp bootable yesterday I did way more damage than good.  I amd goint to start over.  Luckily I did a backup of xp and vista before I started.  It's going to take a whole day to get this going again but at least I am pretty sure I know what I am doing this time.  I'm pretty bummed out.  I have loaded duel boot systems with ubuntu before no problem.  The raid really threw me off on this one.:(

---

