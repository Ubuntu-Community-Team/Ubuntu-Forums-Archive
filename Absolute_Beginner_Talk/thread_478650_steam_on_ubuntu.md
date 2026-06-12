---
title: "steam on ubuntu???"
date: 2007-06-19
forum: Absolute Beginner Talk
---

### Post by nealj751 on 2007-06-19
is there any way to get valve's Steam running on fiesty? or more specifically the newly release Geometry Wars accesible through steam?  thanks!

---

### Post by Crafty Kisses on 2007-06-19
> **nealj751 said:**
> is there any way to get valve's Steam running on fiesty? or more specifically the newly release Geometry Wars accesible through steam?  thanks!

You should try installing Wine.

---

### Post by diatribe on 2007-06-19
google search steam howto, you basically just install it through wine it is straightforward, also this should be in gaming and leisure

---

### Post by skymera on 2007-06-19
i suggest getting Crossover.
it says its 60 day trial,. but ive had iot for months lol

u can install Steam from that EASILY
and its GUI

---

### Post by Crafty Kisses on 2007-06-19
> **nealj751 said:**
> is there any way to get valve's Steam running on fiesty? or more specifically the newly release Geometry Wars accesible through steam?  thanks!

You can try this:
```
sudo apt-get install wine
```

There's a lot of good tutorials on how to use this Windows emulator.

---

### Post by nealj751 on 2007-06-19
the install file is an .msi file.  when i try to open it with wine i get  Wine: Could not load "blablabla" Bad EXE format for

---

### Post by Crafty Kisses on 2007-06-19
> **nealj751 said:**
> the install file is an .msi file.  when i try to open it with wine i get  Wine: Could not load "blablabla" Bad EXE format for

You can install a program called "AutoMatix" and that will install Wine for you.
[www.getautomatix.com](www.getautomatix.com)

---

### Post by jdzitro on 2007-06-20
> **nealj751 said:**
> the install file is an .msi file.  when i try to open it with wine i get  Wine: Could not load "blablabla" Bad EXE format for

You need to type

**wine msiexec /i SteamInstall.msi**

to make the .msi file work with Wine.

Here is a link to a great HOW TO for Steam on Linux:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam)

It got Counter Strike: Source running pretty well. 

I just bought Geometry Wars on my Steam account tonight. I LOVE this game. Just haven't gotten it to play correctly yet on Ubuntu. I'll let you know if I find anything. Please do the same for me!

---

### Post by DracoPsycho on 2007-06-20
About the game running on Steam, it actually depends on the game, if it uses Source engine it should play fine, if not, then you have to check it out for yourself or here [http://appdb.winehq.org/]("http://appdb.winehq.org/")

Edit:
But I guess it's too new and they don't know that yet either ;)

---

### Post by RexStJames on 2007-07-01
I'm looking to run Geometry Wars through Steam under Wine as well. I got steam installed with wine just fine, and I installed Geometry Wars, but when I try to run it it just sets my resolution to 640x480 (or something like that) and dumps me back at the gnome desktop. 
I'll keep trying, but if anyone has any breakthroughs with this game, let us know!

---

### Post by jdzitro on 2007-07-01
....that's exactly what happens to me. :-(

---

### Post by arochester on 2007-07-01
Look at "Steam, Half-Life, Half-Life 2, Counter-Strike 1.6 and Source with Wine" at [http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam)

---

### Post by jdzitro on 2007-07-01
As I said before, that is what I used to get Counter-Strike: Source and the other hl2 games running. Geometry Wars doesn't work under this. We're looking for something that does.

---

### Post by inuyokai on 2007-07-01
Make sure you have Wine - [www.winehq.org](www.winehq.org) - and that it is installed correctly. You should be able to get the latest version by running the package manager and searching for Wine.

After Wine is installed then install Steam. You could try to install the .msi file by opening terminal and typing msiexec /filepath/filename but I never had success with it.

The attached file should be much easier for you as its SteamInstall.exe. Once you're sure Wine is installed just  click SteamInstall.exe.

It works fine on Kubuntu, except I'm having sound issues - but thats global and not just steam. Whats cool is that it will even put Steam in the system tray when you minimize/close and its just like Windows.

Have fun

---

### Post by jdzitro on 2007-07-01
> **inuyokai said:**
> It works fine on Kubuntu, except I'm having sound issues - but thats global and not just steam.

What works fine?? 
AS WE SAID BEFORE
Steam works fine for us. We want GEOMETRY WARS to work. PLEASE

---

### Post by Enverex on 2007-07-01
> **Codename said:**
> You can install a program called "AutoMatix" and that will install Wine for you.
[www.getautomatix.com](www.getautomatix.com)

Why in gods name did you recommend doing that? It's *nothing* to do with his problem and wouldn't help it at all. To install Wine follow the instructions on > [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

To install MSI files you do "wine msiexec /i whatever.msi"

---

### Post by Motoxrdude on 2007-07-01
As far as i know geometry wars does not work with wine. Sorry.

---

### Post by Tomosaur on 2007-07-01
Fear not! 

There is a great Geometry Wars clone called Grid Wars 2: [http://www.getdeb.net/app.php?name=GridWars+2](http://www.getdeb.net/app.php?name=GridWars+2)

---

### Post by dfreer on 2007-07-01
Also, for the 640x480 problem, do you have 640x480 listed under your correct color depth in /etc/X11/xorg.conf? AFAIK, ubuntu doesn't always list resolutions below the maximum (for example, my max is 1280x800, and by default that is the only resolution listed under 24 color depth). Try adding all of the resolutions below your max, like for me I add "1280x800" "1024x768" "800x600" "640x480" under each and every color depth.

Make sure to backup your /etc/X11/xorg.conf file before you edit it!

---

