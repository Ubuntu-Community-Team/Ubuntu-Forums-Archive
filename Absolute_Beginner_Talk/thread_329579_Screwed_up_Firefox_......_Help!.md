---
title: "Screwed up Firefox ...... Help!"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Skitzer on 2007-01-01
Ok, I'm kind of new to Ubuntu ..... actually Linux for that matter. I tried Ubuntu once almost a year ago, 5.10 I think, but never got serious about it and removed it. 
I installed  FC6 a few days ago but didn't like it so I thought I'd try Ubuntu again.
I Did a clean install of 6.10 Edgy Elf on a separate hard drive and am dual booting with Windows XP. 
(I've decided that now is the time to totally break free from Microsoft because I have no desire to spend several hundred dollars for an overbloated and seriously flawed OS.)

Everything went smooth and it installed without a hitch. I had to research and finally installed my nvidia drivers and set the correct resolution for my LCD (1680x1024). It was a real adventure but I made it through it. I then installed Automatix and selected the items I needed to view DVD's and play mp3's. By this afternoon everything was working perfectly with the exception of my Canon scanner but I have yet to look into that.

My problem: While I was changing fonts in Firefox it crashed suddenly. After it crashed I couldn't open it again and it gave me no error message ...... just wouldn't open. I tried rebooting but that didn't help. So I figured I would uninstall and reinstall it. I went into Synaptic Package manager, located it under World Wide Web and selected to remove it. I noticed that it had selected a few other items that had to be removed as well and I should have written them down but unfortunately I didn't.

Anyway, now I can't reinstall Firefox, it errors out saying it can't overwrite something.
I would hate to have to reinstall Ubuntu from scratch so I'm wondering if someone here could walk me through a quick reinstallation of Firefox. 
I guess if I knew what else it had uninstalled I could fix it myself. 
I have since installed Opera 9.1 and it is working fine but I would rather use Firefox. 
Any help is greatly appreciated.

---

### Post by MkfIbK7a on 2007-01-01
you could install swiftfox with automatix ([www.getautomatix.com](www.getautomatix.com)) instead of firefox (its also mozilla almost exactly the same as firefox)

---

### Post by Skitzer on 2007-01-01
Thanks, I'll check it out.

---

### Post by Hankers on 2007-01-01
You could try the instructions on this link - [http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox")

Hope this helps with your issue. :)

---

### Post by obsidion on 2007-01-01
There are a couple of things to try,
From a terminal cd .mozilla/firefox
type ls enter here to find the randomly name firefox directory and cd to it.
In linux cli, tab is your friend ie type cd thefirstbit of the directory and hit tab it will auto complete. Look for a lock or .parentlock file. Note ls -a will show hiden files.
 Also try from the terminal sudo apt-get install -f
to se if there are broken dependicies. Also note that the error codes do actually mean something in linux so finding out what it can't overwrite will help us to help you.

---

### Post by Skitzer on 2007-01-02
obsidion, I will do the sudo apt-get install -f and post the exact error I am getting.
Hankers, I tried the instructions at the link you sent me to but am getting the same error.
I am at work right now so will post later when I get home.
Thanks all and I'll keep posting until I get this fixed.

---

### Post by Skitzer on 2007-01-02
When I try to reinstall Firefox using Synaptic I get this error: 
E: /var/cache/apt/archives/firefox_2.0.0.1+0dfsg-0ubuntu0.6.10_i386.deb: trying to overwrite `/usr/lib/mozilla-firefox', which is also in package mozilla-acroread
When I try the command line sudo apt-get install -f I get this:
bob@bob-desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bob@bob-desktop:~$ 
Any ideas on how I can get Firefox reinstalled?
Thanks in advance for your help!

---

### Post by aysiu on 2007-01-02
Maybe try [this](http://www.ubuntuforums.org/showthread.php?p=271764#post271764)?

---

### Post by Skitzer on 2007-01-02
Now I am getting this:

bob@bob-desktop:~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
bob@bob-desktop:~$

---

### Post by MkfIbK7a on 2007-01-02
are you runnimg synaptic, add-remove, or another installation program at the same time?
if so dont

---

### Post by Skitzer on 2007-01-02
Ok, wert613 you were right. I had Synaptic open when I ran that command.
So I installed Swiftfox with Automatix and it installed Ok but will not run when I try to open it. The wheel spins for about 15 seconds and then goes away ...... no error messages. It is doing the exact same thing it was before I tried to uninstall/reinstall it.
Any way to fix it ....... anybody seen this before?
Thanks again for your help, it's much appreciated!

---

### Post by MkfIbK7a on 2007-01-03
yes i have seen it press ALT+F2 and type
swiftfox

---

### Post by arnieboy on 2007-01-03
> **Skitzer said:**
> Ok, wert613 you were right. I had Synaptic open when I ran that command.
So I installed Swiftfox with Automatix and it installed Ok but will not run when I try to open it. The wheel spins for about 15 seconds and then goes away ...... no error messages. It is doing the exact same thing it was before I tried to uninstall/reinstall it.
Any way to fix it ....... anybody seen this before?
Thanks again for your help, it's much appreciated!

try running the following from terminal:
```
/opt/swiftfox/swiftfox
```

---

### Post by Skitzer on 2007-01-03
wert613, I get an error as follows when trying to run swiftfox:
Could not open location 'file:///swiftfox'
The location or file could not be found.

arnieboy, I get the following when I run that command in terminal:
bob@bob-desktop:~$ /opt/swiftfox/swiftfox
Floating point exception (core dumped)
bob@bob-desktop:~$

I have absolutely no idea how to fix this issue and maybe should just bite the bullet and reinstall, although I may try Blag and see if that works better for me. 

Thanks for all your help.

---

