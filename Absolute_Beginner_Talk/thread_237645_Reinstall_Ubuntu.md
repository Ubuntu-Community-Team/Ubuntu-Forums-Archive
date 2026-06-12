---
title: "Reinstall Ubuntu?"
date: 2006-08-16
forum: Absolute Beginner Talk
---

### Post by purebuilt on 2006-08-16
I'd like to reinstall Ubuntu and get a fresh start. When I try to it gives me a smaller choice for partioning. How do I install over the partition (I have Window on the other 2) I already installed Unbuntu on? Is there a way to start over?

It is working great otherwise (does not recognize my PS2 mouse though).

Thanks.

DB

---

### Post by zxee on 2006-08-16
> It is working great otherwise (does not recognize my PS2 mouse though).
If the only problem you're having is the mouse-that probably can be fixed. 
Post your /etc/X11/xorg.conf
 Or do dpkg-reconfigure xserver-xorg and choose the correct selection for your mouse.

You should be able to re-install over your other install though.

---

### Post by goatflyer on 2006-08-16
When you get to the partitioning portion of the install, you have to select to partition manually.

Then tell it to use your old ext3 partition for the new install.

---

### Post by purebuilt on 2006-08-16
is ext3 the name? How do I make sure I get the right one? The manual partition is a little confusing.

Thanks.

DB

---

### Post by Klaidas on 2006-08-16
purebuit, don't worry. I've done that when I was upgrading to Dapper (reinstalling to breezy's partition.)
When you get to partitioning, just choose to install to "/" partition, which should be ext3 (it's the filesystem, not the name) with reformating the partition.

If I could do it, you will be able to do it too.

You can also check [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html) too see what you are up to.

But you should be carefull - make sure the partition you are going to format is really linux, that is, /dev/hdax, where x is a number.
To check, ```
df -h
``` in terminal. The one that is mounted to "/" is the one you need.

---

