---
title: "I'm done! I need help getting Linux off of my hard drive"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Native Dialect on 2007-03-28
About a month ago, I was reading up on Linux on Wikipedia. Needless to say, it seemed to offer something enjoyable. A learning experience that was free of pitfalls. Or at least so I thought. A month after having installed it, I've run into problems time and time again. From problems with my resolution settings not being retained, to programs (GAIM mostly) crashing at random. Between that, and the some what unfriendly interface of the Terminal...I've decided that Linux just isn't for me. 

So I booted up windows (I was dual booting the entire time I had Linux) and decided to merely format my slave drive, because that is what I had Linux installed to. The format went beautifully. I transfered my old backed up video files to my newly formatted hard drive...and went about business for the rest of the day. I shut down Windows and went to bed feeling alright...until this morning. I turn on my machine and something familiar pops up. The GRUB 1.5 loading screen. I thought this to be odd as I had formatted the drive that Linux was on. But sadly...it was to be true. And now, my computer can no longer boot windows. Why? Because GRUB can't load. Which makes sense, because I deleted Linux...or at least I thought I did. So here I am...running the Live CD, seeking your help. How do I remove Linux completely, so I can go back to running Windows only? I don't want to try and reinstall Linux on a small partition of my slave drive, just so I can use Windows. Is there any way to help, or am I just screwed, for lack of a better word?

---

### Post by aysiu on 2007-03-28
You need to use the *fixmbr* utility on the Windows CD.

Microsoft has an article on this:
[http://support.microsoft.com/kb/247804](http://support.microsoft.com/kb/247804)

---

### Post by oilchangeguy on 2007-03-28
how did you format the slave drive?

---

### Post by igknighted on 2007-03-28
The issue is that you installed grub to your windows drive and not the linux drive.  You need to insert the windows install disk, go to the recovery shell and type "fixmbr" to restore the windows bootloader to that drive.

---

### Post by Native Dialect on 2007-03-28
1)Thank you all for helping to clear that up.

2)If you boot Windows and go to my computer, you can right click it and you'll see some options. Select "Management". From there you should see an option for "Disk Management." This will show all drives connected to your computer (using Windows or not) and from there you can partition, repartition or format a drive.

---

### Post by kahrytan on 2007-03-28
[Fdisk ]("http://support.microsoft.com/kb/69013")/mbr will work just fine as well.

The reason your computer can't boot is because Grub is installed on the Master Boot Record. And accesses the Linux Partition. When you deleted the Linux partition, you deleted the config file for Grub. Thus Disabling Grub.

You shouldn't give up on Linux. Take small steps. You don't have to use Linux fulltime.

---

### Post by NicoleM on 2007-03-28
and just as a clarification about how this happened, i have a similar format for my dual boot setup...windows on primary master, ubuntu on primary slave.

your bios can only pick one drive to boot from on startup (unless you wanted to change bios settings every tim eyou wanted to boot into a new OS, but even linux isn't that much of  a pain ;)) so even though you installed linux on your slave drive, GRUB has to be installed in the MBR of the primary master drive in order for it to affect the boot sequence and be recognized on startup.

since you formatted the slave drive, I assure you linux is gone and once you follow the advice that's been given here GRUB will be too and you should be able to boot into windows as normal.

also, conversely, if you had to format the primary drive for whatever reason and reinstall windows you would have not been given any boot options but only because you erased grub, not the linux OS.

it looks like i was beated to the punch on the explanation though :)

---

### Post by arbulus on 2007-03-28
Don't give up on Linux completely.  The greatest thing about the GNU/Linux world is the diverstiy.  There are many different distros that you can choose from that work better or worse on different hardware.   For example, I tried Fedora Core 6 and Yellow Dog on my iMac, and both of them performed very poorly.  Neither of them worked well with my hardware, but Ubuntu worked like a dream.  I've not tried any other distros installed, but like I said, there are so many choices that you are bound to find one that would work well for your system.

On my computer (iMac G5), I have 2 partitions on an 80GB hard drive: one that is 70GB for OS X and one that is 10GB for Linux.  I use that 10GB partition to play around with different distros and OS X is never bothered by it, and I can boot to that whenever I like.  So you might be able to try a dual-boot setup on your system so that you can experiment with different distros and see which one works best for you.  Just remember, most of us didn't start out in Linux full time: it was either in a dual-boot or installed on a spare computer separate from our main workstation. 

Just remember, no OS is going to give you an experience that is free of problems, and when moving from one OS to another, there will always be a learning curve.  I just hope this experience hasn't soured your outlook on Linux completely.

Best of luck to you.

---

