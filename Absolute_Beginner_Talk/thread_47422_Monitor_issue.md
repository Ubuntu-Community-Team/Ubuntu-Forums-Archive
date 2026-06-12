---
title: "Monitor issue"
date: 2005-07-08
forum: Absolute Beginner Talk
---

### Post by Dale McGarry on 2005-07-08
Hello,

Very,very, new to Kubuntu and Linux. I'm having issues with the monitor screen size. After installation it reads 640x480 or 320x240 with a refresh rate of 60Hz. I read some of the posts to try and find out how to correct this problem, but no luck so far.

Here is what I can do so far. I can open the terminal manager and at the prompt type xdpyinfo and I can see my monitor settings under dimensions:   640x480 pixels (217x163 millimeters). At the end of this list is another prompt and I can type kwrite and it takes me to the editor and from there I am lost. The other posts talk about inserting a edit/etc/X11/xorg.conf command, but I haven't had any success in using it at any prompt or the editor.

Help please.

---

### Post by frodon on 2005-07-08
OK
if you have kubuntu you don't have gedit but you can use or install another text editor (like emacs or nedit). 
For exemple if you want to install nedit: ```
sudo apt-get install nedit
```Then post here the content of your xorg.conf file, important if you want help :```
sudo gedit /etc/X11/xorg.conf
```or```
sudo nedit /etc/X11/xorg.conf
```or replace the gedit by any text editor you have.

---

### Post by supenguin on 2005-07-08
There's not really a command. They just mean open the /etc/X11/xorg.conf file in your favorite text editor. You'll want to make sure the refresh rates and resolutions are set to what you want them to be.

Here's a sample of what I'm talking about:

```
Section "Monitor"
    Identifier      "NEC FE1250"
    VendorName      "NEC"
    ModelName       "NEC61ab"
    HorizSync 31 - 110
    VertRefresh 55 - 160
End Section

Section "Screen"
     Identifier      "Default Screen"
     Device          "Intel Corporation 82865G Integrated Graphics Device"
     Monitor         "NEC FE1250"
     DefaultDepth    24
     SubSection "Display"
         Depth           24
         Modes           "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

Note that whatever resolution you list first, your system will attempt to use first. Also, this isn't my whole xorg.conf, just the bits you'll most likely need to change.

---

### Post by Dale McGarry on 2005-07-08
Thanks,
 I found my way to that section and attempted to make changes, but when I clicked  to save, it would not allow me. What did I do wrong?

---

### Post by poofyhairguy on 2005-07-08
[QUOTE=Dale McGarry]Hello,

Very,very, new to Kubuntu and Linux. I'm having issues with the monitor screen size. After installation it reads 640x480 or 320x240 with a refresh rate of 60Hz. I read some of the posts to try and find out how to correct this problem, but no luck so far.

Here is what I can do so far. I can open the terminal manager and at the prompt type xdpyinfo and I can see my monitor settings under dimensions:   640x480 pixels (217x163 millimeters). At the end of this list is another prompt and I can type kwrite and it takes me to the editor and from there I am lost. The other posts talk about inserting a edit/etc/X11/xorg.conf command, but I haven't had any success in using it at any prompt or the editor.

Help please.[/QUOTE]


There is an easier way. Enter this command in a regular terminal:

> sudo dpkg-reconfigure xserver-xorg

Tell it what it wants to know and things should work....

---

### Post by frodon on 2005-07-08
You forgot [COLOR=DarkRed]sudo[/COLOR] before the command you type in terminal (sudo gedit /etc/X11/xorg.cong). Use [COLOR=DarkRed]sudo[/COLOR] before each command you want to run as root. All the configuration files are in the root space, a simple user can't modify it, that's why you need to add [COLOR=DarkRed]sudo[/COLOR] to your command when you want to modify a configuration file.

---

### Post by Dale McGarry on 2005-07-08
Didn't get it to work yet, but thanks for your help.

---

### Post by aysiu on 2005-07-08
[QUOTE=Dale McGarry]Didn't get it to work yet, but thanks for your help.[/QUOTE] Didn't get *what* to work? So you tried entering *sudo gedit /etc/X11/xorg.conf*? Then what happened? Did you get an error? Were you still unable to save?

---

