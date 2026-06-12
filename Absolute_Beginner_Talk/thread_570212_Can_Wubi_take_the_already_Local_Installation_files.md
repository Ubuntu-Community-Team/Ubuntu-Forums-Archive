---
title: "Can Wubi take the already Local Installation files instead of Internet download?"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by srinathtk on 2007-10-08
Dear Friends,

I have a peculiar problem. I have a SATA DVD drive which is not bootalbe. past 15 days, I have trying to install Ubuntu on my system by some method or not.

 I have already downloaded my Ubuntu 7.4 installation CD. As this needs to be booted and my DV writer donot boot from CD/DVD, I am tying other method.Recently I was trying to Install Ubuntu through Wubi. Once Wubi is installed, it checks for the Internet connection for Download.

As I am already haveing the Download with me, it there any method to redirect 'Wubi' to take files from 'Already Existed installation files' from my Harddisk or CD?

Also Wubi asks for minimum of 4GB HDD space. I am already having 15GB of my HDD space converted to .Ext2 format. Can I make the installation on to that partition?

I heard of something called 'alternate iso'. What do you mean by alternate iso? Is it different from 'Regular' download?

Please Help...

Regards,

Srinath
india

---

### Post by overdrank on 2007-10-08
> **srinathtk said:**
> Dear Friends,

I have a peculiar problem. I have a SATA DVD drive which is not bootalbe. past 15 days, I have trying to install Ubuntu on my system by some method or not.

 I have already downloaded my Ubuntu 7.4 installation CD. As this needs to be booted and my DV writer donot boot from CD/DVD, I am tying other method.Recently I was trying to Install Ubuntu through Wubi. Once Wubi is installed, it checks for the Internet connection for Download.

As I am already haveing the Download with me, it there any method to redirect 'Wubi' to take files from 'Already Existed installation files' from my Harddisk or CD?

Also Wubi asks for minimum of 4GB HDD space. I am already having 15GB of my HDD space converted to .Ext2 format. Can I make the installation on to that partition?

I heard of something called 'alternate iso'. What do you mean by alternate iso? Is it different from 'Regular' download?

Please Help...

Regards,

Srinath
india

HI I have never used Wubi but as I understand it you can download the alternate cd iso and place it in the Wubi folder and then when you install Wubi will use the iso instead of downloading.
You may find some help here also 
[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)
And you can find the alternate cd here
 [http://releases.ubuntu.com/feisty/](http://releases.ubuntu.com/feisty/)
Scroll down to the alternate cd and Good luck!

---

### Post by skipb on 2007-10-08
From my understanding wubi installs to a hard drive image file inside your windows partition, I don't think it will allow  you to install to an ext2 partition. I don't think you can use your cd that you burned as the wubi installer uses the alternate cd.

The altrernate cd is an installation cd that allows for more flexibility during the install, it uses a text based installer rather than a live cd environment, it's ideal if you have a machine with little ram or need more than the graphical install offers (note that I would not use this image unless you feel comfortable with linux)

You may look at something like 
[http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive](http://learn.clemsonlinux.org/wiki/Ubuntu:Install_from_USB_drive)
but it looks like the instructions are looking for you to already be in linux.

I wish you the best of luck in getting things to work.

---

