---
title: "Grub Error 15 after hard drive clone"
date: 2006-11-14
forum: Absolute Beginner Talk
---

### Post by Wrightster80 on 2006-11-14
Hello all,
I've recently started to use Ubuntu Edgy, ive been doing ok with it for the past week but ive hit a problem. Ive just replaced my PATA 40GB Hd with a 200GB Maxtor drive. It is a dualboot system with windows xp. I cloned the old to the new with Acronis True Image and, perhaps foolishly, thought that i could plug in the new drive and carry on. However i now get a GRUB error 15 message when i try to do anything. Ive followed a few tutorials with no avail, the last thing ive done is to remove grub with windows fixmbr and restore it with 

sudo grub
find /boot/grub/stage1
root (hd0,5)      (*this is my ext3 partiton)
setup (hd0)

but i still get the error 15 message when i try and use ubuntu either normally or in the recovery mode. I can use grub however to load my windows installation with no problems.
I'm really stuck now :???:  any help will be much appreciated
Thanks

---

### Post by Ecthelion on 2006-11-16
Maybe you can find a solution[ here...]("http://ubuntuforums.org/showthread.php?t=43591")

It's a thread about someone who had the same error...

---

