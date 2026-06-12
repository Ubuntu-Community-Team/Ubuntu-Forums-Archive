---
title: "Partitions. . ."
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by rebeccacalvetti on 2006-07-20
How can I use Ubuntu to read another partition already on my drive? I have some important documents on there that I would like to transfer. I am new to linux as per this forum, and would appreciate simple instructions.

P.S.
what kind of program could I use to encode .WAV to .MP3 in linux? I noticed that Ubuntu recognizes my Ipod, but I can't seem to use the soundjuicer to make them.

---

### Post by madmetal on 2006-07-20
your other partition is windows partition NTFS?
if you have dual boot system (ubuntu/windows) its better to have a fat32 partition with your files.
about ipod and mp3 i dont know i am also new :)

---

### Post by rebeccacalvetti on 2006-07-20
I am not certain if I have a dual boot system or not. It began as a windows system, was changed to ubuntu by my boyfriend, and I believe it was already partitioned (to protect my mother---- whom I inheireted the comp from---'s scientific data) at the time when it was changed over to linux. Previously, he had moved all of my mp3s to the D drive (all this terminology confuses me greatly; I'm not computer savvy in the least!)

Now I have an ipod, and I am trying to rescue the files he moved (about 5-6G worth of music), and I have no clue what to do. Thanks for your quick reply.....Maybe this clears things up some?

---

### Post by RRS on 2006-07-20
First thing is to see for sure which partitions you have.

Open System>Administration>disks
The first page will show the hard drive(s) in your computer, the second will list the partitions of the drive.

Note the partition labels ("device") and the file system type for each.

Follow [this guide]("http://www.psychocats.net/ubuntu/mountwindows.php") to mount the partitions. The instructions are much clearer then what I could provide.

You'll find that most tutorials in linux use the command line rather then the GUI. under Applications>Accessories open "Terminal"

Unless your a much better typist then I am copy/paste is the safest method to follow instructions.

I'm afraid I can't help you with the ipod but I'm sure the "Howtos" section of the forums has just what you need. Also Aysui's site has a lot of other usefull info too.

Hope this at least gets you started to solving your problem.

---

