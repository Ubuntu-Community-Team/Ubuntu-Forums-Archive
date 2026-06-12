---
title: "First Time Using Linux or Ubuntu, got alot of questions."
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by rjmrjm on 2007-07-24
hello im a first time ubuntu user that came from vista premium legit. i have some questions that could be answered thats not too hard for a noob. I am NOT going back to windows.
1) how do i install my nVidia graphic card which is 6600.
2) how do i install steam? i tried looking at threads.
3)whenever i try and use terminal and i use sudo it asked me for a password?
4)how do i install beryl?

Thank you and i would really perfer answers in noob.

---

### Post by Sef on 2007-07-24
What version of Ubuntu are you running?  Feisty, Edgy, Dapper?

---

### Post by rjmrjm on 2007-07-24
feisty ubuntu looks great so far.

---

### Post by lemonseed on 2007-07-24
All I had to do for my NVidia drivers was go to System > Administration> Restricted Drivers Manager and put a check for [x] Enable. As far as "sudo" asking for a password is because the command itself is granting you admin rights, so the password is part of it's security since you will possibly be changing system files.

---

### Post by Sef on 2007-07-24
> 1) how do i install my nVidia graphic card which is 6600.

System > Administration > Restricted Drivers Manager


> 2) how do i install steam? i tried looking at threads.

I don't know.   Someone else will have answer that one.


> 3)whenever i try and use terminal and i use sudo it asked me for a password?

That is correct.   Sudo gives you temporary administrative rights.


> 4)how do i install beryl?

Try System > Preferences > Desktop Effects

---

### Post by meborc on 2007-07-24
3) well... doing "sudo" will need your account password... just type it, you will not see it for security reasons... just type it and hit enter

---

### Post by splintercellguy on 2007-07-24
To install Steam, you'll need Wine, a compatibility layer for running Windows applications on Linux. Use this link to obtain the latest Wine version: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

Directions for installing Steam after installing Wine are here in this AppDb entry: [http://appdb.winehq.org/appview.php?iVersionId=1554](http://appdb.winehq.org/appview.php?iVersionId=1554)

For the tahoma font the instruction mentions, just install the msttcorefonts package from the Ubuntu repo.

---

### Post by KyleBrandt on 2007-07-24
If you are doing a bunch of administrative stuff, and don't want to keep typing sudo.  Just type "sudo -i".  Then "exit" when you are done.

---

### Post by swoskow on 2007-07-24
Welcome - everyone has lots of questions when they first start because Ubuntu is not Windows and most people come from a Windows background.  Try to read some of the WIKI and familiarize yourself with the basics (how to install programs, file permissions etc.) their are a number of good sites to help.  It will make your experience much better.  I also recommend a few web sites that have very good info - Lifehacker ([http://lifehacker.com](http://lifehacker.com)) and twomadgeeks ([www.twomadgeeks.com](www.twomadgeeks.com)).  If you are using firefox thier is also a Ubuntu Forum add on that places links to the forums right in the Firefox toolbar - very helpful.

To answer your questions.

1.  This should help with installing NVDIA [http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499)

2.  To install Steam go to Synaptic (System>administration>Synaptic package manager). Read about how to use Synaptic and aptitude - you will need these.  First in Synaptic start by making sure you have the repositories checked.  Open synaptic go to settings>repository and on the Ubuntu software tab check all the boxes in the download from the internet section.  Repositories are where you get programs.  You may need third party repositories for some programs.

3. Sudo always requires a password.  It is somewhat of a pain in the rear but it is a safety feature that stops unauthorized people from accessing your computer.  When it asks for the password just type in your password and hit enter (same password you use to log in).  Once you become more familiar you may want to download a root terminal then you don't have to type sudo.

4.  Beryl can be installed from synaptic.  However, you may want to become more familiar with the basics of Ubuntu.  Make sure your graphics card is installed correctly.  The Beryl web site has very good documentation also.

Have fun - once you get used to Ubuntu you will like it.  Lots of great programs, all free and the community is wonderful.

---

### Post by rjmrjm on 2007-07-24
how do i install warcraft 3 which is in my cd drive?

and also id like to thank all of you, nice to know that ubuntu has a nice community.

---

### Post by swoskow on 2007-07-24
> **rjmrjm said:**
> how do i install warcraft 3 which is in my cd drive?

  

Some of the games do not play well in Ubuntu - I am not a gamer so I am not sure about Warcraft specifically.  You should search the forums I am sure the answer is there.  If it does not play in Ubuntu their is a program called Wine that lets you run Windows programs in Ubuntu so you may need it to run Warcraft.  Check the forums and I am sure you will find help there.

---

### Post by splintercellguy on 2007-07-24
> **swoskow said:**
> 2.  To install Steam go to Synaptic (System>administration>Synaptic package manager). Read about how to use Synaptic and aptitude - you will need these.  First in Synaptic start by making sure you have the repositories checked.  Open synaptic go to settings>repository and on the Ubuntu software tab check all the boxes in the download from the internet section.  Repositories are where you get programs.  You may need third party repositories for some programs.

Steam in Synaptic? Do you mean Wine? :) The Wine AppDb is your friend, use it :D. Warcraft III entry is here: [http://appdb.winehq.org/appview.php?iAppId=897](http://appdb.winehq.org/appview.php?iAppId=897)

---

### Post by swoskow on 2007-07-24
> **splintercellguy said:**
> Steam in Synaptic? Do you mean Wine? :) The Wine AppDb is your friend, use it :D. Warcraft III entry is here: [http://appdb.winehq.org/appview.php?iAppId=897](http://appdb.winehq.org/appview.php?iAppId=897)


I just did a search for Steam in synaptic and a program did come up - this must not be the same one he is referring to so yes Wine is the way to go - Wine is certainly your friend.  I was not sure about Warcraft so I recommended Wine but is that correct?

---

### Post by rjmrjm on 2007-07-24
i need tahoma font and i dont wanna pay 70$
someone post a link?

AND also how do i install warcraft? the link you gave me doesnt work for me.

---

### Post by rjmrjm on 2007-07-24
Remaining Problems
1)Warcraft III still doesnt work
2)Steam doesnt work
3) how do i unrar rar files.

