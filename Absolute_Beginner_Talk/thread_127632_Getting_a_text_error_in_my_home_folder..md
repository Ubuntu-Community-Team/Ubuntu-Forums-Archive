---
title: "Getting a text error in my home folder."
date: 2006-02-09
forum: Absolute Beginner Talk
---

### Post by WickedGood on 2006-02-09
I tried adding a skin to Vlc and now no matter what i try i can't seem to get it to work, i've tried uninstalling through synaptic but to no avale, ant help please.

Below is a text log that ends up in my home folder everytime i try and open it.

```
main debug: using interface module "skins2"
main debug: interface initialized
main debug: thread 2967985072 (manager) created at priority 0 (src/interface/interface.c:196)
skins2 debug: Using skin file: /tmp/vltG5tlAV/theme.xml
main debug: looking for xml module: 2 candidates
main debug: using xml module "xml"
main debug: creating access '' path='/tmp/vltG5tlAV/theme.xml'
main debug: looking for access2 module: 4 candidates
vcd debug: trying .cue file: /tmp/vltG5tlAV/theme.cue
access_file debug: opening file `/tmp/vltG5tlAV/theme.xml'
main debug: using access2 module "access_file"
main debug: pre buffering
main debug: received first data for our buffer
skins2: skin: VLC OSX Interface  author: BigBen
skins2 debug: Unable to open the font /home/deanlawrence/.vlc/skins2/fonts/FreeSans.ttf
skins2 debug: Unable to open the font share/skins2/fonts/FreeSans.ttf
skins2 debug: Loading font /usr/share/vlc/skins2/fonts/FreeSans.ttf
main debug: looking for decoder module: 22 candidates
main debug: using decoder module "png"
main debug: looking for video filter2 module: 3 candidates
ffmpeg debug: input: 424x152 RV24 -> 424x152 RV32
ffmpeg debug: libavcodec already initialized
main debug: using video filter2 module "ffmpeg"
skins2 debug: Loading font /tmp/vltG5tlAV/FreeSansBold.ttf
skins2 debug: Loading font /tmp/vltG5tlAV/FreeSansBold.ttf
main debug: unlocking module "png"
main debug: unlocking module "ffmpeg"
main debug: unlocking module "xml"
main debug: unlocking module "access_file"
skins2 debug: Loading theme configuration
main debug: unlocking module "png"
main debug: unlocking module "ffmpeg"
main debug: unlocking module "xml"
main debug: unlocking module "access_file"
skins2 debug: Loading theme configuration
```

---

### Post by aysiu on 2006-02-10
I don't know what the folder is for VLC exactly, but every program has a hidden configuration file somewhere in your /home directory.

To view the hidden files press Control-H (in Gnome) or Alt-V, then H (in KDE).

I see, for example, that my Firefox settings are in .mozilla and that my Wine settings are in .wine.

Maybe there's a .vlc folder hidden in there somewhere? If so, delete it and restart VLC.

---

