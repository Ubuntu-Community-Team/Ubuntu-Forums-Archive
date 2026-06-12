---
title: "XP/Ubuntu/Vista Setup"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Steel Bovine on 2007-02-19
Hello everyone!  This is my first post.  I've heard great things about the Ubuntu community and just wanted some thoughts on how I've chosen to partition my drives.  While I'm at it, I'll ask if anyone who's reading wants to give me any advance warning about conflicts resulting from my hardware configuration.

I built a new PC this weekend and first installed XP on it.  Once I was happy with my XP installation I inserted the Ubuntu Live CD.  I have 0 Linux experience; I'm just a Windows "power user" looking to try something new.

I was a bit disappointed when after electing to run Ubuntu from the Live CD and try it out, I suddenly lost the monitor signal.  Didn't get very far before encountering a problem, but I wasn't deterred.  I heard some drums, so I knew at least my on-board audio was fine and Ubuntu was loading up and not hanging.  So anyway, I got the monitor working fine.

My hardware configuration:
[LIST]
[*]MSI P965 Platinum Motherboard
[*]Intel Core2 Duo E6400 Processor (running at 2.8 ghz, love this chip)
[*]2 GB DDR800 memory (5-5-5-15)
[*]ATI Radeon X1900GT video
[*]Lite-On DVD-RW Optical drive (IDE, which isn't natively supported by my chipset, which gave me some problems in windows trying to get it recognized as a recordable device to burn my Ubuntu cd)
[*]74GB SATA HD (Raptor!  woot.)  Partitioned as follows:
[LIST]
[*]18GB Windows XP and Programs (ntfs) - not using a swap file in windows
[*]18GB Linux (2GB linux-swap and 16GB ext3 for root)
[*]20GB MSDN and Games (ntfs)
[*]16GB Vista (ntfs)
[/LIST]
[/LIST]

In the works is a 1 TB RAID5 array that will hold all my media.  I'm not sure how I will set this up, perhaps FAT32 so I can read/write in both linux and windows with no problem.  Suggestions welcome.

Tonight I'm going to begin working in earnest to customize Ubuntu to my needs.  This weekend all I managed to do was get on the web with Firefox (on board gigabit LAN works fine).  So far I like Ubuntu for ease of use: my compatibility issue was fixed with 1 copy/paste command line.   GNOME is awesome and I'm using a Human visual style on XP now at work (I like the "for human beings" marketing, it works).  Ubuntu also loads more quickly (but we're splitting hairs with my raptor: 11 seconds for XP and 6 for Ubuntu).

I won't be able to escape Windows entirely though: C# is the only programming language I'm fluent in and I develop in it for work.  I'm interested in picking up a new language or 10, though, and I'm really interested in seeing how well the code I've written will work in mono (with the ultimate goal of convincing the higher-ups here to switch platforms, at least in certain cases).

Thanks in advance for any help, if you can anticipate problems I might have.  If not, thanks for reading and thanks for the warm welcome.  There's a lot of information that makes switching easy..

Next project after this one: resurrect my old Toshiba satellite pentium II laptop.

---

### Post by GuitarRocker2562 on 2007-02-19
well, I am glad you are using ubuntu, hope you like it. THe only thing I have to say that you can decrease the size of your swap partition, you have got 2GB of RAM. Also, you can keep NTFS for your windows partitions, just check this guide 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_users_read_and_write_access)

and even though it is still BETA, I have not had any problems whatsoever

---

