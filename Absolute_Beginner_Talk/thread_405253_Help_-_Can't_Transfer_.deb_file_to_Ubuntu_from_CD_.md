---
title: "Help - Can't Transfer .deb file to Ubuntu from CD Created in XP"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by F_r_e_d on 2007-04-09
Hi everyone.  Please note that I am really new to Linux, but I want to make the move to Linux permanent, so I am very motivated.

I needed to download a .deb file and install it in Linux, so I had to download it from the XP side since I have no internet access on the Linux side.  I have a dual-boot system (two hard drives).  I downloaded the .deb (that is, debian extension) file to a CD-RW on which I have a bunch of files created in XP (with all kinds of extentions like .pdf, .doc, .exe).  When I booted into Linux, I inserted the CD-RW, and the CD-ROM icon showed up on the Linux desktop.  But when I opened the CD by double-clicking on the icon, only 3 files showed up, and none of them was the .deb file.

I did some reading and decided it was a mount issue, so I went to the command line function and tried to mount the CD and make it "unhide" the files, but that didn't work.  I thought at the very least I would be able to see the contents of the CD even if I were not able to open the files.  I was suprized that the .deb file didn't even show.

How can I get Linux to show me what is on that CD, and, more importantly, how do I transfer a file downloaded to a CD (in XP), to the Linux side of the box?  Do I first have to format the CD (or something like that) on the Linux side, and THEN download it on the XP side?

I would appreciate any help, or if someone can point me in the right direction.

---

### Post by rai4shu2 on 2007-04-09
I suggest you zip the deb file first, then burn it to disc. Then unzip it in Linux.

---

### Post by terdon on 2007-04-09
First of all, you don't need to use a cd. Linux can read the windows partition. This is very easy if your win partition is vfat and slightly more complicated in NTFS. Check out [ http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows]( http://ubuntuguide.org/wiki/Ubuntu_Edgy#Windows)

Now, for the cd, I assume your cd is mounted at /media/cdrom. If that is so, open a terminal and do ```
 ls -a /media/cdrom/ 
```

That should show everything on the cd. Then you can copy the files using the cp command: ```
cp /media/cdrom*deb /home/yourusername
```

---

### Post by junkman on 2007-04-09
This is an important question...
Some of us, perhaps many of us, HAVE to us such an awkard work-around, like I do, to get ANY Linux flavoured software, due to the situation listed, that being, no internet access when in Ubuntu, with nothing other than dialup access as an option. This plan, as described, is exactly what I was about to try. Download what i needed while in Windows, then reboot into Ubuntu6.10, and then load software previously gathered via the Win side. If this doesn't work, then I'm in a lot of trouble! 
What about using a simple CD-R only? And the question of where/how to format the disk is a good one too. And, if one DID format it in Ubuntu, could one then use it while in Win? I don't think Win would recognize anything not in FAT/CDFS? I'm so new, I don't even know what the right questions are, much less where to find the answers. 
I'm wanting to find whatever it is I need to make the movie player play movies, (dvd) and also to 'see' the other partition, (When in Ubuntu, can't 'see' the Fat/Ntfs part, and viceversa) I have a partial listing of things I need to locate and download, but don't know where to locate them. (Such as: VMware, w32 codecs, libdvdcss2, and a bunch of others) 
I got my distro from a Linux oriented magazine, a double sided DVD, which included various distrors, alternate ISO's, and so on, and this worked out well enough. (The magazine was $15.00 USD, at Barne & Noble, and is called, "Linux Format" from Future publishing, they are out of the UK)  It was well worth the $15.00, and it included Fedora Core 6, Ubuntu 6.10, and a ton of other stuff. (Downloading the CD over dialup didn't work for me, I tried twice, @ about 6 hours each time) 
Maybe there is, or should be, a primer or 'hold me by the hand' file somewhere easy to find? And, make it easy to find the mentioned files, software? (Where do I find w32codecs? I know WHAT it is... I have yet to find WHERE it is) 
The language, the shorthand, slang, call it whatever you will, is a bit hard to catch onto for a true newbie. I am strugling to understand half of what I read. (Bash, deb, other stuff like that) I know, there is, probably, a dictonary/glosery somewhere. Can I access it from within the forum without leaving the forum I'm reading? That would be nice. And shorten the learning curve. So, I'm just adding to what the orginal poster has said. In other words, this isn't a single user's problem. I'd bet it would be something a lot of newbies would like to know.
My 2 cents worth:
Junkman

---

### Post by junkman on 2007-04-09
Uh, forget everything I just said. 
When I first saw the thread, I saw that there were no replies. 
While I was typing my reply, I got bounced off my dialup connection.
When I got re-connected, I saw the answers were there after all.
I'm a dummy. Forgive a newbie?
Junkman

---

### Post by rai4shu2 on 2007-04-09
FWIW, you can access ext2 or ext3 drives in Windows using this:

[http://fs-driver.org/](http://fs-driver.org/)

---

### Post by terdon on 2007-04-09
junkman: just a note on style, it is considered nice if you can break up your message into paragraphs. It is much easier to read long messages that way. As for being a newbie, no worries that's why this forum is here :)

Now, to answer a few of your questions, yes winblows has problems recognizing anything but fat/ntfs, however there are various ways to get around this. The easiest i know is [http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

I haven't used rai4shu2's suggestion but I assume that will also work fine. 
However, linux can work with vfat perfectly and (with a LITTLE tweaking) NTFS as well. Check out the link in my last post. Actually, that page answers most common problems you'll have with edgy.

Most of the things you want to download can be found through ubuntu's package manager, Synaptic (I realize you don't have internet access under ubuntu, wWhat is the problem there? Post something here or, better, make a new post on that subject and we'll see if we can get you up and running. ). The easiest thing for the media stuff and ubuntu is [easyubuntu.freecontrib.org/](easyubuntu.freecontrib.org/)
Or, you can install vlc, ([ www.videolan.org/vlc/]( www.videolan.org/vlc/))a wonderful player for win/linux/mac which plays anything you throw at it. 

This will download install most things you need. Actually, if you can't get ubuntu to connect to the net, you would do better with another distribution since ubuntu is heavily internet orientated. Maybe SuSe, or mandriva. Red Hat is great but not a good starting point for a newbie.

As for bash, deb and other terms yes, it takes some getting used to. Bash stands for Bourne Again SHell, never mind why, and it is essentially what you use when you open a terminal. You can get information about bash and other shells by a simple google search. As for .deb files, they are the equivalent if setup.exe files in windows. They are installers for software.

I hope this answers some of your questions and feel free to ask more. I would recommend you open a new post with a list of questions and we'll see what we can do :)

---

### Post by F_r_e_d on 2007-04-10
OK thanks for all your advice.  I am studying the various options and hope somthing will work.  Any additional advice is welcome!

---

