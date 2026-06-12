---
title: "Installing Games"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by Nachoman on 2007-03-28
I've just started out on Ubuntu 6.10 and would like some help in installing games. I play unreal tournament 2004 and the steam games. I've been looking for guides but they all seem complicated and tell me to do things i have no idea how to do. Could you guys link me or give me a hand in getting these games installed please. Cheers.

---

### Post by ReverendJ1 on 2007-03-28
I believe Unreal Tournament 2004 has a native Linux installer on the CD. Your best bet would be to find that and run it. I cannot say how to do this, because I am not sure how it is set up. I don't have UT 2004 handy (I'm at work). If that doesn't work you can try and run it under wine. Do you have wine installed? It is a Windows emulator to make it so you can use some Windows programs in Linux. I think it is in the repositories. Otherwise you can add wine to the repositories like so:
First, open a terminal window. Then add the repository's key to your system's list of trusted APT keys by copy and pasting the following:

```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```

Next, add the repository to your system's list of APT sources:

```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list
```

Now you should be able to install it like any other program, either through 'Add/Remove Programs' or 'Synaptic Package Manager'.

You can then do this (I am not sure if sudo is necessary or not) to install Unreal: **Note only do this if you can't install it from the linux install for whatever reason.

```
sudo wine /path/to/unrealsetup.exe
```

Obviously, change /path/to/unrealsetup.exe to whatever the path is to the unreal setup, i.e. /media/cdrom/setup.exe

If it doesn't look right then follow the instructions on the following link (from Wine's website, [www.wineHQ.com):](www.wineHQ.com):) [http://appdb.winehq.org/appview.php?iVersionId=3733]("http://appdb.winehq.org/appview.php?iVersionId=3733")

If you  have problems with that just let me know, as I was planning on installing Unreal soon anways, so I could walk you through it. 

As for Steam, I cannot say much about that, because I have never used it myself, but if you follow these instructions for installing Wine you can pick up on this tutorial at step 4.
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam]("http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO%20Steam")

---

### Post by maddog39 on 2007-03-28
Actually the latest version of wine is availible by default in the ubuntu repositories, isnt it? You might want to try and use:
```

sudo apt-get install wine

```
before manually adding the wine repository.

---

### Post by ReverendJ1 on 2007-03-28
I thought it was, or  at least I don't remember adding it when I installed Wine. I just put that there in case it wasn't, because on Wine's download page for Ubuntu it says you need to add it.

---

