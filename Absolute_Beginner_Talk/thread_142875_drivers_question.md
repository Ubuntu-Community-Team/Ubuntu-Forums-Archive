---
title: "drivers question"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by jchutcheson on 2006-03-11
Hi ... Well I finally decided to use this OS , I am a first timer with this OS and using FF , Yeah I know ? what took me so long lol , right ? :mrgreen:  Ok so now I'm curious to know , with Windows basically you needed the 4 main drivers ( chipset , audio , video , internet ) , Does this also apply for this OS ? When installing drivers , How do you tell which is for what type of Linus OS , Like for instance I like to install java but , from sun website there is 2 to choose from ( RPM and the other one ) , which one is for this OS ? Thanks

---

### Post by Koybe on 2006-03-11
No need to install any other drivers. Or yes, just one for your video card if you (and probably will) want 3D acceleration. Then it depends on your video card, you'll find many help for this on this forum or the wiki.

Then to get java, open synaptic package manager and install j2re or type this in a console :
```
sudo apt-get install sun-j2re1.5
```

---

### Post by az on 2006-03-11
Drivers work differently in Linux.

Since this is an open source distro, everything is developed in source form.  The distribution compiles everything for you and you install those packages.  So everyting comes from the centralised repositories.  

Usually, hardware is reverse-engineered to work in ubuntu when the companies who manufacture the things do not release open-source drivers for linux.  That's why you usually do not get drivers for linux in the box that comes with your hardware.


