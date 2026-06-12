---
title: "Adept Manager Wont Open"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-05-10
Message I get:

"The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. Try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem."

---

### Post by [S|G] on 2007-05-10
Try opening a terminal (konsole) and typing this:
```
sudo apt-get update
```
After it finishes updating try opening adept again

---

### Post by LollYouSuckZor on 2007-05-11
> **'[S|G] said:**
> Try opening a terminal (konsole) and typing this:
```
sudo apt-get update
```
After it finishes updating try opening adept again

```
nic@nic-desktop:~$ sudo apt-get update
Password:
E: Type '-e\n' is not known on line 34 in source list /etc/apt/sources.list
nic@nic-desktop:~$
```

---

### Post by Seisen on 2007-05-11
Post your source list

---

### Post by LollYouSuckZor on 2007-05-11
> **Seisen said:**
> Post your source list


Well whats the code.

Every time I post something I get the

-e/n blah blah, crap.

---

### Post by Seisen on 2007-05-11
To post your source list do this in terminal

```
gksudo gedit /etc/apt/soruces.list
```

---

### Post by ZeroWing on 2007-05-11
> **Seisen said:**
> To post your source list do this in terminal

```
gksudo gedit /etc/apt/soruces.list
```


 Then copy that and paste it into one of your posts.

---

### Post by BHelts on 2007-05-11
the two previous posts are correct, but if you are copying and pasting then spell "sources" correct.

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by LollYouSuckZor on 2007-05-11
```
nic@nic-desktop:~$ gksudo gedit /etc/apt/soruces.list
bash: gksudo: command not found
```

---

### Post by icechen1 on 2007-05-11
Try
```
gksudo kate /etc/apt/soruces.list
```
Use this command if on KDE.

---

### Post by LollYouSuckZor on 2007-05-11
> **icechen1 said:**
> Try
```
gksudo kate /etc/apt/soruces.list
```
Use this command if on KDE.

```
nic@nic-desktop:~$ gksudo kate /etc/apt/soruces.list
bash: gksudo: command not found
nic@nic-desktop:~$
```



I am using KDE =\

---

### Post by icechen1 on 2007-05-11
> **LollYouSuckZor said:**
> ```
nic@nic-desktop:~$ gksudo kate /etc/apt/soruces.list
bash: gksudo: command not found
nic@nic-desktop:~$
```



I am using KDE =\

Well use
> sudo [insert name here] /etc/apt/soruces.list
remplace [insert name here] with the text editor you have(eg . kate,gedit,etc)

---

### Post by LollYouSuckZor on 2007-05-11
> **icechen1 said:**
> Well use

remplace [insert name here] with the text editor you have(eg . kate,gedit,etc)


Well I never see gedit, I always see Kate...But I got this!!

```
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-7980' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.

```

Then Kate opened the Sources list and its empty..

---

### Post by LollYouSuckZor on 2007-05-11
Finally looks like I am getting somewhere :D!

---

### Post by djchandler on 2007-05-11
I use Gnome, not KDE, so I don't know if this might be of help or not. I'll try to make it short. That's usually not possible. I both talk and write WAY too much.:) 

This is what happened to me.

Update-manager got hung up when I was still using Dapper and wouldn't finish downloading an update. It's irrelevant which download was hanging, because ultimately that wasn't the problem, even though Adobe get flamed because it just happened to be while retrieving Flash Player. Even though I could log off, reboot, etc., if I tried to run update-manager, synaptic, or apt-get, the system always reported another copy of whichever I was trying to run was already running. The update system must be hyper-sensitive to the smallest LAN or WAN problem, or it's possible a port was being blocked that hadn't been before, even though no configuration settings themselves had been changed puposely. NO OTHER APPLICATION WAS REPORTING PROBLEMS, including Evolution and Firefox, and my wife's WinXP box as well as  the WinXP box I use to run Adobe InDesign (plus other pain in the butt Adobe stuff my clients insist I use) were not reporting any LAN or WAN problems, not even a slowdown. When linux couldn't diagnose exactly what was going on, the error being reported was that another update application was already running, usually, I think maybe always, the same as I was currently trying to use.

The final solution was not with my linux workstation, but with a Linksys router on which I'd recently updated its firmware. Apparently some of its configuration settings got fouled up in that process. I backdated the firmware to a known working version and reset all the router configurations. I've not had a problem since, including full system upgrades to Edgy and Feisty. If you're using broadband via router, the problem could be in your local ethernet, anything from a bad cable/connection, a bad ethernet adapter on your linux workstation, bad router or protocol setting there that's been inadvertently changed, (had any power outages lately?), to a defective cable or dsl modem. If you've not ever had any problems updating before, you might try looking for a hardware problem.

If this doesn't help you, I'm sorry for wasting your time, but maybe somebody else will read this that this will eventually apply to.

---

### Post by [S|G] on 2007-05-12
Try doing this on a terminal:
```
kdesu kate /etc/apt/sources.list
```
In KDE you use kdesu and not gksudo :)
When your sources.list opens, paste this:
```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

```
Save and close kate. When you're back on the terminal, type this:
```
sudo apt-get update
```
Things should work now :)

---

### Post by LollYouSuckZor on 2007-05-12
> **'[S|G] said:**
> Try doing this on a terminal:
```
kdesu kate /etc/apt/sources.list
```
In KDE you use kdesu and not gksudo :)
When your sources.list opens, paste this:
```

# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty main restricted 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu feisty universe multiverse 
deb http://us.archive.ubuntu.com/ubuntu feisty-updates universe multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse

```
Save and close kate. When you're back on the terminal, type this:
```
sudo apt-get update
```
Things should work now :)

Omg Lol :0 When I get to my computer, i'm so going to try this.

If this works I will worship you for the rest of my life.

---

### Post by LollYouSuckZor on 2007-05-12
We'll when I open it, it wont let me edit it.

I'll select it all and try to delete it but it wont.  -.-

---

### Post by [S|G] on 2007-05-12
Are you editing it as root? You can either do that by pressing "alt+F2" and typing:
```
kdesu kate /etc/apt/sources.list
```
or opening a terminal and typing:
```
sudo kate /etc/apt/sources.list
```

It should ask for you password and then let you edit the files.

---

### Post by LollYouSuckZor on 2007-05-12
No:( Il select it all and try deleting it, but it just basically refreshes...

---

### Post by LollYouSuckZor on 2007-05-12
Mwuahh! Thank you guys so much!! I just made a source.list on my desktop, opened it, found the directory of the real source list, pasted the code he gave me above, and saved my source list in that directory.  Updating now :)

---

### Post by [S|G] on 2007-05-12
You can try editing it with VI; open a terminal and type this:
```
sudo vim /etc/apt/sources.list
```
Once it opens, press your Insert key. Then hold down the delete until everything is wiped out. Now, copy the sources.list I pasted above, right click on the terminal and choose paste from the menu. 

Press "esc", then ":wq" and press enter. That should save it. Then you can update:
```
sudo apt-get update
```

If for some reason you get things wrong and get lost in the editor, press "esc" and then ":q!" or close the terminal and start again.

EDIT: If things are working now, don't mess with VI :)

---

