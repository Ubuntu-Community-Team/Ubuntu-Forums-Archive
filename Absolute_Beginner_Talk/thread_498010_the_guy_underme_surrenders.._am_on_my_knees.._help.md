---
title: "the guy underme surrenders.. am on my knees.. help pls."
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by gtjode on 2007-07-10
Hi everyone.. i feel so stupid asking this but i just can't find the answer..

i have Kubuntu installed on my MediaSrv and the Server has a 300gig Partition NTFS.. now my question is..

1) its a server and am going to be sharing that partition with Machines that have XP installed.. if i make the partition EXT3 and i share it in Samba.. will the XP machines be able to read that (I dunno drive? partition? folder?) what ever it is???

2) am following this guide : [http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009") - but at the beginning it says for Dapper or Edgy.. hmm am using Feisty so which one do i use??

3) and for the love of god can i have a friend that i can bug about linux anyone??? that can be my Guru???

Thanks for reading this and helping me out.

---

### Post by KIAaze on 2007-07-10
> 1) its a server and am going to be sharing that partition with Machines that have XP installed.. if i make the partition EXT3 and i share it in Samba.. will the XP machines be able to read that (I dunno drive? partition? folder?) what ever it is???

I don't have a lot of experience in networking Windows with GNU/Linux. I only tried once and I think it only worked in one direction if I remember correctly. I also tried with Samba.

But I think that it should work since the data is transmitted by the OS through Samba.
It will not be Windows reading on the ext3 disk. Ubuntu will read it and then transmit the data to Windows.
Samba takes care of the data transmission so the filesystem has no relevance what so ever.

(Even if this were not the case, there's always the ext2IFS driver to read ext3 partitions from Windows.)

> 2) am following this guide : [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009) - but at the beginning it says for Dapper or Edgy.. hmm am using Feisty so which one do i use??

Use this howto:
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

> 3) and for the love of god can i have a friend that i can bug about linux anyone??? that can be my Guru???

You're always welcome to ask questions here.
That's what this forum is for. :)
I'm no guru, but I have almost 2 years of GNU/Linux experience, so I might still be helpful. :)

Tip: I've heard that people using Gentoo are the greatest Gurus. ^^

---

### Post by dfreer on 2007-07-10
(1) You can share the folder/drive/partition with SAMBA even as NTFS, as it is now. Although reformatting it to a linux friendly format (even FAT32 would work, although I'm pretty sure FAT32 won't support 1 big 300 GB partition). Note linux cannot write to NTFS natively (there are ways with NTFS3G, pretty stable from what I hear), which is why I recommend reformatting it if that is an option for you.

(2) This guide is for Dapper or Edgy, I believe NTFS3G is a lot eaiser to use now, so you might want to try a feisty guide. Lemme see what I can dig up.

(3) Sure, I can help you out (although I wouldn't call myself a "guru" in any sense of the word). I'm on MSN IM alot, plus the forums.

EDIT: 
> Tip: I've heard that people using Gentoo are the greatest Gurus. ^^
because the people who use gentoo are hardcore lol you have to compile or emerge the entire OS, which teaches you alot

---

### Post by gtjode on 2007-07-10
Thanks Guys got the Partition working.. 

but am still going to back it up and change it to EXT3, and my next project is to get Samba working OH YEAH!!!:guitar:

---

### Post by regomodo on 2007-07-10
> **gtjode said:**
> Thanks Guys got the Partition working.. 

but am still going to back it up and change it to EXT3, and my next project is to get Samba working OH YEAH!!!:guitar:

have "fun" editing the smb.conf.

---

### Post by dfreer on 2007-07-10
ubuntuguide.org has some step-by-step tutorials here:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

---

### Post by gtjode on 2007-07-10
:( :lolflag: Yeah the fun just started.. lol

---

### Post by gtjode on 2007-07-10
D did you get my email?

---

### Post by KIAaze on 2007-07-10
:(
Why ask by email?
When you post on the forum others can help and it can help others.
Everybody who has automatic subscription set on gets subscribed automatically to threads after posting once so it's almost like a mailing-list. :)
MSN or IRC I can understand, but mail is about the same as a forum.

---

### Post by gtjode on 2007-07-11
not Mail Mail Forum Mail.. and it wasn't like a help topic.. nvm lol

well this is awsome.. this is like a Mailing list.. man are you guys going to hate in a couple of weeks ):P

---

### Post by dfreer on 2007-07-17
I just now realized you sent me an email, lol. I sent you one back, see ya online!

---

