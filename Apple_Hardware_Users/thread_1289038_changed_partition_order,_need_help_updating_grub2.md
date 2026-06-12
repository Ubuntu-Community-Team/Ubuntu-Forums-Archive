---
title: "changed partition order, need help updating grub2"
date: 2009-10-12
forum: Apple Hardware Users
---

### Post by cool2000m on 2009-10-12
hey guys. this is a 2-part question, so please bear with me.

 i was trying to install windows xp between my os x (partition 2) and my ubuntu 9.10 on my macbook 5.1, but it wasn't working, so I decided to delete it, move the ubuntu install to the left, and make another partition, so that the windows install would be on partition 4, and therefore out of the 'efi' circle thing. but now I cannot boot my linux partition from refit! It just hangs on the "legacy os" diamond screen, and never actually boots. so I tried update-grub2 from the cd (the super grub disk never gets past "stage2........"), and the terminal said that it could not find a disk for / or something.

I was thinking that maybe I needed to re-specify what partition the grub was on. do I need to re-install it on the disk, or can I simply fix it from the live cd commandline?

also, how do I install xp without totally wiping out and re-installing everything on my disk?

thanks!

---

### Post by cool2000m on 2009-10-12
okay, so I tried to sync the partition tables via rEFIt, and this is what is said:

```
Status: gpt partition of unknown found, will not touch this disk
Error: not found returned from gptsync.efi
```

and my os x disk utility doesn't look like my disk at all!

it's supposed to be:
1. efi
2. os x
3. sd0,4 (linux)
4. sd0, 3 (will be windows)
5. linux swap

but instead, it has:

osx
(huge amount of free space)
disk0s3 (windows- really tiny!)
disk0s4 (linux, even more tiny!)
(short gap)
swap

but the actual disk is only shown properly on gparted on the live cd?

should I just backup my files onto my external HD, delete all of the partitions, resize and bootcamp, resize again, and then install ubuntu? I **really** don't want to do this! Please help!!!

---

### Post by cool2000m on 2009-10-12
anybody there?

---

### Post by cool2000m on 2009-10-12
well, I fixed my first problem by re-installing ubuntu:). (a whole day of downloading open source games, down the drain...:mad:) it still won't sync to the GPT or whatever though. I'll get back to you guys later for progress on my winXP install.

---

### Post by cool2000m on 2009-10-12
Help! I get a blue screen of death, every attempt, including any option on advanced mode, and it still won't sync in refit! Does ANYBODY know a solution? I feel like I'm talking to myself, here!

---

