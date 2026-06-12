---
title: "dial up connection"
date: 2006-02-27
forum: Absolute Beginner Talk
---

### Post by kcampbell26 on 2006-02-27
I'm wondering if anyone can give me detailed instruction on how to establish a dialer for an internet connection.  I have a POP3 server thast requires a user ID and password to log on.  I also have a compatable modem (US Robotics) and a local access number.  I don't  see any type of utility like those found in windows that makes this a simple task.  Thanks in advance.

---

### Post by Bartender on 2006-02-27
k- 
Ineffective as dialup is for downloading the impressive amounts of data you'll need for customizing your basic install, (Automatix on dialup would be ugly) setting it up isn't particularly newb-friendly on its best day.

take a look at the lower section of this link

[https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialup%29](https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialup%29)

for some fairly brief descriptions of your options.  There are at least 3 different ways and if you type "wvdial" "ppp", and "modem monitor" or "modem lights" into Search you'll find lotsa posts.  BTW, what the Wiki calls "Modem Lights" is called "Modem Monitor" on my Breezy install.  Maybe "Lights" was its name in 5.04?  Don't know but that little detail didn't help out any.

Although my ISP won't work with Linux (long story) I was able to install Modem Monitor.  Bought 2 external Sportster 0701's on ebay, and tried them both out (one at a time of course!).  They dial out, make a bunch of noises, and appear to be trying to connect when I activate from the red phone icon that Modem Monitor installs in the upper panel.  

There is no newb-friendly procedure like in that other OS.  Sorry

---

### Post by Mustard on 2006-02-27
If you look through the wiki link provided in the previous post, down the bottom of the page is the method of connecting using pppconfig to setup, then pon and poff commands to start it up and shut it down.  Once you are online though, you can install the gnome-ppp package through the Synaptic Package Manager and it is pretty easy to use.  Its a little gui interface to wvdial that makes the whole process possible without having to visit the command line again.

---

### Post by kcampbell26 on 2006-03-02
Got the modem up and running...thanks for all the help.  Now if I can just get real player installed!!  I've found that the wiki can't be followed to the letter, but it does point me in the right direction.  Thanks again!

---

### Post by Mustard on 2006-03-02
There a a few different methods for getting realplayer installed on the wiki.  Which one have you tried so far?

---

### Post by kcampbell26 on 2006-03-03
I've tried all of them....alone and in various combinations.  In the terminal, I get a message saying there is not such file as RealPlayer.  I have downloaded it twice.  Actually, I'm not sure it's what I need anyway.  I've found that I can't play Mpegs.  I get the message that I don't have the right decoders and need to download plugins.

---

### Post by Mustard on 2006-03-03
It sounds like you are perhaps not in the right directory in terminal, or a typo with regards to the filename.

What folder did you download it to?

With regards to mpegs, you need to look at the Restricted Formats page on the wiki...

