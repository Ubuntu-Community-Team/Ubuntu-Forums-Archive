---
title: "Adobe Flash Player"
date: 2006-11-08
forum: Absolute Beginner Talk
---

### Post by hotrodpunk on 2006-11-08
Trying to install Adobe Flash Player Plugin For Mozilla Firefox in the terminal and i get the following error message :( 

ERROR: Your architecture, \'x86_64\', is not supported by the
       Macromedia Flash Player installer.

what does it mean can i get around it?

thanks in advance all

---

### Post by taurus on 2006-11-08
It means that flash is for x86 but not x86_64!  So, you can install the 32bit firefox and install flash for that if you want to run flash with firefox...

---

### Post by linkri on 2007-10-06
In Ubuntu/Gutsy I installed the plugin directly from the repositories using apt-get and it works :)

sudo apt-get install flashplugin-nonfree

---

### Post by marco123 on 2007-10-06
Simply download this script: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)  and run it.:)

---

### Post by sumesh.pt on 2007-10-10
> **linkri said:**
> In Ubuntu/Gutsy I installed the plugin directly from the repositories using apt-get and it works :)

sudo apt-get install flashplugin-nonfree

can u explain what you did? I am facing the same issue.

---

### Post by Perfect Storm on 2007-10-10
It's because it will be available in Gutsy for 64bit. Gutsy will be released in 8 days.

---

### Post by jdfreshwater on 2007-10-11
The best way to use flash on a 64 bit system would be to use nspluginwrapper  This allows you to install 32 bit flash on 64 bit firefox.  It also allows you to view flash in a browser like konqueror.  I have yet to try the gusty stuff yet, I just installed it.

---

### Post by F W Adams on 2007-10-29
Linkri wrote:
In Ubuntu/Gutsy I installed the plugin directly from the repositories using apt-get and it works

sudo apt-get install flashplugin-nonfree
__________________

As a novice I did:
System / Administration / Synaptic Package manager

then search for "flashplugin-nonfree" in the top right list, tick and apply it and it should work with nothing further to do.

---

### Post by hayvanAdam on 2008-01-29
> **linkri said:**
> In Ubuntu/Gutsy I installed the plugin directly from the repositories using apt-get and it works :)

sudo apt-get install flashplugin-nonfree



```

apt-get install flashplugin-nonfree
.
.
.
Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

```

my release 7.10 gutsy :mad:

---

### Post by wolfen69 on 2008-01-29
here's the flash fix for firefox:

if you installed flash-plugin or gnash, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu3_i386.deb)  then just click and install.

---

### Post by Perfect Storm on 2008-01-29
Here's a good thread about it: [http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

