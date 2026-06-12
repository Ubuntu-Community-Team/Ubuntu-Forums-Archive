---
title: "[SOLVED] Launchers not working??"
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by jagannath on 2007-10-23
I recently upgraded to Gutsy from Feisty and I find that launchers I create are not launching the respective programs !! For example, I created a launcher for Wget and just could not get it to run; the same with Efax.

Any ideas anybody,

Many thanks in advance,

--
J

---

### Post by petersjm on 2007-10-23
Did you dist-upgrade or reinstall from downloaded ISO? Apps that you downloaded aren't generally kept if you reinstall over the same partition your apps were originally on, unless they come bundled with the OS. If you CTRL+F2 and type wget, then see if it loads. If it says "cannot find wget" it means you no longer have the app and need to reinstall.

[edit] Sorry, I just realised you said launchers you "create" (ie in Gutsy, right?) and not "created" (ie originally in Feisty). Is that right?

---

### Post by jagannath on 2007-10-23
That's right I created them just now. 
And the upgrade, I did a dist.upgrade.

Synaptic shows Wget and Efax as installed.

Ctrl + F2 doesn't work either!!:confused:

--
J

---

### Post by realvz on 2007-10-23
can you reinstall them from synaptics?

---

### Post by jagannath on 2007-10-23
Well, I tried the re-install too. 
Even with CRTRL+F2 I am drawing a blank!!:confused:

--

J

---

### Post by petersjm on 2007-10-23
What does it say when you CTRL+F2 them? Or better yet, open terminal and type the app name and hit <enter> and see what error it gives. Let us know the output.

---

### Post by jagannath on 2007-10-23
> **petersjm said:**
> What does it say when you CTRL+F2 them? Or better yet, open terminal and type the app name and hit <enter> and see what error it gives. Let us know the output.

CTRL=F2 does not give any output.

This is what my terminal says:

jagannath@jagannath-desktop:/$ wget
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.

--
J

---

### Post by petersjm on 2007-10-23
> **jagannath said:**
> This is what my terminal says:

jagannath@jagannath-desktop:/$ wget
wget: missing URL
Usage: wget [OPTION]... [URL]...

Try `wget --help' for more options.

A-ha! Now I see. Wget does not have a GUI. It's a command line tool for transferring files over HTTP and/or FTP. If you type wget --help in a terminal it will tell you the options you can use.

I've done a search on eFax, too. It also doesn't have a GUI (ie it's a command line tool), but you *can* download a GUI to use with it. See here: [eFax GTK](http://linux.softpedia.com/get/Communications/Fax/Efax-gtk-3705.shtml)

---

### Post by jagannath on 2007-10-23
Many thanks petersjm.
And for thanks for the  efax GUI link too.
I guess wget does not have a GUI. If that is indeed the case, is there any other download manager for Ubuntu with a GUI??

--
J

---

### Post by petersjm on 2007-10-23
> **jagannath said:**
> Many thanks petersjm.
And for thanks for the  efax GUI link too.
I guess wget does not have a GUI. If that is indeed the case, is there any other download manager for Ubuntu with a GUI??

You're welcome. It depends what you want to transfer/download. If you're looking for an FTP client, the most basic of ones is Nautilus or Konqueror (depending on your distro - ie Ubuntu or Kubuntu). I'm assuming Dolphin file manager does this too. Are you looking for FTP transfer, or some other file transfer tool?

---

### Post by jagannath on 2007-10-24
Actually I am looking for a download manager which would integrate itself with the Firefox browser, something which would open up and start the download when I click on a download link; something with more features than the built-in downloader in Firefox.

--
J

---

### Post by petersjm on 2007-10-24
I see. Okay, you can use a Firefox add-on called Flashgot, but you need a download manager, too. Flashgot picks up the manager and opens it on download. Their website lists available managers you can use in conjunction with it (Win, Linux, Mac). [Try it out here](http://flashgot.net/). Good luck!

---

### Post by jagannath on 2007-10-24
Thanks Pete. I'm on the job now. 
In fact as expected I am in trouble again. And another post !!:(

By the way, any idea why my "CTRL+F2" does not respond at all !!
--
J

---

