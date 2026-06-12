---
title: "Installing new programs under Ubuntu/GNOME"
date: 2005-12-19
forum: Absolute Beginner Talk
---

### Post by OldMac on 2005-12-19
Hi everyone,

Stupid questions but I'm very new to linux and am a little lost.

I'm running Ubuntu 5.10 on an iMac G3 400Mhz.

1. When I install a software package, _where_ does it go? If it's not handled properly by the installation process, for example, and nothing appears in the application menu(s), how do I find where it is? (i.e. where do most applications live on a linux system?)

2. How do I uninstall something when the add/remove program utility does not list it as an installed package?

3. Specific problem:  I'd like to upgrade Firefox from v1.0.7 which came with Ubuntu, to v1.5. Using the Synaptic package manager it shows only v1.0.7. Version 1.5 is evidently available, and I have downloaded the archive.... it's extracted and sitting on my desktop. How do I upgrade 1.0.7 to 1.5?

Thanks...

---

### Post by 23meg on 2005-12-19
1) To see where all files of an app are installed, right click its package in Synaptic, hit "Properties" and check out the installed files tab. To run an app that you've installed if it's not in the menus (assuming the executable name is the same as the package name; it usually is), hit Alt+F2 and type its name. To add it to the menu, hit Applications / System Tools / Applications Menu Editor. To create a launcher to it on your desktop, right click the desktop, hit "Create launcher" and enter its name in the "Command" field.

2) With Synaptic (right click package, hit "Mark for removal", hit "Apply") or "sudo apt-get remove package_name".

3) [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

For more information on installing software, check this out: [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php)

---

### Post by OldMac on 2005-12-19
Followed the instructions given to install Firefox 1.5 precisely.

Now I can't run Firefox at all.

Says it's unable to execute /opt/firefox/firefox-bin

Is it too much to ask that software comes with either its own installation executable or script (or comes in a form that Synaptic can (a) find and (b) successfully install)? Or at least a readme file that says "Put this here..."?

Failing to be won over by linux here...

---

### Post by 23meg on 2005-12-19
> Is it too much to ask that software comes with either its own installation executable or script (or comes in a form that Synaptic can (a) find and (b) successfully install)? Or at least a readme file that says "Put this here..."?The instructions I pointed to you contain everything you should do to install 1.5 while preserving your existing Firefox installation **in Ubuntu**; there is most likely a readme file that tells you what to do in the Firefox 1.5 package you downloaded, but if you were to obey that, you'd lose the ability to roll back smoothly to 1.07 and miss some integration features. The tar.gz file you download contains a generic Linux version and the instructions in it are generic instructions not meant for Ubuntu.

In other terms, Firefox 1.5 isn't officially available for Ubuntu at the moment; what I've pointed to you is a workaround that lets you install it without overwriting 1.07 **in Ubuntu**. It's [in the process of being backported ]("http://www.ubuntuforums.org/showthread.php?t=96595") though, so you'll be able to install it via Synaptic as well in the near future.

Try running Firefox from terminal and see what error messages you get.

---

### Post by 23meg on 2005-12-19
Also try doing ```
sudo chmod +x /opt/firefox/firefox-bin 
```

---

### Post by Rackerz on 2005-12-19
I don't usually run firefox 1.5 from firefox-bin. I usually run it from just 'firefox' is that something which i shouldn't do?

---

### Post by 23meg on 2005-12-19
Doesn't matter; once you follow the instructions in the wiki typing "firefox" executes firefox-bin from /opt/firefox anyway.

---

