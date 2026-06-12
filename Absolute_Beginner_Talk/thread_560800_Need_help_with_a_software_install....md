---
title: "Need help with a software install..."
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by PsycoGeek on 2007-09-26
I'm trying to install Evince 2.20.0.  I have downloaded two separate from Softpedia ( [link to evince]("http://linux.softpedia.com/get/Text-Editing-Processing/Others/Evince-30154.shtml") ), and am trying to install following the directions in the INSTALL file, but not getting anywhere.  It says to use "make" as the first step, but I get the error "No targets specified and no make file found."  

???

I wish software creators would include the exact code you need to do an install in the readme or INSTALL files so newbs like me didn't have to ask Q's like this...

---

### Post by rsambuca on 2007-09-26
Evince is installed by default in ubuntu.  Is there something specific in this version that you require?

---

### Post by kellemes on 2007-09-26
The tarball includes "INSTALL", this gives you a detailed explanation.

---

### Post by PsycoGeek on 2007-09-26
> **kellemes said:**
> The tarball includes "INSTALL", this gives you a detailed explanation.

Ummm... please read my post.  I followed the directions and got "No targets specified and no make file found."  I'm asking for help to get past that problem.  Am I doing something wrong by just typing "make"?  The INSTALL file does not help me here.  And yes, I am in the proper directory.

I wanted to install 2.20.0 to have the latest version.  A hold over from my Winodws days, I guess.  If the program has been updated, why isn't it being updated by the Update Manager?  I thought that's what it was for?

---

### Post by rsambuca on 2007-09-26
The update manager only provides security updates for the most part.  Each version of Ubuntu essentially takes a snapshot of the Debian sid (unstable) branch repositories every six months.  The packages are made as stable as possible and packaged into Ubuntu.  If you continually want the latest and greatest versions of software and can't wait the six months for the next release, then I suggest you might be happier using Debian Sid, or another distro.

Unless there is something specific you need in the newer version, I personally wouldn't bother.  You'll go crazy trying to keep up with manual upgrades in the Opensource world!  They are much more frequent than for Windows programs.

---

### Post by tdrusk on 2007-09-26
FIrst of all I suggest taking the advice of the others in this thread. You may not need to do all of this...

