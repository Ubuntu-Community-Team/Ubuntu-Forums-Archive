---
title: "Sudo code error"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by TeamMicron on 2007-04-27
I am a beginner at using ubuntu/linux and need help.  I am trying to install the avr environment onto my box in order to compile C code onto my AVR board.  Here are the command lines and corresponding errors: 
 * sudo chmod 666 /dev/parport0 /etc/apt/sources.list
* sudo apt-get update
*sudo apt-get install avr-libc avrdude avra gcc-avr

  After "apt-get install" command, I get an error reading "Couldn't find package avr-libc". What am I doing incorrectly.  Thanks for your help.

---

### Post by wormser on 2007-04-27
Apt-get cannot find the package in the repositories.  The places where it is searching does not have that package.  You need to open up the repository that has the avr-libc package.  Your apt-get source list is located in /etc/apt/sources.list.  I am not sure which repository has the package but it probably is in universe or multiverse.  To enable them uncomment them in sources.list.  

```
sudo nano /etc/apt/sources.list
```

Nano is a text editor for the shell.  Go threw the file and remove the # infront of the repository link.  If you have any problems post sources.list.

---

