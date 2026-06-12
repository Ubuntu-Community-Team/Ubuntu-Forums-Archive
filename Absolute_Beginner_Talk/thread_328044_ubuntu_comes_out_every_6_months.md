---
title: "ubuntu comes out every 6 months ?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by Sasa_Ivanovic on 2006-12-30
I know that it comes out every 6 months. But starting from when ?
Is a new version coming out after new year, Or is there a particular date ?

---

### Post by Solver on 2006-12-30
The last version was released in late October, so the next version should be expected in April.

You can use Ubuntu versions to tell when they've been released. The current version is 6.10, which means it was released in the 10th month of 2006. Assuming the next version gets released okay in April, it would be numbered 7.04, and so on.

---

### Post by rbhigday on 2006-12-30
will we have to manual update to the new version or is there a way to have our current version automatically updated?

---

### Post by Sasa_Ivanovic on 2006-12-30
Well i gues we have to delete it, and install again, or am i wrong ?

---

### Post by anaconda on 2006-12-30
> **Sasa_Ivanovic said:**
> Well i gues we have to delete it, and install again, or am i wrong ?

That is what I do, but you can also use apt-get to dist-upgrade to the new version.

---

### Post by Sef on 2006-12-30
> Well i gues we have to delete it, and install again, or am i wrong ?

You can update it through the directions that are provided.   However, a clean install is best, i.e. installing via a cd.

---

### Post by insane_alien on 2006-12-30
clean installs tend to have less problems but i've not yet had a problem with dist-upgrading

---

### Post by rbhigday on 2006-12-30
Thus for each upgrade we must backup all files and then everything is wiped and then replace back all our data files. Am I correct in this? 

If I am I better figure out how to make a second hard drive fit in my laptop :)

---

### Post by macogw on 2006-12-30
> **anaconda said:**
> That is what I do, but you can also use apt-get to dist-upgrade to the new version.

That doesn't work well.  Not all dependencies are fixed, so a lot of it breaks.  You type in the terminal
sudo "update-manager -c"
which brings up your regular update manager with a button that says there's a new version available.  If you click that, it'll upgrade flawlessly.


Sef, using the GUI updater, it works perfectly.  Dist-upgrade was the problem last round, according to a Kubuntu dev I was talking to last month.  I took her advice (see above) on the last one I updated, and she's right.  There are things the command line doesn't know to update, that the gui was set up to do.

---

### Post by Papa-san on 2006-12-30
Another very good choice is to go with whatever version is the LTS and stick with it... LOL
I have found that 6.06 is working well, and have no real reason to upgrade it. For the most part, there is very little functionality added with the new versions that can't be added to an old one through the repo's

---

### Post by autocrosser on 2006-12-30
I run two installs---One stable branch & one testing branch on two drives--so if the testing one "blows" up, I can just reboot into my stable OS & pull the mail,etc I need to keep working.. 

Thats how I see what the newest-greatest is without the pain of a massive update--when the new OS is stable, I take a "snapshot" by backing up the install with .tar (look thru the forums for system backups) & write it on my stable drive--and go thru the whole thing all over again;) (of course, I reccomend you do a system backup before EVERY time you do a major change to your system--this has saved me so many times--I just cd to my "dead" install & reinstall--takes about 20 minutes or so & I'm back up running)

Of course--you "need" to like doing bug work & not minding "little" things--like black screens--apps seg faulting--keyboards/mice not working & other fun debugging work:D (all things I've had happen in the last few years doing testing work--my wife hates it every once in a while--but she gets over it;))

---

### Post by macogw on 2006-12-30
or like Feisty's installer freezing if you try to change the time (X, back, forward, and cancel all cease to function, only minimize works) and then freezing halfway through the install if you make it through that part...I want to play with the unstable but it's too unstable for the installer to run.

---

### Post by otaviofcs on 2006-12-30
Hi all, as a matter of fact you don't need to clean and install, you could only change our repositories to point to the new version. But I never, ever, did that. I use to backup my /etc folder and then make a clean install for it.

I have 2 folders that are in separated partitions that I never format: /home and /downloads (this one is not created by default, is a personal folder).

---

### Post by insane_alien on 2006-12-30
> **rbhigday said:**
> Thus for each upgrade we must backup all files and then everything is wiped and then replace back all our data files. Am I correct in this? 

If I am I better figure out how to make a second hard drive fit in my laptop :)

not quite. if you have a seperate /home partition then you don't need to back up your docs every time you upgrade. aysiu has a page on it.

---

### Post by macogw on 2006-12-30
> **otaviofcs said:**
> Hi all, as a matter of fact you don't need to clean and install, you could only change our repositories to point to the new version. But I never, ever, did that. I use to backup my /etc folder and then make a clean install for it.

I have 2 folders that are in separated partitions that I never format: /home and /downloads (this one is not created by default, is a personal folder).

changing repos and doing dist-upgrade is the reason everybody broke going to edgy.  It's bad.  Use the GUI updater. [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades) See?  Command line NOT RECOMMENDED (all caps like that)

---

### Post by autocrosser on 2006-12-30
Yes--Fiesty is having "problems" right now--I'm in my Edgy install waiting for updates--for me, the fun is making the new OS work--I am "addicted" to running the very bleeding edge stuff & knowing code is a bit of a help:D

So to pass the time, I've setup a seperate user with Enlightenment unstable--fun to set it up & it looks great!!

---

### Post by Papa-san on 2006-12-30
> **macogw said:**
> That doesn't work well.  Not all dependencies are fixed, so a lot of it breaks.  You type in the terminal
sudo "update-manager -c"
which brings up your regular update manager with a button that says there's a new version available.  **_If you click that, it'll upgrade flawlessly._**


Sef, using the GUI updater, it works perfectly.  Dist-upgrade was the problem last round, according to a Kubuntu dev I was talking to last month.  I took her advice (see above) on the last one I updated, and she's right.  There are things the command line doesn't know to update, that the gui was set up to do.

The highlighted part above... PLEASE make SURE you have it keep all your customized settings. It will offer you the choice to keep them or overwrite them... I made the mistake of letting them be replaced the first time... lol

---

### Post by macogw on 2006-12-30
> **Papa-san said:**
> The highlighted part above... PLEASE make SURE you have it keep all your customized settings. It will offer you the choice to keep them or overwrite them... I made the mistake of letting them be replaced the first time... lol

So it came out brown?  Or did it get rid of ATI drivers or something?  The whole reason I use upgrade instead of clean install is that I want to keep my settings, so I wouldn't have even attempted to tell it "sure, get rid of my settings."  Yay for warnings though.

---

### Post by rbhigday on 2006-12-30
SO when you do the first install it make the home partition/drive, but after that it only reformats the main partition where ubuntu is installed and leaves the home drive/partition alone along with any other partitions you have. Am I correct in this?

---

### Post by neowolf on 2006-12-30
> **rbhigday said:**
> Thus for each upgrade we must backup all files and then everything is wiped and then replace back all our data files. Am I correct in this? 

If I am I better figure out how to make a second hard drive fit in my laptop :)

There's a much easier way than that if you want to clean-install to the latest version each time. Put your /home directory on a different partition then when you upgrade only the system files and stuff on / needs to be formatted and reinstalled, then the /home partition is mounted in your new system with all your personal files, sounds complicated but is really quite easy.

Partition #1 (eg. 8GB) = / - root directory, all system files
Partition #2 (eg. 32GB) = /home - all your users personal files and configurations

On new install, format Partition #1 and set the mount point to /, then check 'Do Not Format' for Partition #2 and set the mount point as /home; this way you will have upgraded to the latest version and kept all your files.

---

