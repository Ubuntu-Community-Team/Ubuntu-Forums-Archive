---
title: "Terminal frustration"
date: 2005-10-03
forum: Absolute Beginner Talk
---

### Post by canadianwriterman on 2005-10-03
Hi all,

As a Linux newbee, I find working in a terminal windows at times very frustrating. Here's an example. I'm trying to install a downloaded bin file of the Java Runtime Environment. I've placed the bin file in my Home directory and have created a folder in Home called "java" in which to install. The directions tell me to change to the directory into which I want to install JRE. As you can see below, I could "cd" to Home, but I couldn't find any combination of command lines to "cd" to the "java" folder, even using "sudo" first. What am I doing wrong? Thanks for your help.

stephen@stephen-desktop:~$ cd /home
stephen@stephen-desktop:/home$ cd /java
bash: cd: /java: No such file or directory
stephen@stephen-desktop:/home$ cd ./java
bash: cd: ./java: No such file or directory
stephen@stephen-desktop:/home$ sudo cd /java
sudo: cd: command not found
stephen@stephen-desktop:/home$ sudo cd ./java
sudo: cd: command not found
stephen@stephen-desktop:/home$

---

### Post by Ampersand on 2005-10-03
Hi
The home directory contains seperate directories for each user. When you first open a terminal, it'll be in /home/stephen, so you just need to type 'cd java'.

To get back to your home directory after changing directory to somewhere else, you can type 'cd ~/' .

---

### Post by KingBahamut on 2005-10-03
Terminal Frustration gets us all canadian.....even the advanced users at times.

---

### Post by Master Shake on 2005-10-03
You may want to check out [http://www.linuxcommand.org](http://www.linuxcommand.org)  Very good site, geard towards the n00b (like me :) )

---

### Post by lao_V on 2005-10-03
[quote=canadianwriterman]Hi all,

As a Linux newbee, I find working in a terminal windows at times very frustrating. Here's an example. I'm trying to install a downloaded bin file of the Java Runtime Environment. I've placed the bin file in my Home directory and have created a folder in Home called "java" in which to install. The directions tell me to change to the directory into which I want to install JRE. As you can see below, I could "cd" to Home, but I couldn't find any combination of command lines to "cd" to the "java" folder, even using "sudo" first. What am I doing wrong? Thanks for your help.

stephen@stephen-desktop:~$ cd /home
stephen@stephen-desktop:/home$ cd /java
bash: cd: /java: No such file or directory
stephen@stephen-desktop:/home$ cd ./java
bash: cd: ./java: No such file or directory
stephen@stephen-desktop:/home$ sudo cd /java
sudo: cd: command not found
stephen@stephen-desktop:/home$ sudo cd ./java
sudo: cd: command not found
stephen@stephen-desktop:/home$[/quote]

I would suggest you spend few moments reading this [Linux Command Guide]("http://www.linuxcommand.org/")

---

### Post by UbuWu on 2005-10-03
cd /home/stephen/java

or:

cd ~/java

or:

cd ~
cd java

(you won't need sudo for any of this)

---

### Post by az on 2005-10-03
Midnight Commander rocks!

install mc from universe.  Fire it up.  Hit F9 to configure.  Enable lynx-like motion and you are good to go.

You also need to diable gnome-terminal's grabbing of F10, so that when you hit F10, you can quit mc.

---

### Post by weasel fierce on 2005-10-03
The dash does 2 things:

It separates directories (which isnt needed in your example)

And it represents the root directory (which isnt needed either)

Hence, you dont need it in your example.


Now, if you're in your root directory (right after opening the terminal), it'd be cd /home/java

The first / is root directory, the second one is just to separate home from java.

---

### Post by UbuWu on 2005-10-03
[QUOTE=azz]Midnight Commander rocks!
install mc from universe.  Fire it up.  Hit F9 to configure.  Enable lynx-like motion and you are good to go.[/QUOTE]

lynx-like motion? :???:

---

