---
title: "x server failed to start"
date: 2006-01-15
forum: Absolute Beginner Talk
---

### Post by pmaury on 2006-01-15
I am trying to boot from live CD everything seems to load fine until I get to GUI it sayes 'failed to start Xserver it is likely that it is not set up correctly.would you like to veiw the Xserver output to diagnose the problem?' I don't know how to proceed from there. I am using X window system version 6.8.2(Ubuntu [email]6.8.2-7720051010174819root@crested.warthogs.hbd.com[/email])

---

### Post by pmaury on 2006-01-15
I don't know if it helps but i am using ubuntu 64 and a AMD64 processor.on the live disc

---

### Post by pmaury on 2006-01-16
I actually have mepis linux on my hardrive but it is 32 bit and it doesn'trecognise my CD-rw as anything but aCD-ROM.plus I really want to figure this out. Are there any boot promps i can use to reconfigure xserver or is there an online how-to somewhere.:)

---

### Post by pmaury on 2006-01-16
-also- I don't really know how to use a boot promt.:???:

---

### Post by matthewv on 2006-01-16
if xserver doesn't start you will be dropped to a command prompt...
run the command ```
sudo dpkg-reconfigure xserver-xorg
``` to reconfigure your xserver

---

### Post by xmastree on 2006-01-16
And no-one's jumped in yet...

Did you try to view the xserver output? That's the first thing to do, to see what's actually failing.

You're going to need to use that command prompt, since it's all you have for now...

I helped on another thread like this, live CD, no x server. I'll try to find it and post a link for you.

Edit: I found the thread:
[http://www.ubuntuforums.org/showthread.php?t=79827](http://www.ubuntuforums.org/showthread.php?t=79827)
In particular, [post # 27]("http://www.ubuntuforums.org/showpost.php?p=441434&postcount=27"), where I compared to xorg.conf to a pizza recipe! :rolleyes:

His problem was with the video driver, I would try that first.

---

