---
title: "temporary connection"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by animus1 on 2007-03-21
hello im a new ubuntu noob,this is my first quastion.



i want to make a temporary connection whit my laptop,
i want to use the cable that i normaly use for my pc this because i only have 1 output in my router-modem.
if i disconnect the cable from my pc and connect it to my laptop and then startr windows xp on my laptopi can just surf the net whitout configuring something.
now the problem is if i do the same whit ubuntu i doesnt configure automatically.
i already tryed starting ubuntu whit the cable already plugged in.
nothing works .

(i have a dualboot sytem windowsXP and ubuntu 6.10)

here is a screenshot i made whit copieeng the file to my usb stick
[http://img144.imagevenue.com/img.php?image=96232_ubuntuconnect_122_471lo.jpg](http://img144.imagevenue.com/img.php?image=96232_ubuntuconnect_122_471lo.jpg)
[[IMG]http://img144.imagevenue.com/loc471/th_96232_ubuntuconnect_122_471lo.jpg[/IMG]](http://img144.imagevenue.com/img.php?image=96232_ubuntuconnect_122_471lo.jpg)

---

### Post by Bartender on 2007-03-21
This is such a basic step lots of people miss it.  If your router was already talking to your other PC there was a DHCP address established.
Kill the power to your router.  Don't just turn it off.  That doesn't work.  Turn it off, then unplug the power to it for a minute.  Then plug it back in, connect the router to your Ubuntu PC, then turn the Ubuntu PC on.
See if that helps.

---

### Post by animus1 on 2007-03-21
okey treyed that didnt work.
someone on irc sayed i had to enter sudo dhclient eth0
then i got this and i had still no connection.
[http://img165.imagevenue.com/img.php?image=98992_ubuntu_connect2_122_560lo.jpg](http://img165.imagevenue.com/img.php?image=98992_ubuntu_connect2_122_560lo.jpg)

there was also someone who sayed i had to install ubuntu whit the cable plugged in, but i dont believe that.
now i justhave a problem .

ow and btw windows on the same laptop recognizes the connection immediatly and automatically.

---

### Post by Bartender on 2007-03-21
> **animus1 said:**
> there was also someone who sayed i had to install ubuntu whit the cable plugged in, but i dont believe that.

You're right not to believe them.  I've installed several Linux distros without any internet connection at the time - all connected later.

I wish I had some better ideas for you to try.

EDIT: Is the router indicating no activity at all when you try to connect to the internet?  I wonder if it's as simple as disabling IPV6?  If you're seeing any sign of communication with router try disabling IPV6 in Firefox first.
[http://www.linuxforums.org/forum/linux-newbie/63087-firefox-connection-time-out.html](http://www.linuxforums.org/forum/linux-newbie/63087-firefox-connection-time-out.html)

If Firefox starts working then disable IPV6 across the entire Ubuntu OS
[http://neoaddict.wordpress.com/2007/01/27/disable-ipv6-in-ubuntu/](http://neoaddict.wordpress.com/2007/01/27/disable-ipv6-in-ubuntu/)

---

### Post by animus1 on 2007-03-21
i noticed that if i press my network icon on the top of my screen(the 2 pc on top of eachother) that there is a red sign. and if i press it i got this error;  please contact your system administrator to resolve the following problem: SIOCGIFFLAGS error no such device

---

### Post by animus1 on 2007-03-21
someone on irc sayed i should change that so i clicked the icon then selected another name .
then the erro and the warning sign disappeared but i still have no internet.
this is a screenshot.
[http://img18.imagevenue.com/img.php?image=05410_1_copy_122_367lo.jpg](http://img18.imagevenue.com/img.php?image=05410_1_copy_122_367lo.jpg)

--------edit--------
i saw your'e edit.
if i i disconnect my cable the 1 led goes off then if i connect him to my laptop it goes back on again.
my connection is still down after changing the ipv6 setting.

strange knoppix 3.8 and windowsxp work fine.
im also going to try if ubuntu works an my pc, just have to download the i386 version.

okey ubuntu worked on my pc but that is a pentium3 32bit maybe that ubuntu doesnt support
amd tl50 x2.
im going to try another distrubitiun of linux this is to much time consuming.

---

