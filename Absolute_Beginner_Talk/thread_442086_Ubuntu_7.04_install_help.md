---
title: "Ubuntu 7.04 install help"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by chuckles1066 on 2007-05-13
Hi,

I'm brand new to Linux but determined to give it a go.

But............I'm attempting to install Ubuntu 7.04 and I've got as far as the "select your country/time zone" screen.  I've selected London but there seems no way to get onto the next stage of the install?

No "next" button, nothing!

How can I get past this sscreen?

Thanks in advance!

---

### Post by Wiebelhaus on 2007-05-13
you can configure the time zone later , double click on one that works and move on.

---

### Post by chuckles1066 on 2007-05-13
double clicking has no effect!

Doesn't matter which city I click on?  I'm stuck on this screen!

---

### Post by wpshooter on 2007-05-13
Have you checked the integrity of your Feisty CD by running the verification function that is found on the initial Feisty boot screen menu ?

Personally, I would not attempt to install Feisty at this point in that IMO it is not ready for prime time.  I would install Edgy instead.

---

### Post by chuckles1066 on 2007-05-13
CD checks out just fine :confused: 

First impressions of Linux aint good guys!  I was really looking forward to this as well :neutral:

---

### Post by lepz on 2007-05-13
It has worked for 30 million other users so maybe it's not a Linux problem ;)

---

### Post by .Morpheus on 2007-05-13
Did you check the ISO's MD5 sum?

---

### Post by Happy_Man on 2007-05-13
Yes, it sometimes happens. Force-quit the installer and then open it again. That usually does it for me...I have the same problem. 

@ everyone else who's posted: Why must EVERYTHING be an ISO corrupt problem? Seriously, if it's a bug and nobody knows about it, burning 15 CDs won't help any...

---

### Post by chuckles1066 on 2007-05-13
Yep, the checksum checks out ok with winMd5Sum.

is it a buggy installer?

---

### Post by kmslinux on 2007-05-13
Try this:

Get an Edgy CD.
Open up /etc/apt/sources.list in a text editor.
Change every 'edgy' to 'feisty' (without the quotes)
Open up a terminal.
Type this: (without the quotes) "apt-get dist-upgrade"
You'll have Feisty in no time.
By the way, it worked for me so it should work for you.

---

### Post by cborga1985 on 2007-05-13
> **kmslinux said:**
> Try this:

Get an Edgy CD.
Open up /etc/apt/sources.list in a text editor.
Change every 'edgy' to 'feisty' (without the quotes)
Open up a terminal.
Type this: (without the quotes) "apt-get dist-upgrade"
You'll have Feisty in no time.
By the way, it worked for me so it should work for you.

or just use the alternate install cd

---

### Post by chuckles1066 on 2007-05-13
> **lepz said:**
> It has worked for 30 million other users so maybe it's not a Linux problem ;)

Shame it wasn't 30 million and one users?

I'd have loved to have given Linux a go, I really would.  But if the installer can't get me past a "where in the world are you" screen, it isn't going to compete with Windows.  Ever.

Haven't Linux programmers heard of a "next" or "skip" button?

I'll try a different flavour of Linux another time and hopefully I'll get to experience it because I really, really would like something alternative to Bill Gates' intrusive crap.

---

### Post by simon303 on 2007-05-13
> **cborga1985 said:**
> or just use the alternate install cd

i'm thinking of upgrading to feisty too, but where do you get the alternate install cd? all i can find is a normal cd to install from scratch

---

### Post by Happy_Man on 2007-05-13
It's the "server" edition off the download...

---

### Post by chuckles1066 on 2007-05-13
Surely just put up an ISO that works?:confused: :confused: :confused:

---

### Post by Miroku on 2007-05-13
[http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/7.04/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/7.04/)

thats the mirror i use -- install with the alternate CD -- worked for me

and here:

[http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

pick a mirror, any mirror =]

---

### Post by thetejon on 2007-05-13
> **chuckles1066 said:**
>  I've selected London but there seems no way to get onto the next stage of the install?
No "next" button, nothing!
You have a screen resolution problem, not an installer problem.  There is a "forward" button, it's just off the screen and you can't scroll to it.  I set the panel at the bottom of my screen to auto-hide, and set the panel at the top to be at the left instead, and then I could see the button to continue.

---

### Post by simon303 on 2007-05-14
> **Miroku said:**
> [http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/7.04/](http://mirror.cc.columbia.edu/pub/linux/ubuntu/releases/7.04/)

thats the mirror i use -- install with the alternate CD -- worked for me

Thanks, i will download that when i get home

---

### Post by chuckles1066 on 2007-05-20
> **thetejon said:**
> You have a screen resolution problem, not an installer problem.  There is a "forward" button, it's just off the screen and you can't scroll to it.  I set the panel at the bottom of my screen to auto-hide, and set the panel at the top to be at the left instead, and then I could see the button to continue.

Nice post, thanks :D

Followed your instructions and there was the elusive button!  But that's shoddy coding surely?

It's installing as we speak, I'm sure I'll be back with more questions :)

---

