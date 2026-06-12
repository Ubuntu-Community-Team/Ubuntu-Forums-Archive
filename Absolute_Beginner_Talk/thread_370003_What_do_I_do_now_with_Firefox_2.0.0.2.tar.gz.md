---
title: "What do I do now with Firefox 2.0.0.2.tar.gz"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by captgadget on 2007-02-25
I downloaded Firefox 2.0.0.2.tar.gz, got it decompressed and now I don't know what to do. I've never tried to include a screen shot before so I hope it works. If not please be patient - I'm trying!! I wiped Windows of the hard drive and installed Ubuntu 6.1 from live CD and this really rocks!!! Just need a little help here and there.

---

### Post by highneko on 2007-02-25
Firefox comes pre-compiled when you got it from their website. There should be an obvious filename like "firefox-bin" or "firefox".

---

### Post by Mornedhel on 2007-02-25
OK, first it's likely you got Ubuntu 6.10, not 6.1.

Now if you just want to run Firefox, you do not need to download any sources or manually get an installer from the Internet, all you need to do is start Synaptic and install the package named 'firefox' or something like that. You might want to run a console instead and type sudo apt-get install firefox, if you want to start learning the console. Keep in mind this will not install the latest version of Firefox, only the latest it can find on the Ubuntu repositories (1.5 I believe). If you really need Firefox 2, I believe pre-compiled binaries are available for download at their website, just make sure you download the binary for the right architecture.

[Edit : hmm, Firefox 2 available for Edgy users. Gotta upgrade someday.]

---

### Post by Maestro23 on 2007-02-25
Also, are you running Dapper or Edgy?  If running Edgy, FF 2.0 in there by default. If for some reason, you don't have it:

> sudo aptitude install firefox

If running Dapper and you want FF 2.0: [https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

IF you are new to Ubuntu/Linux, never try and compile from source first. Always check your Repositories first for a program.  When installing from source, you can run into a lot of dependency problems as you can already tell.  One thing you need for installing from source is build-essential.

> sudo aptitude install build-essential

Here are some links for you to read/bookmark:

Installing in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

Good luck.

---

### Post by mk04 on 2007-02-25
From what I see from your screenshot. You already have firefox installed. On your top panel, click the icon next to "system". Firefox should open. If your running 6.06, you have FF 1.5. If your running 6.10, you have FF 2.0. To find out what version you have open FF and go to Help > About Firefox.

---

### Post by Mornedhel on 2007-02-25
True that, Firefox comes with the default install.

---

### Post by captgadget on 2007-02-25
I appreciate everyone's input, but Firefox came out with an update 2.0.02 for security purposes and that's what I'm trying to install. I'm running Edgy.

---

### Post by Bachstelze on 2007-02-25
From a terminal :

```
gksudo firefox
```

You will be prompted for your password and then Firefox will run with root privileges. *Don't* do any surfing like that ! You can then use the Automatic update checket in the Help menu. When the update is done downloading, *don't* choose to restart firefox automatically. Choose to restart it later and close it yourself. Then, run *gksudo firefox* again to install the update. when it is done, close firefox and you can use it normally again.

---

### Post by captgadget on 2007-02-25
"check for updates" is grayed out.

---

### Post by Bachstelze on 2007-02-25
When you run it normally, not when you run it with gksudo...

---

### Post by kerry_s on 2007-02-25
What i do is just grab the regular tgz(not the installer one)this-> [http://www.mozilla.com/products/download.html?product=firefox-2.0.0.2&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-2.0.0.2&os=linux&lang=en-US)
unpack it then, then open nautilus root(gksu nautilus /) and go to /usr/lib rename the firefox there to firefox.old and then copy the firefox you just unpacked there. Then test it if it works by clicking on your regular firefox icon and checking the help to make sure it's the updated. If you want you can delete the old one once you know the new one works. Oh and don't forget to copy the plugins over to the new one. You might have to install libstdc++5 for it to work, i already have it installed.

---

### Post by captgadget on 2007-02-25
Kerry, I extracted the files, but you still can't use them yet so what do I need to do now?

---

### Post by captgadget on 2007-02-25
I don't understand what I'm doing wrong but it comes back grayed out everytime.

---

### Post by captgadget on 2007-02-25
Got it going. Thanks for the help.

---

