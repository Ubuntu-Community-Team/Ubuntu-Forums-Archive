---
title: "I like Kubuntu, but..."
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by Iarwain ben-adar on 2006-08-14
Hi everyone,

i've been using Kubuntu for about 2 months now, and i'm very pleased about it.
Problems are: 
1) GRUB resets itself (or so i believe) after every boot
2) X won't start itself (and kdm doesn't want to start)

1) Recently i've taken my 1st HDD out (an old 20G drive) who was set as primary master. The only thing that was on it was Windows XP. Ubuntu is installed on my primary slave.
Once the primary master was taken out, i made the Ubuntu drive master. 

That's where (i believe) GRUB freaked :( 

=> GRUB said that Ubuntu was still on hd(1,6) while NOW it is on hd(0,6)
I changed it a couple of times (via live cd) and saved it, but everytime i  want to reboot, it just keeps giving the same damn thing...

Do note: i can succesfully reboot once (and most of the time only once) and Ubuntu loads. After a second or third reboot, GRUB says again that Ubuntu is on the hd(1,6)...

2) As of today, my X doesn't want to start itself no more... I do get the Kubuntu start up screen ("loading xyz        ok" kind of stuff), but after the screen goes away (the blue start up screen), it comes back, only to show no progress and no activity :( 
I then go to tty1 and "startx", but i always get the error returned that X couldn't be started (the first error was something about the Nvidia drivers. The errors are quite ?random? i think)

I get X working by "sudo dpkg-reconfigure -phigh xserver-xorg", but that's it. Kdm doesn't want to start ("sudo kdm")...


Iarwain

---

### Post by Iarwain ben-adar on 2006-08-14
Number 2 is solved =)

Some reading on the forum gave me the hint that i could try to reinstall my nvidia-glx =)

A simple ```
sudo apt-get reinstall install nvidia-glx
``` did the trick :D


Now just the first problem that bothers me...


Iarwain

---

