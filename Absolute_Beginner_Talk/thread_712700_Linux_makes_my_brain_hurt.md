---
title: "Linux makes my brain hurt"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by iwannabealinuxuser on 2008-03-02
Hello,

I am totally totally new to Linux (Ubuntu) I installed it on my laptop last night and ran my updater and upgraded from 7.04 to 7.10 so far I have only used Internet and Word Processor.  So basically I have only skimmed the GUI because I have a major problem.  I do not know how to work Linux what-so-ever.  I do not know any command lines/programming. I used to know a very little bit of visual BASIC but have forgotten it.  So without being able to use Ubuntu which I so badly want to master I need some advice on my first problem.  Right now my audio is not working although surprisingly Ubuntu auto-detected and installed my graphics and wireless drivers as far as I know.  So what do I do because I do not know where to find a Conexant High Definition Audio driver for my HP dv2315nr laptop, nor do I know how to install drivers.  My friend who is more experienced in Linux said something about having to go into the command line locating the driver, connecting it with the device, then defining the capabilities. He's a mac fan so afterwards he went on some rant about how OS X is so superior to all other computers which was expected. Of course I do not understand any of his Linux answer.  

I am not complete jackass in the ways of the computer because I can operate OS X and Windows pretty well.  Also I have built my own pc twice, so I know a good amount about basic computers; a little over the average computer user I guess. I can operate pretty well through GUIs but have never bothered learning windows or mac command lines so I lack a significant amount of knowledge.  So I want to attack command lines and programming head on by learning Linux which I've actually wanted to do for awhile.  My reason is because I want to make robotics my future career so I need to learn how to do this stuff regardless. So please help me first get my audio working, and then can you give me some kind of guidance as to how to get on the right path.  Right now I'm looking at linuxcommand,org should I be doing that or is there something better that you guys recommend?

Sorry for the life story,

J0330H

---

### Post by NightwishFan on 2008-03-02
If you are using Ubuntu you will find that Linux is only as hard as you want it to be. You can keep to the basics, or tweak on your own. Someone should be able to fix your problem with the audio as well.

Edit: Oh yeah, I forgot. Welcome to the community. ^^;;

---

### Post by HermanAB on 2008-03-02
Start by reading all the stickies at the top of all the forums.  You will likely find the answer after a while.

Cheers,

Herman

---

### Post by iwannabealinuxuser on 2008-03-02
Like I said, I really have no clue what to do

---

### Post by NightwishFan on 2008-03-02
Please try the search feature. It may be able to help find someone with a similar problem. Also someone will likely be able to help you here soon enough. I am sorry I can not be of help, my audio has always worked by default for me. Only thing I would like to ask is:

Volume not muted? (Just in case, it has happened to me before) Also if the sound worked in the live cd or not, although you likely did not use sound then.

---

### Post by justsomedude on 2008-03-02
If you want to dig into robotics, this should be a walk in the park for you:

[http://blog.ifitcangowrong.com/open-source/linux/ubuntu/configure-the-hp-dv2000-for-ubuntu-sound#more-51](http://blog.ifitcangowrong.com/open-source/linux/ubuntu/configure-the-hp-dv2000-for-ubuntu-sound#more-51)

---

### Post by pissedoffdude on 2008-03-02
Go to applications>accessories>terminal and copy and paste the following:
```
aplay -l
lspci -v
```
Then post the output of it

---

### Post by Irihapeti on 2008-03-02
Have a look at [www.psychocats.net](www.psychocats.net) . It's a great resource for Ubuntu beginners. Also the offline help file in Ubuntu (the help icon at the top of the screen) has lots of info on basic (and not so basic) things - and it seems to be fairly well written.

---

### Post by 3rdalbum on 2008-03-02
The command-line is just a different way of running different sorts of programs; it's nothing to do with programming, so you can safely forget all your lessons in Visual Basic if you haven't already. If you do want to learn actual programming, I recommend taking a tutorial of Python.

And, it's not surprising that Ubuntu has already set up your graphics and wireless cards. That's what it's designed to do. But I'm delighted that you were surprised by the friendliness of it!

There is a good wiki page about audio troubleshooting: [https://wiki.ubuntu.com/DebuggingSoundProblems]("https://wiki.ubuntu.com/DebuggingSoundProblems")

I had to follow it once when my friend's laptop audio didn't work. If you end off having to compile a new version of ALSA (like I did!), and you get stuck, feel free to send another forum topic or an IM to me.

---

### Post by iwannabealinuxuser on 2008-03-02
ok guys i turned off my laptop (this is the third time since i've installed ubuntu) came back around 2 hours later and... suddenly sound works. I'm really confused, also my wall paper was changed, I checked to see if I accidentally booted into a safe mode or something but I restarted and sound is still working. Anyone care to explain?  Also thank you so much for the contributions to the robotics and guides : ).  During the process before sound worked, my previous session, I experimented a bit with the command line, and tried installing some beta driver but I could've sworn it failed and I messed with my sound preferences but that didn't seem to do anything either during the last session.

---

### Post by justsomedude on 2008-03-02
> Anyone care to explain?

Updates. Ubuntu is smart and spiffy. Enjoy.

---

### Post by iwannabealinuxuser on 2008-03-02
yes but I already ran the update manager one last time before I shut down and it told me I was already up-to-date so why would the sound just decide to kick in now? also, that doesn't explain why my wallpaper changed.  I apologize if I seem rude.

---

### Post by justsomedude on 2008-03-02
Did you get a notification about restricted drivers being available?

Maybe sound was just turned off in alsa.

Or, your attempts to get it running weren't so unsuccesful after all. If you successfully install a driver, it is likely to work in the next session.

---

### Post by iwannabealinuxuser on 2008-03-02
> **justsomedude said:**
> Did you get a notification about restricted drivers being available?

Maybe sound was just turned off in alsa.

Or, your attempts to get it running weren't so unsuccesful after all. If you successfully install a driver, it is likely to work in the next session.

The only restricted drivers I have are wifi and graphics which I've had on since the beginning.

---

### Post by jflarm on 2008-03-02
You could try this on a terminal:
more /var/log/messages
The file /var/log/messages has many messages about what happens within your computer, maybe you could see something about your sound card.

To go pages down just press the space bar or the arrow key, and to go back the "b" letter lowercase. To quit just press "q" and you will be again in your prompt.

---

### Post by Presto123 on 2008-03-02
> **iwannabealinuxuser said:**
> yes but I already ran the update manager one last time before I shut down and it told me I was already up-to-date so why would the sound just decide to kick in now? also, that doesn't explain why my wallpaper changed.  I apologize if I seem rude.

Two questions:

1) Did you just restart or totally shut down from your last Windows session? Or are you dual-booting at all?

2) Did you set your wallpaper from Firefox or move the wallpaper into a different file?