[https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

You'll find a download link on the page for w32codecs and also installation instructions.  Again you should take note of what folder you download it to, as your going to need to change the 'working directory' of the terminal to execute commands on it using the cd command.

For instance if its on the Desktop then you would need to do..

```
cd ~/Desktop
#change working directory to Desktop of current user
```

..prior to executing other commands on the downloaded package. To see what you current 'working directory' is you can use this command..

```
pwd
#show working directory
```

For some basics on using the command line try these links...

[http://ubuntuforums.org/showthread.php?t=45651](http://ubuntuforums.org/showthread.php?t=45651)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

The majority of commands in linux come with manuals available in through the command line.  For example to see the manual for the dpkg command you would type..

```
man dpkg
#display manual for dpkg
```

To exit the manual in terminal, hit the 'q' key.

---

### Post by kcampbell26 on 2006-03-04
Thanks for your patience!  It downloaded to my desktop both times.  I don't think it offered a choice on that.  Is there any  set rule on how to install software and plugins on Linux?  Mastering this is becomming an obsession! I have learned a lot in the three weeks or so that I've had it, but it's like getting a sip of water from a fire hose!

---

### Post by Mustard on 2006-03-04
[QUOTE=kcampbell26]Thanks for your patience!  It downloaded to my desktop both times.  I don't think it offered a choice on that.  Is there any  set rule on how to install software and plugins on Linux?  Mastering this is becomming an obsession! I have learned a lot in the three weeks or so that I've had it, but it's like getting a sip of water from a fire hose![/QUOTE]

A lot of the flexibility of linux is great, but on the flip side of the coin flexibility can lead to complexity.  There is simple way of installing most software, that is by using the nice graphical user interface called Synaptic Package Manager which is in your System>>Administration menu.  For those that prefer the command line the apt-get command does basically the same thing as opening up the Synaptic Package manager but without the GUI.   Synaptic/apt-get is the way most things should be isntalled on your system.  The packages are known to work on your system, will not break your installation and its very easy to remove them afterwards.  Synaptic will make you aware of when upgrades are available and tell you when two applications conflict with each other as well as other great features.  The versions of the software available through Synaptic are updated at regular intervals and if you are patient the version you want of a particular application will eventually be available in a future upgrade. The only real complication with Synaptic and apt-get is that there  are repositories that are maintained by the ubuntu developers themselves and there are repositories maintained by the 'community'.  The community repositories are not enabled by default.  They are know as the universe and multiverse repositories.  Instructions for enabling them abound throughout the forum.  They can be enabled through the Synaptic repository preferences.

Now we come to the flexibility part.  Your not limited to just using the packages available in the online repositories through Synaptic, you can go out there and find the latest version for yourself.  This is when it starts to become more complex.  You can find newer .deb packages, or convert .rpm packages (rpm's are installation packages from another version of linux) or even find the source code for the latest version and compile from source.

There is another added layer to this situation.  Applications that have non-free licences, such as proprietory licences are not included in Ubuntu by default, or it would be necessary for royalties to be paid or some other complication with the licence conflicts with the goals of Ubuntu.   Ubuntu's goal is to be free to the user, so these packages/applications are not available in the usual online repositories.  The issue for the user is, that a lot of these 'restricted formats' are just the ones we want to have installed.  This is why getting mp3, mpeg's, avi's, realplayer, Sun java and others requires a bit of knowledge and jumping through hoops to get them installed.  This is a hurdle for the new user to overcome, but on the flip side Ubuntu remains free to all because of it. You can get linxu distributions which you pay for, that have these things installed already.  It's just something that as an Ubuntu user you go through because you like what Ubuntu is trying to do. :)  

I hope this clarifies a few things for you and hopefully I have explained it accurately.  I'm sure someone will correct me if I have erred in my explanation. :D

Here is a link to a guide in pdf format, created by a forum member, that includes some information on ways of installing things on Ubuntu. [http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf](http://ubuntu.xgn.com.br/ubuntu_user_guide.pdf)

---

### Post by kcampbell26 on 2006-03-06
I understand your point completely, and frankly, I'm enjoying the cahllenge and frustrations presented by UBUNTU.  I managed to get real player installed along with Mozilla M-player.  I also downloaded and installed (I think) the codec package for Totem, altho it still doesn't seem to want to read the mpegs.  Here's a new problem that came up suddenly.  My floppy formater won't work.  The error message simply says it can't initilalize any device and can't proceed.  Oddly enough, I can now read and write to a floppy, which I couldn't do before this happened.  That is to say, the disk has to be already formatted by windows!  And by the way, thanks again for the interest in my petty questions.  What part of oz are you in?

---

### Post by majikstreet on 2006-03-06
Glad to see you got your dial up working... I just wanted to chime in and say that you'd probably get more responses to your other questions if you made seperate threads for them..

enjoy ubuntu :D

---

### Post by Mustard on 2006-03-07
[QUOTE=kcampbell26]I understand your point completely, and frankly, I'm enjoying the cahllenge and frustrations presented by UBUNTU.  I managed to get real player installed along with Mozilla M-player.  I also downloaded and installed (I think) the codec package for Totem, altho it still doesn't seem to want to read the mpegs.  Here's a new problem that came up suddenly.  My floppy formater won't work.  The error message simply says it can't initilalize any device and can't proceed.  Oddly enough, I can now read and write to a floppy, which I couldn't do before this happened.  That is to say, the disk has to be already formatted by windows!  And by the way, thanks again for the interest in my petty questions.  What part of oz are you in?[/QUOTE]

I'm from Queensland. :)

As mentioned by majikstreet, its probably better to start a new thread for each particular problem so that they can be handled separately.  People will be coming into this thread drawn in by the subject of a 'dial up connection' and may not know the answers to your other questions.

---

