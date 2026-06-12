---
title: "sudo gedit command won't work"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by carloyyz on 2006-04-17
I've run into several situations where the command sudo gedit (file) does not work on my system. The command does nothing.
Is there a fix for this problem.

Thanks.

---

### Post by jrib on 2006-04-17
You should always use gksudo instead of sudo when opening any gui application.  So you should do for example:

```
gksudo 'gedit /etc/apt/sources.list'
```

You should use the quotes like that too.

But, I don't think that is your problem... does sudo work normally?  What does ```
sudo echo hi
``` do?  Is gedit the only thing you are having problems with?

---

### Post by carloyyz on 2006-04-17
[QUOTE=_jason]You should always use gksudo instead of sudo when opening any gui application.  So you should do for example:

```
gksudo 'gedit /etc/apt/sources.list'
```

You should use the quotes like that too.

But, I don't think that is your problem... does sudo work normally?  What does ```
sudo echo hi
``` do?  Is gedit the only thing you are having problems with?[/QUOTE]
sudo echo hi results:
hi
I am having no other problems with sudo.

---

### Post by aysiu on 2006-04-17
Maybe you're using Kubuntu? In which case, you'd use KWrite instead of Gedit.

---

### Post by carloyyz on 2006-04-17
[QUOTE=aysiu]Maybe you're using Kubuntu? In which case, you'd use KWrite instead of Gedit.[/QUOTE]
No, I am using Ubuntu.

---

### Post by carloyyz on 2006-04-17
[QUOTE=_jason]You should always use gksudo instead of sudo when opening any gui application.  So you should do for example:

```
gksudo 'gedit /etc/apt/sources.list'
```

You should use the quotes like that too.

But, I don't think that is your problem... does sudo work normally?  What does ```
sudo echo hi
``` do?  Is gedit the only thing you are having problems with?[/QUOTE]
I used your example and got the following message:

carlo@carlo:~$ gksudo 'gedit /etc/apt/sources.list'
(gedit:8874): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then while I was preparing this reply, gedit opened but it took several minutes.

---

### Post by jrib on 2006-04-17
[QUOTE=carloyyz]I used your example and got the following message:

carlo@carlo:~$ gksudo 'gedit /etc/apt/sources.list'
(gedit:8874): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then while I was preparing this reply, gedit opened but it took several minutes.[/QUOTE]
Those warnings are normal afaict.  If you type ```
gedit /etc/apt/sources.list
``` it is not slow in opening?

---

### Post by carloyyz on 2006-04-17
[QUOTE=_jason]Those warnings are normal afaict.  If you type ```
gedit /etc/apt/sources.list
``` it is not slow in opening?[/QUOTE]
gedit /etc/apt/sources.list

Opened instantly.  But if the warning message and time lag for gksudo 'gedit is normal then I will consider this problem solved.

Thanks very much.

---

### Post by jrib on 2006-04-17
[QUOTE=carloyyz]gedit /etc/apt/sources.list

Opened instantly.  But if the warning message and time lag for gksudo 'gedit is normal then I will consider this problem solved.

Thanks very much.[/QUOTE]

a time lag of minutes is not normal imo, I don't really know what would cause it either

---

### Post by dannemil on 2006-04-26
[QUOTE=carloyyz]I used your example and got the following message:

carlo@carlo:~$ gksudo 'gedit /etc/apt/sources.list'
(gedit:8874): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Then while I was preparing this reply, gedit opened but it took several minutes.[/QUOTE]


I am having the identical problem. It also shows up if I try to open a root terminal using gksudo. It opens, but it takes it minutes before the prompt shows up in the window.

Jim

---

### Post by carloyyz on 2006-04-26
Another thing I've noticed is that every time I see sudo and gedit used together, it's always "sudo gedit" not "gksudo gedit".

What's the difference?

---

### Post by aysiu on 2006-04-26
[QUOTE=carloyyz]Another thing I've noticed is that every time I see sudo and gedit used together, it's always "sudo gedit" not "gksudo gedit".

What's the difference?[/QUOTE] Read [this thread](http://www.ubuntuforums.org/showthread.php?t=165957).

---

### Post by carloyyz on 2006-04-26
[QUOTE=aysiu]Read [this thread](http://www.ubuntuforums.org/showthread.php?t=165957).[/QUOTE]
I get it.

Thanks.

---

### Post by carloyyz on 2006-06-09
Update:
This problem resolved itself after I upgraded to Dapper.

---

### Post by cuplex on 2006-11-04
hi, im not sure if you already fixed your problem!?

well i had the same problem but when i used the sudo gedit command it gave ma an error it can not load some icons! 
i checked the folder /usr/share/icons/gnome/
i could find all sizes but 36x36 and that was exatcly the size my gedit was missing! i dont know why or how to fix it easier...

is just copied the 32x32 folder to 36x36 folder and voila sudo gedit works^^

---

### Post by Kiel on 2006-11-23
I have this problem now as well.  sudo nor gksudo gedit will work or it takes a ridiculous amount of time.  trying to start it from a root terminal does the same thing.  Just gedit works perfectly and up to 20 minutes ago sudo gedit did as well.

I had this problem once before under a fedora 4 installation and I never found the reason why.  

If anyone know any way to fix this issue it would be much appreciated.

---

### Post by kaqmak on 2006-12-23
I'm having the same problem.
If I type "```
sudo gedit
```" the nothing happens. If I type in ```
gksudo gedit
``` it gives me the same ```
(gedit:7163): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```-thing, and then it takes about 5 minutes before it opens.
Does anyone have a clue of what might be wrong? The problem is really annoying me.
\Kaqmak

---

### Post by sup on 2006-12-30
the same here:-(. should not we fill a bug (probably to gedit), I have found plenty oif threads about this in the forums

---

### Post by macogw on 2006-12-30
I would just call this "time to learn vim" :confused:  This is a weird problem.  

Anyone up for learning a new text editor?  Vim and Nano both just open inside the terminal, so there's no real load time.  Something's definitely wrong.  Anyway to figure out what yours is doing in the background that mine (assumably, been ages since I used sudo gedit instead of sudo vim) isn't?

---

### Post by jrib on 2006-12-30
I can't recreate this, so I can't help debug the problem.  But I remeber reading somewhere that this has something to do with the gtk theme being used by the root account.  

Try playing with the settings stored in /root.  I'm not sure if things run with gksudo end up using gconf or not, but that would be where I would start.  Hopefully this gives you an idea to work with. ** Do this only if you feel very comfortable with what you are doing.**

---

### Post by raul_ on 2006-12-30
> **macogw said:**
> I would just call this "time to learn vim" :confused:  This is a weird problem.  

Anyone up for learning a new text editor?  Vim and Nano both just open inside the terminal, so there's no real load time.  Something's definitely wrong.  Anyway to figure out what yours is doing in the background that mine (assumably, been ages since I used sudo gedit instead of sudo vim) isn't?

Try using evim. If you have vim installed, evim should be too. You don't have to learn anything. It's a vim without the commands

---

### Post by macogw on 2006-12-30
nope, I don't have evim installed.  I didn't manually install vim, though.  It's always already there.

---

### Post by raul_ on 2006-12-30
Oh...well give it a try then :) it's pretty straightforward.

---

### Post by macogw on 2006-12-30
eh, I like using a terminal text editor.  the fewer windows need to be open the better.

---

### Post by sup on 2006-12-30
well, i prefer gedit... if only for its find feature (i guess vim has something as well... - but I am not reallt motivated, I am using kedit instead) - and I know how to use vim, my wireless router running openWRT has no X so no graphical text editors, but i still prefer gedit, most of the time.

> Try playing with the settings stored in /root. I'm not sure if things run with gksudo end up using gconf or not, but that would be where I would start. Hopefully this gives you an idea to work with. Do this only if you feel very comfortable with what you are doing.
Maybe when I have more time. I am always very comfortable when destroyng my computer, thanks for the warning, though:-D.

---

### Post by sup on 2007-02-11
the problem self-solved. maybe some problems, I do not know - ubuntu is starting to be like windows - only the other way around :-D

---

### Post by munkar on 2007-02-11
i'm having the same problem as kaqmak. :( 
my guess is that it has something to do with the recent important-looking updates....

> **kaqmak said:**
> I'm having the same problem.
If I type "```
sudo gedit
```" the nothing happens. If I type in ```
gksudo gedit
``` it gives me the same ```
(gedit:7163): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
```-thing, and then it takes about 5 minutes before it opens.
Does anyone have a clue of what might be wrong? The problem is really annoying me.
\Kaqmak

---

### Post by munkar on 2007-02-12
this issue suddenly resolved itself...weird.

---