Most of your hardware will be autodetected and set up when you install.  For more advanced driver things look here. [https://wiki.ubuntu.com/BinaryDriverHowto](https://wiki.ubuntu.com/BinaryDriverHowto)

For java and other restricted formats, see here:[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

(Sun's Java is not licenced in a way that allows you to distribute it if you want to distribute other java implementations.  It is therefore not distributed with Ubuntu - it's still available and works fine, just not distributed through Ubuntu.)

---

### Post by jchutcheson on 2006-03-11
Hi ... Oh ok , Well I have to be totally honest here even if it make me look stupid and I am thankful for your assistance but , I have no idea as to what you mean , I think I should of asked is , Where does one go to learn to understand this OS as to how it works ? I am assuming this OS isn't for the average Joe ( Novice users ) like myself , Though I would like to try to understand it , Maybe someone can point me in the first stage direction , just like a baby learning to walk for the frist time ? Thanks

---

### Post by jchutcheson on 2006-03-11
I have to ask , What do I do with this >>> sudo apt-get install sun-j2re1.5  <<< ? Or where do I go with that ? Thanks

---

### Post by mstlyevil on 2006-03-11
[QUOTE=jchutcheson]Hi ... Oh ok , Well I have to be totally honest here even if it make me look stupid and I am thankful for your assistance but , I have no idea as to what you mean , I think I should of asked is , Where does one go to learn to understand this OS as to how it works ? I am assuming this OS isn't for the average Joe ( Novice users ) like myself , Though I would like to try to understand it , Maybe someone can point me in the first stage direction , just like a baby learning to walk for the frist time ? Thanks[/QUOTE]

Here go a few links that might help you in learning about Ubuntu.

[Ubuntu Guide]("http://ubuntuguide.squarecows.com/doku.php")

[Breezy Customization Guide]("http://doc.gwos.org/index.php/BreezyCust")

[Another Ubuntu Guide]("http://easylinux.info/wiki/Ubuntu")

[Ubuntu Linux Resources]("http://www.psychocats.net/linux/index.php")

---

### Post by mstlyevil on 2006-03-11
[QUOTE=jchutcheson]I have to ask , What do I do with this >>> sudo apt-get install sun-j2re1.5  <<< ? Or where do I go with that ? Thanks[/QUOTE]

You copy and paste the command into the terminal then enter your password and it will download and install that package. You have to have your sources enabled first and them guides I posted will tell you how to do all of that.

To get to the terminal go to Applications-->Accessories-->Terminal on the top  toolbar on the left side. I hope all of this information helps.

---

### Post by az on 2006-03-11
[QUOTE=jchutcheson]I am assuming this OS isn't for the average Joe ( Novice users ) like myself , Though I would like to try to understand it , [/QUOTE]

Actually, it is for the novice.

Most of the time, you install it and everything works.  You don't even have to know what a driver is...

---

### Post by jchutcheson on 2006-03-12
[QUOTE=azz]Actually, it is for the novice.

Most of the time, you install it and everything works.  You don't even have to know what a driver is...[/QUOTE]


Well thats good to know and I just learn my first lesson , I am guessing to install stuff you have to go to the "Terminal" and copy and paste , correct ? Well I try to do so for java but it came back saying something about its not there , I am curious how do you view your hard drive ? 

PS: Mstlyevil thanks so much for all those links :D

---

### Post by Mustard on 2006-03-12
[QUOTE=jchutcheson]Well thats good to know and I just learn my first lesson , I am guessing to install stuff you have to go to the "Terminal" and copy and paste , correct ? Well I try to do so for java but it came back saying something about its not there , I am curious how do you view your hard drive ? 

PS: Mstlyevil thanks so much for all those links :D[/QUOTE]

The easiest way for people to answer your questions is to see the actual command you typed in and the error message you received.  To do this you would copy and paste those things from your command line and paste them in here.  Normally you enclose this type of 'code' in special forum codes, like this...
 [noparse]```
 ..place your text in here...
```[/noparse].  

This makes it easy to read for us and it appear like this to us.

```
..place your text in here...
```

All installation in Ubuntu is not done by the command line, but the command line is the easiest way to explain it.  There is actually a program in your System>>Administration menu called Synaptic Package Manager.  Most things can be installed using this graphical interface.  Telling someone to click here, then select this menu, then click here is quite a long drawn out process, so its often easier  to just tell someone how you would do the same thing via the command line.

I would mention also that when you first install Ubuntu, there are a few initial thing you will probably need to setup to get yourself to a point where it feels like your doing all the same things you were doing in windows.  This can seem like an insurmountable task at the time, but when you get to the other side of it then its much easier.  The problem is that a lot of common things that people use in windows, like mp3's for instance, have restrictive licences on them.  With windows the right to have these these formats in windows by default is essentially built into the price of the product.  For Ubuntu, being a free operating system, there is a bit of jumping through hoops to do before these things are setup and working.  If you read over the links above though you should be well on your way to doing some of these things, and for anything you don't understand you can come back here and ask.

---

### Post by jchutcheson on 2006-03-12
Well I am starting to get an idea , which seem to be very interesting , Thanks . I will take now a good view at those links and get a little better idea about this OS :-D 

I hope I do this right , here goes 

```
 JCH@ubuntu:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5
JCH@ubuntu:~$ 
```

---

### Post by az on 2006-03-12
[QUOTE=jchutcheson]Well thats good to know and I just learn my first lesson , I am guessing to install stuff you have to go to the "Terminal" and copy and paste , correct ? [/QUOTE]
No.  Just use synaptic.  The command line is the exception, when you don't want to install something that is officially supported or something.

[QUOTE=jchutcheson]
Well I try to do so for java but it came back saying something about its not there , I am curious how do you view your hard drive ? 

PS: Mstlyevil thanks so much for all those links :D[/QUOTE]

You need to activate the universe repository.  You do that through synaptic (or the command line, too, if you want)

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

And you use Nautilus to navigate your filesystem.

---

### Post by jchutcheson on 2006-03-12
[QUOTE=azz]
You need to activate the universe repository.  You do that through synaptic (or the command line, too, if you want)

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

And you use Nautilus to navigate your filesystem.[/QUOTE]

Hi ... Ok I went to that link where it more or less shows how its done , Though its not exactly as to what I was able to view but I still found the place , I did the update and I saw it being install , Also notice on a reboot it doesn't stay saved , Any ways I gave the installement of the universe repository another shot , did the update again , then when to try to install the java this time and I still get the same error as before in the above post , So what am I doing wrong ? Thanks

---

### Post by Mustard on 2006-03-12
[QUOTE=jchutcheson]Hi ... Ok I went to that link where it more or less shows how its done , Though its not exactly as to what I was able to view but I still found the place , I did the update and I saw it being install , Also notice on a reboot it doesn't stay saved , Any ways I gave the installement of the universe repository another shot , did the update again , then when to try to install the java this time and I still get the same error as before in the above post , So what am I doing wrong ? Thanks[/QUOTE]

Actually I don't think the sun JRE 1.5 package is part of the repositories anymore.  There are instructions for installing the latest Sun Java on this page though (see first link below).  There are different versions of Java available but the Sun JRE Java is the best one to download and install, so skip the instructions on the Blackdown Java (its too old for some applications), and skip the instructions on the Sun SDK Java (SDK is for developers of Java applications).

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

The above instructions are the standard method that most users would use to install Java.  There are are other options.

Some people might have even more 'unofficial' repositories, but as a general rule its not advisable to use them, unless you know what you are doing.  One of these 'extra' repositories are those provided by a fellow who goes by the nickname Seveas from the Netherlands.  It is possible to just browse to a repository via a web browser and simply download the package to your computer locally and install using a dpkg -i packagname.deb  command to install the package.

[https://wiki.ubuntu.com/SeveasPackages](https://wiki.ubuntu.com/SeveasPackages)

Seveas has a Sun JRE 1.5 package all made up in his repositories, so its quite feasible to download that and install using a dpkg command.


-edit-

I'm going to be in the IRC support channel for a couple of hours, so if you want, hop onto IRC using the xchat IRC client in your Applications>>Internet menu and join the 'Ubuntu Servers' in the server list.  The actual server is irc.freenode.net  and the channel is #ubuntu.  If you type my IRC nickname, which is mustard5, it should set off my nick notification and make my IRC start flashing etc and alert me to your presence. :)  I can walk you through this part if you want some realtime assistance with it.

---

### Post by jchutcheson on 2006-03-12
Mustard >>> I will set up a account on IRC chat on a other day , Its just a little to much at the moment to grasp lol but I am getting there , I'm trying not to learn to much at one time , This way I can remember what it is that I did learn LOL , Thanks though for the thought of helping me there ... Its just this java is starting to drive me nuts here lol Ok here where I am stuck , The site say to save it on the hard drive and I have added the image as to what I should select , Also it mention to do this as well 

You must first accept the licence, then click on &#8220;Linux self-extracting file&#8221; (jre-1_5_0_06-linux-i586.bin). Save this file to your hard drive.

Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type 

I like to know where or how do you go about making this change , Where is this command lind ? Thanks goes to everyone in helping , MUCH APPRECIATED !> [QUOTE][QUOTE][/QUOTE][/QUOTE]

---

