---
title: "Ubuntu Or Xubuntu for a server OS on a “P3 550, 256mb ram”"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by LoicNyssen on 2007-03-20
I have an old Pentium 3, with about 256 mb of ram, and I currently have ubuntu installed on it and it works ok, When I am not doing anything on it, its running at about 25% CPU usage, and 50% memory usage… 

But I recently discovered Xubuntu, now will it really make a difference? And is it designed to be used as a server os? Or more of a os for people with old comps that are just going to be used as pc’s?

---

### Post by zvacet on 2007-03-20
[http://www.xubuntu.org/]("http://www.xubuntu.org/")

---

### Post by LoicNyssen on 2007-03-20
> **zvacet said:**
> [http://www.xubuntu.org/]("http://www.xubuntu.org/")

yes i was just reading that site, I just wanted to get peoples opinions...

---

### Post by steve101101 on 2007-03-20
i am currently running a server using the same amount of resources as yours at idle and runs fine. if its working just leave it alone.

---

### Post by steve101101 on 2007-03-20
if you want a really light weight Server OS look into FREE NAS. it runs very well with no troubles.

---

### Post by K.Mandla on 2007-03-20
> **LoicNyssen said:**
> I have an old Pentium 3, with about 256 mb of ram, and I currently have ubuntu installed on it and it works ok, When I am not doing anything on it, its running at about 25% CPU usage, and 50% memory usage… 

But I recently discovered Xubuntu, now will it really make a difference? And is it designed to be used as a server os? Or more of a os for people with old comps that are just going to be used as pc’s?
Xubuntu is a full-fledged desktop system and will probably make it a little more usable. [Fluxbuntu]("http://www.fluxbuntu.org") will turn it into a speed demon. If you're willing to put a system together yourself, you could try a server installation of Ubuntu, plus Openbox or Fluxbox or IceWM or FVWM. Any one of those will make it move a lot faster. 

But if you want an all-in-one package that will liven it up, I'd recommend Fluxbuntu.

---

### Post by az on 2007-03-20
> **LoicNyssen said:**
> I have an old Pentium 3, with about 256 mb of ram, and I currently have ubuntu installed on it and it works ok, When I am not doing anything on it, its running at about 25% CPU usage, and 50% memory usage&#8230; 

The ram usage is irrelevant, since more ram usage is better.  There is no reason to not use ram if you have it and you don't seem to be doing anything that needs all that much ram.

Howerver, the CPU running at 25 per cent is not right.  It should be pretty much zero when you are not doing anything.  That is, unless you have  alot of stuff running in the background, but that doesn't seem to be what you are describing.

If you are concerned about performance, look into what it chewing up 25 percent of your cpu all the time.  That's not normal.

> **LoicNyssen said:**
> 
But I recently discovered Xubuntu, now will it really make a difference? And is it designed to be used as a server os? Or more of a os for people with old comps that are just going to be used as pc&#8217;s?

The LAMP server stack can run on any Ubuntu setup.  Pretty much any other server, too.  The fact that a lot of people suggest Xubuntu to people who don't want a command-line-only system is simply because Xubuntu was the first "lean" ubuntu derivative and was easy to install.  

It is frankly useless for anything you would need to do to get a web server up and running, though.  It just gives you a desktop.  You don't need a desktop to run a webserver, it's contraindicated (but mostly harmless), in fact.

---

### Post by LoicNyssen on 2007-03-22
> **K.Mandla said:**
>  you could try a server installation of Ubuntu,

I didn't know there was such a thing as a "server installation" of Ubuntu... 


How is that done?

---

### Post by az on 2007-03-22
You can use the alternate cd to do a server installation. There is nothing special about a server installation other than it just installs a base system and the LAMP stack as an option.

You can also download the Ubuntu server cd which does the same thing.  The only difference between those two is that the server cd will install the server kernel.  You can run a server perfectly fine with the generic (desktop) kernel.  The server kernel is better tuned for high-performance server hardware.  Unless you are running it on hardware that was made to be used as a server, use the generic kernel - it works better with most home computer hardware.

---

