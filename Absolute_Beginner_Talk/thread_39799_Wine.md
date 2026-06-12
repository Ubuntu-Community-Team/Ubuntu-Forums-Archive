---
title: "Wine"
date: 2005-06-06
forum: Absolute Beginner Talk
---

### Post by alexmoose on 2005-06-06
as much as we all detest windows, occasionally i prefer to play a few games. on mr previous attempt to configure WINE, i destroied the Kernal, so i figure maybe i should to it with some help this time. what do i need to do to get it to run properly? what proprietary Dlls do i need to download, and where do i copy them to. I haven't done anything yet, so i need to download it, which i MIGHT be able to handle

---

### Post by daller on 2005-12-01
What games do you wanna play?

---

### Post by Kvark on 2005-12-01
Just install Wine with Synaptic and then click on an exe file in Nautilus or run the Windows program with Wine.

But Wine can't play 3D games, you'll need Cedega for that.

---

### Post by polpak on 2005-12-01
[QUOTE=Kvark]Just install Wine with Synaptic and then click on an exe file in Nautilus or run the Windows program with Wine.

But Wine can't play 3D games, you'll need Cedega for that.[/QUOTE]


Not really true. I've had at least as much success with Wine for 3d games as I have with Cedega. Just use the lastes wine releases rather than the stuff in the universe repos. 

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by Robgould on 2005-12-01
Why do you detest Windows?  It is what it is.  Most of us would never have used a computer if not for windows.

---

### Post by Vlammetje on 2005-12-01
Actually... most of us know windows because it happens to be the most common OS... but if any other OS were predominant most of us would just have gotten used to that instead.. I know I would still be using computers, long diustance communications necessity and all that.... windows is not the cause of my PC usage... my windows knowledge is sort of the result of it though ;)

---

### Post by Robgould on 2005-12-01
Just saying...I don't have windows.  I like linux, and it is my choice, but windows is just an operating system, nothing to hate.

---

### Post by arnieboy on 2005-12-01
[QUOTE=alexmoose]as much as we all detest windows, occasionally i prefer to play a few games. on mr previous attempt to configure WINE, i destroied the Kernal, so i figure maybe i should to it with some help this time. what do i need to do to get it to run properly? what proprietary Dlls do i need to download, and where do i copy them to. I haven't done anything yet, so i need to download it, which i MIGHT be able to handle[/QUOTE]
install and configure the latest version of wine with [automatix]("http://ubuntuforums.org/showthread.php?t=66563")

---

### Post by dosed150 on 2005-12-03
ive used automatix to install wne  it told me to use wine cfg to finish set up[ of wine how do i do this

---

### Post by arnieboy on 2005-12-03
[QUOTE=dosed150]ive used automatix to install wne  it told me to use wine cfg to finish set up[ of wine how do i do this[/QUOTE]
open up terminal and type:
```
winecfg
```
and press enter

---

### Post by dosed150 on 2005-12-03
i did that and i just get command not found

---

### Post by arnieboy on 2005-12-03
[QUOTE=dosed150]i did that and i just get command not found[/QUOTE]
but did u install wine from automatix first? u need to install wine and then run winecfg.

---

### Post by dosed150 on 2005-12-03
yeh i opened automatix clicked on wine and it ran

---

### Post by dosed150 on 2005-12-03
its sorted noe so how do i actually open wine?

---

### Post by arnieboy on 2005-12-03
[QUOTE=dosed150]its sorted noe so how do i actually open wine?[/QUOTE]
there are two ways to use it.
1) wine <path to exe>
2) right click any exe and hit properties and select "open with" and choose wine.
now whenever u double click any exe it will open with wine.

---

### Post by cs378 on 2006-01-05
thats what i did too using automatix to install wine

but i cant run winecfg nor wine

both command were not found.

:(

---

### Post by cs378 on 2006-01-05
Just did

sudo apt-get install wine

it seems that when i did automatix it didnt really finish downloading wine so therefore not installed. after during that, it resumed the download and continued with the installation.

now

winecfg works

:)

---

### Post by R3linquish3r on 2006-01-05
anyone know a way to isntall wine on 64bit? it  tells me its impossible to install when i try to do it in synaptic

---

### Post by iand675@gmail.com on 2006-01-05
I think you can force the architecture, but I don't know if that's recommended.

---

### Post by jeffreyvergara.NET on 2006-01-06
hello (sorry if I hijack this thread), where can I get wine version 0.9.1.deb? I need it to try Photoshop CS? it said it worked with 0.9.2 but I cant, then someone said it worked in wine 0.9.1 version

---

