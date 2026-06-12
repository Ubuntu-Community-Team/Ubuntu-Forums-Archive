---
title: "-bash: startx: command not found"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by yelkhatib on 2007-06-28
I'm very new to Linux and I'm doing a project for school. I installed the Ubuntu 6.06 server version. I need to install a Zimbra server over Ubuntu but I don't know command lines so I'm trying to install the GUI.
I was told to run: sudo apt-get install ubuntu-desktop
I did and at the end of the installation it said that some packages were not installed,, try using "update" or "fix-missing". I tried both and they worked fine. The problem is that when I run "startx" it will give me "-bash: startx: command not found" so what am I missing to have the GUI running?

Thank you for your help!

Yaser

P.S. the first image is after I did the upgrade command, then the second one shows the error I get.

---

### Post by speaker219 on 2007-06-28
Try:
```
sudo apt-get install x-window-system
```

---

### Post by yelkhatib on 2007-06-28
> **speaker219 said:**
> Try:
```
sudo apt-get install x-window-system
```
Dear speaker219,
Thank you for the tip but it's saying that "E: couldn't find package x-windows-system"
I have also tried: sudo aptitude update, which I found on the forums and it also gave me the same error that it "can't read from E: is the source used with different process?" or something like that!

Please help ... anyone?

Thank you,

Yaser

---

### Post by Rocket2DMn on 2007-06-28
It seems like apt-get is looking to your CD drive as one of the repositories.  Have a look at this: [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by yelkhatib on 2007-06-28
Rocket2DMn,

I went to the link you suggested. They say that they assume I know how to edit a file which I don't!!! How can I edit /etc/apt/sources.list and then save changes?
I just need to take out the # and it should go online instead of going to the CD right?

Thank you,

Yaser

---

### Post by shearn89 on 2007-06-28
Make sure that the universe repos are enabled (terminal commands, as they're easiest):
```

sudo gedit /etc/apt/sources.list

#uncomment the lines with "universe" near the end
#put a "#" in front of any lines about cds
#then

sudo apt-get update

```

And see if that helps.

EDIT: just saw post above - "gedit ****" will let you edit "****".

---

### Post by yelkhatib on 2007-06-28
Thank you but I can't gedit. It says "-bash: gedit: command not found"

I'm really frostrated now! I don't understand what's going on ... I did: vi /etc/apt/sources.list and it worked but it says the file is read only and I can't save changes!!! 

Any ideas?

Thank you,

Yaser

---

### Post by Rocket2DMn on 2007-06-28
Since you're in the command line, I'm not sure if gedit will run.  I know how to use emacs in a command line environment, but I wouldn't suggest it right away.
If you can only work inside the command line, here is a quick tutorial for using vi (instead of gedit):
[http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)
This should give you enough to get the job done until you get your GUI.
The new command is
```
sudo vi /etc/apt/sources.list
```

---

### Post by yelkhatib on 2007-06-28
It's not going to work because, as I said, it's read only file and it will not allow writing to it! what should I do? is there a way to replace the sources.list?

Thank you

---

### Post by yelkhatib on 2007-06-28
Guys I figured out how to save the file. I had to be logged in as SUPER USER to save changes. I will try the previous methods and commands to install the GUI and let you know what happends.

Thank you all ... Yaser

---

