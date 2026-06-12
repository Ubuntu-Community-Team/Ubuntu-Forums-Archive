---
title: "How to acces my NTFS drive."
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by jincast90 on 2006-06-29
I am dual booting Windows Xp and Ubuntu. Ive got this program for windows, so I can acces my Ubuntu partition. What I need know, is the ability, to acces my NTFS partition, were Windows is installed from my Ubuntu partition. I know its not safe to write to it from Ubuntu, but I only need to get the files from the partition. I can see the partition from Computer in Ubuntu, but I cant acces it, how can I do this?

---

### Post by xtacocorex on 2006-06-29
Read this: [http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php) (Credit: aysiu)

---

### Post by FuzZy2006 on 2006-06-29
i recommend you to use captive program, you'll find it at softpedia.com at linux - search. and to run it you have to install fusemount drivers (google). to mount, make directory anywhere for the partition, for example for partition c mkdir /media/c and to mount sudo -t captive-ntfs /dev/hda1 /media/c and so on. they say that it is safe to write files on win partition with this program

---

### Post by jincast90 on 2006-06-29
[QUOTE=jincast90]I am dual booting Windows Xp and Ubuntu. Ive got this program for windows, so I can acces my Ubuntu partition. What I need know, is the ability, to acces my NTFS partition, were Windows is installed from my Ubuntu partition. I know its not safe to write to it from Ubuntu, but I only need to get the files from the partition. I can see the partition from Computer in Ubuntu, but I cant acces it, how can I do this?[/QUOTE]

This seems like a good guide, but I have some questions.

1. How do I know if I already have my Windows partition mounted?

2. How can I find out were its mounted?

---

### Post by rccharles on 2006-06-29
[QUOTE=jincast90]This seems like a good guide, but I have some questions.

1. How do I know if I already have my Windows partition mounted?

2. How can I find out were its mounted?[/QUOTE]
The command:
mount
will show you all of your current mounts with the mount point.

Robert:)

---

### Post by jincast90 on 2006-06-30
[QUOTE=rccharles]The command:
mount
will show you all of your current mounts with the mount point.

Robert:)[/QUOTE]

I Cant seem to find anything called ntfs?

---

