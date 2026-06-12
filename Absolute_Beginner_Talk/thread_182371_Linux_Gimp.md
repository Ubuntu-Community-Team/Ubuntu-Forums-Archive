---
title: "Linux Gimp"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by TheGimp on 2006-05-25
Ok well i just install a dual boot ubuntu system on my Gateway MX7515
And having acouple of problems #1 No Sound #2 No Wireless #3 How do i get into the the root user using the terminal? been awhile since i used linux and just brushing up some can someone here help me or tell me where to go? 



                            THX........................](*,)

---

### Post by Sef on 2006-05-25
> #1 No Sound

Are you using Breezy or Dapper?

> #2 No Wireless

What is your card and system specs?

> #3 How do i get into the the root user using the terminal?

Root is turned off by default.  Use sudo or gksudo if running a program, such as gedit.

[RootSudo]("https://wiki.ubuntu.com/RootSudo")

---

### Post by TheGimp on 2006-05-25
I have a Brodcom Wireless card. AC '97 2.3 Compliant Audio Sound and i just did sudo apt-get install firefox but where can i find the program not in the internet list any idea where it would be?

---

### Post by joshrobinson on 2006-05-25
for the root thing type sudo in front of your commands and it will ask for a password

you can turn root on if you want to, but its not the best thing to do since you really dont have to in ubuntu.. sudo does alot for you.. but if your lazy like me and hate typing sudo all the time

sudo passwd and then put in your password and the password you want for root

then type su  hit enter
and type your password for root terminal

---

### Post by joshrobinson on 2006-05-25
[QUOTE=TheGimp]I have a Brodcom Wireless card. AC '97 2.3 Compliant Audio Sound and i just did sudo apt-get install firefox but where can i find the program not in the internet list any idea where it would be?[/QUOTE]

im guessing your on a laptop? i have a broadcom on my laptop too

you have to use ndiswrapper yoou can grab it at
[http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/")

there is an install guide in the wiki.. but you need a copy of the windows drivers to use the card

make sure its on the ndiswrapper site in the list of working cards also, i know mine was

---

### Post by Sef on 2006-05-25
> AC '97 2.3 Compliant Audio Sound

Are you on Dapper?  If you are, there have been problems with this card, but easily fixable.  

First check the following:

1) Sound Icon on the task bar: Right click > Open Volume Control > Make sure the sound icons are not muted.

2) System > Preferences > Sound:  Make sure your sound card is set as default.

3) From the Terminal:  alsamixer   - Make sure nothing is muted.

If they are ok, let me know and I will provide some other instructions.

---

### Post by TheGimp on 2006-05-25
I'm sorry i dont know what dapper is but there is no sound icon on the right task bar

---

### Post by Shay Stephens on 2006-05-26
"Dapper" is the nickname for the next release of Ubuntu due June 1st.  It will be version 6.06 aka "Dapper Drake".

---

### Post by Sef on 2006-05-26
Are you using Dapper or Breezy?  What window manager:  Gnome, KDE, XFCE, or other?

---

### Post by popkid on 2006-05-26
[QUOTE=joshrobinson]
you have to use ndiswrapper yoou can grab it at
[http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/")[/QUOTE]

If you are using Dapper, you have a choice, you can use ndiswrapper or bcm43xx (linux native driver)

see here:

[http://ubuntuforums.org/showthread.php?t=180936]("http://ubuntuforums.org/showthread.php?t=180936")

pK

---

