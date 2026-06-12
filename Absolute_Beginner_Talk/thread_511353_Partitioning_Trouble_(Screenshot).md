---
title: "Partitioning Trouble (Screenshot)"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Morph89 on 2007-07-27
Hi, I'm new to the forums and new to linux, therefor I am a n00b (but you knew that). I got the install up and running and when I come up to the partitioning manager, I am unable to allocate my preferred size of 10GB:
[IMG]http://i202.photobucket.com/albums/aa106/Morph2007/Screenshot.png[/IMG]

As you can see, the smallest amount I can select is 51.5GB (which happens to be the exact amount of available space on my 120GB hard drive). Is this supposed to happen? Is there a way that I can set the partition to 10GB? I have been doing searches on the forums/google but to no avail - nothing simple at least. Should I use the manual selection? My current hardware:

AMD Athlon XP 2800+
1GB PC2700 DDR RAM
ATi Radeon 9800 Pro 128MB
120GB Western Digitial HD

I thought the problem might be my ATi card because I have heard of difficulties when using ATi, but this shouldn't affect the install so early on, should it? Also, while in the installer, I tried bumping the screen resolution to my monitors native 1680x1050 and everything when garbley/artifacts - this should be fixed once I have a full install/drivers, correct?

Any help would be much appreciated.

---

### Post by Ek0nomik on 2007-07-27
If you use the manual partition editor you can make the partition whatever size you'd like.

---

### Post by kebes on 2007-07-27
I think the resize slider is controlling what size you want to *shrink* your old partition down to. (And you can't make it smaller than the amount of data currently on it.)

Right now you have a 120 Gb disk with 50 Gb used. So you want to free up 10 Gb for Linux, which means you shrink the current partition down to **110 Gb**. 


The manual mode gives a visual layout of the hard drive and what the partition sizes will be. You can go into that mode instead to be sure that it's resizing the way you want.

---

### Post by bren on 2007-07-27
1) use manual option and google pyschocats and hermanzone + ubuntu for guides on installing various configs
2) ATI won't affect partition
3) yes, should be poss to fix screen res when installed.... ATI sometimes a pain
4) read at hermanzone on how to create sepaate /home during install (use alternate CD).   this is great because now if you reinstall ubuntu or even install a different distro/version all your linux programs and data stay

good luck
there is a bit of a learning curve but keep with it...

bren

---

