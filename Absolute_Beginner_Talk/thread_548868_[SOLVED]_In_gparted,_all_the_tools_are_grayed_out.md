---
title: "[SOLVED] In gparted, all the tools are grayed out"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-09-11
I just downloaded and installed gparted in my Feisty 7.04, because I want to downsize the Windows partition on my external hard drive so I can add another partition for my Linux partition. That way I'll be able to backup both the Windows and Linux partitions of my computer. 

But all the tools of gparted are grayed out. What to speak of for the external hard drive, even if I use gparted to view the two partitions of my computer's hard drive and click on one partition and then the other, still all the tools such as "Resize/Move" etc, are grayed out.

How do I activate the tools so they won't be grayed out?

---

### Post by reckless2k2 on 2007-09-11
i'm sure they are greyed out because they are active partitions. being that they are mounted. you need like gparted or parted magic on a cd and boot from it. then you can do that biz. if you are resizing windows though, you have to defrag it a few times to get it packed in as close as possib;e before resizing it using gparted cd. i happen to like parted image better. doesn't matter. they are both small and easy to use. back it all up just in case you blow up though. haha

---

### Post by qpieus on 2007-09-11
The tools are grayed out because your various partitions are mounted. Gparted won't let you work on mounted partitions. I've had way better luck with the live cd version of gparted, located  at:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You boot off this live cd and it will NOT mount any of your drives, so then you are free to use the gparted tools on them.

The other option, since you are talking about an external drive, is to unmount it and then try your installed version of gparted. I've tried that before, too, and still run into the gray tools thing. So I just go with the live cd if I want to mess around with my drives....

---

### Post by swarup on 2007-09-11
I see. But regarding this matter of the drive being mounted, does that apply to the external hard drive as well? I could plug it in and then, when it mounts, give the order to unmount it-- but leave it plugged in. Then should it work? Or is it that, even with the external hard drive, the only way to downsize the windows (Fat32) partition is to boot my entire computer from the gparted live cd? If it is like that, that to do any work one has to boot from the live gparted cd, then what is the point of even being able to download the program onto one's computer. It seems like having gparted on my computer's hard drive is useless, because all the tools will always be greyed out.

[This is a reply to Reckless2k2. When I wrote this, I hadn't seen the posting of qpieus-- which clarified part of my question. But the last part of the above still stands-- that if it is like this, then what is the point of being able to even put gparted on one's hard drive?]

---

### Post by swarup on 2007-09-11
Another related question:

Regarding the hard drive of the computer itself: If I have a dual boot Windows/Feisty and have found that I don't need all the space I originally allocated to the Windows partition, can I use the gparted livecd to boot up and downsize the Windows partition, and then expand the Feisty partition? Or is it  that once this has all been set up and is in use, one cannot change things.

---

### Post by qpieus on 2007-09-11
> **swarup said:**
> Another related question:

Regarding the hard drive of the computer itself: If I have a dual boot Windows/Feisty and have found that I don't need all the space I originally allocated to the Windows partition, can I use the gparted livecd to boot up and downsize the Windows partition, and then expand the Feisty partition? Or is it  that once this has all been set up and is in use, one cannot change things.
yes, that should work (although I have not tried that particular maneuver).

And regarding your previous post - yes, you should be able to unmount your external drive, leave it plugged in, and use the installed gparted to work on the drive. But like I said before, I haven't had a lot of luck with the installed version of gparted, even working with what I thought was an unmounted partition. So yes, I agree, the installed gparted is pretty useless.

Please remember to back up any important data before you go all Chuck Norris on your partitions. I haven't lost data with it, but there's always that possibility...

---

### Post by swarup on 2007-09-11
> **qpieus said:**
> yes, that should work (although I have not tried that particular maneuver).

And regarding your previous post - yes, you should be able to unmount your external drive, leave it plugged in, and use the installed gparted to work on the drive. But like I said before, I haven't had a lot of luck with the installed version of gparted, even working with what I thought was an unmounted partition. So yes, I agree, the installed gparted is pretty useless.

I tried unmounting the external hard drive, but once I did that, gparted did not even recognize there was an external hard (even though it was still plugged in).

So I tried booting from the gparted livecd, but when I did that then even though the external hard drive was plugged in from the very beginning of the boot-up, still gparted did not recognize that there was an external hard drive connected. i.e. there was no other drive present to switch to in the gparted window.

My external hard drive is a pcmcia connection. And I saw when the livecd was booting up, that at a certain point it checked the pcimcia connection and right at that time, the external hard drive turned on. So I know that the livecd identified the pcimcia connection. But I don't know why gparted is not seeing the external HD even via livecd. 

What should I do to get the ext HD recognized by live cd?

> **qpieus said:**
> Please remember to back up any important data before you go all Chuck Norris on your partitions. I haven't lost data with it, but there's always that possibility...

