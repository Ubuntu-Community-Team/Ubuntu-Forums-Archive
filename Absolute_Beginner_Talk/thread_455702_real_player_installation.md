---
title: "real player installation"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by giulian on 2007-05-26
trying to install Real Player after downloading form internet realplayer10gold.bin this the mesage that I got form the terminal:

giuliano@giuliano-desktop:~$ chmod a+x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
giuliano@giuliano-desktop:~$ sudo ./RealPlayer10GOLD.bin
Password:
Sorry, try again.
Password:
sudo: ./RealPlayer10GOLD.bin: command not found
giuliano@giuliano-desktop:~$ 


Can anybody help me?

---

### Post by taurus on 2007-05-26
```
cd ~/Desktop
chmod a+x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin
```

---

### Post by giulian on 2007-05-26
Thank you!

---

### Post by wrongo on 2007-05-27
ok but now i'm stuck here:
[I][COLOR="Sienna"]
Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/adamson/Desktop/RealPlayer]: [/COLOR][/I]

where should i install applications? the process is usually automated (using add/remove programs or synaptic package manager) - ???

---

### Post by taurus on 2007-05-27
You can install it anywhere you want so that path is fine too if you want to install it in ~/Desktop/RealPlayer or you can have it install to /opt/RealPlayer (that's what I would do).

---

### Post by wrongo on 2007-05-27
thank you, i put it in opt/RealPlayer...
[I][COLOR="Sienna"]
cd //

ls -l

cd opt

sudo mkdir RealPlayer

sudo chown [username]:[username] RealPlayer

sudo chmod a=rwx [username][/COLOR][/I]

...now it's not on my Applications->Sound & Video menu:sad:

---

### Post by taurus on 2007-05-27
When you run the command to install it from your $HOME directory, it will ask you where you want to install it.  That's where you type in /opt/RealPlayers and it will then say something like directory is not found and it will create one for you.  At the end, it will ask you if you want it to link to /usr/bin so answer yes there.  It will create an icon in then menu for you so you don't have to do anything extra.

---

### Post by wrongo on 2007-05-27
I'm sorry, what is the command to install RealPlayer10GOLD.bin from my $HOME directory?

Thank you!

---

### Post by ugm6hr on 2007-05-27
@wrongo:
Seems you're having difficulty installing Realplayer10.  If it's Feisty you're using - find my post in here for easier instructions (i.e. download, double-click, done).

[http://ubuntuforums.org/showthread.php?t=454622](http://ubuntuforums.org/showthread.php?t=454622)

---

