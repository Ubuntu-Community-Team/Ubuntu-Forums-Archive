---
title: "partitions and internet"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by iamclueless on 2007-12-17
Hi all

Been playing with Ubuntu and Xubuntu for a couple of days and love it already

Decided to go with Xubuntu to extend the life of my old computer

Running a P3 667, 384 RAM (will make it 768 in a few days).  I was running Windows XP on a 20gb hard drive (2 partitions, 5gb and 15gb)

I have now installed Xubuntu on a different 20gb hard drive.

I have managed to create a dual boot using 2 different hard drives to allow myself to use Xubuntu and let family members go with the familiar WinXP

Just had a couple of quick questions

one is regarding partitions.  I keep reading that having a /home partition will make things easier.  I have access to the 15gb partition on the WinXP hard drive - should i still use a /home partition?  if so how do i go about creating one?  is it basically reinstalling and using the manual partitioning?  have the default /(root), and /swap (1.5 times the RAM?), and create a /home (ext3 right?) using the rest of the available space?

please advice


the other thing is i am running a high speed cable connection using a USB (not 2.0 port on my board!) modem (has ethernet connection, but my comp has no card).  Everything ive read seems to say that USB and linux dont mix well.  My connection seems fine... will getting a network card improve things?

finally a point on performance.  Things get done (running apps) noticeably quickly on Xubuntu compared to WinXP... but i havent noticed a massive improved on internet browsing speed - should there have been a massive improvement or is my old USB port slowing things down?

thanks for all the advice you guys can offer

---

### Post by seventhc on 2007-12-17
An ethernet connection will be faster than usb, as for partitioning, I let ubuntu just use the remaining free space and let it partition automatically for me.  if I do manual partition I would normally give the swap double my ram size but since I havent done it manually on ubuntu I'll let someone else advise on that. and its all preference anway.

---

### Post by iamclueless on 2007-12-18
ok, will pick up a card and go from there

as for partioning... ill wait for help

oh and for playing mp3s... is automatix the way to go?

---

### Post by seventhc on 2007-12-18
I believe automatix is for installing packages, I use xmms for mp3's( I like the way it looks with a good skin and seems to load fast) but you will probably want to try different players to see what you like. as for my  ipod i use gtkpod.

---

### Post by iamclueless on 2007-12-18
thanks man

got mp3s playing easy enough, cant move the player though :(

now i just need advice on partitioning.  well for now anyway :)

---

### Post by iamclueless on 2007-12-18
nm i can move it. thanks again

---

### Post by seventhc on 2007-12-18
When you say move the player, how do you mean??

---

### Post by iamclueless on 2007-12-18
i can move it. for some strange reason i just couldnt drag the player around the screen at first

anyone want to help me out with the making of partitions?  manual partitioning in Xubuntu that is. thanks

---

### Post by seventhc on 2007-12-18
here is a thread about partitioning
[http://ubuntuforums.org/showthread.php?t=634374&highlight=manual+partitioning](http://ubuntuforums.org/showthread.php?t=634374&highlight=manual+partitioning)
and heres another place to look...(might be better)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
but imo if this is your first install and you already have a free partition to use, I would just choose the guided option on the remaining free space and let ubuntu do it for you.
During install you will get to a point with a few options by default it is checked to use entire disk guided, then you can change that to guided remaining free space or manual. the second option is the easiest way. It wont touch your windows(still back up whats important though). when it finishes you will have a boot menu for windows and ubuntu.

---