---

### Post by Mornedhel on 2007-07-24
Do you currently have Wine installed ? If not, either grab it from the Wine website (preferably a .deb package) or install it from Synaptic (or by issuing the command : sudo apt-get install wine).

You do not need to pay anything to get the Tahoma font, it's included in the msttcorefonts package (install from Synaptic, you may need to enable the Medibuntu repositories, ask back here if you do not know how).

Warcraft III (both RoC and TFT) is rated Gold on the Wine AppDB for Ubuntu Feisty Fawn, that means it works almost as well as under Windows (I said * almost *). Once you have Wine installed, open a terminal, change the directory to the one containing the Warcraft installer, and type "wine install.exe" (or whatever the install file is). This will install Warcraft and (after a reboot, dunno why) will add a shortcut to the game in the main menu, under the Wine section.

Steam is rated Gold as well. I tried playing HL² a while ago under Wine, didn't work very well, may have improved since. Same procedure.

For your unraring needs : there's a package called unrar-nonfree I think, get it via Synaptic, and you will be able to unrar files by calling "unrar e yourfilehere.rar". This takes care of RAR v3 (unrar-free does not handle v3 well at the moment, I believe).

---

### Post by rjmrjm on 2007-07-24
i dont know anything about repositories

---

### Post by PryGuy on 2007-07-24
> sudo aptitude install rarwill do also. This will add rar support to the archive manager (file-roller).

As for the Steam and WarctaftIII - Linux (Ubuntu) is not Windows. Generally speaking, there are many Windows applications that you will never be able to launch with wine or some other application. So if you're a gamer - dual boot is the best option for you I think.

---

### Post by Mornedhel on 2007-07-24
OK, let's start with a repository-enabling tutorial.

If you haven't already enabled the Universe and Multiverse repositories, let's walk through that.

In a terminal, type :
gksudo gedit /etc/apt/sources.list

And whenever you see a line that starts :
deb [http://some_url_here.com/](http://some_url_here.com/) feisty-something[FONT=Tahoma] main restricted

add "universe multiverse" (without quotes) at the end of the line.

Add the line :
[/FONT]deb [http://fr.packages.medibuntu.org/](http://fr.packages.medibuntu.org/) feisty free non-free
somewhere in the file, preferably the end so it doesn't get cluttered. Medibuntu is a repository for copyright-touchy stuff (MS fonts, complete DVD support, wmv codecs, etc.).
[FONT=Tahoma]
Save the file and exit gedit. [/FONT][FONT=Tahoma]Now you need to authenticate the Medibuntu repository so you don't get a warning every time you update your repositories :
wget -q [http://fr.packages.medibuntu.org/medibuntu-key.gpg](http://fr.packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
(taken from the Medibuntu website, I used to do this in two steps from Synaptic, but oh well)

Now, still in the terminal : sudo apt-get update

And you finally have all repositories enabled. You may now play with Synaptic to get almost anything you'll ever need.
[/FONT]

---

### Post by rjmrjm on 2007-07-24
1)Warcraft III still doesnt work
2)Steam doesnt work
3) how do i unrar rar files.

ive learned so much ubuntu rocks.

---

### Post by Eddy Dean on 2007-07-24
Warcraft works in Wine (which acts just like an emulator, although it's not exactly). You will have to learn how to work in Wine and how to install software in it. The wine site gives a lot of information on how to install and run software, I recommend you read it before trying to install anything in Wine.

---

