---
title: "Xfce Xubuntu install"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-05-05
Here's what I did:

4a. You'll then likely end up at a prompt that looks like this:

username@ubuntu:~$

4b. Once at that prompt, type sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list

4c. You'll then be editing the sources.list file using the text editor called Nano.

5. Delete the # signs (also called comments) in front of anything that looks like a web address. # signs basically tell Ubuntu "Ignore this line--it doesn't exist."

6. Then save (Control-X), confirm (y), and exit (Enter). Now you have more online repositories to draw from--the ones you need to install Xubuntu.

7. Next type sudo apt-get update
sudo apt-get install xubuntu-desktop 


Here's what I got:
Reading package lists....done
Building dependency tree.....done
E: Couldn't find package xubuntu-desktop

I also tried everything with Xfce4, same results, just insert Xfce4 in place of Xubuntu-desktop

Probably simple, just not as simple as me.

---

### Post by Sutekh on 2006-05-05
Nano can be a bit confusing.  It loads a file, which can be larger than a screen, but the sidebar makes it look like there isn't any more to display.

Did you go through the entire file and uncomment all the lines?  In particular these lines?
```
# deb http://archive.ubuntu.com/ubuntu/ breezy universe
# deb-src http://archive.ubuntu.com/ubuntu/ breezy universe
```
Xubuntu-desktop (and xfce4 for that matter) are in the universe repositories, thus they need to be enabled by removing the comments

---

### Post by bt224 on 2006-05-05
Between steps four and 6 all I got was a blank editor. I scrolled around in every direction and found a few $ signs, but that's it.

---

### Post by Sutekh on 2006-05-05
That doesn't sound good.

If you use this command
```
cat /etc/apt/sources.list
```
it will print the contents of the file to screen.  Can you see any repositories in the print out?

Also were you installing Xubuntu from a blank server installation of Ubuntu?  Or are you adding Xubuntu to a previous Ubuntu installation?

---

### Post by Mano[FA] on 2006-05-15
[QUOTE=bt224]
Here's what I got:
Reading package lists....done
Building dependency tree.....done
E: Couldn't find package xubuntu-desktop
[/QUOTE]

Happened also to me.
Probably you have installed 5.10 (hoary) but you need breezy (or draper).
if you can see the source.list file change hoeary with breezy an then

sudo apt-get update
sudo apt-get upgrade

then you can install Xubuntu

---

