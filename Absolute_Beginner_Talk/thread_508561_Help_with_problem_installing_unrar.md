---
title: "Help with problem installing unrar"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by butterandguns on 2007-07-24
I'm trying to install unrar and when I type "sudo apt-get install unrar" I get the following message.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How can I fix this or is there another program I should be using?
Thanks

---

### Post by lepz on 2007-07-24
> **butterandguns said:**
> I'm trying to install unrar and when I type "sudo apt-get install unrar" I get the following message.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How can I fix this or is there another program I should be using?
Thanks

You can download unrar from Synaptic Package Manager

---

### Post by butterandguns on 2007-07-24
Thanks.  Worked perfectly from the command line.  Just out of curiosity, is there an unrar utility that I can be used without the command line, kind of like in windows.

---

### Post by stchman on 2007-07-24
> **butterandguns said:**
> Thanks.  Worked perfectly from the command line.  Just out of curiosity, is there an unrar utility that I can be used without the command line, kind of like in windows.

7-zip.

---

### Post by testube_babies on 2007-07-24
Can't you open/create RAR files with Archive Manager after you've installed unrar?

Maybe you need to install unrar-free or unrar-nonfree.

---

### Post by Orochi on 2007-07-24
> **butterandguns said:**
> I'm trying to install unrar and when I type "sudo apt-get install unrar" I get the following message.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How can I fix this or is there another program I should be using?
Thanks

Just FYI, that message means another program is open/running that updates or isntalls programs (meaning you have Synaptic, Add/Remove, or Update Programs running, or you have apt-get or aptitude running in another terminal window).

---

### Post by mrazster on 2007-07-24
To get full rar/unrar support you need to do:

```
sudo apt-get install rar unrar unrar-free zip unzip unace
```

and then your chooise of application...I use filer-roller, but ther are others like xarchive, xarchiver, 7-zip e.t.c.

```
sudo apt-get install file-roller
```

---

### Post by imagine.animesh on 2007-07-24
The problem you have mentioned has nothing to do with non-availability of package. 
The error message points that your /var/lib/dpkg/ couldn't be locked by the apt-get process, which is a condition to be satisfied before any process starts package installation.

Just try to see if you have any other application started that locks this directory. Most common applications are synaptic, adept, aptitude etc.

Once you free your /var/lib/dpkg/lock file, you should be through! :)

a one liner to do this is:

kill $(ps -ef | grep adept| cut -c10-14)

Mostly, you just have to close synaptic, adept, that's it.

---

### Post by benx009 on 2007-07-24
> **butterandguns said:**
> Thanks.  Worked perfectly from the command line.  Just out of curiosity, is there an unrar utility that I can be used without the command line, kind of like in windows.

file-roller can do anything:)

---

### Post by stchman on 2007-07-24
> **butterandguns said:**
> I'm trying to install unrar and when I type "sudo apt-get install unrar" I get the following message.

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

How can I fix this or is there another program I should be using?
Thanks

You have to enable multiverse repository as that is where unrar is located.  After that then do the following:

sudo apt-get update
sudo apt-get install unrar

---

### Post by wrongo on 2007-07-29
Yes, but where is this "File-Roller" program, hm?

I double click on my .rar files, and Archive Manager comes up, but the 'window' is BLANK, i.e., there aren't any files.

Now, I'm thinking, either my .rar files are empty, which, at 700 Mb each, is unlikely, or Archive Manager is, shall we say, differently-abled.

The reason I think the latter is that when Archive Manager comes up, again, with a BLANK or EMPTY window, right ABOVE this blank, empty window, the TITLE BAR has the NAME of my FILE stretching across it, all the way to the MINIMIZE, MAXIMIZE, and CLOSE buttons...

...which leads me to think the program just doesn't know how to 'unpack' the file, i.e., all Archive Manager seems to know how to do is open a blank, empty window with the title of my file stretched across the title bar.

But how do I UNPACK my .rar files?

And where IS this much-touted "File-Roller," which can purportedly "do anything?"

If anyone needs information about my computer to aid in the diagnosis, let me know how to get one of those information-packed "terminal printout" thingies, and I'll be happy to comply.

Thanks.

Hoping to UN-rar in the near future,
Jerit

---

### Post by RomeReactor on 2007-07-29
Hi **wrongo**. Can you please post a screenshot of Archive Manager open with this file (press the PRT SCR button; it's usually next to F12)? Are you using Gnome or KDE? are you using a theme downloaded from a website? Do you have Compiz (Desktop Effects) or Beryl enabled? Since you [already installed unrar]("http://ubuntuforums.org/showthread.php?t=511632"), File Roller (Archive Manager) should be able to extract it.

---

