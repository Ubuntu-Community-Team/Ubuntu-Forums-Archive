---
title: "Sharing same home partition... xp/ubuntu"
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by ymmotrojam on 2005-11-24
I would like to share a fat partition between xp and ubuntu on the same pc. I'm a newbie and don't really understand that much about mounting drives, although I can follow instructions ;). I've already tried mounting /home, but it kept giving me some user account errors... I assume because it then wasn't able to locate the files for my user profile, or whatever it's called in Linux...
I'm probably just not doing it correctly...

My setup...
XP Pro - hda1
fat32 - hda2
ubuntu - hda3
swap - hda5

Let me know if you need more info. Thanks for any help!:)

---

### Post by matthewv on 2005-11-24
I think sharing a home partition doesn't work. The home partition, as I understand, must be a linux format. You can, however, mount a shared fat32 partition within your home folder, which is accessable from windows and linux. You need to remember that the home partition in linux contains settings as well as documents/music etc...

Hopefully someone will correct me if I'm wrong

---

### Post by bonjun on 2005-11-24
[QUOTE=matthewv]I think sharing a home partition doesn't work. The home partition, as I understand, must be a linux format. You can, however, mount a shared fat32 partition within your home folder, which is accessable from windows and linux. You need to remember that the home partition in linux contains settings as well as documents/music etc...

Hopefully someone will correct me if I'm wrong[/QUOTE]

you mean, you can only mount /home in linux format, as in ext3 and others, and not on fat?,, and idiotic question, though this query lingers in mind for sometime now, thanks for clarifying..

@ymmotrojam
all you have to do in linux is to mount fat32 , in your case to mount /dev/hda2 to your home or at /mnt directory, which ever you prefer....

this [guide]("http://ubuntuguide.org/") is helpful to newbie in linux like us, i use this very often

---

### Post by matthewv on 2005-11-24
[QUOTE=bonjun]you mean, you can only mount /home in linux format, as in ext3 and others, and not on fat?,, and idiotic question, though this query lingers in mind for sometime now, thanks for clarifying..
[/QUOTE]

Yeah, I meant formats like ext3 and reiserfs, I just wrote linux formats for simplicity. Hopefully someone will clarify me as to why or if this is the case.

---

### Post by schdefan on 2005-11-24
of course one can mount partitions with fat32 format but you cannot use a fat32 partition in ubuntu as your home because of the right management.
To get access to your files on the fat32 partition just mount it (in your case hda2).

In the [starterguide]("http://help.ubuntu.com/starterguide/C/ch05.html") you will find information about mounting partitions.

schdefan

---

