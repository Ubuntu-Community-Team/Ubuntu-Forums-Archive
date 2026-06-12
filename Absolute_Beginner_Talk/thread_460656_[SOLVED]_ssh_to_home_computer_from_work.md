---
title: "[SOLVED] ssh to home computer from work"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by kernel tom on 2007-05-31
I am currently running Xubuntu 7.04 on my home (desktop) computer, and on my laptop that I bring to work.  I was just informed today, that my place of work will be strictly monitoring all network traffic, and reading 'packages' that are transmitted using there network.  This means that they could read all clear text that I send (mainly IM conversations, and recently my password! I never knew that was clear text as well!)

So I have 3 questions...

1) If this is being monitored closely, would I avoid having my packages traced and read by running my applications off my home computer via ssh?

2) If so, how do I set up my home computer so that I can log on to it remotely via ssh, my username and password are the same for my desktop and laptop.

3) Could I also do this for torrenting?  I am not allowed to use torrents during work, so I was wondering if this would also be untraceable...


Thanks for all the help you can give me,
tom

---

### Post by dave-5B on 2007-05-31
once ssh is set up (ubuntuguide.org will have an explanation somewhere)

you can get yourself a domain name from dyndns.com (its free)

if you have a router on your home network you need it to forward port 22 (ssh listen port) to your home machine

if your work computer is using windows there is putty so you can ssh from it

you can change the listen port of ssh to another port if its blocked at work or something (which would be likely if its a big organisation)

EDIT: dyndns is good for home connections because the ip address or your home may change from time to time, you can run a little demon on your computer to tell dyndns when this happens (some routers even support it)

---

### Post by 13thMonkey on 2007-05-31
If you want a nice GUI interface into a GUI desktop then I'd recommend running FreeNX on your server and NoMachine's NX Client (works on Windows and Linux). NoMachine also offers a Linux Server. The NoMachine versions are stupidly easy to setup and install, but are only free as in beer. FreeNX was fairly new when I was looking for a similar solution so I dare say it's improved a lot and would be worth checking out. Either way, they're both encrypted and will ultimately give you a window with your remote desktop on it.

If you want to use your home machine for torrents then I'd recommend torrentflux (it's in the repos). You'll need to install a LAMP server at home but once you have you can access and configure all your torrents via the web.

---

### Post by kernel tom on 2007-05-31
thanks a lot for the ideas so far guys... am i thinking that this is harder to set up then it acutally is?

i use ssh all the time to check email etc, is it as simple as openning something on my desktop?

---

### Post by 13thMonkey on 2007-05-31
'Pure' SSH will just provide you with a command line, which you can do pretty much everything from if you want of course. If you want a GUI then go with the NX solution (free or otherwise). There are other ways, but that was the easiest and most secure thing I found (and I was new to Linux at the time).

If you're comfortable with the command line then just install OpenSSH, but I'd highly recommend torrentflux on top of that if you use torrents a lot. Either way, there's plenty of guides on here that will point you in the right direction for whichever solution(s) you decide to install.

---

### Post by stuart176 on 2007-06-27
I'm not able to install the Nomachine client on my XP machine at work because I lack admin rights. Is there a portable NX client that I could use to attach to my machine at home?

---

### Post by theDaveTheRave on 2007-06-27
> **stuart176 said:**
> I'm not able to install the Nomachine client on my XP machine at work because I lack admin rights. Is there a portable NX client that I could use to attach to my machine at home?

It may be a bit sneaky, but why not use a live Ubuntu CD?? with a copy of the Nomachine client running- Only being a newby I don't know if this would actually work, but would be "interesting" and probably a disciplinary offence! - another thought would be to convince all your work colleagues that you have found a better operating system and get your boss / the local IT team to allow you to try it out via the live CD (and ultimately a dual boot).


Alternatively can you install it onto a USB Drive and run it from there!?

I would appreciate if any others can confirm if any of these would / wouldn't work.

---

### Post by bodhi.zazen on 2007-06-27
> **13thMonkey said:**
> 'Pure' SSH will just provide you with a command line, which you can do pretty much everything from if you want of course. If you want a GUI then go with the NX solution (free or otherwise). There are other ways, but that was the easiest and most secure thing I found (and I was new to Linux at the time).

If you're comfortable with the command line then just install OpenSSH, but I'd highly recommend torrentflux on top of that if you use torrents a lot. Either way, there's plenty of guides on here that will point you in the right direction for whichever solution(s) you decide to install.

That is partially true.

ssh -X user@host ;)

The -X forwards X so you can run a single app or entire desktop.

If you need an X server on Windows, take a look at cygwin.

You can also try vnc : [http://doc.gwos.org/index.php/Reverse_VNC](http://doc.gwos.org/index.php/Reverse_VNC)

---

### Post by PCFascist on 2007-06-27
run in a terminal
```
sudo apt-get install openssh-server
```

Ensure you have opened your port 22 to the internet in your router.

Then at work bring PuTTY and type in your DynDNS Account address or your IP.
PuTTY is here:
[http://www.chiark.greenend.org.uk/~sgtatham/putty/](http://www.chiark.greenend.org.uk/~sgtatham/putty/)

Your admins at work will still know you are doing something over ssh.... they just won't know what. In places I've worked that was enough to get you fired, but we worked with customer's personal credit card/ssn information.

---

### Post by carlosqueso on 2007-06-27
I use SSH at work too....if you need help finding command line alternatives for your programs, just let us know...there are a lot of good ones out there that run in the command line.

---

