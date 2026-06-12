---
title: "Wine's"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by CharlieDancer on 2007-09-01
How do I install wines and get games to work? I went to a site and it just made it more confusing. I'm wanting to play star wars galaxies, and I found a wine that will play it but I dont know how to install it.. I just made the switch from windows about three hours ago after getting fed up with BSOD. I'm loving the layout and all the new stuff I get to look around for. But this hole wine thing I just dont get. I go to run the .exe and it errors on me.

---

### Post by Crafty Kisses on 2007-09-01
> **CharlieDancer said:**
> How do I install wines and get games to work? I went to a site and it just made it more confusing. I'm wanting to play star wars galaxies, and I found a wine that will play it but I dont know how to install it.. I just made the switch from windows about three hours ago after getting fed up with BSOD. I'm loving the layout and all the new stuff I get to look around for. But this hole wine thing I just dont get. I go to run the .exe and it errors on me.

Wine is for emulating Windows programs mostly, not games, but I think you might be interested in the following link:
[http://www.cedega.com/]("http://www.cedega.com/")

Hope this helps. :)

---

### Post by EdThaSlayer on 2007-09-01
Open up the synaptic package manager. Then search for "wine" and then choose Wine and press Apply to allow synaptic package manager to download it from the net. Wine should work, if you have more questions about games I recommend you post in the gaming and leisure section of this forum:[http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93). :D

---

### Post by sumguy231 on 2007-09-01
Wine does not work with all Windows applications. The good news is that according to the Wine AppDB, it is possible to get it working: [http://appdb.winehq.org/appview.php?iVersionId=4504](http://appdb.winehq.org/appview.php?iVersionId=4504)

I hope you kept your Windows installation as well, as nothing at the current moment runs Windows games quite as well as Windows does. ;)

---

### Post by roblinux on 2007-09-01
Hello All,

I'm having the same problem....I put in a cd-rom with a simple 2d game on it and get an error message saying no program is available for automatic installation.

Under Mandriva 2007....after installing wine...inserting the same cd-rom.....the .exe runs and the program is installed and ready to play (Hoyle cribbage 2d)

What do I need to add ???

Thanks 

Roblinux

---

### Post by davidsrsb on 2007-09-01
What is the wine version in your Mandriva?
Wine has a new release every two weeks
The standard Ubuntu 7.04 one is getting a bit old

---

### Post by roblinux on 2007-09-01
> **davidsrsb said:**
> What is the wine version in your Mandriva?
Wine has a new release every two weeks
The standard Ubuntu 7.04 one is getting a bit old

Thanks for the reply....Mandriva is gone now so I don't know the version....

I'll see if I can successfully update wine.

Rob

---

### Post by sumguy231 on 2007-09-01
Run these commands to get the WineHQ repository, which always has the latest version of wine. I've never had problems with the packages from it.
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
```

---

### Post by roblinux on 2007-09-02
Thanks for the reply,

I ran the two commands then did an apt-get install wine but got the message that wine is already the newest version !!??

Rob

---

### Post by MenZa on 2007-09-02
Try doing *sudo aptitude update && sudo aptitude install wine*.

---

### Post by roblinux on 2007-09-02
Thanks for your reply,

I've done the update and now have wine version 0.9.44 from winehq....but.....still no luck with ,exe.

Same error appears !!??

Rob

---

### Post by MenZa on 2007-09-02
Which error is this?

---

### Post by roblinux on 2007-09-02
The error message is...

"cannot open /media/cdrom0/install.exe : No application suitable for automatic installation is available for handling this kind of file."

Rob

---

### Post by Wiebelhaus on 2007-09-02
> **Codename said:**
> Wine is for emulating Windows programs mostly, not games, but I think you might be interested in the following link:
[http://www.cedega.com/]("http://www.cedega.com/")

Hope this helps. :)

Also [Codeweavers]("http://www.codeweavers.com/")

---

### Post by roblinux on 2007-09-02
> **roblinux said:**
> Hello All,

I'm having the same problem....I put in a cd-rom with a simple 2d game on it and get an error message saying no program is available for automatic installation.

Under Mandriva 2007....after installing wine...inserting the same cd-rom.....the .exe runs and the program is installed and ready to play (Hoyle cribbage 2d)

What do I need to add ???

Thanks 

Roblinux

As previously mentioned.....the game in question works fine under Mandriva using wine as the emulator....I put in the cd and the installer runs as if I was using windows !!

There must be a way to link up wine with windows executables or what's the point of wine ??

Rob

Rob

---

### Post by Outrunner on 2007-09-02
> **roblinux said:**
> As previously mentioned.....the game in question works fine under Mandriva using wine as the emulator....I put in the cd and the installer runs as if I was using windows !!

There must be a way to link up wine with windows executables or what's the point of wine ??

Rob

Rob

```
wine /media/cdrom0/install.exe
```

---

### Post by roblinux on 2007-09-02
Thank You,

That is the correct answer.....wine is now working and installing windows programs through the command line.

Rob

---

### Post by davidsrsb on 2007-09-03
automatically associating .exe, .com etc with wine is potentially dangerous as malware could be executed

At least the command line forces you to think about what you are running

---

### Post by nbeerbower on 2007-09-03
Wine's in the Ubuntu program list you can install it from there.

---

