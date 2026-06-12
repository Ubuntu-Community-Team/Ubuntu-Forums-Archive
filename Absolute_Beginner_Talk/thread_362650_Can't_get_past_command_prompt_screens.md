---
title: "Can't get past command prompt screens"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Staplegun on 2007-02-15
Probably missed something in the install, but I'm stuck on the command promp screen.
The current line is computer@ubuntu:~$ but I want it to start up the desktop. This is the first time I've even SEEN the Ubuntu operating system on a computer much less tried to even use it.

---

### Post by s_h_a_d_o_w_s on 2007-02-15
Is the screen all black with the Little white blinker to type? If thats the case you most probably downloaded and ran the Server Edition.

---

### Post by Sklasko on 2007-02-15
Did you install using the Desktop CD or the Alternate CD?

---

### Post by Staplegun on 2007-02-15
I don't quite see a blinker but it is running like MSDOS did right now. I might have downloaded the server edition. Dang, that's kinda wierd, I don't remember clicking the server edition. What happens is it starts that Ubuntu start up screen with all the (ok) things as in it's starting up each module, and then it jumps straight to command promp and leaves it at that. The startup requires some sort of oem login. (I have a lot of computer experience so I do know plenty of things, I just have absolutely no clue with linux, I never wanted to try it lol)

---

### Post by halitech on 2007-02-15
do you remember entering any password at all? sounds like you did the oem install from the alt install cd. The user name would be oem and the password should be whatever you entered.

---

### Post by aysiu on 2007-02-15
This should help:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by Staplegun on 2007-02-15
Halitec you hit it on the spot. My dad downloaded the file, I'll have to ask him about it.

---

### Post by Tomosaur on 2007-02-15
If you don't want to redownload the Desktop (GUI) version of Ubuntu, you can 'convert' your server edition into the desktop version. Once you've found the password and logged in, type:
```

sudo aptitude install ubuntu-desktop

```
It'll take a little while (and if you haven't got broadband, it may not be worth it at all), but it should be quicker than downloading the desktop edition, and reinstalling all over again.

Once it's all downloaded and installed, reboot, and you should have a nice GUI :)

---

### Post by Staplegun on 2007-02-15
I did try that, but i have already done the oem-config-prepare and it's saying towards the end that there is a locked file and I do have broadband. I'm wired in at 100mbps.

---

### Post by Staplegun on 2007-02-15
Sudo commands do not work any more.

---

### Post by Staplegun on 2007-02-15
```
computer@ubuntu:~$ aptitude install ubuntu-desktop
reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not open lock file /var/lib/dpkg/lock - open (13 permissions denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```
That's the exact screen I get.

---

### Post by Sklasko on 2007-02-15
Did you say sudo commands don't work? What do you mean by that?

You should be using "sudo aptitude install ubuntu-desktop".

---

### Post by old_geekster on 2007-02-15
> **Tomosaur said:**
> If you don't want to redownload the Desktop (GUI) version of Ubuntu, you can 'convert' your server edition into the desktop version. Once you've found the password and logged in, type:
```

sudo aptitude install ubuntu-desktop

```
It'll take a little while (and if you haven't got broadband, it may not be worth it at all), but it should be quicker than downloading the desktop edition, and reinstalling all over again.

Once it's all downloaded and installed, reboot, and you should have a nice GUI :)
If you have a high-speed Internet connection, this would be the way to go.  It would certainly save some effort.

I am new to Ubuntu (two weeks), so I am a newbie also, but I have installed it about 10 times in the two weeks.  I keep messing it up.  I am definitely an expert in the installation process.

---

### Post by Staplegun on 2007-02-15
> **Sklasko said:**
> Did you say sudo commands don't work? What do you mean by that?

You should be using "sudo aptitude install ubuntu-desktop".

I type sudo in before the command and it just gives me a new line. Should I reboot the computer and see what's going on?

---

### Post by Tomosaur on 2007-02-15
> **Staplegun said:**
> I type sudo in before the command and it just gives me a new line. Should I reboot the computer and see what's going on?

You need to put your password in the new line. You won't see it being typed in, so you need to know how to spell it :P

---

### Post by halitech on 2007-02-15
are you tyoing in
```

sudo
```

then hitting enter and then typing in

```
aptitude install ubuntu-desktop
```

or are you going

```

sudo aptitude install ubuntu-desktop
```

---

### Post by Sklasko on 2007-02-15
Does the new line look like this?

```
Password:
```

---

### Post by Staplegun on 2007-02-15
> **halitech said:**
> are you tyoing in
```
aptitude install ubuntu-desktop
sudo aptitude install ubuntu-desktop
```

I did both. The first one is what got me a response.

---

### Post by Staplegun on 2007-02-15
No it just gives me a new command promp.
```
computer@ubuntu:~$
```



(sorry to be such a pain. Lol. My downloads for new things NEVER work on the first try. EVER. Quite literally. LOL. Crazyness)

---

### Post by Staplegun on 2007-02-15
I rebooted and started up in recovery mode so it gave me root command mode. Now it's doing something...Nevermind. It's starting to write really fast from the CD.

---

### Post by Tomosaur on 2007-02-15
> **Staplegun said:**
> No it just gives me a new command promp.
```
computer@ubuntu:~$
```



(sorry to be such a pain. Lol. My downloads for new things NEVER work on the first try. EVER. Quite literally. LOL. Crazyness)

Can you copy and paste a full screen of text from the terminal, after you have done:
```

sudo aptitude install ubuntu-desktop

```
?

---

### Post by halitech on 2007-02-15
try a reboot and then try to install the desktop again

---

