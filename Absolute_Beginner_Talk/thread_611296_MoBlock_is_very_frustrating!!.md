---
title: "MoBlock is very frustrating!!"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by 449 on 2007-11-12
I ended up having to unistall Moblock because I could not configure it properly. After I installed it I had no internet connection for Mozilla Firefox. I tried following the guide on this forum, but that didn't work. I'd really like to give it another try ,but I'm going to need a lot of help. Right now I'm running Xbuntu Gutsy Gibbon. To start me off if someone could give me the command to download and install it I'd greatly appreciated it. Thanks!

---

### Post by Maestro23 on 2007-11-12
Follow the directions for your distro under "Grab It!".

[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

---

### Post by 449 on 2007-11-12
I tried the first command under Gutsy Gibbon and it says "command not found."

---

### Post by Maestro23 on 2007-11-12
> **449 said:**
> I tried the first command under Gutsy Gibbon and it says "command not found."

Read the organge text:** "Add to your /etc/apt/sources.list".**

Those lines need to be added to your sources.list file.  Use gedit.

> gksudo gedit /etc/apt/sources.list

Add the lines, save the file and continue with the directions.

---

### Post by 449 on 2007-11-12
Ok, that worked, sorry about that I havn't been able to eat anything today because I have a colonoscopy tomorrow so it's hard to focus. Now for more questions. I tried to start moblock but it wouldn't start so I typed the command to unistall it and got some errors. Anyways when I try to open Package Manager I get an error that says: 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." 

And when I tried to run the installation deb from the moblock thread I got this:

"Only one software management tool can be run at a time" 

I tried restarting but with no luck.

---

### Post by 449 on 2007-11-12
Is there anyway to remove Moblock completely so I can try installing again?

---

### Post by Maestro23 on 2007-11-12
> **449 said:**
> Ok, that worked, sorry about that I havn't been able to eat anything today because I have a colonoscopy tomorrow so it's hard to focus. Now for more questions. I tried to start moblock but it wouldn't start so I typed the command to unistall it and got some errors. Anyways when I try to open Package Manager I get an error that says: 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." 

And when I tried to run the installation deb from the moblock thread I got this:

"Only one software management tool can be run at a time" 

I tried restarting but with no luck.

You need to close any instances of Add/Remove, Synpatic.  Try running the following command as it told you.

> sudo dpkg --configure -a

sudo apt-get update

sudo apt-get upgrade



Post your results.

---

### Post by 449 on 2007-11-12
Ok, it's able to start now; I ran the test and it failed.

---

### Post by 449 on 2007-11-12
I tried updating, reloading, ect and the test still fails.

---

