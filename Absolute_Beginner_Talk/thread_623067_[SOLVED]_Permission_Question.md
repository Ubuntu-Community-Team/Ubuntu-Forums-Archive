---
title: "[SOLVED] Permission Question"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by Tigerhawk on 2007-11-25
Its been a while since I used Linux and the last time I tried to make 2 partitions. One was / and the other was /home/Backup, but I could not get it to work. It always said it belonged to root and wouldnt let me write to it. I also tried /home/myloginname/Backup. Didnt work either.

This time with Gutsy I did the same thing and I did "sudo nautilus" and changed the Owner and Group to my login. It worked but now when I copy, everything I put in it belongs to root. Is it possible to make this Backup partition belong to me? Also, did I do anything wrong by doing a "sudo nautilus". I figured sudo went away when I closed the terminal I did it from, but I thought I should ask.

Thanks in advance


pic of what I did

[http://www.tigersmind.com/linux/screenshot.jpg](http://www.tigersmind.com/linux/screenshot.jpg)

---

### Post by jken146 on 2007-11-25
You need to change the 'file access' setting and click 'apply permissions to enclosed files'.

sudo lasts for 15 minutes (by default) from its first use until it asks you to re-enter your password.  This can be changed if you want (search these forums and I'm sure you'll find a way).

---

### Post by philinux on 2007-11-25
You need 

sudo chown yourusername -R /home/whatever

Check up on the chown command

---

### Post by Tigerhawk on 2007-11-25
Wow, thanks a bunch for the quick answers. That got me where I wanted to be.


SS of where I am

[http://www.tigersmind.com/linux/screenshot2.jpg](http://www.tigersmind.com/linux/screenshot2.jpg)



Thanks so much, I did a chown --help. Great command and I will remember it for the future.


Off to read the forums,  lol

---

