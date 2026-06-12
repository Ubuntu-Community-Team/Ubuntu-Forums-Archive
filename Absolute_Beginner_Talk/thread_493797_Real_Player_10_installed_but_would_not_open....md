---
title: "Real Player 10 installed but would not open..."
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by tepco53 on 2007-07-06
I am on Ubuntu 7.04 and installed Real Player 10 from Automatix2. 
Install seems to have done the job ok. But, when I try to open, it would not open anything. 
I also tried to open it from Command line typing in realplay and I get 

me@ubuntu:~$ realplay
cp: cannot stat `/usr/lib/realplay-10.0.8/share/default/.realplayerrc': No such file or directory
Segmentation fault (core dumped)

What am I doing silly Please!!??

---

### Post by mikeyphi on 2007-07-06
Assuming you launched Real Player from Applications - Sound & Video, and accepted the licence agreement?
If so-  you could try to uninstall using Automatix and then reinstall to see if you get a working program.

---

### Post by starcraft.man on 2007-07-06
Oh no, can it be? A problem with Automatix's install of something, and Arnie no where to be found... whatever is the world coming to?

Couldn't resist (not making fun of you), and you just happen to be using two apps I really don't like >.>. My disdain for Real though is without limit, I despise (with a passion) their stupid format and the fact that lots of sites use it to stream (even some of my favourites). It really hasn't done anything at all for anyone or me, except get me upset.

That said, I've never seen this particular error with Real, I'm gonna assume that its just a bad install (seen that often enough from Automatix, its not perfect).

To fix:
1) As mikeyphi said, uninstall and reinstall with Automatix (I don't like to say that, but its the quickest way since you already have it installed.)

2) In the event the above fails, we'll have to install it manually (its no longer maintained in any of the official or extended repos of Ubuntu). Please uninstall it again from the Automatix menu. Then to ensure it is gone we will purge it. To do so open any terminal please (Applications > Accessories > Terminal):

```
sudo aptitude purge realplay
```

(I dunno how familiar you are in terminal so I'll explain commands to be sure you understand. [sudo]("https://help.ubuntu.com/community/RootSudo") grants the command root power, by default you are of course a limited user as a security measure (you need to be root for any system wide modifications, like being administrator in Windows). Aptitude of course is the base package manager for Ubuntu, handles all the installations, thus we are telling it to purge (dumps the program and the configuration files out of your system) realplay (name of the package of realplayer) from your system).

3) With realplayer removed, please download [this]("https://helixcommunity.org/projects/player/files/download/2151") direct to your home folder (if you download to desktop, put it in there yourself, Places > Home folder). It is the latest stable build of real for linux.

4) Please make sure you are still working in the home directory. To see where you are, use the following command:
```
pwd
```
This command is short for print working directory, it lists in what folder/directory you are working in. By default, the terminal always starts and stays in the home folder unless you change directory. The folders are arranged from left to right (left being root the highest point in the tree folder system and right being where you are down the tree).

It should read:
/home/username
(Where username is of course your userame.)

In the event it does not, please use the following command (again, where I use username, use your own):

```
cd /home/username
```
cd is the command for change directory, and /home/username is the home folder we just spoke about.

5) Now use the ls command, it is the list command and will show you all files in the home folder.
```
ls
```

You should see a list with realplay-10.0.8.805-linux-2.2-libc6-gcc32-i586.bin somewhere in it. This is the installer for realplayer. Now, you have to assign it executing privileges (for more on that read permissions [here]("http://www.linuxcommand.org/lts0070.php")) with this command:

```
chmod a+x realplay-10.0.8.805-linux-2.2-libc6-gcc32-i586.bin
```

6) Almost done, now please run the installer with the following command:

```
sudo ./realplay-10.0.8.805-linux-2.2-libc6-gcc32-i586.bin
```
(sudo again gives you root power and ./ before the name of the file just tells the terminal to run the installer)

7) It will extract, then push enter to continue. Now time to select the place where you want it installed, since its real we will put it in the opt folder. Type this in and push enter:

```
/opt/realplayer/
```

Push enter again to confirm, if you made a mistake push p and then enter to go back one. Next it will ask a question, type y and enter. Then, push enter again to confirm.

Thats it. Go to Applications > Sound & Video > Realplayer 10. It will work now, I am sure. :)

Terminal isn't so scary is it? For more info on the terminal please see [Linux command.]("http://www.linuxcommand.org/learning_the_shell.php") If you ever have to remove it, do so manually since its not installed as a package. Go in /opt and delete the realplayer folder, thats it.

As for Automatix, use it at your own discretion. I don't advise it (for numerous reasons others might debate me on, mostly I just don't think its needed), I prefer using official and perfectly functional means already present in Ubuntu. For more on those see:

[Ubuntu Guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")
[Psychocats]("http://www.psychocats.net/ubuntu/")
[Ubuntugeek]("http://www.ubuntugeek.com/")
[Ubuntu Wiki]("https://wiki.ubuntu.com/")

Have a nice day. :D

---

### Post by hmg on 2007-07-07
hey, thanks.
but, now, when i try bbc, i get -
the content you are trying to play uses an audio codec that is obsolete and no longer supported. please contact the content provider about using a supported codec.
please help.

---

### Post by hmg on 2007-07-07
fixed that. yet, not able to play bbc live news.
something's wrong with streaming just that... am able to get others from the same site

---

### Post by hmg on 2007-07-08
working now without any fixing from me.
all enjoy!

---

### Post by bwallum on 2007-07-16
Hi

I'm trying to get realplayer working with BBC News streams. I can get Realplayer to run the streams by running it as a stand alone application. I can't get it to run in embedded mode. I get the error:

...can't find hxplay or realplay in the system path...

1 How do I find hxplay
2 What is the system path?
3 How do I get hxplay into the system path?


Thanks

---

### Post by starcraft.man on 2007-07-16
> **bwallum said:**
> Hi

I'm trying to get realplayer working with BBC News streams. I can get Realplayer to run the streams by running it as a stand alone application. I can't get it to run in embedded mode. I get the error:

...can't find hxplay or realplay in the system path...

1 How do I find hxplay
2 What is the system path?
3 How do I get hxplay into the system path?


Thanks

[Firefox Extension]("https://addons.mozilla.org/en-US/firefox/addon/446") for media streaming, install it and then designate whichever feeds you want to whatever clients. Will then ensure all embedded streams run fine to external apps of your choice. Hope that helps :).

---

### Post by bwallum on 2007-07-16
Thanks Starcraft.

Unfortunately we have gone backwards....now get a lot of pop up windows. Screenshot attached. What's next?

Bob

---

### Post by inter-m on 2007-08-01
Thanx for this nice miniguide... I did all the steps but I have a problem realplayer will wrok... from the terminal I typed realplay this is what I got :

Segmentation fault (core dumped)

And when I try to start it from the Applications >> Sound and Video it doesnt respond at all...

---