but if you REALLY want to(and please correct me if I'm wrong).

You need to be in the directory.

Assuming the folder in on your desktop, open a terminal and type "cd" without quotes. This means change directory. Drag the folder into the terminal so it looks like

```
cd '/home/tyler/Desktop/directory of program'
```

now remove the "' '" so it looks like

```
cd /home/tyler/Desktop/file
```

Press enter

Now run 
```
./configure
```
```
make
```
```
make install
```

If your lucky it will install.

---

### Post by rsambuca on 2007-09-26
> **fuzzyhair said:**
> FIrst of all I suggest taking the advice of the others in this thread. You may not need to do all of this...

but if you REALLY want to(and please correct me if I'm wrong).

You need to be in the directory.

Assuming the folder in on your desktop, open a terminal and type "cd" without quotes. This means change directory. Drag the folder into the terminal so it looks like

```
cd '/home/tyler/Desktop/directory of program'
```

now remove the "' '" so it looks like

```
cd /home/tyler/Desktop/file
```

Press enter

Now run 
```
sudo make
```
```
sudo make install
```

If your lucky it will install.

I didn't read the install file, but the normal course of installation is

./configure
make
sudo make install

---

### Post by PsycoGeek on 2007-09-26
I see.  You have to forgive the Windows user in me.  It's been ingrained to always get the latest and greatest for all my software packages for many (read 17 years), so I'm still adjusting.

A do appreciate the explanation as I was not aware the update manager was used for that.  But I do have a question... When a new version of a program comes out that adds functionality and fixes a few bugs, are you still advised not to update?  Some examples I am talking about specifically for mysaelf would be HPLIP (the installed version that came with Ubuntu was very basic compared to the newest version published by HP), Photo viewing/editing/printing software (I have used Picasa under Windows and would like to continue to do so), Firefox and Thunderbird (I am using a manager for that- can't remember what it is right now, but I found it on these forums).  

Keeping up to date on any improvements is probably the most important to me as we print our own photo's, and I like to do some basic editing before printing, and right now it looks like photo printing is not quite where I would like it (but I haven't tried any other apps other than Picasa).

---

### Post by PsycoGeek on 2007-09-26
> **rsambuca said:**
> I didn't read the install file, but the normal course of installation is

./configure
make
sudo make install

Did that exactly from within the unpacked directory.  Do you have to do "make" or "sudo make"?

---

### Post by rsambuca on 2007-09-26
A lot of the security updates for new versions of Firefox and Thunderbird are worked into the Ubuntu updates (but not the new features).  I don't know about other programs specifically, although I assume it is similar.

As far as printing goes, I dual boot and switch back to Windows XP for any pictures.  I just can't get the same results with linux yet, but that could be my printer, as Canon doesn't really support linux at all.

For photo-editing, I strongly suggest using Gimp, which comes installed by default.  The learning curve can be a bit steep, but it is quite a powerful program.

---

### Post by tdrusk on 2007-09-26
> **rsambuca said:**
> I didn't read the install file, but the normal course of installation is

./configure
make
sudo make install
I knew I was missing a step. Thanks :)

---

### Post by PsycoGeek on 2007-09-26
> **rsambuca said:**
> A lot of the security updates for new versions of Firefox and Thunderbird are worked into the Ubuntu updates (but not the new features).  I don't know about other programs specifically, although I assume it is similar.

As far as printing goes, I dual boot and switch back to Windows XP for any pictures.  I just can't get the same results with linux yet, but that could be my printer, as Canon doesn't really support linux at all.

For photo-editing, I strongly suggest using Gimp, which comes installed by default.  The learning curve can be a bit steep, but it is quite a powerful program.

Yeah, Canon put me off with their lack of support, so I bought and HP Photosmart C6180, which is working pretty well so far, and it had an add on unit for duplexing.   And HPLIP, the one from HP, helps quite a bit.  Did I mention my printer is networked?  I don't think I did...

Anyhow, I have used Gimp, but I want the family to be able to use it as well, without a learning curve.  We really don't need the advanced features of Gimp anyhow.

---

### Post by Adramelech on 2007-09-26
Linux is a bunch of software in top of another bunch of software, the reason you dont have the latest software is incompatibility, if a library get updated it can break a LOT of software so a distro is a really good harmonized software =).

---

### Post by tdrusk on 2007-09-26
> **PsycoGeek said:**
> Yeah, Canon put me off with their lack of support, so I bought and HP Photosmart C6180, which is working pretty well so far, and it had an add on unit for duplexing.   And HPLIP, the one from HP, helps quite a bit.  Did I mention my printer is networked?  I don't think I did...

Anyhow, I have used Gimp, but I want the family to be able to use it as well, without a learning curve.  We really don't need the advanced features of Gimp anyhow.

I have found Picasa great for minor photo editing.

---

### Post by PsycoGeek on 2007-09-26
> **Adramelech said:**
> Linux is a bunch of software in top of another bunch of software, the reason you dont have the latest software is incompatibility, if a library get updated it can break a LOT of software so a distro is a really good harmonized software =).

Thanks for reminding me of that.  Again, getting used to the way things are done in Linux.

---

### Post by rsambuca on 2007-09-26
OT, but [here]("http://www.members.shaw.ca/northcottwedding/photoeditingrich.html") are some examples of my photoedits using gimp.

---

### Post by PsycoGeek on 2007-09-26
> **rsambuca said:**
> OT, but [here]("http://www.members.shaw.ca/northcottwedding/photoeditingrich.html") are some examples of my photoedits using gimp.

Nice edits.

---

