---
title: "How do I access my WinXP partition?"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-10
I have XP Pro and Ubuntu installed as a dual boot. I'd like to be able to access certain files from Windows, while I'm in Ubuntu. How is that done? Also, is there a way to access Ubuntu while I'm in Windows? Thanks.

---

### Post by miggols99 on 2007-04-10
You can use the ntfs-3g package. Works perfectly for me. I'm assuming your Windows partition is NTFS?

---

### Post by devnulljp on 2007-04-10
You can mount your windows partition anywhere you like and read data from it - last I looked the ntfs drivers were a bit buggy so write is usually disabled. 
You can mount your ext2/3 partitions in windows using Extfs
Remember, goolge is your friend.

---

### Post by robenroute on 2007-04-10
Basically, accessing the other system can only be dealt with on a simple file access level. This means that you cannot run Windows programs in Linux (there is a way to do this, but it involves installing and setting up specialized software) nor can you run Linux programs in Windows.

Basic file level access is done through mounting the respective partition using special mounting instructions. Check [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") web page for more details and instructions (assuming you have 6.10 Edgy Eft installed).

---

### Post by jacatone on 2007-04-11
No, I'm running 6.06. Do you have a link for that? Thanks.

---

### Post by Duck2006 on 2007-04-11
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

