---
title: "Questions From First Timer."
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by Popcorn on 2006-05-16
Hi, 
   My name is Mathew and I have just downloaded Ubuntu and I'm liking it more than Windows at the moment :cool: 

Now there are some things which I have trouble understanding. Read on.

What type of installation do I want for general computer use (Image Editing, Internet Surfing, etc... )?

I installed the distro once already, but I have a usb wireless adapter and the internet is not working with Ubunto. I'm using a virtual machine to test it out first to see how it copes.

How do I log in as a super user? I tried to do the sudo passwd root, then a error about the internet appeared

Cheers. I love free stuff :P

---

### Post by shof2k on 2006-05-16
Welcome to the party.

1) For general use, the standard ubuntu desktop works.  You can get any useful programs from the package manager.  Have a wander through the forums to pick up useful tips.

2) USB wireless can be tricky.  Check out the HOW-TO section and the wiki. It will help if you know the brand of your adapter.

3) You can become a super user either using
```
 sudo *command*
```, then typing your normal password. This will run whatever "command" you type as root.  To become root, type ```
sudo -s
```. You'll notice your prompt become a # to show your root.

Free stuff is cool

---

### Post by Sef on 2006-05-16
> 
What type of installation do I want for general computer use (Image Editing, Internet Surfing, etc... )?


Just do the regular install.  You will be able to do all of that.  Though there maybe packages that you want to add later.

> I installed the distro once already, but I have a usb wireless adapter and the internet is not working with Ubunto. I'm using a virtual machine to test it out first to see how it copes.

Dapper Drake has better wireless support.  It will be stable on 1 June.  What is your wireless card?

> How do I log in as a super user? I tried to do the sudo passwd root, then a error about the internet appeared

Root is disabled by default.  Use sudo instead.

[https://wiki.ubuntu.com/RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by Popcorn on 2006-05-16
Thanks for all your answers. Where do you get those other builds anyway. I can't find them on the download page. Anway.

[USRobotics® 802.11g Wireless USB Adapter]("http://www.usr-emea.com/products/p-wireless-product.asp?prod=net-5422&loc=unkg")
Thats the wireless adapter I'm using.

---

### Post by Sef on 2006-05-16
[http://cdimage.ubuntu.com/releases/dapper/flight-7/]("http://cdimage.ubuntu.com/releases/dapper/flight-7/")

That's the most up-to-date Dapper Beta.

---

### Post by matthew on 2006-05-16
[quote=Popcorn]Hi, 
   My name is Mathew and I have just downloaded Ubuntu and I'm liking it more than Windows at the moment :cool: [/quote]It looks like you are already receiving some good help here so I'll just butt in briefly and say welcome...anyone named "Mathew" must be all right. :)

---

### Post by Popcorn on 2006-05-16
Yes! It's working! Yes! Yes! Yes! :D 

Thanks for all your help

---

