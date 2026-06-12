---
title: "considering reinstall Ubuntu."
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by rocketboys on 2007-05-16
I was considering if it would be helpful to fix the problems I have with Ubuntu right now.

Because past few days I've been fighting with these few problems, and I can't find a way to

fix them.

So I want to ask if I reinstall Ubuntu 7.04, do you think I can solve(or easier to fix) these problems?

I'm having hard time with these problems:
(The post I made yesterday)
 About to give up....:'( (Sound problem)
I've tried many things...and looked up the forums for last 5 days...but

It's keep getting messed up...:'(

I installed alsamixer..so My speakers work now but my External 24 bit live still won't work..

also it won't work as 5.1 speaker. It works as 2.1. And won't even recognize my speaker..

cuz when I checked restricted driver manager, there was only a vga driver.

and also I won't get sounds from videos on the internet. I installed Flash9 and did set up..but

still can't get any sound.

and now I can't get anysounds from my speaker. Before, at least I could listen to my mp3 files

but after I installed PulseAudio Sound Server I won't get any sounds. I can't even listen to my mp3 files. If I do the test on sound panel, It will say "could not open resource for writing"...

so I don't know what to do now..

and also my Hard drive is messed up too. one of my drive is write protected..and

I can't change it to not protect because I can't change the owner, it will say you can't change

the owner because it's read-only drive. and another drive is disappeared or something.

----------------------------------------------------------------------------------------------------------------------------
I'm using Ubuntu 7.04, and I'm using Creative-sound blaster 24bit Live-External.

Thank you..

---

### Post by Happy_Man on 2007-05-16
For your drive problem:
```
gksudo nautilus
```

runs the file manager as root, so you can change permissions willy-nilly.

---

### Post by rocketboys on 2007-05-16
> **Happy_Man said:**
> For your drive problem:
```
gksudo nautilus
```

runs the file manager as root, so you can change permissions willy-nilly.

Yes, Thank you for the response.

I tried that but it will say I can't because it's read-only drive.

---

### Post by Happy_Man on 2007-05-16
Try this, then:
```
sudo apt-get install ntfs-3g ntfs-config
```

If it's an NTFS drive, that will make it writable, and may get rid of your read-only error...

---

### Post by rocketboys on 2007-05-16
> **Happy_Man said:**
> Try this, then:
```
sudo apt-get install ntfs-3g ntfs-config
```

If it's an NTFS drive, that will make it writable, and may get rid of your read-only error...

Thank you for the response!

I've done that too..

---

### Post by Happy_Man on 2007-05-17
Did you run ntfs-config? It should be in your Applications --> System Tools menu.... if it isn't, run ```
ntfs-config
``` from a terminal.

---

