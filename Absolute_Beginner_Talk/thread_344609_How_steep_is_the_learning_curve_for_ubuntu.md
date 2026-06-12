---
title: "How steep is the learning curve for ubuntu?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by b9anders on 2007-01-23
I installed xubuntu on my pc yesterday with no previous experience of Linux, but a fair bit of experience tweaking around in windows for a layman anyway. I have no problems getting to know systems and programs by just playing around with it, but I have to say the reliance on knowing code surprised me, given the reviews I have read saying how Ubuntu had beome accessible to the common pc user. So many programs and tweaks require code writing to install or configure properly I find myself being a bit overwhelmed by it all right now and wondering whether I should drop it and check back in three years to see if Linux has become more userfriendly by then.

What seems to be basic stuff like compiling and making installs is something I have found myself completely clueless about, I still don't understand the concept of root commands or how I can use them properly (i'd go for just opening a root terminal in appfinder, but I can't seem to navigate via the terminal properly either) and why the primary user can't have full access to the system by default.

I've tried tweaking Unthar for network access which took 45 minutes, and still doesn't work consistently. And I don't have the rights to alter the writing and reading settings for the folder which I think is causing the problem (creating another user and logging in with that seems to work though).

installing Wine, let alone using it, I simply had to give up on as it was all code and I wasn't having any luck installing it properly trying to follow the instructions.

I tried installing acpi4asus-0.32 so I could use the special keys for my asus and such, but again, found myself at loss how to work it beyond compiling it (what is compiling anyway that it needs to be different from simply installing?) as the initial commands didn't work.

Other tweaks I have tried to set up because of my service provider (shared network and internet connection) didn't work writing the commands they tell me to, so I surmise that xubuntu uses different commands than ordinary ubuntu.

I don't think it's unrealistic of me to expect to be able to install programs adjusting the systemon a supposedly now userfirendly system without having to learn a new language. Am I just unlucky in running in to unfriendly applications, is the hurdle in front of me much lesser than it appears right now or do I just have to accept that Ubuntu has a steeper learning curve than marketing suggests and come back in a few years when the code language is hidden away to be used only by those who like it that way?

It's a shame because there are a great many things I like about the system and much of it is very intuitive and user-friendly. Right now it doesn't seem worth the hassle to switch from windows though.

---

### Post by nhandler on 2007-01-23
Most applications you don't need to compile by hand. There is a synaptic package manager that will give you a gui where you can find and install any application you want. You can launch it with this command:
sudo synaptic


If you know the name of the package you want to install, you can install it from the terminal with:
sudo apt-get PACKAGE-NAME-HERE


But to answer your question, installing applications shouldn't be too hard. The terminal is used so that people like me can tell you to enter a command or two into the terminal instead of trying to guide you through the menus (which may be different). For me, I find installing software a ton easier than doing it on windows. Hardware, that is a different story.

---

### Post by tribaal on 2007-01-23
Yeah basically using Synaptic, installing software is just a point-and-click experience.
You'll find Synaptic in "System > Administration > Synaptic package manager".

- trib'

---

### Post by buuntuu! on 2007-01-23
don't give up!
i just switched from windows a little while ago and can assure you: learning ubuntu is fast and fun!
i triedthe xubuntu live cd and found it a little less friendly than ubuntu, so if your hardware supports it you might want to consider changing...
even if you need to use the command line once in a while, the forums are great, somebody WILL help and there are numerous howtos around, especially for the classic ubuntu-distro. as i am a newb, for me this is reason number one for choosing ubuntu over the other flavours.
check out psychocats.net for the basics

---

### Post by btolle on 2007-01-23
Whoa! Sounds like you are diving off into the deep end before you got your feet wet.

Do a fresh install and stay away from the command line until you are familiar with the GUI.

I am a total Linux newbie and installed Ubuntu Edgy last week and have been feeling my way through it in my spare minutes.

So far, I have most things working including setting screen resolution, printing, and networking and have never used a command line. That is the best part of Ubuntu, for a Windows user the Graphical User Interface make Ubuntu very easy to transition to.

Take it easy and use the GUI to get your system up and running.

I am not afraid of the command line since I started out before Windows was ever thought of but I am not in a hurry to go back to it until absolutely necessary.

If you start reading any Linux forum you will see lots of posts about using the command line. Just ignore them and I will explain why:

This morning I started my Ubuntu system while doing some other things and let it come up by itself. When I got back to it the screen resolution was back to 800X600 when I had been running in 1280X1024. My first reaction was to go to the forums and search on "screen resolution" where I pulled up a post that had about 6 responses and all of them wanted the user to post all sorts of configuration files and start changing things using the command line.

Reading the responses was frightening!

Once I calmed down and gave the problem a little logical thought I simply rebooted the system and stayed with it as it came up. I selected the first item in the GRUB menu listing when it came up and everything was back to 'normal'. My screen resolution was back to 1280X1024.

Old habits die hard and unfortunately I have seen a tendency in the Linux community to revert to the command line immediately when a problem arises. The whole point of a Graphical User Interface is to make the system easy to use and so far I am very impressed with the GUI in Ubuntu.

Reinstall and try using the GUI for a while. I have installed updates and additional programs and haven't been near the command line yet.

---

### Post by xpod on 2007-01-23
As practically a complete pc noob with only 4 months on a pc before destiny brought me here i can assure you that Ubuntu(the basics at least) is no harder to learn than what sitting down at a Windows pc for the first time is........Easier probably as you dont need to learn a whole heap of nonsense just to be safe using the thing.

