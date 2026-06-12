---
title: "Using nvidia-glx in fiesty without apt-get"
date: 2007-07-31
forum: Absolute Beginner Talk
---

### Post by stil on 2007-07-31
Is this a big issue? I don't have a working internet connection at home. 

I've installed fiesty once already. Everything but the wifi and sound seemed to be ok. Nvidia-glx appeared in synaptic but the version details and info were blank.:confused: I went back to 6.06lt instead because I have a basic idea of how to get the restricted drivers running.

I've been trawling packages.ubuntu.com for fiesty stuff. If someone could point out the packages I'm going to need to get nvidia-glx running (and perhaps glx-dev for wine) that would be most appreciated.

So far I have a list that looks like this...

libc6_2.5-0ubuntu14_i386.deb
libgl1-mesa-glx_6.5.2-3ubuntu7_i386.deb
libglib2.0-0_2.12.11-0ubuntu1_i386.deb
libglu1-mesa_6.5.2-3ubuntu7_i386.deb
libglu1-mesa-dev_6.5.2-3ubuntu7_i386.deb
libgtk2.0-0_2.10.11-0ubuntu3_i386.deb
nvidia-glx_1.0.9631+2.6.20.5-16.29_i386.deb
nvidia-glx-dev_1.0.9631+2.6.20.5-16.29_i386.deb
nvidia-kernel-common_20051028+1ubuntu7_all.deb

and so on...

The number of branching meta-dependencies is quite mind-boggling.8-[

---

### Post by stil on 2007-07-31
btw, a long shot, but is there anyone reading this who has a toshiba A200 series laptop? and can you give an impression of how your system is going with fiesty?

---

### Post by psyopper on 2007-07-31
I would start with 

sudo aptitude install nvidia-glx nvidia-glx-dev

Aptitude should look through the dependencies of the packages you are installing and install them as well, unlike apt-get which requires you to list the dependencies in the apt-get command.

Of ocourse it depennds on your video card - If it's a GF4 or older you want nvidia-glx, if it's a GF 5,6 or 7 you'll want nvidia-glx-new. If it's a GF 8 you'll want to manually install the drivers from Nvidia's site. For the love of all that is good and might, please do not use Envy to install your drivers unless it is your absolute last choice.

---

### Post by wolfen69 on 2007-07-31
> sudo aptitude install nvidia-glx nvidia-glx-dev

before doing above, you must:
```
sudo aptitude update
```

---

### Post by stil on 2007-07-31
I have no idea what Envy is. So far most of my tinkering has been through the console and manual installation of .deb files

aptitude isnt going to try and access the internet, is it? For the most part, whenever I need something that's listed under synaptic, any installation I attempt tries reach the net. It's quite frustrating. Is there a way to sort by what is actually available from the CD *only*?

My GPU is a Go7300. This seems to register correctly under nvidia-glx in dapper. I'll try -new anyway.

---

### Post by stil on 2007-07-31
> **wolfen69 said:**
> before doing above, you must:
```
sudo aptitude update
```

I don't want to sound like I'm harping on about this, but could please explain what that actually does? Is all well and good if it works, but if I don't understand what I just did...:confused:

---

### Post by hessiess on 2007-07-31
google sertch ubuntu pacages, its not hard to find. and sertch for what you need. i uset to have a internet problem on linux too:)

---

### Post by stil on 2007-07-31
> **hessiess said:**
> google sertch ubuntu pacages, its not hard to find. and sertch for what you need. i uset to have a internet problem on linux too:)

I've gotten some results doing this. The problem with this method is running into dependency problems. Things get very hairy very quickly.:lolflag:

---

### Post by hessiess on 2007-07-31
bet your dependency problem is faster to rectofy than mine was, only had a net conection on a windows install that took 10 munites to boot!

you should alredy have all the dependencys for nvidia-glx

is it just a problem with ubuntu and net at home? or do you have no conection atall?

---

### Post by stil on 2007-07-31
I have to visit my sister and use her connection. I have no internet connection at home at all. I dont even have a landline (still necessary for adsl)

---

### Post by psyopper on 2007-07-31
> **stil said:**
> I don't want to sound like I'm harping on about this, but could please explain what that actually does? Is all well and good if it works, but if I don't understand what I just did...:confused:

From the man pages on Aptitude:
       update
          Updates the list of available packages from the apt sources (this is
          equivalent to &#8220;apt-get update&#8221;)

It essentially goes to the list of repositories you have configured as usable and searches through them. Aptitude keeps a list of all of the packages in your repositories on your local computer so it knows what is available to download. The Update command makes Aptitude go to each repo and check what software is available, particularly what software has been added or changed since the last time you ran Update.

If there is a command you are curious about you can look at that commands "man" page. "man" is short for manual. TO look at the man pages for Aptitude open a terminal:
```
man aptitude
```
To quit the man page and get back to the terminal simply press the Q button. Page Up/Down pages up and down, and the arrows up and down will scroll line by line.

Unfortunately you are kind of stuck without an internet connection. You can force it to use the CD, but there's not nearly as much there as there is online. What about a local coffee shop with a wifi connection? I realize you are in NZ and not the USA and I'm not really sure if you guys do that sort of thing down under...

---

### Post by stil on 2007-08-01
My Wifi isn't actually supported afaik, until I can get ndiswrapper working. Which equals more back and forth shenanigans... At the moment I'm using the laptop exclusively for writing. (yay, free office app) There's no rush to go back to Xp or whatever.

---

### Post by hessiess on 2007-08-01
if you intend to stick with ubuntu as your main os, it may be easier to just buy a new wi fi card withc is supported out the box

---

### Post by stil on 2007-08-01
afaik, being a notebook system the wifi is part of the motherboard. If I can just get wifi going things will be much easier, I can appreciate that a lot, but buying more hardware isn't an option right now.

---

