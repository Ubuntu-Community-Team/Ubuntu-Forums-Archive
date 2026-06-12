---
title: "Problems with Synaptic - and updating software."
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by nafetski on 2007-12-06
The situation that I'm having seems different from the ones others are experiencing when I search the forums/google.

Synaptic finds software updates daily and notifies me of them...most of the problems that I've seen people having with Synaptic has something to do with their source list, if mine is finding updates is it safe to assume that my sources are fine?

When I click on "install Updates" it has the "Checking for New Updates" dialogue box come up as if I pushed the "Check for New Updates" button.  It never installs...everytime I click install it just checks for the updates again.

I've been installing the updates from the command line, but I forgot the command >_<  I had it written down and can't find it on a search...however I'd much rather have the GUI version working!

---

### Post by mali2297 on 2007-12-06
Try updating from the command line and see if you get any errors.
```

sudo apt-get update
sudo apt-get upgrade

```

---

### Post by mali2297 on 2007-12-06
> **nafetski said:**
> 
Synaptic finds software updates daily and notifies me of them...most of the problems that I've seen people having with Synaptic has something to do with their source list, if mine is finding updates is it safe to assume that my sources are fine?

When I click on "install Updates" it has the "Checking for New Updates" dialogue box come up as if I pushed the "Check for New Updates" button.  It never installs...everytime I click install it just checks for the updates again.


It sounds like you use the update manager, not Synaptic. It is possible to update from Synaptic though, try it.

Also, try starting the update manager from the command line
```

gksudo update-manager

```
Any errors?

---

### Post by nafetski on 2007-12-06
When I run

gksudo update-manager

Nothing happens.  No errors, no program load...just goes right back to the command line.

When I upgrade/update from the command line it works fine.

I didn't know that update manager wasn't part of Synaptic...that would explain why when I reinstalled synaptic I didn't notice any difference ;D

Also...should mention that it does show that updates are available (at the top right of my screen) is that a function of update manager, or synaptic?  

Thanks again for the replies

---

### Post by mali2297 on 2007-12-06
> **nafetski said:**
> When I run

gksudo update-manager

Nothing happens.  No errors, no program load...just goes right back to the command line.

When I upgrade/update from the command line it works fine.

I didn't know that update manager wasn't part of Synaptic...that would explain why when I reinstalled synaptic I didn't notice any difference ;D

Can you run Synaptic without any problems then?

> 
Also...should mention that it does show that updates are available (at the top right of my screen) is that a function of update manager, or synaptic?  

That belongs to the update manager.

---

### Post by drs305 on 2007-12-06
```
sudo aptitude reinstall update-manager
```

---

### Post by nafetski on 2007-12-06
> Can you run Synaptic without any problems then?

Good call, I haven't tried running Synaptic directly actually...I went to applications > add/remove and when I tried to install an application it just said 

"Application Installation Failed
There has been a problem during the installation of the following application
Dosbox Emulator" (Does it with allt he applications I've tried.

When I go to run synaptic directly from System > administration I get no error, but I also get no program loaded....I tried reinstalling, and still no program loads.  Could I be trying to reinstall the wrong package?

```
aptitude reinstall synaptic
``` looks like it reinstalls correctly, but the program does not load.

I'm assuming this could be the root cause of my update manager not working?  If so, any pointers on how to fix it?  When I googled I saw a lot of people who at least had error messages pointing them in the right direction...I get nothing!

---

### Post by mali2297 on 2007-12-06
Might the error concern **gksudo**? Try
```

gksudo gedit

```
Does Gedit open?

---

### Post by nafetski on 2007-12-06
I tried it...and nothing happened (just got pushed back to command line)...

Then, just on a hunch I logged in as root and tried it.  I got the following error message

```
root@sflee-laptop:/home/sflee# gksudo gedit

(gedit:10206): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

Tho gedit DID open when I tried it as root

---

### Post by rsambuca on 2007-12-06
You are obviously missing some packages from your installation.  Try

sudo apt-get install ubuntu-desktop

---

### Post by rsambuca on 2007-12-06
> **nafetski said:**
> I tried it...and nothing happened (just got pushed back to command line)...

Then, just on a hunch I logged in as root and tried it.  I got the following error message

```
root@sflee-laptop:/home/sflee# gksudo gedit

(gedit:10206): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

Tho gedit DID open when I tried it as root

And why have you activated root login?

---

### Post by mali2297 on 2007-12-06
The problem is then with gksu/do.

View the hidden files in your home directory and move files such as **.gksu.lock** to some other location.

Also try reinstalling gksu,
```

sudo apt-get --reinstall install gksu

```

---

### Post by nafetski on 2007-12-06
Reinstalled gksu, and moved the .gksu.lock file around (but wasn't sure where to put it...was that to just test file permissions?)

I don't really have a reason as to why I logged in as root to be honest.  sudo has always been kind of finakey when I used it (like I said, linux noob...and I know I know, I shouldn't log in as root probably ever) so its a bad habit I have.

Initially was going to just poke around on Ubuntu to learn my way around, but I installed Gutsy 3 weeks ago and I haven't logged onto my windows machine once.  Just trying to get everything as cleaned up as possible tho =p

So if the problem is in gksu/do then how can I fix it?  I did both of your reccomendations of reinstalling gksu, and checking for any missing packages in my installation...neither warranted any results.

Thanks again for the replies and time!

---

### Post by nafetski on 2007-12-07
New updates available today, update manager still being a butthole.  Any other ideas before I just backup and reinstall?

---

