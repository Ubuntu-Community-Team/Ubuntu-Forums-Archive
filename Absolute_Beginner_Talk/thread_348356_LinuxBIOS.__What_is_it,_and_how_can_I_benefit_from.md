---
title: "LinuxBIOS.  What is it, and how can I benefit from it?"
date: 2007-01-28
forum: Absolute Beginner Talk
---

### Post by SendDerek on 2007-01-28
Hello Fellow Ubuntu'ers...

I have some questions about LinuxBIOS.  I did a little search on these forums, but I couldn't find anything that actually explained what it was and how it could benifit an average linux user.  Even after looking in the [ LinuxBIOS Wiki]("http://www.linuxbios.org/Welcome_to_LinuxBIOS"), I was still unable to figure out how it could benifit me.

So, my question is this:  For an average everyday destkop/laptop user running Ubuntu, what does LinuxBIOS mean to us, and how can it benifit our systems in layman's terms?  Does it replace the BIOS that is currently 'installed' on our systems like Pheonix, Award, or American?

I have a slight hope that maybe this may be a solution to my Pheonix BIOS dilema of an average load time of >30 seconds (Sony still tells me that this is normal).

Thank you for your interest and time in advance.

-Derek

---

### Post by Azakus on 2007-01-28
Yes, LinuxBIOS is an open-source replacement to propreitary computer BIOSes, like Phoenix, American, and Award. You flash it over your current BIOS, and it loads your computer like a normal BIOS would. As this procedure voids your warrenty, I don't know if you want to procede with it. You can check your motherboard against this list [http://www.linuxbios.org/Supported_Motherboards](http://www.linuxbios.org/Supported_Motherboards).
More info: [LIST]
[*][Wikipedia Entry]("http://en.wikipedia.org/wiki/Linux_BIOS")
[*][LinuxBIOS offical documentation]("http://www.linuxbios.org/Documentation")
[/LIST]

---

### Post by LKRaider on 2007-01-28
LinuxBIOS is exactly that: a replacement for the closed-source proprietary BIOS we use nowadays (Phoenix, Award, etC).

You can read the benefits right from their frontpage wiki. One of the most attractive is the faster boot time.

That said, it is still very much under development, and if you have a machine that is reported as supported on their page, you should first take a look on the web if people are actually using the LinuxBIOS on the same type of machine as yours and their rating of success.
Also, be sure to know how to backup and restore your previous BIOS if you need so.

It is not a thing to do following a how-to or something, you must know what you are doing at all times or you risk having a large piece of paperweight on your desk :P

That said, if you have a machine that you don't mind experimenting and taking risks with, you could definetly try it. And keep in touch with the other people doing it to report your success or problems while doing so :)

---

### Post by SendDerek on 2007-01-28
Thank you both for your responses. 

I noticed that you had said that the LinuxBIOS is under development.  Is this something that will be very popular in the near future, or will it take a long time in order for it to go mainstream?  

I would love to see some blogs in the future with the headlines of "How To Safely Install LinuxBIOS on Any PC".  Will this someday be a reality?

---

### Post by LKRaider on 2007-01-28
The big hit for LinuxBIOS will probably be the OLPC project, if it gets going as planned.

Having a platform like that with the projected install-base in the millions of units worldwide and large media coverage will attract even more attention to the projects that relate to it, LinuxBIOS inclusive.

OTOH, LinuxBIOS has dependencies on some unfinished projects like GRUB2 for supporting all the proposed features, it also requires manual code adjustments for each different hardware and extensive testing for each of them, slowing down general platform spread.

That said, it's adoption seems to be [growing exponentially]("http://linuxbios.org/Image:Linuxbios_growth.jpg"), so we may well see more of it sometime soon, especially on embedded devices, I believe.

---

