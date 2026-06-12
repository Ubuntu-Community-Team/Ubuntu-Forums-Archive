---
title: "Why is this more difficult than Windows"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by smithchar526 on 2007-06-28
The main reason I want to learn lLinux right now is so I can make a Linux MCE system for my entire house (DVR, DVD server, Music server, all my multimedia anywhere in my house) Everyone that uses linux say that it is so much better then Windows. Im trying really hard to break free from Microsoft and windows, but I am having problems with the easiest things. So here is where Im at:

1. Download and burn Ubuntu 6.10, install was easy
2. Connection to internet with no work.

here is my first problem, resolution was screwed up.after looking forever I found a driver that I think works but I dont know for sure, resolution only goes to 1024 X 768. When I try to look at the screen savers it keeps crashing and makes me log back in. I shut the lid on the laptop and open it again the screen saver is all messed up and I have to play with it to make the screen get back to the log on. 

I also tried to connect to my wireless network....I went to the network setting and it let me put in my ssid , passcode ect. but doesnt work. Must be missing the driver....WHERE DO I FIND MISSING DRIVERS>> in windows its very easy, the laptops an HP I go to hp and download the driver, check computer manager and see if there is any other unknown devices. Is there any way for me to visually see what drivers are missing????? SO I know what works and what doesnt. Is there any sites that have the most common drivers that I would need to download. I have installed ubuntu on a laptop and desktop both HP and have the same issues. 

 THERE HAS TO BE SOMETHING THAT I AM MISSING, if linux is so much better shouldnt it be eaiser to use than windows. I know what crap Vista is and how driver support sucks but so far it seams easier than thiis. Im not trying to bash Linux and I think that I really am just missing something, Im trying not to give up but I can set up an XP machine so much quicker and everything works...maybe Im just not used to command line to do everything, maybe Im just more of a visual person or lazy. SOME ONE PLEASE POINT ME SOMEWHERE I CAN GET THE BASIC SETTINGS WORKING. Im not talking about advance stuff, just the basic stuff, (graphcs, networknig, wireless, ect)

---

### Post by alienexplorers on 2007-06-28
What graphic board (chip) are you using?

---

### Post by tgm4883 on 2007-06-28
First, take everything you learned about Windows and throw it out the window.


Now, there are a few things you need to do.  Easiest thing to do is plug yourself into a wired network and install network manager (sudo apt-get network-manager-gnome).  This should let you connect to your wireless easily.  

Next you need to install 3d drivers for your graphics card.  I can't help you with that unless you tell me what card you have.

---

### Post by dwhitney67 on 2007-06-28
Is there a reason why you chose to install Ubuntu 6.10 vs. the newer version which is 7.04?  The newer version comes with update-to-date drivers and helpful documentation as to where to get certain others which are not included on the disk.

It is unfortunate that a lot of noobs expect Linux to be "perfect" like Windows.  That is not always the case.  There is a lot of hardware out there that is being produced by manufacturers that do not even know what Linux is.  They could care less about it (because there is no serious amounts of money to be had marketing products for it).  Therefore the creation of device drivers for Linux is done by many people who sacrifice their personal time to support the Linux community.  Unfortunately device drivers for Linux cannot be churned out as quickly as the hardware coming from the countless hardware manufacturers.

If you have the patience, Linux can be rewarding.  If you do not, and you want everything spoon-fed to you, then remain with Windows.

I for one will never throw another coin at MS.

---

### Post by euler_fan on 2007-06-28
I usually prefer wifi-radar as my wireless network manager. It is available under Add/Remove programs.

It is nice, clean, simple, and it just works on my machine.

Good luck!

---

### Post by starcraft.man on 2007-06-28
> **smithchar526 said:**
> The main reason I want to learn lLinux right now is so I can make a Linux MCE system for my entire house (DVR, DVD server, Music server, all my multimedia anywhere in my house) Everyone that uses linux say that it is so much better then Windows. Im trying really hard to break free from Microsoft and windows, but I am having problems with the easiest things. So here is where Im at:

1. Download and burn Ubuntu 6.10, install was easy
2. Connection to internet with no work.



Started with good intentions.

> 
here is my first problem, resolution was screwed up.after looking forever I found a driver that I think works but I dont know for sure, resolution only goes to 1024 X 768. When I try to look at the screen savers it keeps crashing and makes me log back in. I shut the lid on the laptop and open it again the screen saver is all messed up and I have to play with it to make the screen get back to the log on. 
[Envy]("http://albertomilone.com/nvidia_scripts1.html") installs drivers for both NVidia and ATI (most of the time for ATI) without any effort, even configures the xorg. As for screensaver, if the problems persists after configuring the driver properly, disable it. System > Preferences > Screen Savers. If this isn't an ATI or NVidia card, good luck, specialized cards are usually less supported.

