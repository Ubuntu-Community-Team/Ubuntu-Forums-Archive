---
title: "[SOLVED] Flash plugin is installed"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by boriquajake on 2007-12-17
This morning I needed to access a site that required a flash plugin, you know the little pop-down info bar showed up. Anyway I clicked on it and selected the Adobe version and went through the steps to get it installed. Everything seemed to be fine and at the end it said that I would need to restart Firefox to get the plugin to work. No problem I closed out firefox and tried again. Still said that I needed to install the plugin. This time I rebooted the computer before trying to access the site again but the same "additional plugins are required..blah blah" so I clicked to install the plugin. This time the system tells me that the flash plugin is already installed so I guess I have it installed, how do I get it to activate or otherwise start to work?

---

### Post by rickycodie on 2007-12-17
you might have to install it on ubuntu. use synaptic.

---

### Post by boriquajake on 2007-12-17
> **rickycodie said:**
> you might have to install it on ubuntu. use synaptic.

That makes sense. OK, when I open synaptic I get an odd error message. (see screenshot) I fear that error has something to do with me doing something to get sites like youtube to work. I opened terminal and did this:

```
sudo apt-get install ubuntu-restricted-extras
```

I thought that process went smooth as silk but when I continued to the next step in the instructions (I have been down this path before successfully [http://ubuntuforums.org/showthread.php?t=627806](http://ubuntuforums.org/showthread.php?t=627806)) I got an error message so I left that problem alone and went on about my business. It was an hour or so later that I needed the flash plugin and here we are.

If these are two unrelated issues I am sorry.

---

### Post by erfahren on 2007-12-17
this is a bug that was supposedly fixed.

Anyway, do this: open Synaptic Package Manager (through System > Administration) and search for "flashplugin-nonfree" and mark it for complete removal and apply.

Then see: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by lswest on 2007-12-17
i had troubles too, ended up having to install the flash plugin manually (e.g. go to [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux) and download the tar.gz, extract, run the script and remember that the path to mozilla is /usr/lib/mozilla)

---

### Post by erfahren on 2007-12-17
about the Synaptic problem (yes, they're related)

close Synaptic and in the terminal do what it says
```

sudo dpkg --configure -a

```
then see if it's fixed
```

sudo apt-get update

```

---

### Post by boriquajake on 2007-12-17
> **erfahren said:**
> about the Synaptic problem (yes, they're related)

close Synaptic and in the terminal do what it says
```

sudo dpkg --configure -a

```
then see if it's fixed
```

sudo apt-get update

```

That did appear to fix it  so of course, like the genius I am, I promptly went back to try running```
sudo apt-get install ubuntu-restricted-extras
``` again and it is again stuck. Oh well, at least now I know I can run sudo dpkg --configure -a and get it unstuck.

---

### Post by FuturePilot on 2007-12-17
> **boriquajake said:**
> That did appear to fix it  so of course, like the genius I am, I promptly went back to try running```
sudo apt-get install ubuntu-restricted-extras
``` again and it is again stuck. Oh well, at least now I know I can run sudo dpkg --configure -a and get it unstuck.

Hit Tab, then Enter

---

### Post by boriquajake on 2007-12-17
OK now, back to the flash plugin problems. I searched for the flash plugin in synaptic and checked it for reinstallation. After the thing went through its process the last word in the little progress window said:

> download done
md5sum mismatch install_flash_player_9_linux.tar.gz
The flash plugin is NOT installed.


Why would that be?

---

### Post by boriquajake on 2007-12-17
> **erfahren said:**
> this is a bug that was supposedly fixed.

Anyway, do this: open Synaptic Package Manager (through System > Administration) and search for "flashplugin-nonfree" and mark it for complete removal and apply.

Then see: [http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

Wow, I jumped right over what you said. It looks like you have fixed the problem!!

---

### Post by boriquajake on 2007-12-17
You people are freaking sweet!

---

### Post by ApOgEEs on 2007-12-18
awesome dude!! million thanks for the fix!!

---

