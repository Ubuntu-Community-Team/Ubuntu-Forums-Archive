---
title: "Wine - Installed, now what?"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by ~Beck~ on 2007-02-09
I have it installed... it doesn't show up in my program list. Unless I need to restart? Though the tutorial didn't specify that.

---

### Post by meng on 2007-02-09
No you navigate to the directory with the .exe file and type
wine (name of file).exe

---

### Post by aktiwers on 2007-02-09
did you remember to run: winecfg
in terminal?

---

### Post by ~Beck~ on 2007-02-09
Could not find 'wine'

Hmmm. :/

---

### Post by meng on 2007-02-09
How did you install wine? You talk about a tutorial but I can't be sure which one you're talking about.
Also what was the error message exactly, was it
"bash: wine: command not found"
or was it something else?

---

### Post by ~Beck~ on 2007-02-09
Yeah, it is the bash one.

> **taurus said:**
> [http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

That's the tutorial.

---

### Post by aktiwers on 2007-02-09
I always use Automatix2 to install wine..   Try it, its a lot easyer. :)

---

### Post by ~Beck~ on 2007-02-09
> **aktiwers said:**
> I always use Automatix2 to install wine..   Try it, its a lot easyer. :)

Have you got a link?

---

### Post by meng on 2007-02-09
Well it's probably not installed.
What response did you get to
sudo aptitude install wine

?
If you can't remember, try it again.

---

### Post by ~Beck~ on 2007-02-09
It's doing the norm, downloading and installing, etc.

---

### Post by aktiwers on 2007-02-09
[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by meng on 2007-02-09
> **~Beck~ said:**
> It's doing the norm, downloading and installing, etc.
It doesn't download and install unless it wasn't installed properly the first time around. Therefore we can deduce that it wasn't installed properly first time around. Try running wine again after the installation.

---

### Post by ~Beck~ on 2007-02-09
> The following NEW packages will be installed:
  wine
0 packages upgraded, 1 newly installed, 0 to remove and 120 not upgraded.
Need to get 8785kB of archives. After unpacking 41.4MB will be used.
Writing extended state information... Done
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe wine 0.9.9-0ubuntu2 [8785kB]
Fetched 8785kB in 5m41s (25.8kB/s)
Selecting previously deselected package wine.
(Reading database ... 81309 files and directories currently installed.)
Unpacking wine (from .../wine_0.9.9-0ubuntu2_i386.deb) ...
Setting up wine (0.9.9-0ubuntu2) ...



That's all it did... got the input back.

EDIT: Got winecfg up now.

EDIT: EDIT: It's not opening any programs now.

---

### Post by ~Beck~ on 2007-02-09
Bump.

---

### Post by meng on 2007-02-09
bump, bump, little bit impatient are we? :D
What do you mean it's not opening any programs?
What programs are you trying to open? What commands are you giving?
We've already wasted a fair bit of time because of assumptions made due to you not giving detailed information, so if you're in a hurry to get a solution, do yourself and favor and supply some details!!

---

### Post by ~Beck~ on 2007-02-09
> **meng said:**
> bump, bump, little bit impatient are we? :D
What do you mean it's not opening any programs?
What programs are you trying to open? What commands are you giving?
We've already wasted a fair bit of time because of assumptions made due to you not giving detailed information, so if you're in a hurry to get a solution, do yourself and favor and supply some details!!

Yes, very.
It just hangs there... loads for a few moments then seems to give up.
I'm testing it out with things like Firefox and I'm using the command "wine firefox.exe"

---

### Post by meng on 2007-02-09
Okay, slightly weird. Two questions:
1. You are aware that running firefox through wine is, well, silly, right? I assume you're just doing it for the sake of testing wine, not because you actually want to run firefox in wine.
2. Did you INSTALL firefox in wine first or are you trying to run it off a Windows partition? You can't do that latter.

While it's natural to want your problem solved quickly, bumping the thread after such a short time is going to be interpreted as being a breach of basic forum etiquette, and I suspect is more likely to cause others to IGNORE the thread than to help you out. I'm sorry I didn't answer more quickly, but I had other commitments ... like bathing my son and putting him to bed.

---

### Post by ~Beck~ on 2007-02-09
> **meng said:**
> Okay, slightly weird. Two questions:
1. You are aware that running firefox through wine is, well, silly, right? I assume you're just doing it for the sake of testing wine, not because you actually want to run firefox in wine.
2. Did you INSTALL firefox in wine first or are you trying to run it off a Windows partition? You can't do that latter.

While it's natural to want your problem solved quickly, bumping the thread after such a short time is going to be interpreted as being a breach of basic forum etiquette, and I suspect is more likely to cause others to IGNORE the thread than to help you out. I'm sorry I didn't answer more quickly, but I had other commitments ... like bathing my son and putting him to bed.

1. Yeah, I know. :P Hence the reason Firefox is built into Ubuntu.
2. AH. That's the problem. I see, thankyou, I'll try installing something.

Sorry about that. It's 1:40PM in Australia and I forget about timezones sometimes.

---

### Post by aktiwers on 2007-02-09
If I double-clik a exe, wine automaticly opens it..  this is not the case for you?

---

### Post by ~Beck~ on 2007-02-09
> **aktiwers said:**
> If I double-clik a exe, wine automaticly opens it..  this is not the case for you?

I need to install it for it to work with WINE. :P

---

### Post by ~Beck~ on 2007-02-09
Alright, turns out that maybe it won't work even with installers. :/ Any suggestions?

---

### Post by meng on 2007-02-09
Hmmm. What program? Not all Windows programs work with wine.

---

### Post by ~Beck~ on 2007-02-09
I'll try Filezilla to see if that'll work.

---

### Post by shareMenaPeace on 2007-02-09
>ou can install Filezilla with

System -> Administartion -> Synaptic Package Manger and search for it and install.

---

### Post by ~Beck~ on 2007-02-09
It doesn't matter *WHAT* it is. Oh well, don't worry about it.

---

### Post by Repent on 2007-02-10
So what do you do when you get this?

joe203@joe203-desktop:~$ winecfg
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

---

### Post by dustman on 2007-02-10
Hello, can anyone tell me please how can I uninstall a program that I have installed with wine :confused: 

THanks!

---

### Post by MrKlean on 2007-02-10
Go to "places,home folder,View, show hidden files.. then you should find it..it's a hidden file...

---