If I tried to resize the two partitions of my computer's HD, I'd certainly back up the data (although first I need to get the Linux partition set up on my back up HD with gparted!)

And as for when I downsize the Windows partition on the External HD, I don't know where I'd put that data to back it up. That IS my backup HD.

---

### Post by swarup on 2007-09-12
I hope someone can help with the above situation. Here it is in a nutshell: 

The Windows partition now takes up my entire backup hard drive, and I need to downsize it and put a 2nd partition on it for Feisty so I can start doing backups of my dual boot computer. I tried with livecd as well as with gparted in my Feisty install, but the gparted of livecd doesn't acknowledge that there is an external HD, and using the gparted of my computer, no matter what I do the gparted tools remain grayed out when I look at the external hard drive.

The external hard drive is a pcmcia connection, and I know the livecd sees it because at a certain stage of the boot up it acknowledges the pcmcia connection and right then, the external HD starts running. But when the bootup finishes and I open gparted, I cannot turn its attention to the external drive. It only shows the internal harddrive in its register. So what should I do to get the external HD recognized in gparted (livecd) so its downsize tools etc will be usable?

---

### Post by mostwanted on 2007-09-12
You did open it using sudo or gksudo, right?

---

### Post by swarup on 2007-09-12
> **mostwanted said:**
> You did open it using sudo or gksudo, right?

Are you referring to how I open gparted inside my Feisty install? No, nobody said I need to open it that way. I just go to System>Administration>GNOME Partition Editor. Is that the wrong way to open it?

I don't think your question pertains to my use of the livecd, does it? Actually I should be precise and state that I've been using the Rescue livecd. It has gparted on it. When it boots up, then you just right click on its desktop and select "gparted". But you're not referring to sudo/gksudo for this, are you? (I do also have the actual gparted livecd, but as far as I understand the gparted on both livecd's is the same thing.)

---