### Post by halitech on 2007-02-15
> **Staplegun said:**
> I rebooted and started up in recovery mode so it gave me root command mode. Now it's doing something...Nevermind. It's starting to write really fast from the CD.

hopefully this is good and it's going to install the desktop for you

---

### Post by Staplegun on 2007-02-15
I think it is, because it's installing programs that the site said that ubuntu comes with, like openoffice and firefox. It's working now I think. I'll post an update in a few minutes when it's done doin whatever it's doing. Also, this isn't a terminal, it's a computer for my mom.

---

### Post by halitech on 2007-02-15
when we speak of the 'terminal' we mean the Command Line, the DOS Prompt would be the windows equivilant, not a computer type

---

### Post by Staplegun on 2007-02-15
Oh, ok oops sorry heh. I believe it's installing now. It's giving me a download rate of around 450-600kb/s so I think it's working. Thanks for your help all. If it doesn't work, then I'll update you on it.
And, this is a separate computer from the one that I'm working with ubuntu on, but you guys might have already figured that, I'm not sure because I've heard it's possible to run both at the same time or SOMETHING like that. Not sure.

---

### Post by halitech on 2007-02-15
no worries :)

there's 2 possiblities. first you can dual boot (so not technically running at the same time) and second, you can run a virtual system with something like VMWARE. Basically acts as a virtual desktop. wouldn't recommend doing that unless you have a decent system

---

### Post by Staplegun on 2007-02-15
Ahh, ok I see now. MY system that I pay for and use is pretty descent or so I think it is. It was when I pieced it together lol. I don't really plan on using ubuntu myself unless it runs any different. Can I optimize Ubuntu to run games better like, instead of running all this stuff in the background, can I make all the processing power in my computer go towards running the game?

---

### Post by old_geekster on 2007-02-15
> **Staplegun said:**
> Oh, ok oops sorry heh. I believe it's installing now. It's giving me a download rate of around 450-600kb/s so I think it's working. Thanks for your help all. If it doesn't work, then I'll update you on it.
And, this is a separate computer from the one that I'm working with ubuntu on, but you guys might have already figured that, I'm not sure because I've heard it's possible to run both at the same time or SOMETHING like that. Not sure.
Yes, it is possible.

Linux, Ubuntu in particular, is far different from XP.  The only time I have had to reboot was after a complete update at install.  Then, it has you reboot to finish the install.  Any other time, it will install a program without a reboot.

Also, I open a second "Tab" when installing a program and surf.  This would not happen in XP.

You are in for some interesting and exciting times.  You will be astounded what you are getting for the price.:)

---

### Post by Staplegun on 2007-02-15
> **old_geekster said:**
> Yes, it is possible.

Linux, Ubuntu in particular, is far different from XP.  The only time I have had to reboot was after a complete update at install.  Then, it has you reboot to finish the install.  Any other time, it will install a program without a reboot.

Also, I open a second "Tab" when installing a program and surf.  This would not happen in XP.

You are in for some interesting and exciting times.  You will be astounded what you are getting for the price.:)

Oh, shoot, what's this tabbing I hear about? I love tabbing systems lol. Does it tab out into another desktop or what does it do?

(UPDATE ON STATUS: System is currently rebuilding the database)

---

### Post by halitech on 2007-02-15
> **Staplegun said:**
> Ahh, ok I see now. MY system that I pay for and use is pretty descent or so I think it is. It was when I pieced it together lol. I don't really plan on using ubuntu myself unless it runs any different. Can I optimize Ubuntu to run games better like, instead of running all this stuff in the background, can I make all the processing power in my computer go towards running the game?

alas you have just found the achilles heel of linux. unfortunately most windows games do not run very well in linux although there are ways to do it. Cedega  is a pay for service that some people use, some will play under WINE but for most, unless it has a native linux version, probably not going to run very well. Windows is still the platform of choice for gamers.

---

### Post by Staplegun on 2007-02-15
Dang, oh well then. I guess I'll stick with windows then. But yes, I must be off, my mom wants me to go to bed. It's doing a lot of setting up stuff so I believe it has worked. Thanks for all your help. I'll get back up with you tomorrow and tell you if it finishes or not.

---

### Post by old_geekster on 2007-02-15
> **Staplegun said:**
> Oh, shoot, what's this tabbing I hear about? I love tabbing systems lol. Does it tab out into another desktop or what does it do?

(UPDATE ON STATUS: System is currently rebuilding the database)
I am using Firefox 2.0.0.1.  It allows for "Tab" browsing.  You can have as many "Tabs" open at once as you want.  Then, you simply click on a "Tab" when you want to go to it.

As far as for vitual desktops, it allows for 4 separate desktops.  There will be a "Switch between workspaces" area in the far right bottom of your desktop.  It will have two desktops as default, but you can add two more.

---

### Post by Staplegun on 2007-02-15
> **old_geekster said:**
> I am using Firefox 2.0.0.1.  It allows for "Tab" browsing.  You can have as many "Tabs" open at once as you want.  Then, you simply click on a "Tab" when you want to go to it.

As far as for vitual desktops, it allows for 4 separate desktops.  There will be a "Switch between workspaces" area in the far right bottom of your desktop.  It will have two desktops as default, but you can add two more.

Oh, firefox? Yeah, my windows PC uses that. Virtual "tabbed" desktops?? Wow, that grabs my attention. If windows games worked just as well on linux then I'd most certainly swap to linux. :)

---

### Post by Staplegun on 2007-02-15
The desktop is now installed. It started up pretty fast heh. Again, thanks for your help everyone. I'll come back when I have more issues with it.

---

### Post by halitech on 2007-02-15
glad we were all able to help you out and getting things running. I'm sure your mother will enjoy using it :)

---

