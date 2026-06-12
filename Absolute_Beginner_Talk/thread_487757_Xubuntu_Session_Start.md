---
title: "Xubuntu Session Start"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Nimaran on 2007-06-29
Ok, I am new to Linux and I've only started using it. This morning I wanted to boot into and everything popped up, I typed in my user and password, and my mouse flashing splash came, that kind of cut short and then a blue screen appeared, not a hideous bright blue, but the color gradient of my desktop and my mouse pointer that is all, I didn't know what to to I hit ctrl alt back tried agin no difference, so I'm not sure what to do. I do have beryl, but it's booted in fine before. The only problem was when shutting down last night it wouldn't close so I hit ctrl alt esc and clicked with the skull and crossbones, it waited a minute and then a black screen with a bunch of text popped up more than usual, I don't remember what it said, then it shut down. I WANT MY LINUX WORKING, umm.. sorry. Any help with this issue would be great, I do like Linux, but if I can't get to it what use is it. Please help.

-Thanks in advance,

-Nimaran

---

### Post by Rocket2DMn on 2007-06-29
Sounds like it could be a problem with Beryl.  Have you tried booting into a different desktop session (not Beryl).  Your options are at the bottom left of the login screen.

---

### Post by Nimaran on 2007-06-29
I tried booting into new Xfce session, but with no luck. Of course beryl is set to start up when I log on. I don't get what its problem could be it was working fine.

---

### Post by Rocket2DMn on 2007-06-29
Selecting a different window manager before login should get you around the problem, but you can reconfigure your video stuff from scratch by running the command
```
sudo dpkg-reconfigure xserver-xorg
```
This will take you through a dozen screens or so that will help you reconfigure your hardware (most importantly, the video stuff).
You should be able to get to a virtual terminal from the login screen by hitting CTRL+ALT+F2.  There are 7 terminals available (F1-F7).  This is where you can do the reconfiguration since you can't login to the GUI.

---

### Post by Nimaran on 2007-06-29
Sounds scary but I'll give it a try. I don't know any code so terminals won't be able to help besides that command. Thanks.

---

### Post by Rocket2DMn on 2007-06-29
Most of it is just hitting Enter on your way through, but you should read the stuff (to an extent) so you know what's going on.  When you get to screens with different options you can hit TAB to cycle through them and SPACEBAR to select them (like on the page where you select resolutions - in this case you should select your max resolution your monitor supports and everything less than it.)
It's pretty self-explanatory, just take your time and do it right the first time.

---

### Post by Nimaran on 2007-06-29
No luck, I tried it. It asked a lot of complicated questions, then it got to something about color-bit and I tried answering it, but the terminal came up and said something about overwriting something, and I had no choice, but to restart the computer and boot into Linux, my resolution looked smaller or bigger... all the images were slightly larger, but I still couldn't log on, please someone help I don't want to give up on Linux.

Thanks

---

