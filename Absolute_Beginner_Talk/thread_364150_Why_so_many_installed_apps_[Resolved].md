---
title: "Why so many installed apps? [Resolved]"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by cctez on 2007-02-17
Admittedly, I am a noob/retard, very accustomed to Windows.

That said, I am a long time tech pro/programmer and feel like I am catching on pretty fast. So far I am loving Ubuntu 6.10. I installed using the desktop install image.

I assume that I am ***must*** have missed a step somewhere, that said: 

Here's the one thing I just don't get, why are so many irrelevant packages installed by default? For example: drivers for GPUs I don't have, bluetooth libraries, tons of digital camera stuff, etc. Why didn't Ubuntu poll for these devices before it loaded me up with their drivers? 

I ask because, the biggest thing that I dislike about the XP install is - The Bloat. You know it's one thing to copy the files onto a machine, but it's another to go ahead and install them without reason! I hate that I need to roll my own slipstream installation, just to get rid of the massive amount of bloat ware that's forced into the target machine. 

What did I do wrong, or what should I do in the future to avoid the bloat ware?
Thanks,
- C

---

### Post by aysiu on 2007-02-17
> **cctez said:**
> 
What did I do wrong, or what should I do in the future to avoid the bloat ware? You did the standard install.

Next time, use the Alternate CD (not the Desktop CD) and select the *Install a Server* option. It doesn't actually install a server (that's what the Server CD does). It gives you a total barebones installation.

From there, you can install whatever else you want on that--no bloat, only the packages you've handpicked.

I would advise starting with this: ```
sudo apt-get update
sudo apt-get install x-window-system-core xterm gdm icewm menu firefox synaptic
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm start
``` From there, you'll have a graphical user interface, a terminal, a web browser, and a graphical way to install more software.

---

### Post by cctez on 2007-02-17
Hi aysiu. Thank you, very clear. 

I knew that I must have made a simple mistake. So, if I want to start over, can I run that from my existing install or do I need to download the Alternate CD image?
- C

---

### Post by aysiu on 2007-02-18
> **cctez said:**
> Hi aysiu. Thank you, very clear. 

I knew that I must have made a simple mistake. So, if I want to start over, can I run that from my existing install or do I need to download the Alternate CD image?
- C
Well, the problem is that you already have a lot of crap installed.

So the "easiest" way to do it would be to just uninstall everything except the base system. I'm not sure what all those packages are, though.

You'd essentially be doing the opposite of what I just described--instead of starting with almost nothing and adding only what you want, you'd be looking through everything you already have installed and removing what you don't need. This is kind of annoying, but it would actually take less time than downloading an entire ISO and then reinstalling Ubuntu. Your choice as to which is preferable.

If you want to remove things, go to Synaptic Package Manager (System > Administration > Synaptic Package Manager), sort by what's installed (the little green box to the left of the package list) and just right-click and mark for removal anything you don't like. Synaptic will warn you if that also will remove something you *do* want to keep.

---

### Post by cctez on 2007-02-18
Sure, my initial instinct was to do just that.

This is where my knowledge of the OS architecture kills my ability to make the right choice. If you do this in windows, it orphans so much junk in the file system and registry. And, I do know we are talking apples and oranges here. But, if I remove tons of stuff, will I end up with a clean installation or will it leave a trail of garbage behind?
- C

---

### Post by aysiu on 2007-02-18
> **cctez said:**
> Sure, my initial instinct was to do just that.

This is where my knowledge of the OS architecture kills my ability to make the right choice. If you do this in windows, it orphans so much junk in the file system and registry. And, I do know we are talking apples and oranges here. But, if I remove tons of stuff, will I end up with a clean installation or will it leave a trail of garbage behind?
- C
There may be some garbage.

Considering the kinds of questions you're asking, I think it may be worth your time to download the Alternate CD and install a barebones and add from there--you'll be happier in the end.

---

### Post by irish_flu on 2007-02-18
Synaptic will help you clean up *some* of the garbage, though.  You can mark for "removal", or mark for "complete removal" (which will also remove configuration files and such).

---

### Post by cctez on 2007-02-18
> **aysiu said:**
> There may be some garbage.

Considering the kinds of questions you're asking, I think it may be worth your time to download the Alternate CD and install a barebones and add from there--you'll be happier in the end.

Thanks for the honest advice aysiu, you're a champ. I will go ahead and reinstall from the Alternate CD.

- C

---

### Post by cctez on 2007-02-18
Well, I am back from a very skinny install... 

