---
title: "Root account"
date: 2005-07-19
forum: Absolute Beginner Talk
---

### Post by krzychusss on 2005-07-19
Hi.
Sorry for my bad english - I'm from Poland :)
I have experienced very strange problem - I can't login on root account!
I've read that I should use password of first created user. It doesn't work...
"krzysztof is not in the sudoers file.  This incident will be reported." - krzysztof is the name of my account - I see this message, when I write
"sudo passwd root" in Konsole.
Help me please!
Use "english for beginners" please :)

---

### Post by dave9191 on 2005-07-19
Czesc :) 

When you first install ubuntu you can get a root console by typing

sudo bash 

and then entering YOUR PASSWORD. 

Then you will be able to set the root password from there. If thats not working, then something has gone wrong with your install. 


Dave

---

### Post by krzychusss on 2005-07-19
Thanks, but it doesn't work :(
Well, propably you're right - it was few problems (segmentation fault), but I don't know why.
I think, that some part of my pc is... you know, it doesn't work :) But I don't know which.
Anyway - Thanks.

Na razie :)

---

### Post by Lord Illidan on 2005-07-19
Did you install ubuntu in Expert mode?

---

### Post by codejunkie on 2005-07-19
[QUOTE=krzychusss]Thanks, but it doesn't work :(
Well, propably you're right - it was few problems (segmentation fault), but I don't know why.
I think, that some part of my pc is... you know, it doesn't work :) But I don't know which.
Anyway - Thanks.

Na razie :)[/QUOTE]
reboot the pc at the grub menu scroll down to this option ```
Ubuntu, kernel 2.6.10-5-386 (recovery mode)
``` choose this it will log you into a fail-safe root terminal now you will be able to set the password with ```
passwd root
``` reboot the pc login to ubuntu like normal  and you will have root access by opening a terminal and typing ```
su
``` and entering the password you set hope this helps.

---

### Post by odin on 2005-07-20
I also have a problem with that but in a different way.I have been using warty and I loged in in gnome with the root account normally.

The problem came when upgraded to hoary.Now when I try to log in to gnome then i get a message saying something like:"the system administrator is not allowed to login from this screen"¨

I can login as root in another tty but only in text-mode.

It is not that I cant do root's tasks but it would be nice to work in Gnome as root without doing all the sudo thing. :-P 

Thank's

---

### Post by codejunkie on 2005-07-20
[QUOTE=odin]I also have a problem with that but in a different way.I have been using warty and I loged in in gnome with the root account normally.

The problem came when upgraded to hoary.Now when I try to log in to gnome then i get a message saying something like:"the system administrator is not allowed to login from this screen"¨

I can login as root in another tty but only in text-mode.

It is not that I cant do root's tasks but it would be nice to work in Gnome as root without doing all the sudo thing. :-P 

Thank's[/QUOTE]
if you already have the root account enabled and want to login as root through GDM you have to go to System/Administration/Login Screen Setup under the security tab put a check in allow root to login  with gdm and that should do it.

---

### Post by odin on 2005-07-20
thank's codejunkie :grin:

---

### Post by codejunkie on 2005-07-20
[QUOTE=odin]thank's codejunkie :grin:[/QUOTE]
happy to help.

---

### Post by f0rmula on 2005-07-20
Phew!

Thanks god I found this thread :)

Every other linux distro I've used have required me to set a root password as I setup the system.  I've had a couple of beers, and had a horrible feeling that I'd set it to something wrong by accident :D

Where *should* I have found this information?  I.e. sudo with my current password etc.  Was I told this during installation?

This is the only glitch I (nearly :)) had when setting up the system.  Congrats on a supurb and smooth setup..

James

---

### Post by dave9191 on 2005-07-20
Yeh, the screen you typed the password on explained the use of sudo. I overlooked it the first time I installed the system, assumining it was a root password I was typing in :) As for where to find out about sudo, there is the wiki and pleanty of threads on the forums. I think that the ubuntuguide.org also mentions it. 

Dave

---

### Post by f0rmula on 2005-07-20
[QUOTE=dave9191]Yeh, the screen you typed the password on explained the use of sudo. I overlooked it the first time I installed the system, assumining it was a root password I was typing in :) As for where to find out about sudo, there is the wiki and pleanty of threads on the forums. I think that the ubuntuguide.org also mentions it. 

Dave[/QUOTE]

beer => !sensible_linux_configuration

Quite easy to miss though.  I'd expect it catches out quite a few people :)

I am so impressed with this distro (so far).  Nothing I've tried to do has been difficult or awkward.  For a beginners linux, this is absolutely beautiful.  

James

---

### Post by dave9191 on 2005-07-20
Yeh, a lot of people are caught out by sudo, I see it on the forums all the time. 

As for ubuntu, its great. Nothing else worked out of the box and was so easy to use. And now that my linux skills are much better then before I think that Ill give gentoo a try again, and get a fast streamlined system that only has what I want ;) 

Dave

---

