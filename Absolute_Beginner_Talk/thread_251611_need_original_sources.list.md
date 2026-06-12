---
title: "need original sources.list"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by crunchystrike on 2006-09-05
Can somone provide me a way to get the original Ubuntu sources.list, i need it because everytime i open synaptic package manager, it gives me this popup:


Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences


if anyone can help me fix this problem, or post their source.list, it would be great, oh and also, i have tried to copy and paste the source.list original from somewhere from the net, but it doesn't let me save it, so... yeah.

---

### Post by Skogix on 2006-09-05
To edit your sources.list you must be superuser/root.

My sources.list:
```
# Dapper Final Release Repository
deb http://archive.ubuntu.com/ubuntu dapper main
deb-src http://archive.ubuntu.com/ubuntu dapper main

deb http://archive.ubuntu.com/ubuntu dapper restricted
deb-src http://archive.ubuntu.com/ubuntu dapper restricted

deb http://archive.ubuntu.com/ubuntu dapper universe
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

# Dapper Security Updates
deb http://archive.ubuntu.com/ubuntu dapper-security main
deb-src http://archive.ubuntu.com/ubuntu dapper-security main

deb http://archive.ubuntu.com/ubuntu dapper-security restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-security restricted

deb http://archive.ubuntu.com/ubuntu dapper-security universe
deb-src http://archive.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper-security multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-security multiverse

# Dapper Bugfix Updates
deb http://archive.ubuntu.com/ubuntu dapper-updates main
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main

deb http://archive.ubuntu.com/ubuntu dapper-updates restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates restricted

deb http://archive.ubuntu.com/ubuntu dapper-updates universe
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe

deb http://archive.ubuntu.com/ubuntu dapper-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates multiverse

# Dapper Backports (new software versions, provided by the Ubuntu Backports Proj ect)
deb http://archive.ubuntu.com/ubuntu dapper-backports main
deb-src http://archive.ubuntu.com/ubuntu dapper-backports main

deb http://archive.ubuntu.com/ubuntu dapper-backports restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-backports restricted

deb http://archive.ubuntu.com/ubuntu dapper-backports universe
deb-src http://archive.ubuntu.com/ubuntu dapper-backports universe

deb http://archive.ubuntu.com/ubuntu dapper-backports multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-backports multiverse

# Ubuntu Commercial
deb http://archive.canonical.com/ubuntu dapper-commercial main
deb http://archive.canonical.com/ubuntu dapper-commercial multiverse

```

---

### Post by crunchystrike on 2006-09-05
may i ask how do i use superuser/root? sorry i am 2 days new to ubuntu

---

### Post by Skogix on 2006-09-05
I'm guessing you have all the normal ubuntu programs installed.

Then try ```
sudo gedit /etc/apt/sources.list
```

sudo = SuperUser DO
gedit = a texteditor

---

### Post by jd65pl on 2006-09-05
add the pre-fix sudo on commands typed in the terminal [see here]("https://wiki.ubuntu.com/RootSudo") for more info on sudo

If gedit doesn't work try "nano" this is a CLI text editor

---

### Post by crunchystrike on 2006-09-05
thank you so much, you know, i think one of the reasons i switched to linux is becuz it has not such big community, but that community kicks @$$

---

### Post by Skogix on 2006-09-05
:)

Now run ```
sudo aptitude update
``` and then install your programs with ```
sudo aptitude install <program>
```

---

### Post by crunchystrike on 2006-09-05
hey, im sorry to bother u again, but i need help in something else thats bothering me:  when i like want to remove wine, or some other stuff, this happens:

'dpkg --configure -a' to correct the problem.

and then when i type in sudo 'dpkg --configure -a'  it starts Setting up flashplugin-nonfree (7.0.63.3ubuntu3) ...


thing is i cant get past that cuz flash is already installed, and i have already installed flash, this thing happens all the time, how can i stop this flashplugin from bugging me again?

sorry again

---

### Post by vincentvee on 2006-10-12
this happened to me when i had the same problem, try rebooting it and then running the command,that was the only way i could get it to work
V

---

