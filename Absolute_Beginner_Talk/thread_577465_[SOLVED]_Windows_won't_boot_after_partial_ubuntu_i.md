---
title: "[SOLVED] Windows won't boot after partial ubuntu installation"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by Jon Law on 2007-10-16
I wanted to install Ubuntu on my work machine. I have no experience with Linux and wanted to delve into it. I booted up the cd and went to the install option. At the partition section, i selected 70gb as my partition for ubuntu as I was setting up a dual boot. The next screen told me that this wasn't possible and that 8gb was the largest amount i could use (think this was because i never defragmented my hard drive; i'm as green as can be). To cut a long story short, i just cancelled out of the whole thing because it was getting late, removed the cd, restarted the computer and booted windows as normal to check my email. Everything went fine and i shut down my computer as normal. I came in this morning then and my PC won't boot windows at all. The screen just goes blank after the screen with the option to enter the BIOS. I ran Knoppix and it can see my hard drive and tell me how much free space is on it but i can't access it. Can anyone tell me how i can get windows going again first as this is a work pc and i kinda need it!! I know this is a ubuntu forum but i intend installing ubuntu once i make sure i have things running correctly again. Help much appreciated.

---

### Post by LowSky on 2007-10-16
you need your windows disc, and run the repair windows option

---

### Post by Jon Law on 2007-10-16
What do i do if windows came installed on computer and i don't have a windows disk?

---

### Post by bliffle on 2007-10-16
> **Jon Law said:**
> What do i do if windows came installed on computer and i don't have a windows disk?

You should be able to get a repair disk from the manufacturer, but they may tell you that the recovery disks are on a hidden partition on your HDD and you have to recover them from there. They SHOULD have easy-to-follow instructions somewhere, but in this era of increasing irresponsibility GOOD LUCK. You probably need competent technical help. You may also have a big management/people problem at your place of employment, since you attempted something beyond your competence.  You have to deal with the problem of whether you did this on your own initiative or whether you were told to do it by your boss. It's a dangerous business to mess with the Operating System and partitions on a computer. Very often there are hidden partitions and wanky boot records that never allowed for subsequent OS installations.

The way I do a ubuntu dual boot install is to get a new HDD then copy the old system to the new HDD (usually you have to fix a lot of old OS problems on your HDD) and test it out to make sure it's working. Then I run the "liveCD" for ubuntu, which doesn't change your HDD until you make that decision, but it allows you to run ubuntu direct from the CD. Sure, it's a little slow, but it's safe.

---

### Post by Jon Law on 2007-10-16
Cheers Dudes,
Everything back to normal. I ran the chkdsk from the windows repair cd but for some reason it used to get to 73% then drop back to 50%. It did this a number of times so i just got tired of it and turned the computer off. When i turned it back on it loaded up windows so happy days. Now to defragment and install ubuntu. Thanks for the help.
:guitar:

---

