---
title: "How do I use root permissions via GUI?"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by Verminox on 2006-11-18
I'm currently using Kubuntu 6.06 LTS. I read about the sudo command, which gives me root privellages via the command line interface. But what about via GUI? 

For example, I opened a tar.gz file via Ark, and tried to extract it to /usr/local/bin but it said I don't have the write permissions for the file. How do I use root privellages via such programs with GUI that require them?

---

### Post by madmetal on 2006-11-18
i think 
gksudo nautilus
:-k

---

### Post by Tomosaur on 2006-11-18
Nautilus does not have a built-in function which will allow you to become root. However, you can become root BEFORE running nautilus, and will then be able to use it with all permissions, by typing 'gksudo nautilus' into the command line.

---

### Post by cantormath on 2006-11-18
If you install automatix2, there is a nuatilis script that lets you right click anything and open with root permissions.  
here
[http://www.getautomatix.com/](http://www.getautomatix.com/)

or you can open terminial and sudo whatever program you want opened as root.....

---

### Post by Verminox on 2006-11-18
Err isn't Nuatillis for GNOME? I'm using Kubuntu, and therefore KDE. Konqueror is my File Manager.

---

### Post by anaconda on 2006-11-18
You are right. And gksudo also is a gnome thing. Dont remember what it is in KDE, but sudo works just fine.

eg.
sudo kongueror
sudo ark
or just open a terminal and type:
sudo su
and then you can start any programs without having to type sudo...

---

### Post by cantormath on 2006-11-18
> **anaconda said:**
> You are right. And gksudo also is a gnome thing. Dont remember what it is in KDE, but sudo works just fine.

eg.
sudo kongueror
sudo ark
or just open a terminal and type:
sudo su
and then you can start any programs without having to type sudo...

yes gksudo..

---

### Post by taurus on 2006-11-18
For KDE, try to run it with kdesu...

---

### Post by Oki on 2006-11-18
I have used the gksudo nautilus command in GNOME, and on a other forum one wrote that I should add -- nodesktop at the end of that command – but he never wrote why. Do you know why?

---

### Post by Jamesbowden on 2006-11-18
I don't know about kubuntu, but on ubuntu if you want to log in as root in a GUI log on you do this:

go to: system > administration > Login Window.

then switch to the security tab. and check the box that says "allow Local system administrator login"

then, log out and log in with the user name "root"

i wouldn't recommend a GUI root login encase you accidentally delete something you shouldn't or you are exposed to some malicious script or virus while on the internet.

---

### Post by d3v1ant_0n3 on 2006-11-18
> **Oki said:**
> I have used the gksudo nautilus command in GNOME, and on a other forum one wrote that I should add -- nodesktop at the end of that command – but he never wrote why. Do you know why?

I don't know about in GNOME, but i know if you run kdesu nautilus in KDE, it loads up your desktop (wallpaper etc) with it. So the --nodesktop command just makes nautilus run on its own.

---

### Post by aysiu on 2006-11-18
I thought the OP was using Kubuntu, not Ubuntu.

You want to press Alt-F2 and type ```
kdesu konqueror
```

---

### Post by Verminox on 2006-11-18
kdesu was all I was looking for :p

Thanks everyone.

---

### Post by TheWizzard on 2006-11-18
> **Verminox said:**
> I'm currently using Kubuntu 6.06 LTS. I read about the sudo command, which gives me root privellages via the command line interface. But what about via GUI? 

For example, I opened a tar.gz file via Ark, and tried to extract it to /usr/local/bin but it said I don't have the write permissions for the file. How do I use root privellages via such programs with GUI that require them?

i understand your desire to launch GUI apps with root permissions. however, i would strongly advise you to be very careful. it is - in the end - the easiest **and** safest to use the CLI for administrator tasks. 
but i admit it took me quite a while before i was used to this.

---

### Post by aysiu on 2006-11-18
> **TheWizzard said:**
> i understand your desire to launch GUI apps with root permissions. however, i would strongly advise you to be very careful. it is - in the end - the easiest **and** safest to use the CLI for administrator tasks. 
but i admit it took me quite a while before i was used to this.
You'e obviously entitled to your opinion, but I strongly disagree.

For example, if you type ```
sudo rm -r /usr/local/bin/program
``` to remove a directory, and you accidentally hit **Enter** before typing in *usr*, you could end up deleting almost your entire system!

The CLI is too powerful. I would do most administrative tasks through *gksudo nautilus* or *kdesu konqueror*. Just my opinion. You're welcome to disagree.

Also, many people don't bother to use ```
sudo mv /usr/local/bin/program ~/.Trash/
``` They use the *rm* command, which deletes the folder outright. In the GUI, the default is "move to trash," which allows you to recover the file later, should you wish to do so.

---

### Post by 23meg on 2006-11-18
You may like [this trick]("http://www.ubuntuforums.org/showpost.php?p=116371&postcount=1").

---

### Post by TheWizzard on 2006-11-18
> **aysiu said:**
> You'e obviously entitled to your opinion, but I strongly disagree.

For example, if you type ```
sudo rm -r /usr/local/bin/program
``` to remove a directory, and you accidentally hit **Enter** before typing in *usr*, you could end up deleting almost your entire system!

The CLI is too powerful. I would do most administrative tasks through *gksudo nautilus* or *kdesu konqueror*. Just my opinion. You're welcome to disagree.

Also, many people don't bother to use ```
sudo mv /usr/local/bin/program ~/.Trash/
``` They use the *rm* command, which deletes the folder outright. In the GUI, the default is "move to trash," which allows you to recover the file later, should you wish to do so.

aysiu, you're absolutely correct that the cli is powerful. and you're example illustrates this well.
i always cd into the folder if i want to remove a file. and quite often i type the entire command before putting sudo before the line. 

the problems i've encountered when using konqueror with root permissions is that i often forgot konqueror was actually running with root permissions. 
if the default konqueror with root permissions had e.g. a red background to warn users, i would definitely agree with you. 

cheers.

---

### Post by aysiu on 2006-11-18
> **TheWizzard said:**
> 
if the default konqueror with root permissions had e.g. a red background to warn users, i would definitely agree with you. You could certainly change your theme in root Konqueror to be different or a different color.

I believe this is the default for Thunar in Edgy, though--a red background to let you know you're running as root.

---