### Post by jw5801 on 2007-09-12
The gparted CD is a much newer version of GParted than on the Ubuntu LiveCD. And you don't need to use gksu if you opened it from the menu, it'll ask that automatically anyway. It's not actually possible to run GParted within your install without root permissions. In your feisty install, let, Ubuntu mount your external drive then use gparted to unmount it and you should be able to play with it then. You defineately can't see your external drive in the devices drop-down list in the top right hand corner? Also to stop ubuntu automagically mounting your drive while you're trying to partition it you might want to run ```
sudo killall gnome-volume-manager
```

---

### Post by swarup on 2007-09-12
Ok, I tried running the gparted I have in my Feisty install. And this time I started gparted using gksudo. But it didn't make any difference. When I point gparted to the external hard drive, all the gparted tools are still grayed out.

I don't care whether I do the downsize of my external drive's windows partition using the gparted livecd or using the gparted internal to my Feisty. But I need SOME way to work. How can I get this done?

---

### Post by jw5801 on 2007-09-12
When you're in GParted, with the partitions on your external drive showing, right click on one of them and select unmount. Then see what happens.

By the way, if you can't see your external drive, then go to "File > Refresh Devices" and it should appear.

---

### Post by swarup on 2007-09-12
Just now saw your posting. Somehow I missed it as it went onto the second page of the thread.

> **jw5801 said:**
> The gparted CD is a much newer version of GParted than on the Ubuntu LiveCD.

I am not using the Ubuntu Livecd.

I have two separate livecd's with gparted on them. As far as I am aware, both are quite new. I just made both cd's from fresh downloads around 3 weeks ago. One is the actual gparted livecd. And the other is called "rescue livecd". It is a livecd with a variety of applications on it, one of which is gparted. But it has no distro on it. It has nothing to do with the Ubuntu LiveCD.

> **jw5801 said:**
> And you don't need to use gksu if you opened it from the menu, it'll ask that automatically anyway. It's not actually possible to run GParted within your install without root permissions. 

I see. I just tried it with gksudo because someone on this thread suggested that I should.

> **jw5801 said:**
> In your feisty install, let, Ubuntu mount your external drive then use gparted to unmount it and you should be able to play with it then.

Ok. I'm not sure where the command is in gparted to unmount the external drive. I'll have another look, but till now I hadn't noticed any such command.

> **jw5801 said:**
> You defineately can't see your external drive in the devices drop-down list in the top right hand corner? 

When I use the gparted inside feisty, then sure I can see my external drive in the devices drop-down list in the top right hand corner? And if I point to it, then it comes under view with all the info available about it etc. But all the gparted tools for manipulating it, downsizing it etc, are grayed out.

For that matter, when I point to the internal drive's feisty partition then the tools are grayed out too. It is only when I point to the internal drive's Windows partition, that the tools light up ready to be used.

> **jw5801 said:**
> Also to stop ubuntu automagically mounting your drive while you're trying to partition it you might want to run ```
sudo killall gnome-volume-manager
```

ok. But I guess first we'll have to solve the above problem of grayed out tools.

---

### Post by Maestro23 on 2007-09-12
Hey swarp, I know you've got alot going on.  I saw this thread, and just wanted to bring it to your attention.

[http://ubuntuforums.org/showthread.php?t=428799](http://ubuntuforums.org/showthread.php?t=428799)

Hope it helps man. If you've already saw it or tried what is in it, disregard.  Good luck man.

*Make sure the drive is not mounted.

---

### Post by jw5801 on 2007-09-12
EDIT: Beat me to it :p

---

### Post by swarup on 2007-09-12
> **jw5801 said:**
> When you're in GParted, with the partitions on your external drive showing, right click on one of them and select unmount. Then see what happens.

I tried it. I right clicked on "unmount" while the external drive was under view. And then it just gave a message in the lower left corner of the screen, "scanning all devices". And the orange progress bar has been moving left-right-left-right etc for 2-3 minutes. It doesn't look like it is going to stop any time soon. In short, I don't think this command is working for some reason. Somehow, it is not registering properly with gparted.

Note: I further checked by starting Nautilus, and found that indeed the external drive is not even unmounted. It is fully registered still in Nautilus and I can view all its contents. So that means that gparted did not even execute the "unmount" command when I gave it. It just froze up the application. Perhaps when the drive is being viewed in gparted, it is not permitted to unmount it at that time?

> **jw5801 said:**
> By the way, if you can't see your external drive, then go to "File > Refresh Devices" and it should appear.

It was only using the rescue livecd that I couldn't see the external drive. I could try it again, but somehow I don't think that the above maneuver is going to help in that scenario. The external drive was plugged in throughout the entire bootup process. If livecd were going to register it, it surely would have done so.

---

### Post by jw5801 on 2007-09-12
Can you unmount the drive on your desktop?

---

### Post by swarup on 2007-09-12
> **jw5801 said:**
> Can you unmount the drive on your desktop?

Yes. I did that (using Nautilus, actually), and the drive unmounted just fine. 

But I have already tried that previously, and so in reply to your possible next question, -- No, once i've unmounted it in Nautilus, but kept it physically connected, then gparted cannot see it at all and it does not appear in the drop-down menu.

---

### Post by JBAlaska on 2007-09-12
Coincidently I tried gparted for the first time tonight, I used the ubuntu live cd and right clicked the drive icon on the desktop to unmount the disk..unfortunately ubuntu kept automounting the drive  when I loaded or rescanned with gparted.

Then I ran "gnome-volume-properties" in a term and unchecked all the boxes..success the options in gparted were available..I started to resize my partition and gparted threw a unspecified error..twice..

So I gave up booted winblows and used acronis disk director to resize my partition, I no this is a cop out..but gparted didn't work for me, acronis went off without a hitch

---

### Post by jw5801 on 2007-09-12
> **swarup said:**
> Yes. I did that (using Nautilus, actually), and the drive unmounted just fine. 

But I have already tried that previously, and so in reply to your possible next question, -- No, once i've unmounted it in Nautilus, but kept it physically connected, then gparted cannot see it at all and it does not appear in the drop-down menu.

Did you use the "Refresh Devices" option? I just reformatted a spare usb drive I had lying around and the same thing happens. Once I unmount it it disappears from the list, but if I refresh the list it comes back again, unmounted so I can do whatever I want to it,

---

### Post by jw5801 on 2007-09-12
> **JBAlaska said:**
> Coincidently I tried gparted for the first time tonight, I used the ubuntu live cd and right clicked the drive icon on the desktop to unmount the disk..unfortunately ubuntu kept automounting the drive  when I loaded or rescanned with gparted.

Then I ran "gnome-volume-properties" in a term and unchecked all the boxes..success the options in gparted were available..I started to resize my partition and gparted threw a unspecified error..twice..

So I gave up booted winblows and used acronis disk director to resize my partition, I no this is a cop out..but gparted didn't work for me, acronis went off without a hitch

This is why I always suggest that people use the GParted LiveCD to play with their root partitions. Ubuntu keeps being helpful and remounting the disk for you. If you kill the gnome-volume-manager process (as I mentioned earlier) you should avoid this problem, however it's best to use the GParted LiveCD anyway, it's a much better version of the software.

---

### Post by swarup on 2007-09-12
> **jw5801 said:**
> Did you use the "Refresh Devices" option? I just reformatted a spare usb drive I had lying around and the same thing happens. Once I unmount it it disappears from the list, but if I refresh the list it comes back again, unmounted so I can do whatever I want to it,

When I unmount the external hard drive through Nautilus, and then click on "Refresh Devices" in gparted, that just throws gparted into an endless cycle of "scanning all devices" which it never comes out of. Ultimately I have to close down the application. So for some reason, that maneuver isn't working. Don't know why. Further suggestions?

---

### Post by armandh on 2007-09-12
try parted magic
[http://partedmagic.com/](http://partedmagic.com/)

---

### Post by swarup on 2007-09-12
> **armandh said:**
> try parted magic
[http://partedmagic.com/](http://partedmagic.com/)

Ok, I'll burn a disc now and see how it works. I went to the site and checked out what is on it. It has the same version of gparted that my rescue livecd has on it. Do you think it'll do anything different? Anyhow, I'll try it and see. Maybe it will work its "magic"!

---

### Post by swarup on 2007-09-12
I made the partedmagic livecd, but neither of my two computers would boot from it. The disc is an iso, that is, a raw image of the iso that was downloaded. So I presume that is the way it should be. I made it via the Gnome Baker CD burner, just imported the iso file using "add" in the burner program, and burned it. Should have worked, right? It worked like that with my live rescue cd, and with the gparted livecd. But I tried it on two computers, one a dual boot Vista/Feisty, and the other Win98/Feisty. Neither would accept it.

It seems like I've exhausted all the possibilities I can think of for accessing my Ext HD to downsize its Windows partition: the gparted in feisty has all the tools grayed out; the gparted on the live rescue cd can't see the external HD; the partedmargic livecd won't boot.

So what is the next step? How will I be able to downsize the Win partition on my external HD so to be able to add an ext 3 partition onto it?

---

### Post by swarup on 2007-09-12
Could someone please give some guidance about the above described problem?

Thanks!  :)

---

### Post by Maestro23 on 2007-09-12
> **swarup said:**
> Could someone please give some guidance about the above described problem?

Thanks!  :)

If it was burned properly, then it should have been recognized.  Did you burn it as an image and not just a data cd with the image on it? Did you burn at a slow speed?  I've never used Gnome Breaker, so I can't help you there. Might want to try a different burning program.

---

### Post by swarup on 2007-09-12
> **Maestro23 said:**
> If it was burned properly, then it should have been recognized.  Did you burn it as an image and not just a data cd with the image on it? Did you burn at a slow speed?  I've never used Gnome Breaker, so I can't help you there. Might want to try a different burning program.

Ok, what burning program would you recommend?

I did not see any option in Gnome Baker burner for burning it AS an image rather than as a data disk with the iso image on it. 

Please let me know a burning program that would have this option in it.

---

### Post by s26c.sayan on 2007-09-12
> **swarup said:**
> Are you referring to how I open gparted inside my Feisty install? No, nobody said I need to open it that way. I just go to System>Administration>GNOME Partition Editor. Is that the wrong way to open it?

I don't think your question pertains to my use of the livecd, does it? Actually I should be precise and state that I've been using the Rescue livecd. It has gparted on it. When it boots up, then you just right click on its desktop and select "gparted". But you're not referring to sudo/gksudo for this, are you? (I do also have the actual gparted livecd, but as far as I understand the gparted on both livecd's is the same thing.)

My limited experience suggests that you need to run the partitioner program (gparted) as **superuser** if you want to work with partitions!!

---

### Post by swarup on 2007-09-12
> **s26c.sayan said:**
> My limited experience suggests that you need to run the partitioner program (gparted) as **superuser** if you want to work with partitions!!

I'm not certain what you mean by "superuser", but someone else suggested one must run it from terminal using sudo or gksudo (which I tried without result), and then another person said it isn't needed anyway, since when gparted opens it always asks you for your password, anyway.

---

### Post by s26c.sayan on 2007-09-12
Superuser =  root

If even that didn't work, then problem is elsewhere!!

---

### Post by swarup on 2007-09-13
To bring closure to this discussion, I want to express here that ultimately jw5801's suggestion worked, and worked flawlessly. That is, his suggestion to use the gparted on my Feisty install to manage the partition work on my Ext HD. I unmounted the Ext HD but kept it connected, and I had to wait a little while but the gparted utility ultimately stopped "scanning for drives" and accepted the unmounted Ext Drive. I was then able to do the partition work. 

So for the benefit of anyone else who may read this thread wanting to use the tools discussed, they should know that jw5d01's suggestion works well. Many thanks to him for all his help.

I will mark this thread as SOLVED.

---

### Post by eljaydub on 2007-09-22
I'm having similiar trouble to swarup but nothing is working. JBAlaska, looks like you succeed in doing what I'm trying to do. Here's my thread:
[http://ubuntuforums.org/showthread.php?p=3410375#post3410375](http://ubuntuforums.org/showthread.php?p=3410375#post3410375)
I'd appreciate any advice anyone can offer!

---

