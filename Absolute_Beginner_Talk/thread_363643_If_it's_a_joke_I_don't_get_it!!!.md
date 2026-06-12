---
title: "If it's a joke I don't get it!!!"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by deadmonkey77 on 2007-02-17
I can't play wmv files on my totem player, I can't play files i've converted with the ace ripper. At the moment ubuntu is unable to do anything!! Can someone please help me in a language I can understand, where do I get plugins? How do I install them without ubuntu telling me it is unable to do it! Microsoft doesn't seem so bad after all!!

Thanks
:confused: :confused: :confused: :confused: :confused: :confused: :confused: :confused:

---

### Post by highneko on 2007-02-17
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
I think this guide explains all. Good luck, have fun.

---

### Post by villindesign on 2007-02-17
Easiest way is to get automatix and let it install the restricted formats. Go to the [Automix install page [link]]("http://www.getautomatix.com/wiki/index.php?title=Installation") and select the package for your OS version. Download the package and let the deb installer install it for you. Then, you can run the program usually by selecting Applications>>System Tools>>Automatix or by typing automatix2 in the terminal. Once the program appears, go to the 'Multimedia' section and select 'AUD - DVD Codecs' and 'Multimedia Codecs'.  Then click 'start' up top and let it install the codecs. Now you should be able to play restricted formats.

---

### Post by Maestro23 on 2007-02-17
Slow down and take a deep breath.  Do a little reading and walk before you try to run.  Some links that will help you:

Enable Extra Repositories: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

How to Install: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

*Link to the Ubuntu noob guide is in my sig.

Good luck.

---

### Post by rolando2424 on 2007-02-17
I don't think totem can play wmv though, try using VLC player or Mplayer.

---

### Post by xpod on 2007-02-17
> Easiest way is to get automatix and let it install the restricted formats. Go to the Automix install page [link] and select the package for your OS version. Download the package and let the deb installer install it for you. Then, you can run the program usually by selecting Applications>>System Tools>>Automatix or by typing automatix2 in the terminal. Once the program appears, go to the 'Multimedia' section and select 'AUD - DVD Codecs' and 'Multimedia Codecs'. Then click 'start' up top and let it install the codecs. Now you should be able to play restricted formats.

:) 
Dont forget to mention that asides from the codecs Automatix also has numerous other handy applications that you`ll most likely want a few of such as  flash,java,graphics card drivers,p2p programs,mediaplayers and many others besides.

It`s not the "proper" way to install stuff many will tell you but if you just want an easy life these first few days then AX is a really good bet.
You`ll have plenty time later to learn the many other ways of doing stuff.

[http://monkeyblog.org/ubuntu/installing.html](http://monkeyblog.org/ubuntu/installing.html)

---

### Post by deadmonkey77 on 2007-02-17
Thanks people, that's been a great help. It's like trying to learn a whole new language, but I think i'm getting the hang of it. Does anyone know how to convert MS exe files into applications on Ubuntu???

---

### Post by Maestro23 on 2007-02-17
> **deadmonkey77 said:**
> Thanks people, that's been a great help. It's like trying to learn a whole new language, but I think i'm getting the hang of it. Does anyone know how to convert MS exe files into applications on Ubuntu???

Running Windows programs under Ubuntu:

Wine: [http://www.winehq.com/](http://www.winehq.com/)

For games: [http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1](http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1)

*Wine is available from the Ubuntu Repositories via apt-get or Synaptic(GUI).

---

### Post by TeraDyne on 2007-02-17
> **deadmonkey77 said:**
> Thanks people, that's been a great help. It's like trying to learn a whole new language, but I think i'm getting the hang of it. Does anyone know how to convert MS exe files into applications on Ubuntu???

You can't, really. However, many Windows applications run under WINE. Automatix has an option to install WINE in it, so you shouldn't have too many problems there.

After installing WINE and using the "winecfg" command in a terminal, you can usually install and application by opening a terminal (or using one that's already open) and typing "wine FILENAME.exe", where FILENAME is the name of the .exe file.

Keep in mind that not all programs will work. iTunes, for example, won't work under WINE.

---

### Post by putt1ck on 2007-02-17
Wine, CrossOver Office and/or Cedega are the best solution for running Windows applications on Linux. Between them they will get most applications operational, although some will fail (similar compatibility ratio as Vista!).

However, gaming apart, most applications run on Windows will have an equivalent for Linux, even if it is not from the same supplier e.g. for MS Office, use OpenOffice or KOffice, for MS Publisher use Scribus, for Adobe Photoshop use Gimp, for ESRI ArcGIS use gvSIG or QGIS, etc..

HTH

Chris

---

### Post by MetalMusicAddict on 2007-02-17
Also deadmonkey77 please remember that linux isnt windows. There are many things that we cant do by default because of license restrictions.

---

### Post by xpod on 2007-02-17
Once you get your head round the Ubuntu basics and IF you still cant find alternatives to your Windows programs then you could always have a look at VirtualBox

[http://www.virtualbox.org/](http://www.virtualbox.org/)

Virtual machines surely dont come no easier as even i manage to use it without any real trouble.
It`s apparently much better(and easier) than the alternative VM options although i`m only going on what i`ve seen others say.

Get to know your Ubuntu first though......You might just forget all about your Windows apps:)

---

