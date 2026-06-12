---
title: "Hostname problem"
date: 2006-05-07
forum: Absolute Beginner Talk
---

### Post by gummylindz on 2006-05-07
Hey everybody, good morning! (in west europe anyway ;)) 

I recently changed the name of my computer, the hostname, to "LINDSEY'S LAPTOP" (so I can know which one it is on my broadband router webpage, between the 3 computers we have connected to it). The thing is, I reckon " ' " isn't allowed, because now I can't start any Administrative Applications (such as synaptic package manager, or I can't do things in terminals anymore) and I get the following error:

> Bad key or directory name: "/desktop/gnome/peripherals/keyboard/host-LINDSEY'S LAPTOP/0/numlock_on": `'' is an invalid character in key/directory names

The problem is, due to the above, I can't actually access the **System - Administration - Networking** menu where I changed the name in the first place to change it back....

Is there any *other* way of changing the hostname?? :confused: 

Thanks, Lindz

---

### Post by Sendervictorius on 2006-05-07
I believe you do it by editing the file /etc/hostname. I'm not sure whether there will be other dependencies though. Worth trying if your only other option is to do a reinstall!

---

### Post by gummylindz on 2006-05-07
ok, I tried doing that......... but I can't do it directly entering the folder, opening the file, editing it and saving it because it says i "don't have permission" or something...... is there a way of doing it through a terminal? like sudo... 

I'm quite new to ubuntu..... help me please :(

oh and great avatar! I love asterix & obelix!!!! :D

---

### Post by gummylindz on 2006-05-07
ok. i'm new to ubuntu but i'm adventurous :D 

this is what I did:

first i made a new hostname readme file and saved it to the desktop. then i opened a terminal and wrote:

> lindz@LINDSEY'S LAPTOP:~$ cd Desktop
lindz@LINDSEY'S LAPTOP:~/Desktop$ sudo cp -R hostname /etc
sudo: unable to lookup LINDSEY'S LAPTOP via gethostbyname()


...to try and replace it. but as you see, it didn't work :( 

I don't know what to do!!!

:confused:

---

### Post by gummylindz on 2006-05-07
can anybody help???

---

### Post by monomaniacpat on 2006-05-07
[QUOTE=gummylindz]ok, I tried doing that......... but I can't do it directly entering the folder, opening the file, editing it and saving it because it says i "don't have permission" or something...... is there a way of doing it through a terminal? like sudo... 

I'm quite new to ubuntu..... help me please :([/QUOTE]

If you want to edit system files you have to use a text editor. Under gnome, this is gedit, under kubuntu it is kate. For gedit, enter the following:

```
sudo gedit /etc/hostname
```

Changing the host name should do the trick.

---

### Post by ubuntu_demon on 2006-05-07
$ sudo hostname *yournewhostname*

But I believe you have to also change it in gnome.I don't know for sure

---

### Post by gummylindz on 2006-05-07
im confused :s so I open a terminal and directly type sudo gedit /etc/hostname?? cus that doesnt work.

please help me!!!!

---

### Post by gummylindz on 2006-05-07
[QUOTE=ubuntu_demon]$ sudo hostname *yournewhostname*

But I believe you have to also change it in gnome.I don't know for sure[/QUOTE]

```
lindz@LINDSEY'S LAPTOP:~$ sudo hostname LINDSEYS LAPTOP
sudo: unable to lookup LINDSEY'S LAPTOP via gethostbyname()

```

that doesnt work either..... :confused:

---

### Post by ubuntu_demon on 2006-05-07
okay I did a bit of research

-reboot.
-press esc to get into the grub menu (if necessary)
-start into recovery mode
-pico /etc/hostname .. and change it to the hostname (the one without the '-symbol) (press control-x after editting)
-pico /etc/hosts and change your hostname there too (press control-x after editting)
-hostname newhostname
-reboot and report back here

I don't know whether gnome stores your hostname somewhere also. But we'll soon find out :)

---

### Post by confused57 on 2006-05-07
Might be a problem with using caps or having a space, may want to try:

lindseys_computer or something to that effect

good luck....

---

### Post by gummylindz on 2006-05-07
[QUOTE=ubuntu_demon]okay I did a bit of research

-reboot.
-press esc to get into the grub menu (if necessary)
-start into recovery mode
-pico /etc/hostname .. and change it to the hostname (the one without the '-symbol) (press control-x after editting)
-pico /etc/hosts and change your hostname there too (press control-x after editting)
-hostname newhostname
-reboot and report back here

I don't know whether gnome stores your hostname somewhere also. But we'll soon find out :)[/QUOTE]

hehe can you explain alla that a bit more up there? or should I understand it when i get into the recovery mode?

thankyou.....

ps: is what that person said about the capitals relevant? could be...

and what the hell is "pico" :confused:

---

### Post by ubuntu_demon on 2006-05-07
[QUOTE=gummylindz]hehe can you explain alla that a bit more up there? or should I understand it when i get into the recovery mode?

thankyou.....
[/QUOTE]

sorry. no problem. wait a minute.

[QUOTE=gummylindz]
ps: is what that person said about the capitals relevant? could be...
[/QUOTE]

I don't know. I always have a lowercase hostname.

[QUOTE=gummylindz]
and what the hell is "pico" :confused:[/QUOTE]

You can't start a graphical editor in recovery mode. pico is an text-mode editor. You can try it on a file in your home directory to practice. $ pico example.txt

---

### Post by ubuntu_demon on 2006-05-07
The reason why you have to boot into recovery mode is that you probably can't use sudo anymore.

1)
reboot your computer

2)When booting press enter somewhere in the beginning when Ubuntu starts up to get into the grub menu. 

3)
From there you can select recovery mode. It's probably called something like : "Ubuntu, kernel 2.6.15-21-686 (recovery mode)"

4)wait until booting is done. It might take a bit longer if your harddisk is scanned for errors.

In recovery mode you don't have to type sudo because you are root. You have the ultimate power over the system :)

5)
type this (without the $) :
$ pico /etc/hostname 

And change the hostname to the new hostname.

6)
type this (without the $) :
$ pico /etc/hosts

And change the hostname to the new hostname. Leave the rest alone.

7)

$ hostname newhostname

8 )

$reboot

reboot and report back here

I have to go now. I'll be back in a couple of hours. I hope you understand otherwise someone will help you hopefully.

(alternatively you can use a live cd if you can't get into recovery mode for some reason .. I'll explain later if needed)

---

### Post by uboat on 2006-05-07
1 opren terminal
2. cd  /
3.cd etc
4. give the ls command
5. use pico , vi ,etc to make the needed changes to the  hostname file.

---

### Post by gummylindz on 2006-05-07
ubuntu_demon, thankyou lots and lots and lots and lots :D 

I didn't even need the super instructions in the end cus I worked it out but thanks for working them all out for me anyway and golly!!! you're my hero!!! :KS 

in the end i just went for the simplest: "lindsey" (lowercase and all, hehe)

now I can update and install things again and use terminals and.... wow, ive only been with ubuntu for a month and sometimes it can be really frustrating (having being pampered by windows for so long...) but when you get some ismple instructions from someone who knows its all so easy to do :)

thanks again! (and everyone else for the suggestions) :rolleyes:

---

### Post by ubuntu_demon on 2006-05-07
No problem. Glad to be of help :)

---

### Post by bcdeck on 2006-05-10
thanks for these steps!

---

