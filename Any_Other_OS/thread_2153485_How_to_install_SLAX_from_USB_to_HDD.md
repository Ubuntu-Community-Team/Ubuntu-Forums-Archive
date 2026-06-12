---
title: "How to install SLAX from USB to HDD"
date: 2013-06-11
forum: Any Other OS
---

### Post by soresger on 2013-06-11
Hello dear users,

I have a common problem but I couldn't find an answer to it anywhere.

Here it goes:

I installed SLAX 64-bit on a 64GB USB drive using YUMI (USB tool), it  runs fine from USB but I can't manage to use wireless Internet. 

Here is what I want to do:

Install SLAX to my harddrive permanently from my USB drive and also be able to use wireless Internet on it.

I'll be glad if people can show me how to do this.

Thanks.

---

### Post by UltimateCat on 2013-06-11
Hi:

If you have another operating system on your computer and you do not want Slax to take over the entire HDD you will need to use G-parted to shrink the partitions of that OS first.

This article should help.
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

During installation the internet configuration may be done for you and all you have to due is enter your key.

Otherwise; once Slax is installed your wireless should work.  If not you can manually use your (network manager) to set up your wireless and put in your key.
If your wireless is still not working it may be that you need a driver for your network interface card.
You can run: "lspci" in the terminal to find out what NIC you have and look for a driver online from there.

The Slackware documentation may be of use. 
[http://docs.slackware.com/](http://docs.slackware.com/)
[http://www.slax.org/en/documentation.php](http://www.slax.org/en/documentation.php)

Hope that helps

---

