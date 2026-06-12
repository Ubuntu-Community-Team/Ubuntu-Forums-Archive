---
title: "need help identifying my modem"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2006-09-02
scanModem either isn't working properly on my comp, or i don't understand how it works. It's supposed to produce a text file called modemData.txt, which it doesn't. I suspect that I simply haven't gotten it to work properly, and partly that may have something to do with it not being called scanModem, but rather scanMomdemSept1. Do I have a zip utility with the package install of Ubuntu 6.06? If not with an app, what line command do i need to open scanmodem file? Thank you very much in advance.
Ricardo

---

### Post by kidders on 2006-09-02
Hi Ricardo,

All Linuxes tend to come with a few command line zip utilities pre-installed. There are many graphical tools that run on top of them, such as KDE's Ark.

Exactly what you type into a terminal depends very much on exactly what kind of archive you're dealing with.

```
unzip archive.zip
tar xf archive.tar
tar xzf archive.tar.gz
tar xjf archive.tar.bz2
etc, etc...

```

As far as your modem is concerned, I'm afraid I'm not familiar with the tool you mentioned :( however there are plenty of other ways of figuring out what modem you have. The sept1 bit makes it sound as if you downloaded a CVS build or something, which could very well be broken.

If you like, give this a try. With any luck, it'll give you enough information for whatever you need it for...

All modems respond to a basic set of commands (called the AT command set). You can try sending the "Information" (ATI) command to your modem and see what it tells you. All you need to know is the /dev entry that points to your modem. Let's say, for the sake of argument, that it's /dev/ttyS0

[LIST=1]
[*]Open two terminal windows.
[*]In the first, type: **sudo cat /dev/ttyS0** The terminal will just hang. The "sudo" is just in case your modem's permissions are too restrictive.
[*]In the second window, type: **sudo echo -e "AT\n"** to initialise the modem. Some stuff may appear in the first terminal window when you do this.
[*]Now provide the modem with an initial instruction (Second terminal): **sudo echo -e "ATE0V1\n"** The modem should respond with "OK" (First terminal)
[/LIST]

Now it's time to find out what kind of modem you have. Send the following, one by one, and watch for interesting responses:

```

sudo echo -e "ATI0\n"
sudo echo -e "ATI1\n"
sudo echo -e "ATI2\n"
...
...

```

The modem won't respond sensibly to ALL of them ... maybe up as far as ATI8 or so will be your limit. Each one will give you a fragment of info, such as the manufacturer, model number, and so on. ATI3 is often helpful. You might also give **AT+GMI** or **AT+GMM** a go.

I hope this is of some help ... even if it *is* a bit technical.

---

### Post by ricardisimo on 2006-09-02
Are you kidding? This is exactly the sort of response i was looking for! I desperately want someone to walk me through this step-by-step. I'm a total noob, so this is great. Granted, this might not work at all and I won't know until tomorrow, but thank you so much anyway. I'm off to dream happy ubuntu dreams...:grin: 
ricardo

---