---

### Post by iwannabealinuxuser on 2008-03-02
ok well now I'm trying to install beryl (am I in over my head?) and I downloaded the beryl core.tar.gz file off their website, but not sure how to install

---

### Post by Presto123 on 2008-03-02
> **iwannabealinuxuser said:**
> ok well now I'm trying to install beryl (am I in over my head?) and I downloaded the beryl core.tar.gz file off their website, but not sure how to install

Compiz is already installed by default...you don't need Beryl.

---

### Post by iwannabealinuxuser on 2008-03-02
how do i configure compiz?

---

### Post by jflarm on 2008-03-02
System--->Preferences-->Appearance
Go to Visual Effects and enable them.


[http://ubuntuforums.org/showthread.php?t=659317](http://ubuntuforums.org/showthread.php?t=659317)
This was a guide someone made for his customizations, but you could try the Search function in the forum and find something easier for a beginner (this one is not hard, but...).
Hope this helps you!!

---

### Post by Presto123 on 2008-03-02
Go into Add/Remove and search for "Compiz". Download the first program named "Advanced Desktop Effects Settings". When that is installed, go into System/Preferences/Advanced Desktop Effects and enjoy.

One thing, If you want the cube, I would make sure that you enable "Rotate Cube" and "Desktop Cube". Click on "General Options" and in the Desktop Size tab, change the Horizontal Virtual Size to 4. At that point, you should be able to push in your scroll wheel on your mouse (if you have one) or use CTRL+ALT+Button 1 and see a full cube.

---

### Post by iwannabealinuxuser on 2008-03-02
how do you make a custom cube, and I thought Beryl and compiz were two different things

---

### Post by jflarm on 2008-03-02
Beryl is old...now it is compiz.
Open the "Synaptic Package Manager" and install this packages:
compiz
compizconfig-settings-manager
compiz-core
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-gnome
compiz-plugins
emerald
libcompizconfig0
libcompizconfig-backend-gconf
libemeraldengine0
libdecoration0
python-compizconfig

It is easier through the command line:

sudo apt-get install compiz compizconfig-settings-manager compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins emerald libcompizconfig0 python-compizconfig libcompizconfig-backend-gconf libemeraldengine0 libdecoration0

This are the packages I have installed. After you finish, then go to System-->Preferences-->Advanced Desktop Effect Settings
There you can find your cube and many other effects.

---

### Post by aparabola on 2008-03-02
Hey there iwannbealinuxuser,

I am right there with you man and share your pain on the vast amount of what adds up to be a huge pile of fluffy nothingness when it comes to the "terminal" or the "command line." I just wanted to jump in here real quick to let you know, wait, to remind you, no, wait, I wanted to re-assure you, yeah, that's it, re-assure you that you're not the only one who is stumped yet has a deep yearning for the good graces of all things geek, as in penguinitis maximus fatal...lol. Doode, I'm right there with you bro...right there. So there we be.

Good Luck...to *us*...  :confused:

---

### Post by iwannabealinuxuser on 2008-03-03
> **aparabola said:**
> Hey there iwannbealinuxuser,

I am right there with you man and share your pain on the vast amount of what adds up to be a huge pile of fluffy nothingness when it comes to the "terminal" or the "command line." I just wanted to jump in here real quick to let you know, wait, to remind you, no, wait, I wanted to re-assure you, yeah, that's it, re-assure you that you're not the only one who is stumped yet has a deep yearning for the good graces of all things geek, as in penguinitis maximus fatal...lol. Doode, I'm right there with you bro...right there. So there we be.

Good Luck...to *us*...  :confused:

good to know

---

### Post by zabien1970 on 2008-03-03
Just reading through this, your sound issue coulda been an update which didn't take till you restarted, fixed now so let's move on.
Beryl was the old special effects programs but has been replaced with compiz (same game different name), have you gotten it working yet?

---

