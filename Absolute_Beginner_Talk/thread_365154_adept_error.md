---
title: "adept error"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by fivexgrand on 2007-02-19
i installed kubuntu on friday, and i am quite lost since i havent used any os other than windows before, but i really dont want to go back to using windows full time again.

i have managed to mount a fat drive, and install a few programs, but now the adept package manager isnt working.
at first the problem was that i couldnt see or access any repositories at all, so i rebooted the computer to see if it would make a difference.
now when i try to load up adept, the password box comes up, i type in the correct password and this error comes up:

"could not open cache - adept manager
the apt database could not be opened! this may be caused by incorrect apt configuration or some similar problem. try running apt-setup and apt-get update in terminal and see if it helps to resolve the problem".

i have no idea what im supposed to do. i know how to use the terminal to some extent, but if anyone can tell me how to fix things i would appreciate it.

also, i have another problem with trying to play music. i have a fat32 hard drive with music on it in mp3 format. when i create a playlist in amarok or kaffeine, the music wont play. it appears to play, but the songs seem as though they are about one second long as both programs just scroll through the entire playlist without playing anything, but in amarok in the information panel, it shows that the tracks have been registered as played.

please help, because i feel very tempted to just do a fresh install of kubuntu, but then i will lose all the progress ive made. thanks.

---

### Post by bernied on 2007-02-19
Hello and welcome to ubuntu.

Firstly, doing a fresh install will not solve your mp3 issues, because this is to do with ubuntu's policy of only including 'free' (in the sense of free speech, not free beer) software. While mp3 codecs are free (as in beer) to obtain, I believe they are a proprietary format with licencing restrictions, so (strange as it may seem) mp3 support has to be added manually to a ubuntu install - as far as I know (someone tell me if I'm wrong here). Anyway, the most common solution here is to use something like [EasyUbuntu](http://easyubuntu.freecontrib.org/), or [Automatix](http://www.getautomatix.com/). I think I'd suggest EasyUbuntu as the better alternative (because I understand it uses only ubuntu repositories, whereas Automatix uses unofficial repositories), though EasyUbuntu did not work when I tried it, and being lazy, I just used Automatix instead.

As for your Adept troubles, have you tried the two suggestions that the program gave you? > the apt database could not be opened! this may be caused by incorrect apt configuration or some similar problem. try running apt-setup and apt-get update in terminal and see if it helps to resolve the problemWhat was the result?

If you don't understand what it is suggesting, apt-get is the basic, underlying core of the package management system in ubuntu, and it has more functionality than the pretty user interface Adept. So some things you can only do with apt-get, though they will apply to Adept.

So, to do what it is suggesting, open a terminal and type:
```
sudo apt-setup
```and see if it gives you positive feedback.
(You will be asked for your password - this is part of Ubuntu's security system).
And/or:
```
sudo apt-get update
```
If these look like they are telling you positive things (absence of words like 'Error' or 'Could not' or 'Unable to'), then try running Adept again.

Post any output here (from those two commands) if this doesn't solve the problem.

---

### Post by jvc26 on 2007-02-19
I'd run those two commands it suggested to you (note bernied's instructions have a slight typo ;))
```

sudo apt-setup
sudo apt-get update

```
It will ask you for your password. If that works, all good, if not please post up output/other errors.
Il

---

### Post by ikonone on 2007-02-19
i am in the exact same spot as fivexgrand, literally almost exactly the same situation. my method of messing up adept can be explained here.

[http://www.ubuntuforums.org/showthread.php?t=363911](http://www.ubuntuforums.org/showthread.php?t=363911)

as i said in that thread i tried to follow the instructions in some of the links in that thread to be able to play mp3's and i messed something up.

one missing link for me was that i had to type sudo before the commands, i was just typing them in and not getting anywhere. anyway, i tried those commands as you two have suggested with the sudo in the command line and i got this feedback:

sudo: apt-setup: command not found

and

E: Type 'Uncomment' is not known on line 10 in source list /etc/apt/sources.list

so just as i suspected, i messed up that line that i discussed in the other thread. so how can i fix this without being able to get back into adept? thanks for the help everyone!

---

### Post by Lady Jane on 2008-05-12
Hi,
I also had the same Adept problem. I know what I did wrong...but not how to solve it. 
I tried to install Skype with Adept, but Adept couldn't find Skype in its updates. So I tried to add it in the reposotories. But I added it a a source over the original source of updates from Ubuntu. 
So now it gave the following messages in Konsole:

marianne@Lavinia:~$ sudo apt-setup
[sudo] password for marianne:
sudo: apt-setup: command not found
marianne@Lavinia:~$ apt-setup
bash: apt-setup: command not found
marianne@Lavinia:~$ apt-get update
E: Type 'http://skype.com/go/getskype-linux-ubuntu' is not known on line 56 in source list /etc/apt/sources.list

The last 2 lines explain why it doesn't work. But, now how do I solve this?

Cheers, 
Jane

---

### Post by Tekovro on 2008-05-19
i have the same problem except mine says..

"E: Type 'http://3v1n0.tuxfamily.org/apt-repository/dists/feisty/eyecandy/index.html' is not known on line 56 in source list /etc/apt/sources.list
"

I'm a noob in linux and i tried to install the some plugins for compiz by clicking on a deb file and i believe after then it started to give me problems... what can i do??

---

### Post by Tekovro on 2008-05-19
> **Lady Jane said:**
> Hi,
I also had the same Adept problem. I know what I did wrong...but not how to solve it. 
I tried to install Skype with Adept, but Adept couldn't find Skype in its updates. So I tried to add it in the reposotories. But I added it a a source over the original source of updates from Ubuntu. 
So now it gave the following messages in Konsole:

marianne@Lavinia:~$ sudo apt-setup
[sudo] password for marianne:
sudo: apt-setup: command not found
marianne@Lavinia:~$ apt-setup
bash: apt-setup: command not found
marianne@Lavinia:~$ apt-get update
E: Type 'http://skype.com/go/getskype-linux-ubuntu' is not known on line 56 in source list /etc/apt/sources.list

The last 2 lines explain why it doesn't work. But, now how do I solve this?

Cheers, 
Jane


Hey i found out how to fix the problem if your running in Kubuntu type:
```
kdesu kate /etc/apt/sources.list
```

to bring up the sources.list or if your not in kubuntu find out what the command is to bring up Sources.list and once you get it to show up scroll down and find the line "http://skype.com/go/getskype-linux-ubuntu" and delete it. save and then it should fix the adept problem.

---

