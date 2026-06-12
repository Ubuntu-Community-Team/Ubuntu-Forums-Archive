---
title: "How to install Gnome on server edition?"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by uberhaxor??? on 2007-08-08
Hello. I am a complete and utter noob. I need help with this. Please don't use complicated language and so on, just tell me the simple, basic thing to do. 

I have installed ubuntu server edition. To my complete and utter surprise, it was command-line based! I was lost. What do i do to install GNOME? I have tried apt-get install gnome; I have tried apt-get install ubuntu-desktop. All those options. It can never seem to find the package, and i don't know how to connect to the internet to download it. 

Please help me with this big problem!:(:(:(

---

### Post by Inxsible on 2007-08-08
so are you saying that you internet is not working or simply your wireless ?

you have 3 options with the 1 st being the fastest

1) if your internet works, then connect it to a lan cable and then do ```
sudo aptitude install ubuntu-desktop
```2) Or download an ubuntu desktop edition iso, burn it on cd and re-install the OS

3) Order a ubuntu desktop edition cd from Canonical

---

### Post by uberhaxor??? on 2007-08-08
My internet connection does work, its a lan cable, but i heard that you need to enable universe or something like that. I haven't done any of that. i have done the aptitude thing but it doesn't work.

---

### Post by Rocket2DMn on 2007-08-08
Remove the # sign in front of the lines for universe and multiverse in your sources.list file, then update apt (not upgrade):
```
sudo nano /etc/apt/sources.list
sudo apt-get update
```
Now you can try to install the stuff you need:
```
sudo apt-get install ubuntu-desktop gdm
``` Then start gdm (GNOME desktop manager)
```
sudo /etc/init.d/gdm start
```

---

### Post by uberhaxor??? on 2007-08-08
Ho do i edit the file? how do i even reach it?

---

### Post by tgm4883 on 2007-08-08
Oh the mis-information in this thread.

If apt-get doesn't work, aptitude isn't going to work.

The best idea came from Rocket2DMn, as he hit the nail on the head.  (although maybe by accident)

ubuntu-desktop is in main, so you don't have to activate universe or multiverse.

You do need to do sudo apt-get update.

Then do sudo apt-get install ubuntu-desktop

---

### Post by uberhaxor??? on 2007-08-08
How do i edit the file? how do i even reach it?

---

### Post by uberhaxor??? on 2007-08-08
Sorry, i see what you mean

---

### Post by uberhaxor??? on 2007-08-08
it still says that ubuntu-package can't be found!

---

### Post by Inxsible on 2007-08-08
> **tgm4883 said:**
> Oh the mis-information in this thread.

If apt-get doesn't work, aptitude isn't going to work.

I dont see any mis information. in his first post he said he used apt-get install ubuntu-desktop which is very different than sudo apt-get install

i was not trying to show the difference between apt-get and aptitude but rather the difference between sudo'ing and not sudo'ing

---

### Post by uberhaxor??? on 2007-08-08
well i used sudo, and it still doesn't work. I'm over this. Can anyone please tell me how to install x window manager?

---

### Post by RomeReactor on 2007-08-08
Hi. If you *do* have a wired connection working, try pinging Google:
```
ping -c 3 google.com
```
please post the results here.

---

### Post by tgm4883 on 2007-08-08
> **Inxsible said:**
> I dont see any mis information. in his first post he said he used apt-get install ubuntu-desktop which is very different than sudo apt-get install

i was not trying to show the difference between apt-get and aptitude but rather the difference between sudo'ing and not sudo'ing

I stand corrected.  I thought you were saying to use aptitude since apt-get didn't work.

To the OP.  Install the desktop version.

---

### Post by uberhaxor??? on 2007-08-08
Ping results host not supported or recognised or something like that.

---

### Post by sisco311 on 2007-08-08
please post the results of
```
lspci
```
and
```
ifconfig
```

---

### Post by Rocket2DMn on 2007-08-08
If those packages actually installed, but you just can't get the X-server to run, try running this configuration for the X-server.   Use TAB to move around and SPACEBAR to select when appropriate:
```
sudo dpkg-reconfigure xserver-xorg
```
Then you should be able to run X, we'll make sure your on runlevel 5 first (you never know):
```
sudo init 5
startx
```

---

### Post by gn2 on 2007-08-08
> **uberhaxor??? said:**
> well i used sudo, and it still doesn't work. I'm over this. Can anyone please tell me how to install x window manager?
.
These instructions are for Xubuntu but should work perfectly for installing ubuntu-desktop 

[https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)

---

### Post by Kuroda_Shun on 2007-11-09
So we can not install Gnome over a server edition? Is Xubuntu as close to the same thing?

---

### Post by Willye on 2007-11-09
i think, that  you should reinstall ubuntu with desktop version, i had the same problem than you, and i did all that the others users told to you, then i'm downloading the desktop version and i'll try to install again

Good Luck my frined    :guitar:

---