6 months i`ve used Ubuntu now and other than a couple of lines in my xorg thingy for beryl there hasn`t been one thing that has required me to use obscure lines of code etc.

Of course i do use the terminal for a few things but not because i need to....i`ts just so much quicker once you get your head round it.

Given time and patience you will surely see for yourself why this is just sooo much better than that other thing......imho

---

### Post by mikewhatever on 2007-01-23
The learning curve, or the amount of hardship, really depends on your expectations. You may have read good things about Ubuntu, written by those trying to promote it. They usually tell how great it is, and do not always tell about the drawbacks. Another mistake is to rely on Windows experience. It doesn't help here. If you find thing difficult to install or configure, search for howtos or use one of the guides. Wine may be not the thing I'd install first.
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
Good luck

---

### Post by Medieval_Creations on 2007-01-23
I would agree Synaptic is definately the best place to start.  I would dare say that every program that a new user would need is in the repositories.  Once you become more familiar with Linux and the command line you can start playing with customizing application installs.

One other option to install some frequently used software is Automatix.  You'll get mixed reviews about it, but it does do it's job.  I admit that I been lazy and used it a couple of times.  :)

Link: [http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by b9anders on 2007-01-23
I did use synaptic to install programs like openoffice, etc. and it was a snap. It also says that I have installed wine but I can't seem to find the program anywhere. appfinder doesn't seem to want to recognise it.

---

### Post by Sef on 2007-01-23
The terminal should be learned little by little.   The easiest way commands to do are the update commands.  Open the terminal (Applications > Accessories > Terminal):

then 

```
sudo aptitude update
```

then 

```
sudo aptitude upgrade
```

Also besides synaptic, there is Applications > Add/Remove.

---

### Post by tagra123 on 2007-01-23
Since you are just getting started you might prefer to use CrossOver Office instead of wine. It'll keep you off the command line and let you be productive.

The other program is VMPlayer or VMServer to install windows as a Virtual MAchine.  There are how tos here in the forum and on google. 

EasyUbuntu is another one I'd recommend for a beginner.

---

### Post by wh0rd on 2007-01-23
Start here. It answers a lot of questions:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

Install Automatix:
[http://ubuntuguide.org/wiki/Ubuntu:Edgy/Repositories#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu](http://ubuntuguide.org/wiki/Ubuntu:Edgy/Repositories#How_to_install_Automatix2_on_Ubuntu.2C_Kubuntu.2C_and_Xubuntu)

If you like tweaking, then Linux is for you.

---

### Post by hyper_ch on 2007-01-23
After you have installed wine you need to open a terminal and execute the following command:
```

winecfg

```
--> that will create a fake windows drive in your user's home location... and you will then get a window with some configuration options... once that is done... you can wine use just like:
```

wine winamp.exe

```

The wine binary will be in the path so you will have to execute that command where you have some .exe located...

e.g. wine /home/user/Desktop/winamp/winamp.exe

---

### Post by Darko Beta on 2007-01-23
I recommend automatix to get things installed if you are extremely frustrated.  When you have the time, it can be fun to learn other ways, but if you just want to get some things up and running--go automatix.

---

### Post by _simon_ on 2007-01-23
As well as Automatix there is also EasyUbuntu: 

[http://easyubuntu.freecontrib.org/overview.html](http://easyubuntu.freecontrib.org/overview.html)

Ubuntu is user friendly, you just have to realise that it's not Windows and won't act like Windows. It took me a good 3 months to be fully comfortable with Ubuntu. How much time, effort and how quickly you can grasp things will influence how long it takes you.

---

### Post by Khepri on 2007-01-23
I know what you mean...as I ran into the same bewilderment with my full blown Debian install...I was in over my head...LOL

Hence I have installed Ubuntu next to it...believe me, this is a breeze compared to Debian learning curve-wise...

I may be at an advantage though as I found the commandline to be familiar territory from my DOS days...and I did not really understand Linux until I got on the commandline...

The thing I'm having trouble with still...and you seem tobe also...is the package management and the dependencies issues that some up...this I'm completely unfamiliar with...but the longer I stick with it the more comfortable it becomes...

Honestly...I decided to take the hard road with Debian on purpose and found Aptitude to be a complete nightmare for a noob!...lol

Apt-get was far easier to work with...and Synaptic has been a dream come true...

Although I find my experience with install manaully on Debian was a big help later I soon realized I seemingly created dependncy conflicts by going outside the package managers..

These I have no clue how to resolve as yet...but will someday I imagine....

I'm yammering...later...

Khepri

---

### Post by b9anders on 2007-01-23
Thanks for the pointers, guys. I am determined to get the hang of this, so I hope you will be patient as I will be using this board for all my noob questions and I have a lot of them!:D :( :roll:

---

### Post by jvc26 on 2007-01-23
Thats what we're here for :) I hope you can get your problems worked through :)
Il

---

### Post by ardchoille42 on 2007-01-23
Learning curve? I started using Linux in 2001.. started with Fedora Core I believe. Then I had switched to other distros. When I installed and began to use Ubuntu (then warty), I almost got rid of it because it was too easy - there wasn't much to do on it and I like to tinker. But, I kept it because it was super-easy. Now, I'm glad I kept it because I feel it is the easiest distro around.. not to mention it has huge repos and I can do more on it than I did in Windows.

---

