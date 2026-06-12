---
title: "Partitioning Question and some others.."
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Blots on 2007-04-19
Hi Everyone!

 This is my first post here in the Ubuntu forums, though I have lurked here for quite a while. Now, it's finally time to speak! I have a question, and I hope you guys can help me out with it. So here's the situation:

I've had Ubuntu 6.06 LTS (Dapper) for some months now, but because I've been extremely busy, I haven't had time to set it up properly. I haven't gotten to installing drivers until now, and I've hardly made any changes, for fear of messing up my system due to my skim knowledge of computers. Now due to urging from family members, I'm hoping to upgrade to 6.10 as well as getting a KDE environment. I'm a bit stumped on how to do that. I think I can install KDE, but I'm not exactly sure about updating to 6.10. 

In addition, I've just read about a swap partition, which, up 'till now, I didn't know I could have. (*cradles head in shame* Yes, I do not know much about computers) Is there any way I could repartition my drive to include a swap partition, or would I have to format my harddrive?

Oh.. and a question unrelated to Ubuntu, if that's alright..
 -- I recently got a new moniter which is supposedly better than my old one. It's widescreen and very large, but the problem is that the colors are much duller than my old moniter, and much too dull in comparison to any other moniter I've used.  Is this the moniter's problem, or have I not installed something properly?

If you've taken the time to read through this, thank you!!
- Yu

---

### Post by h0ax on 2007-04-19
KDE: You can handle installation - you said so at least ? :P

Distribution Upgrade: Simple command, but it will take a while
something like apt-get dist-upgrade ( I would search for that one, I forgot exact command )

Reading about the swap partition is good, but if you installed Ubuntu - you already have a swap partition.  It's like extra memory, but on the disk, a lot slower, but can be useful.

You probably need better video drivers on the monitor - or check the brightness / contrast options.

---

### Post by rillip on 2007-04-19
Installing KDE should be fairly trivial.  I guarentee if you search the forum for "installing kde" you'll find a tutiorial.  I believe you'll just need to run

sudo apt-get install kde-desktop

As for upgrading, you should check out the sticy at the top with the official upgrading method.

Not sure on the monitor question, I haven't fiddled with that in Linux (no need), you may be able to find drivers for it.  Try googling something about your monitor version, linux and drivers.  Is the montior similarly afflicted in Windows?

Additionally, you should have had a swap partition created by default when you installed.  The LiveCD installer uses gparted (sudo apt-get install gparted) to parition the drives.  You can see if you have a swap parition there.  If so, you can disable it temporarily and a parition you can steal some space from (not your root parition, or you'll have to boot form CD to disable it) and bump it up if you like.  If you do have to take from /, you'll have to get the gparted boot cd or use the LiveCD installer again so you can disable your / partition and resize it.

General guideline for swap is 2x your ram, however if you think about it, 1x your ram would let you put it into hybernate.  Giving too much swap will actually slow your system down, as it will write more and more to the (relatively) very slow HDD instead of letting you know "hey, you're doing too much."

I use KDE, so to disable my drives the easiest way is to go to the K-menu, system settings, disks and file systems.  It's pretty obvious from there; not sure what it looks like in Gnome.

---

### Post by Blots on 2007-04-19
Rillip and h0ax, thanks for your replies!

You make my problems seem so easy. Well, I guess they are. [I should've read up on the upgrade, sorry.] I've successfully installed Kubuntu on my main computer and am in the process of updating another. As for the moniter, the problem persists in both Windows XP and Ubuntu. Hmm.. I'll google that one later.

Thank you for the help!
- Yu

---

### Post by antoz on 2007-04-19
You can have a look at your partitioms just click System-Administration-Disk-Partitions, I am sure you will have a swap partition as was mentioned before in the other posts.
As far as your monitor if this is your first LCD depending on the make they are not as bright as the old carthode ray monitors, maybe there are some settings on the monitor itself to improve the brightness etc...

---