### Post by Rocket2DMn on 2007-06-29
OK, so if it's not the session/window manager or the xserver configuration, I'm rapidly running out of ideas.  Unless somebody has a better plan, it might be worthwhile to reinstall xubuntu-desktop.  Wait a few minutes to see if anybody has other suggestions, then let's try to reinstall the GUI stuff:
Bring yourself back to the terminal -
```
sudo apt-get remove xubuntu-desktop

sudo apt-get install xubuntu-desktop
```
(I'm assuming you want to keep using Xfce and not GNOME or KDE)

---

### Post by Nimaran on 2007-06-29
Does this require an internet connection? I haven't got that working yet, and I can't without having acess to Xfce.

---

### Post by Rocket2DMn on 2007-06-29
Err, typically it does, but if you have your install CD that can be used instead.
In the file /etc/apt/sources.list there should be an entry regarding using the CD as a repository source.  Type
```
sudo cat /etc/apt/sources.list
```
If there is a # in front of that line, you will have to remove it, otherwise you're OK.
To remove the #, you need to edit the file from the command line which means you will have to use vi since gedit is unavailable.
I'm not a big fan of vi, but here's a basic tutorial should you need it, the learning curve is steep - [http://www.cs.colostate.edu/helpdocs/vi.html](http://www.cs.colostate.edu/helpdocs/vi.html)

After you remove the # sign, you can run the commands above and to reinstall xubuntu-desktop.

Feel free to post the output of the "cat" command here

---

### Post by Nimaran on 2007-06-29
Yeah, I have the live CD, so do I boot into the CD and then do what your talking about. I apologize for my incompetence in all of this, I'm good with computers, but new to Linux. Though I'm not a programmer. Again thank you.

---

### Post by Rocket2DMn on 2007-06-29
I've never had to actually do this, but you should just be able to put the cd into the drive while the computer is running (as long as it's mounted)

---

### Post by Nimaran on 2007-06-29
Is their any other way besides reinstalling the whole OS. I mean Linux can't be that impressive if you shut it down wrong and *BAM* you have to reinstall and you lose all your files. Is their no other way?

---

### Post by Rocket2DMn on 2007-06-29
(I thought I posted a few minutes ago, but I don't see it - let me retry)
What I suggested was not reinstalling the OS, just the GUI stuff - all your other stuff will remain intact.  We are just telling apt-get to look to your live cd as a repository since you don't have internet setup yet.  It can reinstall xubuntu-desktop from there using the 2 commands i mentioned earlier (remove and install).  We just have to make sure apt-get is actually looking to the cd drive.
Have you tried what I mentioned above with the /etc/apt/sources.list file?

---

### Post by Nimaran on 2007-06-29
Ohhhh.... Ok. I thought that was going to kill everything, so I'll try to give it a try now its alittle complex, but I'll see if I can get it.

---

### Post by Nimaran on 2007-06-29
Ok. I tried but I didn't see anything about a CD. Did I have to boot into the CD or my normal one, because what I did was boot into the Xubuntu on my hard drive hit ctrl f2 log in. Type the sources.list command you gave me and I didn't see anything about a CD.

---

### Post by Rocket2DMn on 2007-06-29
Are you totally sure on that?  There should be a section near the top that looks similar to this (from an ubuntu feisty file):
> ## If you have a install CD you can add it to the reposity using 'apt-cdrom add'
## which will add a line similar to the following:
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
#deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

You would uncomment the line
#deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted
changing it to
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted

Do NOT copy and paste that, it will be slightly different on your machine

---

### Post by Nimaran on 2007-06-29
Yeah, I'm pretty sure that didn't happen. I'll go check again while waiting for your reply.

---

### Post by Rocket2DMn on 2007-06-29
You might try the command
```
sudo apt-cdrom add
``` but from what I'm reading, it might not work in Xubuntu.
I'm going to lunch right now, hopefully you can have something new when I get back.  Good luck!

---

### Post by Nimaran on 2007-06-29
No, the CD sitll didn't pop up, but I have an idea. Couldn't I boot into the live CD, acess that portion of my HD go to the file add or take away what I need type in the right command reinstall the graphical interface and be good to go, when your done with lunch tell me what you think.

-And again I have taken a lot of your time thank you for all your help I greatly appreciat it

---

### Post by Rocket2DMn on 2007-06-29
You can boot from the live cd into a GUI, but it still doesn't solve the problem of not having internet.  I don't know how to go about just reinstalling the xubuntu-desktop from that.

However, we might be going about this the wrong way.  If we truly think Beryl is the source of the problem, we can try and remove it.
```
sudo apt-get remove beryl
```
Then go to your home directory (in terminal) and delete the following (according to [this]("http://ubuntuforums.org/showthread.php?t=486544&highlight=beryl+remove") thread):
```
rm -r .beryl
rm .beryl-managerrc
```
where "rm" is the remove (delete) command and the -r acts recursively on the .beryl directory.

After you have tried this, restart the X-server either by doing CTRL+ALT+BACKSPACE from your graphical login screen  or by just restarting the computer.  Then attempt to log in using any session (like Xfce).

---

### Post by Nimaran on 2007-06-29
Okay, I tried that I think it removed Beryl, but I'm not sure about the config file. Did I have to do anything special besides type in those rm commands, because I didn't and it didn't say anything after it, regardless I tried logging in again to no avail, lets see what else we can pull out of our hats. That might tell us the problem isn't beryl or I still need to remove the config

---

### Post by Rocket2DMn on 2007-06-29
I really wish we could get some screenshots or terminal outputs, but not having an internet connection seems to  make that impossible.
Have you tried booting with in recovery mode (the second option on the GRUB screen before xubuntu starts loading)?

---

### Post by Nimaran on 2007-06-29
Sorry it took so long to respond. My connection is not being happy today.

I have, but all I get is a terminal. See I'm still trying to figure out [I]what[I] is wrong, because it logs in, but all I get is my background color, and my mouse cursor. I can move my mouse wherever and stuff, just nothing else loads. Do you know anyone else on the fourm who might be able to help us? Its just baffling one minute it works the next. Nothing.

---

### Post by Rocket2DMn on 2007-06-29
I dont know anybody in particular who can help, it's really just a matter of people trying to track down your problem without being able to see and screenshots or terminal output.
I'm not sure if this has any effect, but you can remove the emerald theme manager that comes with beryl.

```
sudo apt-get remove emerald-themes
```

By the way, what video card and driver do you have?  Any other relevant computer specs might be helpful at this point.

---

### Post by Rocket2DMn on 2007-06-29
OK, I'm pulling now from [this]("http://ubuntuforums.org/showthread.php?t=353813") thread as a last ditch attempt.
```
sudo apt-get --purge remove beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings beryl-settings-bindings beryl-vidcap emerald libberyldecoration0 libberylsettings0 libemeraldengine0

sudo apt-get autoremove
sudo apt-get autoclean
rm -r ~/.beryl

rm -r ~/.emerald
rm -r ~/.beryl-managerrc
```
That's all I got left for you man, we've tried just about everything.  It's just not easy (or even possible) to fix these kinds of problems without the ability to share more data like screenshots and terminal output.  A lot of people who have these kinds of problems just end up reinstalling.

---

### Post by Nimaran on 2007-06-29
Well, I would like to thank you so much for all your help. That last list of commands you gave me do I enter each line separately, or what? Thanks again. I'll post if it ever works out. I'll keep subscribed in case any more ideas pop into anyone's heads.

By the way:

System: Dell Dimension 2400

RAM: 768MB

Graphics Card: Nvidia GeForce Fx5200

-Again Thank you everyone I'll see if I can get it working.

---

### Post by Nimaran on 2007-07-01
I'm getting closer. I think Beryl is somehow set to boot up automatically with Xfce, which I guess causes problems. Even though, I have removed the autoboot

---

### Post by Nimaran on 2007-07-01
I fixed my computer. Please see this thread.

[http://ubuntuforums.org/showthread.php?t=488716](http://ubuntuforums.org/showthread.php?t=488716)

:D
:D
:D
:D

---

