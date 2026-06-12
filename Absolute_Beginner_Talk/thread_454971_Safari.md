---
title: "Safari"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by sethdotcom on 2007-05-26
Is there anyway to run Apple's Safari in windows or Ubuntu?

---

### Post by jwelsh405 on 2007-05-26
No i do not think there is a way seeing how it is apples web browser and they are very hush about their code unless the code is meant to be cracked hahahahaha

---

### Post by teddybairs1 on 2007-05-26
I was just reading that Safari is based on KHTML the same as Konqueror for KDE. Konqueror is, in effect, an open source "sister" of Safari.

---

### Post by sethdotcom on 2007-05-26
> **teddybairs1 said:**
> I was just reading that Safari is based on KHTML the same as Konqueror for KDE. Konqueror is, in effect, an open source "sister" of Safari.

Really I allways thought Konqueror  ran like safari they are both blazing fast

i just wanted to run safari, it is very fast

---

### Post by teddybairs1 on 2007-05-26
Yeah, I did a google search for "Safari Linux" to see if I could come up with a port of Safari to Linux and found several articles with Steve Jobs saying that they had taken the KHTML code and done their own polishing to it to produce Safari. Most of the articles are three or four years old. so, I guess if you like Safari, then Konqueror is the next best thing on Linux given their "genetic" relationship.
I usually use Firefox just because most websites now support it for video etc. and they don't support the other browsers on Linux very well. But I've used Opera, Konqueror, Epiphany, and Iceape as well. Where speed is concerned, on the Gnome desktop I recommend Epiphany, and then Konqueror for KDE. But both of these will limit your web browsing just because Firefox is better supported now than they are, but otherwise they;re good, fast, lightweight browsers.

---

### Post by ripperzane on 2008-04-01
Easily Said: Play on Linux has a preset for installing Safari on Ubuntu 7.10. Worked for me and I am running the x64 version of Ubuntu 7.10.

RZ oh goto HowtoForge and search PlayforLinux, or go [here!]("http://tinyurl.com/33m5sm")

Hope this helps.
RZ


---

### Post by altonbr on 2008-04-10
> **ripperzane said:**
> Easily Said: Play on Linux has a preset for installing Safari on Ubuntu 7.10. Worked for me and I am running the x64 version of Ubuntu 7.10.

RZ oh goto HowtoForge and search PlayforLinux, or go [here!]("http://tinyurl.com/33m5sm")

Hope this helps.
RZ

Please don't use tinyurl so people know where they're being linked to.

---

### Post by Jest3r on 2008-04-10
Could always try wine, But might be better just using some native software

HOWTO taken from winehq - [http://appdb.winehq.org/appview.php?iVersionId=8248](http://appdb.winehq.org/appview.php?iVersionId=8248)
 
**HOWTO**
Installing and Running Safari
(recommend to use latest wine)

   [LIST]
[*]1. Download winetricks ([http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)) and run

```
sh winetricks winver=winxp corefonts vcrun2005
```

[*]   2. Download Safari Beta 3.0.4 "for Windows XP or Vista" (without Quicktime) from [http://www.apple.com/safari/](http://www.apple.com/safari/) and run it with

```
wine Safari304BetaSetup.exe
```

[*]      Deselect Install Bonjour for Windows and Install Apple Software Update.

[*]   3. Start Safari.exe from ~/.wine/drive_c/Program Files/Safari/.
```

wine ~/.wine/drive_c/Program Files/Safari/Safari.exe

```
**Known Issues**

[*]    * No space between menu items in menubar
[*]    * It tries to install Bonjour although you have unselect it and so the installation doesn't work.
[*]      Solution: This is fixed with Safari Beta 3.0.4 installer

**Hints**

[*]    * For using embedded Flash you need to install Adobe Flash Player from [http://www.adobe.com/products/flashplayer/](http://www.adobe.com/products/flashplayer/) (wine install_flash_player.exe).
[/LIST]

---

### Post by PmDematagoda on 2008-04-10
Please do not resurrect old threads, it is usually just in vain since it is very likely that the OP would have fixed his/her problem.

---

