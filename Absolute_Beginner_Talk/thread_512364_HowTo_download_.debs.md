---
title: "HowTo download .debs"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by jnorthr on 2007-07-29
My ubuntu is not attached to the web therefore i cannot download packages directly. I would like to find java-package. Is this a .deb file ? Can anyone pls provide a link to it ?
Thx

---

### Post by atomkarinca on 2007-07-29
i guess you're looking for this: [http://packages.ubuntu.com/feisty/misc/java-package](http://packages.ubuntu.com/feisty/misc/java-package)

edit: and this site is where you can find all the debs you need in the world :)

---

### Post by AlexenderReez on 2007-07-29
other alternative website is [www.getdeb.net:](www.getdeb.net:))

---

### Post by jnorthr on 2007-07-29
Ah, yes. Thanx for that. I was just over looking at desktops:
[http://www.gnome-look.org/index.php](http://www.gnome-look.org/index.php)

---

### Post by mdebusk on 2007-07-29
> **jnorthr said:**
> My ubuntu is not attached to the web therefore i cannot download packages directly. I would like to find java-package. Is this a .deb file ? Can anyone pls provide a link to it ?
Thx

What I usually do is select everything I want in Synaptic and then have it create a "download script". I'm not in front of my own PC right now, so I can't tell you where in the menus to find it, but it's there. It'll create a text file with URLs pointing to all the selections and their dependencies.

The download script looks like this:
```

#! /bin/bash
wget -c<url-to-file>
wget -c<url-to-file>
wget -c<url-to-file>

```

I usually just remove the first line and the "wget -c" from each line and grab them all with:
```

wget -i download.script.file

```

I then move it all to /var/cache/apt/archives/, select them in Synaptic again, and install normally.

---

### Post by ugm6hr on 2007-07-30
> **mdebusk said:**
> What I usually do is select everything I want in Synaptic and then have it create a "download script". I'm not in front of my own PC right now, so I can't tell you where in the menus to find it, but it's there. It'll create a text file with URLs pointing to all the selections and their dependencies.


This is very clever - I have previously had to try manually installing everything, and waiting for dpkg to tell me what was missing - only to search through the archive website for the next bit!

Just had a look - it's in the File menu in Synaptic - Generate Package download script.

Had a thought though - if you're not online - is there any way to update the repo information (like it does when you click reload in Synaptic).  Otherwise, presumably, all the packages you chose could be outdated...

---

### Post by deadgobby on 2007-07-30
[https://launchpad.net/aptoncd](https://launchpad.net/aptoncd)

Gobby

---

### Post by mdebusk on 2007-07-30
> **ugm6hr said:**
> Had a thought though - if you're not online - is there any way to update the repo information (like it does when you click reload in Synaptic).  Otherwise, presumably, all the packages you chose could be outdated...

I've never messed with that, as I'm online through dialup. My GF has a broadband connection, as does my job, so sometimes I borrow their bandwidth. It depends on how much I have to grab.

There has to be some way of doing it, though. The package lists are downloaded from the repos and stored somewhere on your PC. It shouldn't be tough to track them down.

---

### Post by jnorthr on 2007-07-30
Great !  Many thanks to each of you. I like the idea of a "requirements" list out of synaptic, a list out of "repo" and a match of the two - then downloading what's missing onto a local usb disk drive. I can then mount the usb on my ubuntu machine and "install" the .debs.  
Now how can we do this using an 'xp' system as the internet link ? The 'APTonCD' tool is a wonderful idea - it just needs to be portable - something like a java app (cause we have java jre's on windows kit) as there may be a java ftp client that can get this down from the repo server.
:popcorn:

---

### Post by ugm6hr on 2007-07-30
Found the software lists in : /var/lib/apt/lists
And the files are named as per their url, with a "_" instead of a "/" (found that by checking *sudo apt-get update*)

But it would be pretty time consuming to copy all 20-odd files manually....

---

### Post by cjm5229 on 2007-07-30
Applications>Add/Remove>APTonCD, If you can get hooked up to broadband long enough to download and burn CDs or if someone you know has a Ubuntu computer hooked up to Internet you can put the entire Repositories on CD, then install what ever you want by enabling the CD in Software Sources. Check DeadGobby's post.

---

### Post by mdebusk on 2007-07-31
> **jnorthr said:**
> Now how can we do this using an 'xp' system as the internet link ? The 'APTonCD' tool is a wonderful idea - it just needs to be portable

Our old friend, wget, is available for Windows. I use it all the time. A quick Googling will turn it up.

---

### Post by mdebusk on 2007-07-31
> **ugm6hr said:**
> But it would be pretty time consuming to copy all 20-odd files manually....

Here's what I'd do:
* Dump the list of filenames to a text file
* Replace all the "_" with "/" and preface each line with "ftp://"
* Put the text file on a nerdstick, along with WGet for Windows;
* Ask a broadband-enhanced friend if you might borrow their bandwidth;
* wget -i repo-filename-list.txt -P path_to_nerdstick; and
* Move all files to your /var/lib/apt/lists/ .

You'd only have to do the first three steps once unless you add or remove a repo. You'd only have to do the fourth once if you start dating a girl who has broadband.

---

### Post by ugm6hr on 2007-11-23
I know this thread is old now.  But in case someone searches and finds it - it looks like there is a very slick solution for the problem of "borrowing" an internet connection from a second computer:
[http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

---

