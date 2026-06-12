---
title: "[SOLVED] DVD player"
date: 2006-08-05
forum: Absolute Beginner Talk
---

### Post by Cariboo1938 on 2006-08-05
Hello all, 
I have installed ubuntu 6.06 successfully and I tried to play a DVD movie. I got the error message: 'No URI handler implemented for "dvd"'.
What is to do?
Juergen

---

### Post by nikku_neko on 2006-08-05
have you installed the plugins to handle dvd discs?  
i got that error when i first got ubuntu running.

go to the restricted formats page on the ubuntu wiki and follow the instructions for encoded dvd's

---

### Post by Titus A Duxass on 2006-08-05
Go System => Preferences => Removable Drives and Media.
Click on the Multimedia Tab, in the videoDVD window a will probably be totem %m, your problem lies here.

Try changing it to totem dvd://

If you want to use xine for DVD playback which has better support for menus enter the following:

xine -pfhq --no-splash dvd%//

---

### Post by Cariboo1938 on 2006-08-05
> **nikku_neko said:**
>  
go to the restricted formats page on the ubuntu wiki and follow the instructions for encoded dvd's How can I get there? Please give more details. Thank you.

---

### Post by Cariboo1938 on 2006-08-05
> **Titus A Duxass said:**
>  
Try changing it to totem dvd://
I did so, and again I got the message:
[COLOR="Magenta"]Totem could not play 'dvd://'
No URI handler implemented for'dvd'[/COLOR]
Then I tried:> **Titus A Duxass said:**
> If you want to use xine for DVD playback which has better support for menus enter the following:
xine -pfhq --no-splash dvd%//
Assuming this is a command line, I opened a terminal and typed 'xine -pfhq --no-splash dvd%//'. Here I got the response:
[COLOR="Magenta"]bash: xine: command not found.[/COLOR]
What is to do?
Thank you
Juergen

---

### Post by Cariboo1938 on 2006-08-06
:?: Sorry, I just don't understand what you mean by
> **nikku_neko said:**
> go to the restricted formats page on the ubuntu wiki and follow the instructions for encoded dvd's
Would you mind to give me more detailed instructions what to do?
Thank you in advance
Juergen

---

### Post by Jagot on 2006-08-06
Go to this page:

[http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

On the menu to the left you will see something about playing encrypted DVD's.  Click on the link and it will take you to the instructions you need to enable DVD playback.

That website at the present moment appears to be not working for me - work may be being performed on it, so if you cannot access it straight away then try again a little bit later.

---

### Post by Cariboo1938 on 2006-08-07
I went to this page and did everthing as it was described for the AMD64 architecture. I checked if the installation of the necessary packages was ok and when I ran the command line
*sudo /usr/share/doc/libdvdread3/examples/install-css.sh*
I got the message 
*command not found*
Do you have any idea?

---

### Post by Jagot on 2006-08-07
OK, so you're sure you have build-essential, debhelper and fakeroot installed before you run it?

---

### Post by Cariboo1938 on 2006-08-08
> **Jagot said:**
> OK, so you're sure you have build-essential, debhelper and fakeroot installed before you run it?
Yes, I'm ablolutely sure because I checked with Synaptic Package Manager what packages are installed!

---

### Post by Cariboo1938 on 2006-08-10
Quote:
Originally Posted by Jagot View Post
OK, so you're sure you have build-essential, debhelper and fakeroot installed before you run it?
Yes, I'm ablolutely sure because I checked with Synaptic Package Manager what packages are installed!

Hello Jagot you probably forgot me...?[-X

---

### Post by Jagot on 2006-08-10
Nope - didn't forget.  Unfortunately, regardless of whether I forgot or not, I have no idea what to do.  You really need another 64bit users to help you out with this one - 'fraid I'm only a 32er.  Good luck.

---

### Post by Cariboo1938 on 2006-08-10
> **Jagot said:**
> Nope - didn't forget.  Unfortunately, regardless of whether I forgot or not, I have no idea what to do.  You really need another 64bit users to help you out with this one - 'fraid I'm only a 32er.  Good luck.
Thanks any way! I keep trying...keep you posted eventually!

---

