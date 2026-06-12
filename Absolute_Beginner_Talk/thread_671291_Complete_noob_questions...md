---
title: "Complete noob questions.."
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by adileader on 2008-01-18
1) I would like to know how to install through Synaptic...
2)I want to know how to get automatix 3 (i can't find a download link anywhere
3) I have Skype 2.0 beta installed on my ubuntu 7.10 gusty but I can't run my camera. All I know about it is that it's names Smart Camera :confused:
4) I have Epson Stylus D92 and it does not print thought it is recognised by ubuntu
5) I would like to change the style/skin of my start menu...I don't want that play old grey skin (don't missunderstand me I don't want to change the color but the skin!!!!!!!)
6) Thanks a lot in advance :D
7) Oh yeah and I would like to know if I can change the background of my compiz top and down cube sides. So not the four sides that I use everyday but those that are just plain images!
8) And my last question: What is the emerald theme manager and where can I download it?

---

### Post by adileader on 2008-01-18
PLease help me...please

---

### Post by adileader on 2008-01-18
Don't answer all the questions just the ones you know the answer

---

### Post by jken146 on 2008-01-18
[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by FuturePilot on 2008-01-18
> **adileader said:**
> 1) I would like to know how to install through Synaptic...
2)I want to know how to get automatix 3 (i can't find a download link anywhere
3) I have Skype 2.0 beta installed on my ubuntu 7.10 gusty but I can't run my camera. All I know about it is that it's names Smart Camera :confused:
4) I have Epson Stylus D92 and it does not print thought it is recognised by ubuntu
5) I would like to change the style/skin of my start menu...I don't want that play old grey skin (don't missunderstand me I don't want to change the color but the skin!!!!!!!)
6) Thanks a lot in advance :D
7) Oh yeah and I would like to know if I can change the background of my compiz top and down cube sides. So not the four sides that I use everyday but those that are just plain images!
8) And my last question: What is the emerald theme manager and where can I download it?

1 For using Synaptic, have a look here
[http://www.monkeyblog.org/ubuntu/installing/#package_manager]("http://www.monkeyblog.org/ubuntu/installing/#package_manager")
2 Automatix is not recommended as it has caused serious problems in the past. Not to mention everything is so easy to install now it's not really needed. You can do everything Automatix can without Automatix
5 Check out System>Preferences>Appearance for changing the theme.

---

### Post by adileader on 2008-01-18
> **FuturePilot said:**
> 1 
5 Check out System>Preferences>Appearance for changing the theme.

Well I know how to change tthe theme but I want to chage the theme of the start menu (the top menu bar)

---

### Post by FuturePilot on 2008-01-18
You can right click on the panel and go to Properties. Click the Background tab and there you can set a custom image for it.

---

### Post by sowelie on 2008-01-18
Check this out for your webcam: [https://help.ubuntu.com/community/Webcam]("https://help.ubuntu.com/community/Webcam")

And for your printer:
[http://ubuntuforums.org/showthread.php?t=491972]("http://ubuntuforums.org/showthread.php?t=491972")

For compiz settings, you need to run this command in the terminal:
```
sudo aptitude install compizconfig-settings-manager
```

Then, you can go to system -> preferences -> advanced desktop settings to change options (including cube caps).

Emerald is easy to install:
```
sudo aptitude install emerald
```

It is a window border manager that adds really nice window borders in conjunction with compiz.  There are tons of themes at [http://gnome-look.org]("http://gnome-look.org").  To install a theme just open the emerald themer at system -> preferences -> emerald theme manager, and click import and locate the .emerald file you downloaded.  To switch the theme just select it in the list.

Before emerald will work you need to restart advanced desktop effects.  Do this by going to system -> preferences -> apperance then click on the visual effects.  Click none, then click custom and you should see a nice red window title / border.

---

### Post by Keith Hedger on 2008-01-18
right click on the bar (on a blank bit) select properties and go from there

---

### Post by FreewheelinFrank on 2008-01-18
In Synaptic, go to Settings>Repositories>Ubuntu Software and tick the boxes you are happy using.

You can then use the Search function to look for software you want to install.

You can also go to Settings>Repositories>Third Party Software and add repositories to get even more software.

You may need to add a key too.

[https://help.ubuntu.com/7.10/add-applications/C/extra-repositories-adding.html](https://help.ubuntu.com/7.10/add-applications/C/extra-repositories-adding.html)

Adding a repository can also be done with a Terminal command.

Medibuntu is probably the repository you'll want to get. There are instructions for how to add the repository via a Terminal command here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

As to your printer, I have an Epson C42 and it works fine.

Go to System>Administration>Printing and make sure your printer is there and is the default printer.

Go to System>Preferences>Default Printer and make it your default printer if it isn't.

In Open Office, go to File>Printer Settings and again your printer should be the default printer.

---

### Post by adileader on 2008-01-18
> **FuturePilot said:**
> 1 For using Synaptic, have a look here
[http://www.monkeyblog.org/ubuntu/installing/#package_manager]("http://www.monkeyblog.org/ubuntu/installing/#package_manager")
2 Automatix is not recommended as it has caused serious problems in the past. Not to mention everything is so easy to install now it's not really needed. You can do everything Automatix can without Automatix
5 Check out System>Preferences>Appearance for changing the theme.

> **Keith Hedger said:**
> right click on the bar (on a blank bit) select properties and go from there

Yeah but I just need a good image not a solid color!!!

---

### Post by FuturePilot on 2008-01-18
> **adileader said:**
> Yeah but I just need a good image not a solid color!!!

You can set an image. It should be the last choice.

---

### Post by adileader on 2008-01-18
> **FuturePilot said:**
> You can set an image. It should be the last choice.

K than how can I cut something out of an image in ubuntu 7.10

---

### Post by FuturePilot on 2008-01-18
You could use the Gimp. Applications>Graphics>Gimp Image Editor.
Or you could go to [http://www.gnome-look.org/]("http://www.gnome-look.org/") and see if they have some panel images.
I found this there
[http://www.gnome-look.org/content/show.php/Gnome+Panel+Images?content=57262]("http://www.gnome-look.org/content/show.php/Gnome+Panel+Images?content=57262")

---

