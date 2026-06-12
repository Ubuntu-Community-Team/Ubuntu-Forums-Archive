---
title: "[SOLVED] Installing Ubuntu on a portable USB hard drive"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by Spiggy on 2008-02-27
Hello guys, I need some help, I hope my questions aren't too stupid. :P

I'd like to use Ubuntu and my files at school and when I'm abroad. I know that the Live CD can be pretty useful but it's not enough, I need a fully functioning Ubuntu system. :mrgreen:

The first (and only)  idea that popped into my head was Ubuntu on a portable USB hard drive. 
I'm no hardware specialist and I'm also pretty new to Ubuntu so I need help. 
First of all, is it going to work?

And the second question... As I said, I don't know anything about hardware (at least when it comes to external hard drives :(), the only thing I know about portable USB hard drives is that they exist. So... what do you recommend? :confused:

---

### Post by sayakb on 2008-02-27
> **Spiggy said:**
> Hello guys, I need some help, I hope my questions aren't too stupid. :P

I'd like to use Ubuntu and my files at school and when I'm abroad. I know that the Live CD can be pretty useful but it's not enough, I need a fully functioning Ubuntu system. :mrgreen:

The first (and only)  idea that popped into my head was Ubuntu on a portable USB hard drive. 
I'm no hardware specialist and I'm also pretty new to Ubuntu so I need help. 
First of all, is it going to work?

And the second question... As I said, I don't know anything about hardware (at least when it comes to external hard drives :(), the only thing I know about portable USB hard drives is that they exist. So... what do you recommend? :confused:

You can even install Ubuntu on a USB flash disk. Ofcourse, you can install it on a portable USB HDD.

---

### Post by philinux on 2008-02-27
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by Spiggy on 2008-02-27
Thanks :smile:

---

### Post by Madmoose on 2008-02-27
This is just what I was looking for! Thanks for the post.

---

### Post by Madmoose on 2008-02-27
I went to pendrivelunix, and did [this ]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/")install on my 8GB Cruzer.

After going through all the steps I did a smoke test, and it doesn't boot. It will sit there with a [ forever. 

Went to the last part, and tried the:
> Note: If your having trouble getting Ubuntu to boot, your memory stick may have a corrupted MBR. To repair the MBR of your USB device, at the terminal type sudo apt-get install lilo then type lilo -M /dev/sdx (replacing x with the letter of your flash device)

When I do that I get this:
```
ubuntu@ubuntu:~$ lilo -M /dev/sdb
Fatal: creat /boot/boot.0810: Permission denied
ubuntu@ubuntu:~$ 
```

Any ideas how to get past this?

Thanks, 

Moose

---