### Post by GSF1200S on 2007-03-31
> **arbulus said:**
> Don't give up on Linux completely.  The greatest thing about the GNU/Linux world is the diverstiy.  There are many different distros that you can choose from that work better or worse on different hardware.   For example, I tried Fedora Core 6 and Yellow Dog on my iMac, and both of them performed very poorly.  Neither of them worked well with my hardware, but Ubuntu worked like a dream.  I've not tried any other distros installed, but like I said, there are so many choices that you are bound to find one that would work well for your system.

On my computer (iMac G5), I have 2 partitions on an 80GB hard drive: one that is 70GB for OS X and one that is 10GB for Linux.  I use that 10GB partition to play around with different distros and OS X is never bothered by it, and I can boot to that whenever I like.  So you might be able to try a dual-boot setup on your system so that you can experiment with different distros and see which one works best for you.  Just remember, most of us didn't start out in Linux full time: it was either in a dual-boot or installed on a spare computer separate from our main workstation. 

Just remember, no OS is going to give you an experience that is free of problems, and when moving from one OS to another, there will always be a learning curve.  I just hope this experience hasn't soured your outlook on Linux completely.

Best of luck to you.

Its not necessarily a bad thing, but some people just dont like Linux. Theyre attracted to it because they hear its stable and offers a lot of cool applications. When they are faced with the hardware difficulties of setting up Linux, they begin to see another side. Sometimes they dont like it.

I agree with you... I really like my gaming laptop now.. Ive got XP running lean and like 7 of the most awesome games for it, Ive got Ubuntu Linux running as my main OS, and all I have to do is tell Grub what world to take me to. But the setup was tough, and I took many smoke breaks a little frustrated trying to come up with a solution to my problems... I decided to stay with it, and others decide they would rather not.

---

### Post by hulland on 2007-03-31
I am just about to re-format the Ubuntu partition when I read this post..sorry to be an ignoramous ( My experience is that a newbie to Ubuntu is certainly made to feel like a dunce, unless you are familiar with the codes and logic needed before starting to experiment with Linux--I feel just like NATIVE DIALECT too )--but HOW do I get rid of GRUB --- BEFORE I dump Ubuntu then??

 Surely there must be a way without goiing down to Fdisk??

---

### Post by 23meg on 2007-03-31
[QUOTE= Native Dialect]A learning experience that was free of pitfalls.[/QUOTE]

That's an oxymoron. What article on Wikpedia gave you that impression? I'm feeling eager to go and edit it.

---

### Post by Herman on 2007-03-31
> I am just about to re-format the Ubuntu partition when I read this post..sorry to be an ignoramous ( My experience is that a newbie to Ubuntu is certainly made to feel like a dunce, unless you are familiar with the codes and logic needed before starting to experiment with Linux--I feel just like NATIVE DIALECT too )--but HOW do I get rid of GRUB --- BEFORE I dump Ubuntu then??
 Surely there must be a way without going down to Fdisk??Hello hulland, 
Here's a link to a web page I made on the subject. [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
I have done my best to make sure it's clear and easy to understand. Let me know if it isn't, and I'll work on it some more. I have that listed first on my Ubuntu install site so that people should read it before they decide to install. That way shouldn't be surprised if they ever decide to uninstall.
There are six different ways explained there you can use to overwrite Grub. Probably there are lots more ways than those to do it too.
I think you will see that it's really very simple no matter which method you choose. It's actually not a major operation at all. It's certainly nothing to worry about.   :)

Regards, Herman :)

---

### Post by NicoleM on 2007-03-31
> **hulland said:**
> I am just about to re-format the Ubuntu partition when I read this post..sorry to be an ignoramous ( My experience is that a newbie to Ubuntu is certainly made to feel like a dunce, unless you are familiar with the codes and logic needed before starting to experiment with Linux--I feel just like NATIVE DIALECT too )--but HOW do I get rid of GRUB --- BEFORE I dump Ubuntu then??

 Surely there must be a way without goiing down to Fdisk??

no worries about your questions, this is the last place to belittle someone looking for help whether it's with installing/using ubuntu or getting rid of it :)

i'm 99% sure it's the same process.

if you installed grub in the MBR initially then just follow the directions above to get rid of it.  there's no other safe/easy way to edit the MBR that i'm aware of (although I'll never say never)

if you're unsure of where you installed grub in the first place you can go ahead and nuke the drive that ubuntu is on and if all seems well then you don't need to use the fixmbr instructions previously posted and you should be all set.  if you get the error similar to this thread then go ahead and follow the instructions.  

not sure what you're implying by "surely there must be a way without going down to fdisk" but with the links provided and the support of the forums it's a very painless process, i promise.

---

