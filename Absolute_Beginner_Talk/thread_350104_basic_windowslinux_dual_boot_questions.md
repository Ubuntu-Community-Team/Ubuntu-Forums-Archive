---
title: "basic windows/linux dual boot questions"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by abuntoyoutoo on 2007-01-31
Hi everyone

I have wanted to dual boot my windows xp computer with linux for a while now and i want to finally have a go at it. I am also reformatting both my computer drives so i would like to do a clean install. Also, I customized my windows xp install last time I reformatted so I am confident I can manage the linux install. However I have never used linux and have zero experience in it (aren't gnomes what you put in gardens?) So I have a few questions about it.

Firstly, I want a linux distribuation that is easy to use but also is powerful for advanced users (which I may eventually become). Is ubuntu a good choice for this?

Secondly, I think you have to use FAT32 for windows to work with linux. However I've read that FAT32 isn't as safe as NTFS. So is it okay to store all your documents as FAT32?

I often use the hybernate and sleep functions on my computer, when i can't be bothered to completely turn it off. Does this still work with linux installed?

Is using linux dangerous for beginning users and can it accidently wipe stuff thats is not in its partition?

The setup I thought would be good for me is: (note that I have 2 hds)
Master HD (160GB)
primary partition 1 : windows xp and programs and documents (120GB) ntfs
primary partition 2 : linux (20GB???) ???
logical partition 1:    shared storage (20GB) fat32

Slave HD (80GB)
logical partition 1: storage (80GB) ntfs (or fat32?)

Note that there isn't a planned swap partition at the moment. I think linux needs a dedicated swap partition. Can windows also use that partition as its swap partition?

Is 20GB enough for linux and most of its useful programs?

Also, note the shared storage partition. I had that as a way to store files that could be used under both operating systems (such as documents). Is this a good way to do things?

Finally, I'm not sure whether to have my storage drive (which would have music, disk images and other large files) should be ntfs or fat32. If it was fat32 it would work with linux, but fat32 is less efficient than ntfs.

Sorry about all the questions! :) 
PS My computer specs:
AMD Athlon xp 2600+
2.13GHz, 768MB RAM
256MB 6600GT Geforce Graphics card

---

### Post by mikewhatever on 2007-01-31
1. I think Ubuntu is quite powerful, whatever you mean by that. Games aside, it is comparable to Windows OS. The easy of use really depends on your experience, the amount of time you spend and the willingness to learn something new. Please note, that your prior experience with Windows is rather a drawback then help. I think the good approach is not to expect too much in the beginning, have patience, and take things easy.
2. You do not have to use FAT32, in fact NTFS is a lot more efficient for Windows, and Ubuntu can natively read NTFS, and write to, with additional driver installed.
3. Yes, you can delete stuff outside Ubuntu partition, if the other partition is FAT32, or NTFS write is enabled. You can also do it from Windows though.
4. Ubuntu needs a dedicated swap partition.
5. 20 GB is a good size for Ubuntu partition.
6. If NTFS writing is enabled, the storage drive can be NTFS, or, you might want to save yourself the trouble, and make it FAT32.

Good Luck

---

### Post by abuntoyoutoo on 2007-01-31
Thanks for the response. This is the setup I think I should have based on what you said

Master HD (160GB)
primary partition 1 : windows xp and programs and documents (130GB) ntfs
primary partition 2 : ubuntu (26GB) 
partition 3             : pagefile (4GB)

Slave HD (80GB)
logical partition 1: storage (80GB) ntfs

I got rid of the 20GB shared storage partition on the Master HD and shared the share memory between ubuntu and windows.

Is there anything wrong with this setup?

---

### Post by mikewhatever on 2007-01-31
Don't think you'll need 4 GB of swap. What's the size of your RAM?

---

### Post by Sef on 2007-01-31
If you have 1 gb ram then you really don't need a swap partition, unless you do heavy gaming or movie editing.

---

### Post by The Foz on 2007-01-31
I would recommend having a decent sized swap partition anyway. One day you may need it, for example if you use KVM to run Windows in a Window under Linux.

Software always expands to exceed the resources available, so future proof by making sure you have plenty of swap space, ideally on a separate drive (for performance).

---

### Post by CongoJim on 2007-01-31
I've yet to find a way that with dual booting you can use sleep et al and have Windows restart at that point. It will shut down but it does a full restart.   

If I were you, give UBUNTU more space, it's real easy to fall in love with and make a despiser of windows out of you. If I didn't have a Dell 924 printer I'd never turn on Windows except to teach my students how to fix it when, not if, it breaks.

---

### Post by AndyCooll on 2007-01-31
The link in my signature is a good place to start for dual-booting queries (and is often quoted in "dual-boot query" threads on these boards.

:cool:

---

### Post by abuntoyoutoo on 2007-01-31
> If I were you, give UBUNTU more space
I've also thought of that as I have been finding more and more supstitute applications for my windows programs.  There is only a few which I couldn't find: 
[LIST]
[*]Microsoft Visio (diagram program)
[*]Outlook (I've tried Thunderbird, but it doesn't have the calender support I wanted)
[*]Virtual Dimension (multiple virtual desktops + window transparence and stay on top)
[*]Visual c++ express (I've found heaps of c++ compilers but not an ide)
[*]Microsoft Project
[*]Backup program
[/LIST]

With an Outlook replacement, it wouldn't bother me if the calender and mail programs were separate.

If I could get those programs, then it would be possible for me to use ubuntu for work and windows for games, which would be cool. With that in mind, how big should the ubuntu partitions be?

Also, can windows read from the ubuntu partition?

> The link in my signature is a good place to start for dual-booting queries (and is often quoted in "dual-boot query" threads on these boards.
Great links! btw, it could be useful if there was a stickied topic for the absolute beginners section with beginner linux links. I had trouble finding them as it was hard to tell if a link was too old or still relevant.

> I'd never turn on Windows except to teach my students how to fix it when, not if, it breaks.
Umm this might sound stupid, but do you need a firewall and antivirus running linux?

Oh and thanks for all the answers so far!

---

### Post by skyhopper88 on 2007-01-31
Honestly, it's less of a hassle to have Windows and Ubuntu on seperate had drives, that way there's less partition/grub headaches. As for Calender support with Thunderbird, try Sunbird/Lightning.

---

