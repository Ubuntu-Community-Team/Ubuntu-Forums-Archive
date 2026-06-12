---
title: "I needs help with install"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by fiddilydee on 2007-11-21
okay here is the whole story. I have a computer that was preloaded with vista. I am now fed up with it's infinite amount of verification and comfirmation and stupid seemingly unfixable errors. I decided to install ubuntu, I am completely new to linux.

I booted off of the cd and messed around with it to make sure I could still do everything I wanted (media and photo editing) of course it is even better than windows for this stuff. So I want to get rid of windows completlely and put Ubuntu on. I boot into it again make a seperate partition for my media and format the windows partition. After a couple of installation attempts (it did stall a few times) it finally completed but it will not accept the username/passowrd i typed in even though I know they are right.

So I try a couple of things I read on here to change the password in recovery mode, it is telling me my user does not exist even though it automatically named my computer the same thing and this is printed in the bottom left corner the whole time. I try installing it again it is still booting from the old computer name and not accepting any of the things I put for username/password.

So I load up my friends external hard drive to put my media on so I can do a full format and it cannot mount it even though it was working fine before. I am starting to get rustrated with this.

Any tips or ways I can format everything besides my media partition because the first install created 3 or 4 locked partitions which I figure is causing my reinstallation issues (not recognizing new user profile)

I know that was long but any help would be appeciatied

---

### Post by Joakim Stokland on 2007-11-21
Try to boot from the live CD. From there, go to the /home folder and see what the folders inside it are called. There will probably only be one folder there, and it has got the name you selected as your username. This is just to be a hundred percent sure that you are typing your username the same way Ubuntu expect you to. (You should type it just like the folder's name, mind using lower-case.)
Also, when you've inserted the live CD, and the boot menu appears, you should find an option to check for errors on the CD.

We'll start from there.

Good luck!
Joakim

---

### Post by 1337455 10534 on 2007-11-21
Get a computer and get the LiveCD on it. Then try using Gparted through Ubuntu to format the HDD. I dont know if that will work though, it seems very circuitious.

---

### Post by dstew on 2007-11-21
The computer name is different from a user name. If you are unsure, or have confused the two, maybe it is easiest just to install it again. When you get to the partitioning, delete the partitions you don't want, and leave the media partion alone.

---