> I also tried to connect to my wireless network....I went to the network setting and it let me put in my ssid , passcode ect. but doesnt work. Must be missing the driver....WHERE DO I FIND MISSING DRIVERS>> in windows its very easy, the laptops an HP I go to hp and download the driver, check computer manager and see if there is any other unknown devices. Is there any way for me to visually see what drivers are missing????? SO I know what works and what doesnt. Is there any sites that have the most common drivers that I would need to download. I have installed ubuntu on a laptop and desktop both HP and have the same issues. 
I never bothered with wireless in Ubuntu can't tell you how to get it working, look at NDISwrapper though, long as it isn't a broadcom card it should work ok. As for other drivers, most other things work with Ubuntu without much more effort.

> THERE HAS TO BE SOMETHING THAT I AM MISSING, if linux is so much better shouldnt it be eaiser to use than windows. 
Why do people still drive stick when automatic works perfectly well most of the time? Why do people still learn to ride a bike today when scooters, motorcycles and cars all get you to where your going faster and with less effort? Why do people still use paper when digital distribution is less costly and more environmental in the long run? The bottom line is just because Windows may "appear" easier doesn't mean it is better, and I assure you it is just an "appearance". I can BSoD any Windows machine in 3 minutes or less with no effort at all, I can also point to you many deficiencies of XP and much easier Vista that are still not fixed, I have used windows for years and do know that it is certainly in no way perfect.

> I know what crap Vista is and how driver support sucks but so far it seams easier than thiis. Im not trying to bash Linux and I think that I really am just missing something, Im trying not to give up but I can set up an XP machine so much quicker and everything works...maybe Im just not used to command line to do everything, maybe Im just more of a visual person or lazy. SOME ONE PLEASE POINT ME SOMEWHERE I CAN GET THE BASIC SETTINGS WORKING. Im not talking about advance stuff, just the basic stuff, (graphcs, networknig, wireless, ect)

Resources for learning Ubuntu:

[Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") site and [psychocats]("http://www.psychocats.net/ubuntu/") for General basics. [LinuxCommand]("http://www.linuxcommand.org/") for learning the CLI/Terminal. [Ubuntu Wiki]("https://wiki.ubuntu.com/") for advanced and specific questions (also forums of course) [Linux app finder]("http://linuxappfinder.com/") for finding programs and applications that suit your needs. [Ubuntu Geek.]("http://www.ubuntugeek.com/")

Oh and, since your aiming at an MCE, have a look at [MythTV]("http://www.mythtv.org/") and [Mythbuntu.]("http://www.mythbuntu.org/") (I think Mythbuntu is still alpha, don't install it as a main system yet, come back to it though).

---

### Post by steveneddy on 2007-06-28
You probably should have:

1. Learned a little more about the OS before you started diving in this far by yourself.

2. Told us a little more about your hardware.

3. Installed a newer, more stable version of Ubuntu with newer video drivers.

4. Forget everything you ever learned about computers by using Windows. 

Linux isn't Windows, doesn't act like Windows and is so much different than Windows that some call it hard. It's not hard, just different. 

Become comfortable with the Command Line Interface ( CLI ). 

Do a little research when you are just starting off. You need to go through a few stages that teach you how to deal with Linux and installing software, where the software is and how to operate or find the software after you have it installed.

Take a deep breath, take Starman's advice and go one step at a time.

Tackle the wireless issue first, then the video drivers and then the MCE part. You are going to have to learn a little about serving files also. 

Good Luck, we're all counting on you.

---

### Post by starcraft.man on 2007-06-28
> **steveneddy said:**
> 
3. Installed a newer, more stable version of Ubuntu with newer video drivers.


Agreed, I forgot to mention that. Really no reason to install Edgy anymore (6.10). Feisty is stable enough, and Dapper (6.06) is for those who need rock solid stability. Since your testing and aiming at an MCE, I'd recommend Feisty like others have.

> Good Luck, we're all counting on you.

Uh, don't ya mean we're here to help or some other? Counting on you is a pressure builder, Linux is about being relaxed no? Maybe I'm picky with words...

---

### Post by lisati on 2007-06-28
> **steveneddy said:**
> You probably should have:

1. Learned a little more about the OS before you started diving in this far by yourself.

2. Told us a little more about your hardware.

3. Installed a newer, more stable version of Ubuntu with newer video drivers.

4. Forget everything you ever learned about computers by using Windows. 

Linux isn't Windows, doesn't act like Windows and is so much different than Windows that some call it hard. It's not hard, just different. 

Become comfortable with the Command Line Interface ( CLI ). 

Do a little research when you are just starting off. You need to go through a few stages that teach you how to deal with Linux and installing software, where the software is and how to operate or find the software after you have it installed.

Take a deep breath, take Starman's advice and go one step at a time.

Tackle the wireless issue first, then the video drivers and then the MCE part. You are going to have to learn a little about serving files also. 

Good Luck, we're all counting on you.

Good points
Having only recently started with UBUNTU 7.04,  I still have to shake off some of the CLI stuff I learnt on MS-DOS (e.g. using / instead of \, a new set of commands to find my way around), and Windows command boxes... fortunately the CLI stuff I learnt on an IBM mainframe is buried in a tame black hole in my memory. 

All the best!

---

### Post by steveneddy on 2007-06-28
> **starcraft.man said:**
> Maybe I'm picky with words...

You're too picky....joking around star dude.

@ smithchar526

Don't forget to read the forums, search for your problems and if you don't find what you are looking for, please post a question. 

Don't type your frustrations, just ask a question or something about your issues, be complete 

(hardware, software recently installed if applicable and what are you trying to accomplish)

try not to type [SIZE="6"]large letters[/SIZE] and just stay calm. We can get you through this. We have either been down this road or someone has another post that we know about that can help you.

Starcraftman gave you the best links you can use at the moment.

---

### Post by starcraft.man on 2007-06-28
> **steveneddy said:**
> You're too picky....joking around star dude.


star dude? STAR DUDE? *twitches....... twitches more.......... flies off in an uncontrolled rage at the nearest Zerg swarm*

You know... I think I really asked to be made fun of when I picked that name, I seriously couldn't think of anything that day, my brain was dead. :p

> Starcraftman gave you the best links you can use at the moment.

Yay! At least I'm good at pasting links :p

---

### Post by tgm4883 on 2007-06-29
I almost asked the same question as to why he chose Edgy over Feisty.....After a little research Linux MCE only installs on Edgy.

---

### Post by calymea on 2007-06-29
hi, I tried to do the same as you said for the other guy with the gnome network manager through a terminal and got an invalid operation message. Any other clues? Thanks.

---

### Post by tgm4883 on 2007-06-29
> **calymea said:**
> hi, I tried to do the same as you said for the other guy with the gnome network manager through a terminal and got an invalid operation message. Any other clues? Thanks.

Not unless you post the output.

---

### Post by sad_iq on 2007-06-29
Funny...no one bothered ...open a terminal...and paste the results from this command so we will know your hardware: ```
lspci
```...and to see if you have your video driver correctly installed try ```
glxinfo |grep direct
```...if it says "direct rendering: Yes" then it's properly installed!!!
 Drop a line here so we can really help!!!

And just a question...do you think windows is easy??? Try installing it on a Pc without knowing what's inside the box and without any driver CD(speaking from experience!!!)...then come back and tell me how easy it was!!!

---

### Post by p0wd3r on 2007-06-29
I too am in the same boat.  Trying to install NVidia drivers for a GeForce Go 7300, it keeps telling me that I can't run X server while installing it, and I'm having the hardest time getting to a pure command line.  Granted I'm probably missing something, but at least windows has the F8 boot interrupt option.  I've read that pressing 3 at the grub promt will work, but that doesn't, I read that CTRL+ALT+Backspace will kill X, but it restarts right after, and if I keep doing it it won't start because it will think it has an error, but then it's at some black screen where anything I type does nothing...

Honestly, comments like "you should learn more about the OS", or "I could kill a windows machine in 3 minutes" or "if you want it spoon fed to you, stay with windows" don't help.  Support forums are for support, and if people ask for help and you look down on them like they're retards for using Windows in the first place, you aren't helping.

I'm not going to point out the flaws in Windows or Linux, because that doesn't help.  I'm only asking how to get to a pure CLI using Ubuntu 7.04 and not having X server running so I can install the video drivers.  So far, all guides I have found haven't worked.  Including the guides I found here...

[http://ubuntuforums.org/showthread.php?t=432056&highlight=install+NVidia+drivers+X+server](http://ubuntuforums.org/showthread.php?t=432056&highlight=install+NVidia+drivers+X+server)

I admit, I haven't touched a Linux OS for 6 years or so, and I stopped using it then because of the same issues, driver support sucks.  But now more drivers are being written for Linux, but if there's no way to install them, then it's just as bad as not having them at all.

:popcorn:

---

### Post by Nythain on 2007-06-29
control alt f2 will take to you a login prompt... log on... then type sudo /etc/init.d/gdm stop will kill x,

---

### Post by nunnst on 2007-06-29
I have HP dv8210us laptop.  Almost everything worked out-of-box. Things you should do:


[LIST=1]
[*]Install Ubuntu 7.04 (Feisty Fawn) - like others have said.
[*]Wireless  - the default driver that loads on install is just a "shell" you need to install the microcode that comes with the driver from Broadcom (assuming you have the same wireless chip set I have). detailed instructions are on here in the forums. This [**[COLOR="Red"]link[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=185174&highlight=HP+dv8210us")
[*]Display - Feisty should solve that problem.
[*]Read the forums (do searches) - incredible help.
[*]Before you install ANY applications, go to [www.getautomatix.com](www.getautomatix.com) and get their SW installer (it's limited) but it easily solved some issues I had, like trying to get embedded video streams to work in Firefox.
[/LIST]

During this sometimes frustrating set-up of my first Linux system, I've come out much more knowledgeable about PC's and the operating software that drives them.  Frankly, I switched to Linux because I was sick and tired of XP continually slowing down and I couldn't afford a Mac.  After 2 weeks, I am fully Linux and have no need for Microsoft and its damned registry any longer.  I did like iTunes until I realized the limitations they were putting on my use of the music I legitimately bought.

Things I like about Linux:

No Norton Anti-Virus - don't need it
Actually have all the software on CD in case of crash (not true with XP from HP - preloaded)
Auto Update without having to worry about Microsoft saying my software was pirated (its not but they didn't care)
Incredible amount of free software applications - the personal and small business accounting is key for me.
Options, options and more options!
Compiz Fusion - kinda silly, but I like it
It's Free!
It's FAST - Boot, shutdown, applications
It's different - if I wanted Windows I would have stayed with it.

Best of luck in your efforts!

---

### Post by tgm4883 on 2007-06-29
> **nunnst said:**
> 

No Norton Anti-Virus - don't need it


Symantec is always a bad idea, no matter what you run

---

### Post by p0wd3r on 2007-06-29
> **Nythain said:**
> control alt f2 will take to you a login prompt... log on... then type sudo /etc/init.d/gdm stop will kill x,

Thank you!

---

### Post by JAmerican on 2007-06-29
I think Windows is easier because I have never experiened it crashing from installing an audio driver posted by the company. RealTek has a Windows driver and a Linux driver. I installed the Windows driver when I was having issues with my XP system's audio. It fixed it fairly easily. 

I tried to use their Linux driver that was made for 2.2 and later Linux kernals (I am using Ubuntu Feisty) and it caused my system to stop logging in. It just has the "Your session only lasted less than 10 seconds." Then logs out. 

I agree that Windows is a lagging, bloated, and very closed OS. But at least it has restoration capabilities that work from time to time. I have not had such ease with Linux at this point. I am only a beginner and don't know much. But, most of my problems have to be solved using a command of some sort that either doesn't fix the problem or makes it worse. I've installed Ubuntu 2 now and Kubuntu once on the same system just because of the Nvidia and RealTek drivers making it impossible to log in. BTW, this installs happened over the course of this week.

Ubuntu has better support for my card and works great but the audio is way to low. 

I hope someone out there can offer a suggestion about my Realtek ALC882 HD Audio driver problems :(

I just fear the day when I get Ubuntu loaded and running that my machine as my main OS and it will not be able to be logged in because of a driver issue. Windows has this too but they also have **Last Known Good Configuration **and **System Restore**

JAmerican

---

### Post by sad_iq on 2007-06-29
> **JAmerican said:**
> 
Ubuntu has better support for my card and works great but the audio is way to low. 

 Open a terminal and type **alsamixer** and see if raising(or lowering) some sliders can improve the sound volume(quality)!!!

---

### Post by chamberlain2006 on 2007-06-29
The "restore point" idea may be available in future releases (maybe Gutsy even *crosses fingers*).  By the way, what's the status on the wireless, cause that's my specialty.  If you still need help, can we move to a new thread?

---

### Post by JAmerican on 2007-06-29
> **sad_iq said:**
> Open a terminal and type **alsamixer** and see if raising(or lowering) some sliders can improve the sound volume(quality)!!!

I just clicked the speaker icon and raised those values and its still low. I have my Speaker on MAX. When I switch to my Xbox 360 or XP install. Its blasting.

JAmerican

---

