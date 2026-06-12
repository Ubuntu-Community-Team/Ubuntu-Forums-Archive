---
title: "Access XP files; no sound"
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by masonpitzel on 2007-11-24
Hi guys.  I installed Ubuntu on a whim this morning, mostly to try some new audio/video programs, and for the most part everything is running fine.  I do have a few questions, though.

1) I installed Ubuntu on a dual-boot with Windows XP Home.  I haven't even bothered with using XP since I installed Linux, I've been liking it so much.  I was wondering, though...while I'm using Ubuntu, is there any way to access files on the non-Ubuntu part of my hard drive (mostly all my photos, music, etc...basically the entire My Documents folder)?  It would really be a hassle to have all my personal stuff trapped in the XP world.

2) I've been having some sound issues.  Now, this is probably an easy fix for you guys, since I'm a complete Linux beginner (WHAT/WHERE THE HELL IS THE COMMAND LINE??) and I don't know much about what I'm doing.  But I think there's something wrong with my sound.  All my system alerts, etc. seem to be coming out of the internal speaker.  I tried making some crappy drum beats in Hydrogen this morning, and though the sound comes out my speakers, everything sounds kind of distorted.  (And sort of on a tangent -- after exporting my drum track as a .wav, none of the programs I have will play it.)  I don't know if this is driver-related, hardware-related, or whatever, I just know I need it fixed.

Any help would be really appreciated!

- Mason

---

### Post by kelbizzle on 2007-11-24
The command line is located in Applications -> Accessories -> Terminal

To read/write your NTFS (XP) partition you want to install the ntfs tool.

Type this into terminal
```
sudo apt-get install ntfs-config
```

It should be now located in Applications -. System tools ([http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html))

As for your codecs issue playing .wavs you may have to install them.

Open Synaptic (System-->Administration-->Synaptic Package Manager) and click on Settings-->Repositories; on the first tab check all the boxes and then press the Reload button. Then search for gstreamer and install the "ugly"plugins (they should be gstreamer0.10-plugins-ugly and gstreamer0.10-plugins-ugly-multiverse.

---

### Post by masonpitzel on 2007-11-25
Alright, I installed the NTFS Config tool, but I think I may have screwed up my dual-boot setup.  When I run the tool, it skips the first two steps (from the link you provided), and the "enable write support for internal device" option is disabled.  Am I unable to access XP?

---

### Post by jcsteele on 2007-11-25
type "fdisk -l" into the terminal and post the output back to us...we can then give you the command you will need to mount your xp partition.  Note: read/write support for NTFS is still fairly new, and I don't recommend using it unless you absolutely have to, but read-only support is very stable and mature and should work without a problem.

As per the sound problem, issue an "lspci" command and post the output back here as well...this will let us know what type of sound card your system has (if any is detected) and what we need todo to fix it.

//jcs

---

