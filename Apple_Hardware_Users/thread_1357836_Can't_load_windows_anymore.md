---
title: "Can't load windows anymore"
date: 2009-12-17
forum: Apple Hardware Users
---

### Post by jhammer619 on 2009-12-17
Hello all. I am very new to linux, so please forgive all of my newbie mistakes. Here is my situation, and I thank anyone in advance for giving me any advice!

-Have macbook pro.

-Using bootcamp, installed windows so I dual boot either OSX Snow Leopard or Windows XP SP3

-installed Ubuntu to an external hard drive because I didn't want to mess with my internal HDD

-Used automatic partitioning during ubuntu installation instead of manual (probably a mistake)

-Cannot get Ubuntu to boot (shows up as Legacy OS, just gives a black screen that says 'GRUB'), but I don't care right now as I am finding out it takes a lot more skill than I currently have to get Ubuntu running on an external drive, and would rather try again on an internal HDD

-When selecting Windows at Refit boot screen, it just gives the same black screen saying "GRUB" indicating I screwed up royally and can't run either Windows or Ubuntu. Thankfully Mac OS starts up fine still.

Question:

How do I repair my boot options so that Windows can properly boot again and my machine can just forget about this Linux ordeal.

Thank you so much, and I apologize if this is a FAQ but I searched and searched and I think I'm at the point where I wouldn't know the correct answer from one that would brick my machine.

Edit: Details of my machine:
MBP 5,5 (13inch 2.26 ghz core2)
Attempted to install ubuntu 9.10 64-bit

---

### Post by jhammer619 on 2009-12-18
Okay, I easily solved this problem by trying the same thing that everyone is saying, everywhere, the fixmbr command. I was just too afraid to try it at first.

For those who have the same problem and need a confirmation:

-boot from your XP cd (by holding down C, since Refit never seems to catch my cd drive). It will spend a couple minutes loading up its installation screen. 

-When it finally gets there, Type R to run Recovery Console

-enter admin password for your XP user account

-type fixmbr

-I only have one XP installed, so I chose "1" which is "C:\Windows"

it will give you a big warning, type Y, enter. Fixed.

I was afraid because I didn't want this to touch my Mac OS partition. And I associate "C:" with the first partition. But it wasn't (for me at least). I'm sure many have seen this before- sorry for the redundancy.

I think where I went wrong here is I didn't properly choose to which partition GRUB was to be installed, and it put it on my Windows partition instead of ubuntu's.

---

### Post by linuxopjemac on 2009-12-18
edit your first post as being "SOLVED"

---

