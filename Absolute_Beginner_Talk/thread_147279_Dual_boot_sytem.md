---
title: "Dual boot sytem"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by Benzorro on 2006-03-19
Yet another newbie.  Presently running XP and I have 2 hard drives.  One with XP and the second for data only.  If I want to run both operating sytems can I leave XP on the primary drive and install Ubuntu and the secondary drive?  I really want to get the hang of this operating system and this seems the easiest way to make the transition and I have other members in the family who are not so open to change.

Another question, I have an old P3 computer but none of the linux distros I tried will load including Red Hat, Fedora, Mandrake and Ubuntu.  Eac one of them recognizes all the components but then hangs up on the install.  From this I am totally convinced that my old desktop does not like linux.  Is it possible something on the motherboard.  I did try flashing the cmos and this did not help.   Windos did load with no problems.  I would like to put Ubuntu on this computer. 

Thanks

---

### Post by Ozitraveller on 2006-03-19
I have Ubuntu running on a PII/400 with no probs. Probably a hardware problem.

Check out my links below, there is a dual boot one there.

---

### Post by Andrew5 on 2006-03-19
I have Win XP Pro running on one drive and Ubuntu running on the other.  It is working fine as of my install of Ubuntu yesterday.  I am still trying to figure out how to turn my sound back on when I boot to Windows though.

I had a bit of a problem, at first, until I was told to go to my BIOS and activate LVM (or something like that) in the disk configuration.  It worked and now I am given a choice as to which operating system to boot to.   If you don't know what I am talking about then I can offer more detailed info.

A

---

### Post by Andrew5 on 2006-03-19
Sorry I activated "IDE" not "LVM."  

Someone is bound to ask what is "LVM."  Don't ask, I got no idea.

---

### Post by Benzorro on 2006-03-22
I was reading your article on dual booting.  You mentioned that you should have a Fat 32 partition so that both OS could read and write to.  Does that mean that Ubuntu can not read or wtite whats in a NTFS file?

---

### Post by Princey on 2006-03-22
[QUOTE=Benzorro]I was reading your article on dual booting.  You mentioned that you should have a Fat 32 partition so that both OS could read and write to.  Does that mean that Ubuntu can not read or wtite whats in a NTFS file?[/QUOTE]

Ubuntu can read NTFS partitions pretty fine. Writing to NTFS partitions under linux is pretty still experimentive. Because of file corruption problems, it's advised not to do so. Someone explains the reasons further in this thread. 
[http://www.ubuntuforums.org/showthread.php?t=148056]("http://www.ubuntuforums.org/showthread.php?t=148056")

Check it out.

---

### Post by Benzorro on 2006-03-22
Thanks, does that mean Ububtu will be able to play my MP3s on the NTFS partition?

---

### Post by Princey on 2006-03-22
[QUOTE=Benzorro]Thanks, does that mean Ububtu will be able to play my MP3s on the NTFS partition?[/QUOTE]

Yes it will. Just make sure that you install all the multimedia codecs using automatix /Automatiks (the latter is for Kubuntu Breezy users).

---

