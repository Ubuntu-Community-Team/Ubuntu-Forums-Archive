---
title: "how to move apple macbook files to ubuntu pc"
date: 2011-09-14
forum: Apple Hardware Users
---

### Post by kokoshmusun on 2011-09-14
I have convince my wife to switch from mac to linux.  I tried to back up her mac files on a portable PC hard drive but I couldn't even get the files to copy on it.  She needs to move all her mac files to her new linux laptop.  What's the best way?  Will there be compatibility issues?  It's mostly music, pictures, text docs. 

Note: I've searched around a bit and discovered that people have done this over the net.  I know very little about ftp, samba, ssh, etc.

---

### Post by jroa on 2011-09-14
How much junk are we talking about?

---

### Post by jonny on 2011-09-14
Option 1: sync them over the web using a service like dropbox.  Easy to do and requires no technical skills, but limited to a few GB of data

Option 2: Copy them onto some kind of portable media - USB stick, CD, DVD, portable hard drive, mobile phone, MP3 player, etc on OS X, then plug the media into the ubuntu box and copy them to thwe hard drive.  Again, no techncial skills needed, but, as you've discovered, other operating systems can be a bit choosy about what media they choose to recognise

Option 3: set up a home network. Share a folder on either the Mac or Ubuntu and use the other machine to copy the files from or into it.  Samba will underpin this, but you do it all through your file manager and won't ever see teh word Samba anywhere on your screen.  The trouble is that you'll need a small amount of networking expertise (eg how to set up a workgroup name)

Take your pick, and someone will guide you through the steps.

---

### Post by kokoshmusun on 2011-09-14
Probably a lot of junk.  Thanks for listing the options, very clear.  I would prefer the samba option but have no time to figure it out now.  I will look at it when I can...

---

### Post by yokohama1970 on 2011-09-15
I respect your desire to move her over to Linux, but my question is why? Is she running an Intel or PowerPC Mac? With Mac OS Lion being so affordable on an Intel Mac, I would stay the Mac OS course.

If it is a PowerPC Mac, then please make the jump to a PowerPC Linux Distro.
Mac OS 10.5 is the last Mac OS to have PowerPC functionality. Plus, with 10.5.8, I found little support for PowerPC apps/programs. I was Dual-Booting between Mac OS 10.5.8 & Ubuntu 8.04 LTS PowerPC. I knew I would have a few issues like Adobe Flash & some minor apps/programs. in Ubuntu, but was Mac OS 10.5. When Ubuntu 10.04 LTS PowerPC was released, I decided to ditch Mac OS on the PowerBook G4. Ubuntu 10.04.3 PowerPC works with the known Adobe Flash issue, but it is a PowerPC Linux Distro.

My Uni-Body MacBook Pro is still Mac OS 10.6 only. Why, because it is Intel & works flawlessly. I will move to Mac OS Lion when necessary
 
If you have an External Hard Drive, DVD +/- or 8gb USB Flash Drive? Why not transfer locally? 

A local transfer worked for my Mac OS to Ubuntu Linux transition.

---

### Post by kokoshmusun on 2011-09-16
We just dislike Apple as a company and how it locks you into its proprietary software and formats and how it bullies the open source community with lawsuits, etc.  So, it's not a matter of practicality.  We find Apple products beautifully designed for the most part, but we want our vote to go to something less aggressively capitalistic. Apple's practices in their Chinese factories have also drawn a lot of negative attention recently, both in terms of labor rights and environmental issues.  

So we would like to stick with GNU/Linux, whether Ubuntu or not (so far, after many distro trials and using Ubuntu for 2 years myself, it's still Ubuntu (xubuntu for some machines), even despite Unity).

---

### Post by yokohama1970 on 2011-09-16
Makes sense. Apple has been busy with lawsuits, lately. I find it interesting that both Mac OS & iOS start with a Unix Kernel, but end up with their proprietary OS for both. 

Is the Ubuntu candidate Mac Intel-Based? If so, it makes life easier. As I mentioned before, PowerPC requires patience, work-arounds & acceptance of certain apps/programs not working. 

My logic is, why dump a completely functional PowerBook G4, when PowerPC Distros work for basic tasks.

How is the Data Transfer project going?

---

### Post by z31200n3 on 2011-09-16
I don't mean to hijack this thread, but my question is extremely similar to the OP's question.

My Macbook Pro has recently refused to boot, so I am using a Ubuntu LiveCD to get my files off the internal HD and onto a USB external HD. My problem deals with gaining permission for the USB HD. I've gained the Mac's internal permission by doing "gksudo nautilus" in a terminal, but I can't seem to gain permission for the USB drive (brand new drive, nothing on it).

Suggestions? I'm a Linux newb....

---

### Post by mbbuntu on 2011-09-18
Rsync?

---

