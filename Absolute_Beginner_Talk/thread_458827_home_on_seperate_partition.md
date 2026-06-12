---
title: "/home on seperate partition?"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by SolidusRegime on 2007-05-30
I was wondering if this was possible, that way I wouldn't lose all my important files, such as music, videos and work documents when I re-install new versions?

Note: I will be performing this on a fresh install on my laptop. So is it possible to do it via the LiveCD?

---

### Post by Outrunner on 2007-05-30
Yes and actually, it's  recommended that you do so. You just make an extra partition and set it's mount point to /home

---

### Post by ambush_xx on 2007-05-30
So If we do so, the patition will not be formatted or changed when we reinstall ubuntu??

---

### Post by SolidusRegime on 2007-05-30
Would there happen to be a step-by-step tutorial on how to do this on install?

---

### Post by Outrunner on 2007-05-30
Unless you set it to be formatted when you reinstall then no, it won't be formatted.

EDIT: I don't know, at least I haven't seen one, but it's really not that hard.

---

### Post by userundefine on 2007-05-30
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Outrunner on 2007-05-30
> This guide is for creating a separate /home partition if you already installed Ubuntu

Not quite what they were looking for, is it?

---

### Post by SolidusRegime on 2007-05-30
Could you possible step me through it, I am on the manual partition screen, kind of looks like this..

Device...............Type...........Mount Point...........Size.................Used:
/dev/sda
.../dev/sda1.........ext3.........../media/sda1...........58498 MB..........3000 MB
.../dev/sda5.........swap....................................1521................0 MB

The dots are just spacers...since the forum removes multiple spaces.
Thats kind of what the screen looks like. Mind you I am doing a fresh install, so it currently has Ubuntu installed on it.

---

### Post by userundefine on 2007-05-30
Ah didn't realize he hadn't installed.

Auto-partitioner will start up.  Give you swap and / partitions.  Reduce / down to 10GB or so, leaving the rest as 'unformatted'.  Then, make a new partition of the 'unformatted' space and make the mount point /home.

---

### Post by DigitalAxis on 2007-05-30
I've got my system set up that way; I did it with an alternate liveCD though; it was a matter of going through and creating not one, but three partitions in the empty space left for Ubuntu. (I actually made four, but I'm starting to regret making a separate partition for **/tmp**)

Anyway, I believe all you need to do is create a swap partition, and TWO Ubuntu partitions.  Hopefully in the liveCD there's a place afterwards to specify its mount point.

The key word here is  'mount point'.  If you can find a way to do it, make sure one (Kubuntu plus a bunch of large extra software, fonts, MIDI Soundfonts, TeTeX, and apparently all the DEBS from KDE 3.5.7 are sitting happily in my 5 gigabyte **/** partition, but 10 GB isn't a bad idea) is labelled as **/**; and the other probably larger one needs to be labelled as **/home**.

The installer should see the **/home** partition, put all your personalized files THERE, and set it up to be transparently mounted under **/home**

---

### Post by SolidusRegime on 2007-05-30
Okay, but as for installing programs, where should that be done, in /home?

---

### Post by freebird54 on 2007-05-30
Definitely doable by the Live CD.  Started out that way myself...

One thing though - don't try to use the same /home for multiple distros (or versions of Ubuntu) can lead to too much confusion!

Does not hurt, on the other hand, to have a /data partition shared many ways. easy to back up what matters that way...

---

### Post by SolidusRegime on 2007-05-30
I formatted the single partition, leaving just unformatted and a 1.5gb swap partition. I then created 2 new partitions, one being 10gb and mount point as / and the other being 48.5gb and mount point as /home. I am now installing the system, so I will let you know how everything goes then get back to you.

Thanks heaps guys.

---

### Post by userundefine on 2007-05-30
> **SolidusRegime said:**
> Okay, but as for installing programs, where should that be done, in /home?
When you install something in Ubuntu, 99% of the time you'll be using a package manager that will handle where to place the files, and that won't be in your /home.  If you have to compile and install something yourself, then you can leave it in your /home or move it to /usr/local, which is for locally built programs.  This differs from the package manager which will place things in simply /usr.

---

### Post by SolidusRegime on 2007-05-30
Which is more secure when re-installing the OS. I don't want broken links and apps in my home dir after I install new Ubuntu releases..

---

### Post by userundefine on 2007-05-30
It's best to let the package manager take care of everything for you, and that wouldn't be a concern.  However, if you did have to install a program by hand, if you left it in your /home, then it'll be run fine in your new Ubuntu upgrade provided the dependencies are fulfilled.

---

### Post by SolidusRegime on 2007-05-30
Alrighty, so anything obtained using sudo apt-get or using Automatix2 will be saved in the /usr/local section?

---

### Post by plcdfa on 2007-05-30
No, as userundefine wrote they will go to /usr. (In fact generally a newly installed program will place stuff in /usr/bin and /usr/share. Libraries go to /usr/lib etc.) /usr/local is for the programs you compile by hand.

---

### Post by SolidusRegime on 2007-05-30
Alrighty, well thanks heaps guys, I have it all working. I will try to keep /home for music and docs only. Don't want any broken crap in there. So if I ever do a system reinstall, I just install it into the 10GB partition? Will I need to do anything to gain access to my /home?

---

### Post by Outrunner on 2007-05-30
> **SolidusRegime said:**
> Will I need to do anything to gain access to my /home?

Don't think so.

---

### Post by plcdfa on 2007-05-30
> **SolidusRegime said:**
> Alrighty, well thanks heaps guys, I have it all working. I will try to keep /home for music and docs only. Don't want any broken crap in there. So if I ever do a system reinstall, I just install it into the 10GB partition? Will I need to do anything to gain access to my /home?

Yes, you will have to set the 10 gig partition mount point as / , and the other as /home, just like now, but next time you should only format the / partition. This way you'll keep all your data and settings.

---

### Post by SolidusRegime on 2007-05-30
Okay, so don't tick to format /home? But does that mean there will be 2 home directories?

---

### Post by plcdfa on 2007-05-30
> **SolidusRegime said:**
> Okay, so don't tick to format /home? But does that mean there will be 2 home directories?
Not at all. You have to mount the same home partition to /home and not format it. After install you'll have all your old stuff in your home folder. (Just be sure to use the same username.)

---

### Post by SolidusRegime on 2007-05-30
Alright then, I will have to see how I go with it, thanks heaps again guys.
If I need any further help, I will let you know. :)

---

### Post by eldepeche on 2007-05-30
One thing to be aware of is your user ID number. If you're the only user on this machine, as it sounds like you are, then everything ought to be fine, as Ubuntu uses the same ID numbers for each install (beginning at 1001, I believe). 

If you're not the only user, then when you reinstall, you have to make sure that users have the same user ID numbers as they did before. Otherwise you can get ugly permissions problems. I think there's an option somewhere in the initial installer to manually choose a user ID number.

---

### Post by moljac024 on 2007-05-30
I have performed multiple OS reinstalls in the past few weeks and setting up a home partition is easy as pie...Just always mount the same partition as home and don't tick format option....even if you choose a different username on another install you can just go up a directory from home and there you will see 

current username <dir> - your current home folder
former username  <dir> - your former home folder

You can just use a simple cut+paste operation

(also i've found that it might be a good thing to get rid of some of the settings in home folder as they can cause trouble sometimes)

---

