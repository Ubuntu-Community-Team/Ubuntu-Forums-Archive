---
title: "Update Manager and dialup"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Hitchhiker42 on 2007-01-23
Hello! I'm really new to Ubuntu, and I need help with the Update Manager. I'm on dialup, and the connection keeps timing out whenever I try to download updates, especially the larger ones, bigger than about a MB or so. I had a couple of different ideas about how to take care of this (besides getting a high speed connection, which isn't feasible at the moment), unfourtuntely, I have no idea how to implement any of them. My first idea was to set the timeout on the Update Manager to something higher. My second idea was to download the packages from a highspeed connection (on a XP machine, most likely) onto my flash drive and bring them back to my computer. Is this possible? If so, how would I go about doing it? Are there any other possible solutions to my problem?

One unrelated question. This isn't my only question about how do things in Ubuntu. Is it better etiquette around here to make seperate posts for each subject, or stick all my questions in one message?

Thanks for all your help!

---

### Post by Ecthelion on 2007-01-23
> My second idea was to download the packages from a highspeed connection (on a XP machine, most likely) onto my flash drive and bring them back to my computer. Is this possible? If so, how would I go about doing it? Are there any other possible solutions to my problem?

You can do that of course. The only thing that you'll have to look twice for is if you have all the dependencies each time. Otherwise your going to run a lot around with your flashstick.

Just downloaded the .deb packages you need, put them on your flash, then put your flash in your computer.
To install, do
```
sudo dpkg -i _*/path_to_the_.deb*_
```
That should do. :-)

If you don't like commandline you can also double-click on a .deb package and an installer will pop-up :-P Maybe that's even easier :lolflag:

---

### Post by zgornel on 2007-01-23
I'd be great if you found a highspeed Ubuntu machine running the same version as yours.

---

### Post by Ecthelion on 2007-01-23
> **zgornel said:**
> I'd be great if you found a highspeed Ubuntu machine running the same version as yours.

Yes but it's hard to have all the same packages installed everywhere...
One update and the two machines wouldn't be synchronised anymore.

What you could try to have all the correct dependencies each time:
Select the programs you want to install in Synaptic, and let it select the dependencies.
Then, instead of make him start download, do
File > make script to download on other system
And normally you should get a script that can download all the dependencies etc for you.
I haven't tried it myself since I have broadband, but if the option is there it should work shouldn't it :-)

---

### Post by Hitchhiker42 on 2007-01-24
Thank y'all so much for your help! I probably would have spent several hours trying to get the URLs for about 75 packages if you hadn't mentioned the script. I haven't downloaded them yet, but I'll probably have them tomorrow. Again, thanks so much for all your help.

<b>ETA:</b> Step by step instructions for downloading packages on a Windows machine.
1) Go into Synaptic and mark all the packages you want to install
2) File -> Generate Script for Download
3) Exit Synaptic
4) Open the script in Notepad on Windows machine
5) Copy URLs and download files
6) Create a folder on your Ubuntu machine copy all the package files to it
7) Open Synaptic and File -> Install Downloaded Packages (not sure of the exact name, as I'm in Windows at the moment... It's the option under the script one from earlier)
8) Select the folder your packages are in and install
9) Huzzah!

---

