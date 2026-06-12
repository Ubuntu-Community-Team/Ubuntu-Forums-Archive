---
title: "[SOLVED] Limewire?"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-02-07
Okay, so I went to the official limewire site and downloaded the linux version, It's on my desktop I open it, click install package, but it makes me put my password in to make sure the download is okay to download, then it closes that window, and re-opens it and when I click install package it says. 
**Only one software management tool is allowed to run at the same time**
Please close the other application e.g. 'update manager', 'aptitude' or 'synaptic' first.

There IS nothing else opened but yet it says that. Can somebody either help me with this problem or provide a working limewire download?

---

### Post by Steveway on 2008-02-07
Why not install frostwire instead?
It's Limewirepro, free and legal.
sudo apt-get install frostwire
should install it, I think it's in Multiverse or Universe.

---

### Post by FuturePilot on 2008-02-07
...

---

### Post by ubuntu27 on 2008-02-07
It's on my desktop I open it, click install package, but it makes me put my password in to make sure the download is okay to download, **then it closes that window, and re-opens it** and when I click install package it says.

Are you sure it is not open? Close all windows, and try to click the LimeWireLinux.deb again. 
Double CLick on the deb icon, click on install, type your SuperUser password (OR your password), and then close when finished.


A tip for youi. I recommend you to use [frostwire]("http://www.frostwire.com/") instead of Limewire. FrostWire is  Free, doesn't have advertisement, it has the same functionality as LimeWire, and it is faster.

Frostwire

[http://www.frostwire.com/](http://www.frostwire.com/)

---

### Post by blasteryui on 2008-02-07
> **ubuntu27 said:**
> It's on my desktop I open it, click install package, but it makes me put my password in to make sure the download is okay to download, **then it closes that window, and re-opens it** and when I click install package it says.

Are you sure it is not open? Close all windows, and try to click the LimeWireLinux.deb again. 
Double CLick on the deb icon, click on install, type your SuperUser password (OR your password), and then close when finished.


A tip for youi. I recommend you to use [frostwire]("http://www.frostwire.com/") instead of Limewire. FrostWire is  Free, doesn't have advertisement, it has the same functionality as LimeWire, and it is faster.

Frostwire

[http://www.frostwire.com/](http://www.frostwire.com/)

I Tried frostwire same thing happens, and the windows are closed I even have a dock so it show the windows there also, so I tried the sudo terminal way and got this msg.

dexter@dexter-desktop:~$ sudo apt-get install frostwire
[sudo] password for dexter:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
dexter@dexter-desktop:~$

---

### Post by FuturePilot on 2008-02-07
While Frostwire isn't in the repos, you still have a problem which is why I think you are getting errors.
Run the command it tells you
```
sudo dpkg --configure -a
```

---

### Post by MariusSilverwolf on 2008-02-07
Not to sound like the paranoid type, but is there any particular reason you're tying to use an antiquated file sharing system when you can make use of torrents and grab the data you want faster?

The RIAA scours places like LimeWire and catalogues IP addresses.  It's becoming a dangerous system to use.

I do believe that ends my 2 cents worth.

---

### Post by FuturePilot on 2008-02-07
What makes you think they don't do the same for torrents?

---

### Post by blasteryui on 2008-02-07
> **FuturePilot said:**
> While Frostwire isn't in the repos, you still have a problem which is why I think you are getting errors.
Run the command it tells you
```
sudo dpkg --configure -a
```

Alright I got it to work, thanks!

---

### Post by MariusSilverwolf on 2008-02-07
> **FuturePilot said:**
> What makes you think they don't do the same for torrents?

I've no doubt they do, but there's not the same community aspect to pulling down torrents like there is to programs like LimeWire.

Without sharing anything, I can hop onto LimeWire, do a search for names, and start collecting IP addresses.  To gather data with torrents I have to be actively involved in the transfer.

And, because of the collective nature of gathering the data through torrents, I spend less time downloading the files in question, which lowers the risk of discovery.  A DVD quality movie can take 6 - 8 hours to download through LimeWire, but take less than 30 minutes for a widely distributed torrent.  It's more efficient.

---

### Post by NJC on 2008-02-07
> **MariusSilverwolf said:**
> The RIAA scours places like LimeWire and catalogues IP addresses.
 
Hmm, so they do:> 
A New York judge is being asked to decide whether a company that gathers evidence on behalf of the [_[COLOR=#0000ff]Recording Industry Association of America (RIAA)[/COLOR]_]("http://www.pcworld.com/tags/Recording+Industry+Association+of+America.html") in illegal file-sharing cases should be required to have a private investigator's license in order to do so.
The issue, which has come up in the past, is being raised again in a case involving Rolando Amurao, who has been charged by Lava Records LLC and other music recording labels with illegally distributing 528 copyrighted music files** over the Limewire peer-to-peer (P2P) file-sharing network**. The case is being heard in the U.S. District Court for the Southern District of New York.

 
[http://www.pcworld.com/article/id,142209-c,copyright/article.html](http://www.pcworld.com/article/id,142209-c,copyright/article.html)

---

