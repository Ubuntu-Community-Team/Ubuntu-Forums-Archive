---
title: "Why can I istall anything in the terminal?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by karq on 2008-01-28
When I trie to install something in the terminal.
When compiling is done, then I type make and aftert that it says:
make: *** No targets specified and no makefile found.  Stop.
and it allways says this.

---

### Post by Flyingjester on 2008-01-28
what's the program you are trying to install? and ./configure completed with no errors?

---

### Post by philinux on 2008-01-28
What you trying to install?

Have you installed build-essential from synaptic?

---

### Post by seventhc on 2008-01-28
cd to directory
```
./configure
make
sudo make install
```But not everything installs this way, open the folder and view the readme, usually it will tell you what to do. Some have both a readme file and an install file, if so...read them. :)
what are you installing?

---

### Post by karq on 2008-01-28
I tried to install this

[http://ubuntuforums.org/showthread.php?p=2093300](http://ubuntuforums.org/showthread.php?p=2093300)

---

### Post by seventhc on 2008-01-28
Are you sure you didn't miss a step?? I just installed it using the first method and it went fine. I would think either you missed a step or you could maybe be mixing option 1 with option 2???

---

### Post by PeterJS on 2008-01-28
At the the top of the thread it says that it's not being updated anymore and you should use the instructions in this thread:
[http://ubuntuforums.org/showthread.php?p=2307772](http://ubuntuforums.org/showthread.php?p=2307772)
instead which includes instructions for compiling and installing binary packages. I highly recommend the binary route for two reasons, 1) it saves you the trouble of compiling it, 1.5) saves you the trouble of working with checkinstall which I personally still haven't gotten to work with AWN 2) It gets all the package manager meta data right making it easier to uninstall/upgrade later.

---

### Post by Flyingjester on 2008-01-28
are you using option 1 or option 1? agreed, using the binary is much better.

---

### Post by philinux on 2008-01-28
This looks easier.

[http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html](http://www.ubuntugeek.com/howto-install-avant-window-navigator-awn-in-ubuntu-710-gutsy-gibbon.html)

---

### Post by karq on 2008-01-28
> **seventhc said:**
> Are you sure you didn't miss a step?? I just installed it using the first method and it went fine. I would think either you missed a step or you could maybe be mixing option 1 with option 2???

I tried the first method and it installed well :D But now I cant run it, I click the icon but nothing happens, where is the problem?

---

### Post by seventhc on 2008-01-28
> **karq said:**
> I tried the first method and it installed well :D But now I cant run it, I click the icon but nothing happens, where is the problem?
It's been a long time since I've used awn, but if I remember correctly you need desktop effects enabled (right click on desktop>change desktop background>visual effects)
You should have Avant Preferences under 'System>preferences>avant preferences
and another icon under 'Applications>Accessories>Avant window navigator

I think you need to go to the preferences first, but I can't remember exactly what I did, and I don't have effects on the machine I am on atm. So even though I have it installed I can't actually run it unless I do some things to make this comp able to have desktop effects. As i recall in the preferences it is quite simple, you will see. :)

---

### Post by karq on 2008-01-28
> **seventhc said:**
> It's been a long time since I've used awn, but if I remember correctly you need desktop effects enabled (right click on desktop>change desktop background>visual effects)
You should have Avactsnt Preferences under 'System>preferences>avant preferences
and another icon under 'Applications>Accessories>Avant window navigator

I think you need to go to the preferences first, but I can't remember exactly what I did, and I don't have effects on the machine I am on atm. So even though I have it installed I can't actually run it unless I do some things to make this comp able to have desktop effects. As i recall in the preferences it is quite simple, you will see. :)

I have desktop effeckts enabled, but when I click those avant icons, nothing happens :S

---

### Post by seventhc on 2008-01-28
I don't think I know enough about AWN, but I'm sure someone here will know more about it than I do.

---

### Post by PeterJS on 2008-01-28
What happens if you (try to) launch AWN from a terminal? It's pretty much guaranteed that if you launch something from a terminal you'll get a more verbose error message.

---

### Post by enoughsaid05 on 2008-01-28
go to the avant windows navigator and read its installation instructions. The things that you need to download is from this website:

[https://launchpad.net/awn](https://launchpad.net/awn)

The instructions will do most of the job basically.

The reason why makefile is not created is that your system needs some of the key files by downloading from the repositories (i.e. sudo apt-get install). Without the files, your awn can't be installed. 

good luck

---

### Post by karq on 2008-01-29
Everything is ok now :D Used another howto and it works now.

---