Aysiu, is your scripting a tad bit off? I had trouble getting everything to roll in that way. Regardless, I worked through it. Watching the install tick by from the command line helped me learn a lot and get a better feel for the kernel versus shell packages...

Although this puts me in a great position for a tidy installation, getting here was tough for a guy with only 12 hours of recent Linux experience. I wouldnt recommed this process for most new users.

Thanks again,
- C

---

### Post by aysiu on 2007-02-18
Yeah, sorry. I just realized that [*x-window-system-core* has suddenly become a "transitional package"](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=x-window-system-core&searchon=name&subword=1&version=all&release=all).

Glad you got it figured out eventually.

---

### Post by cctez on 2007-02-19
No problem, thanks for the help. Learned quite a bit in the process...
- C

---

### Post by aysiu on 2007-02-19
> **cctez said:**
> No problem, thanks for the help. Learned quite a bit in the process...
- C
Just for future reference, do you know what package replaced *x-window-system-core*?

---

### Post by lucia_engel on 2007-02-19
I believe it's *xorg*.

---

### Post by aysiu on 2007-02-19
> **lucia_engel said:**
> I believe it's *xorg*.
Great. Thanks!

---

### Post by kinematic on 2007-02-19
@cctez

next time you might want to use aptitude for installing packages.
aptitude is a front end to dpkg(the debian package management system)just like apt-get but it handles and resolves dependencies much better.
one thing to keep in mind is that if you use apt-get stick with it.
if you use aptitude stick with that because the two of them don't always play nice.

---

### Post by cctez on 2007-02-19
> **lucia_engel said:**
> I believe it's *xorg*.

I think that was correct, I used xorg...

---

### Post by cctez on 2007-02-19
> **kinematic said:**
> @cctez

next time you might want to use aptitude for installing packages.
aptitude is a front end to dpkg(the debian package management system)just like apt-get but it handles and resolves dependencies much better.
one thing to keep in mind is that if you use apt-get stick with it.
if you use aptitude stick with that because the two of them don't always play nice.

Thanks kinematic. I'll try that next time.

Since then, I have run the install a bunch of times to get a better feel for things. I need to be rock solid on the OS, since I am a developer. Each time I run into a snag it's taking less time for me to resolve. Hopefully, I can manage the transition away from Windows.
- C

---

### Post by Dave / Mosaic on 2007-02-20
aysiu, cctez--

Another newbie / borderline retard here...

I've been following your discussion and doing more or less the same thing yesterday and today.  I've been trying to get 6.10 to install (my first Linux) on a blue and white G3 power mac; with the desktop CD I get the installer hanging at 91% looking for an IDE driver called (IIRC) aec62xx...  Last night I downloaded the alternate CD to try that, but I got a different sort of hang - the installer would hang during "Select and Install Software" and refuse to do it; the rest of the install proceeds okay, though, and so I end up with a command line (base, I think) kernel...

Anyway: when I follow these instructions:

> sudo apt-get update
> sudo apt-get install x-window-system-core xterm gdm icewm menu firefox > synaptic
> sudo dpkg-reconfigure xserver-xorg
> sudo /etc/init.d/gdm start

I get some other errors (besides the already-mentioned x-window-system-core thing):

-- icewm and menu also couldn't be found, as best as I recall...

-- the command to start gdm gives a message that it is starting, but doesn't do anything...

I got a working X desktop, however, by installing the target "ubuntu-desktop" last night for the first time, however, so I know I can get this to work somehow.  I'd like to end up with a more minimal system, however, minus all the excess junk like for playing movies, etc., so any advice you all can give, as to what you actually used to get to a minimal working X desktop, I would appreciate much.

Thanks--

--Dave

---

### Post by kerry_s on 2007-02-20
Cause the instructions are incomplete. PPC version-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current/images/powerpc/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-powerpc/current/images/powerpc/netboot/mini.iso)
grab that mini.iso. You'll be installing the latest straight from the web.

type> server <to do the server install
At the software selection, just tab and enter. Your going to select your own packages later.
login
sudo su
nano /etc/apt/sources.list
comment(#) out all the deb-src lines and uncomment all the deb lines
ctrl and x and y and enter to save
apt-get update
apt-get install x-window-system-core gdm icewm firefox synaptic
type> reboot
choose icewm from the session menu and login
open synaptic and continue selecting what you want, you'll need a file manager,editor,etc...

When i'm building light, i'll use->
apt-get install x-window-system-core gdm fluxbox emelfm leafpad dillo firefox synaptic

emelfm= file manager
leafpad= editor
dillo= small fast web browser
firefox=bigger web browser

---

