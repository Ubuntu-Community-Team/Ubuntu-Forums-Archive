---
title: "Whining about Wine"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by arielette on 2007-07-16
[SIZE="2"][FONT="Arial Narrow"][SIZE="3"]Hi there:

I keep trying to install wine through the command line and get this every time:
[COLOR="DarkRed"]
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.[/COLOR]

What am I missing here?  :-({|=

Thanks![/SIZE][/FONT][/SIZE]

---

### Post by Al3xK3aton on 2007-07-16
I'm not sure you're missing anything. It looks like you posted the whole thing.

---

### Post by arielette on 2007-07-16
[FONT="Arial Narrow"][SIZE="3"]
Meaning what am I doing wrong?  :confused:

[/SIZE][/FONT]

---

### Post by agurk on 2007-07-16
You say you're "trying to install wine through the command line", could you explain that a bit? The errors you list are not related to installation, but to running wine itself.
Also we need more info, what distro are you running, what version of wine (type 'wine --version' in a terminal)?

---

### Post by arielette on 2007-07-16
[FONT="Arial Narrow"][SIZE="3"]Sorry I will try to be more clear:

I am running Ubuntu 7.04.  After I installed wine (wine-0.9.40) and I tried to configure it using the winecfg (wine configuration utility) I got the above posted output.  Thanks for your help.
[/SIZE][/FONT]

---

### Post by stchman on 2007-07-16
> **arielette said:**
> [SIZE="2"][FONT="Arial Narrow"][SIZE="3"]Hi there:

I keep trying to install wine through the command line and get this every time:
[COLOR="DarkRed"]
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.[/COLOR]

What am I missing here?  :-({|=

Thanks![/SIZE][/FONT][/SIZE]

Here is how to install WINE:

From a terminal, type the following.  I will assume you are running Feisty.

```

wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list
sudo apt-get update
sudo apt-get -y install wine

```

WINE will then be installed.

---

### Post by agurk on 2007-07-16
Right, if you have compiled wine yourself, please try the install method described by stchman above instead.

---

### Post by Sweet Spot on 2007-07-16
Fixed.

---

### Post by fatsheep on 2007-07-16
You do not need a Windows partition to install Wine but you will need a different installation method if you are using 64-bit Ubuntu.  Here is Kilz's topic on installing Wine to 64-bit Ubuntu:

[http://www.ubuntuforums.org/showthread.php?t=185557](http://www.ubuntuforums.org/showthread.php?t=185557)

---

### Post by Majorix on 2007-07-16
Why do you have to post exact same thing on two threads, and without even checking if you have the answer in the first thread?

---

### Post by Sweet Spot on 2007-07-16
Nevermind.

---

### Post by Sweet Spot on 2007-07-16
Before I go out, I need to ask:  What do you guys who use WINE usually use for the sound drivers, oss, or alsa ? I'm going to leave it open till I get home, since I remember it crashing the last time I chose a sound driver on my other install. 

Thanks. 

Doug

---

### Post by cookies on 2007-07-16
Depends on what sound drivers you are using. Ubuntu by default uses ALSA.

---

### Post by arielette on 2007-07-16
[FONT="Arial Narrow"][SIZE="2"][COLOR="Indigo"]Thanks for the input everyone....I am still working on the problem...think I will sleep on it..](*,).[/COLOR][/SIZE][/FONT]

---

### Post by Sweet Spot on 2007-07-16
> **cookies said:**
> Depends on what sound drivers you are using. Ubuntu by default uses ALSA.

Gotcha, thanks. Oss was ticked by default, but have unticked it and switched to the Alsa drivers. Also, (and I've always been confused about this) which Windows version should I use from the drop down list,  Win 2000; ME; 98; 95 or NT 4.0 ?   

Thanks again, 

Doug

---

