---
title: "How do I intall something without synaptic?"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by Amablue on 2006-06-02
I have a game I downloaded, but I don't know how to go about using it since I'm only familiar with Synaptic so far. 

Also, how would I go about installing the latest version of FireFox? I'm using the one that came with my Ubuntu (1.0.8 ) but I'd rather have 1.5 or whatever the current one is. 

:-k

---

### Post by BobSongs on 2006-06-02
Install Automatix to get Firefox 1.5.0.3 going.

We'll need a bit more information on the downloaded game. Is it an .exe file? Is it a .tar.gz file? A .deb file?

---

### Post by Iowan on 2006-06-02
There's also **apt-get** and **aptitude**.

---

### Post by Amablue on 2006-06-02
[QUOTE=BobSongs]Install Automatix to get Firefox 1.5.0.3 going.

We'll need a bit more information on the downloaded game. Is it an .exe file? Is it a .tar.gz file? A .deb file?[/QUOTE]

I did a search for Automatix in Synaptic and didn't find it there. Where should I be looking?

The game is a .tar.gz file.

---

### Post by linuxa on 2006-06-02
You should be able to double click on tar.gz and have Ark (archiver) start automatically.

If not. Open Konsole, navigate to the directory where the file is, type the following:

**tar -xvf <filename>**

where <filename> is the complete file name, including extension of the game file.

For firefox. If you don't want to go the Automatix path. You can just download the latest firefox from getfirefox.com

Be aware that the downloaded file will be compressed by default. So you'll need to means to uncompress it (e.g. Ark or some other means of uncompressing the file).

There's a firefox script in the uncompressed folder that you execute to start firefox (effective type **firefox** within the uncompressed folder will get you going).

Regards
Linuxa

---

### Post by AndyCooll on 2006-06-02
[QUOTE=Amablue]I did a search for Automatix in Synaptic and didn't find it there. Where should I be looking?

The game is a .tar.gz file.[/QUOTE]

Automatix isn't in Synaptic, it's available through these forums. Easiest way is just to click on the link in my signature.

:cool:

---

### Post by Amablue on 2006-06-02
Gah, Automatix seems to have killed my Firefox. When I click on it now, it just says "Starting FireFox Web Browser" but then never starts. 

I'm also getting this notice: > Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

---

### Post by tehnad on 2006-06-02
Try doing what the message is telling you.  I have found that the debug messages included in Ubuntu are pretty smart.  Open up a command terminal and type this: "sudo apt-get install -f firefox" and see what that accomplishes.  It should at least get your old browser version back running.  For safety reasons you could even do it this way "sudo apt-get install -f --just-print firefox" and let the portage tell you how it is going to fix things without actually making the changes.  If typing just firefox by itself doesn't work then try this:"sudo apt-get install -f --just-print mozilla-firefox" The reason for the "-f " when using the apt-get is to fix broken dependencies.

---

### Post by BobSongs on 2006-06-02
[QUOTE=Iowan]There's also **apt-get** and **aptitude**.[/QUOTE]Uhm. Read this again:[QUOTE=Amablue]I have a game I downloaded[/quote] It's best to read the post before answering. The file was already downloaded. He's looking for help on how to set it up, not just a general question as to how to install things in Linux.

**Amablue**: When running Automatix it's important to read the dialog boxes. We receive this huge warning to shut down all running instances of Firefox before clicking OK. Otherwise terrible things happen.

In Windows we tend to "click OK to make the dialog box go away". But that's a bit more dangerous in Linux.

As far as your game.tar.gz is concerned, that's a bit more involved. First open a folder and then make your way to the location where you downloaded the game. Then double-click the file. The archive manager that comes pre-loaded with Linux should run and show you the contents of your compressed file. There should be an "Extract" button. Click it and select a location where you'd like your game folder saved. Once it's put where you want it to be make your way to that folder then look for an INSTALL or README file. From there... follow the instructions. Need help? Post a new thread and we'll bail you out. Cool?

---

### Post by tehnad on 2006-06-02
My fault.  I thought from reading the postings that he was talking about firefox no longer working after installing Automatix and that he was being told that he needed to run apt-get install -f to fix the problem.  By that I thought that he was asking what he should do.  I will try better next time.

---

### Post by BobSongs on 2006-06-02
[QUOTE=tehnad]My fault.  I thought from reading the postings that he was talking about firefox no longer working after installing Automatix and that he was being told that he needed to run apt-get install -f to fix the problem.  By that I thought that he was asking what he should do.  I will try better next time.[/QUOTE]lol
Did you do something wrong? Look: erroneous advice is far better than inattentive advice or crumbs tossed at a new user.

These forums were very helpful to me when I started. And I'm happy to help out whenever I can. So when I see someone tossing careless answers at a new user it bothers me because it hurts the reputation of this forum.

I made the same mistake: I should have put a link directly to Automatix when I made my post. I made the assumption Amablue knew his/her way around. See? My bad.

We'll keep working it out! :)

---

### Post by aysiu on 2006-06-02
The least intrusive and easiest way to install Firefox 1.5.0.4 is using [this script](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5).

Otherwise, read this: [http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing) or [this thread](http://www.ubuntuforums.org/showthread.php?t=185643).

---

### Post by catlett on 2006-06-02
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Edit: didn't see the previous post

---

