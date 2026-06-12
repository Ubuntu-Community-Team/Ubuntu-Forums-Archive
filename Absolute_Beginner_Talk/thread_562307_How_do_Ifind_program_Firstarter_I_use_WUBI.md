---
title: "How do Ifind program Firstarter? I use WUBI"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by nooby on 2007-09-28
I guess I posted this in wrong sub forum. So I try here. 

I'm totally new to linux and ubuntu. I downloaded the WUBI installer and am curious on if that change anything about ports being shut by default.

How does one know if a port is open? Maybe I should start Firestarter cause that one maybe do show if there are traffic I would not know of without it?

I also wonder if my linux will know when it could update to Gutsy? Do I have to undelete this wubi and then download a new wubi or is it possible to upgrade to Gutsy when it comes.

I like the safety of not doing partition and changing windows. I write in win now cause I need to check if it still works. It did.

I have firefox on windows. How do I migrate my bookmarks from the windows Firefox??

---

### Post by por100pre1 on 2007-09-28
Try the usual method once Wubi is installed.

```
sudo aptitude install firestarter
```

---

### Post by Johnny3 on 2007-09-28
I think I went to System/Administration/Synaptic Package Manager and search for firestarter?
New at this Johnny3
Gainesville, FL

---

### Post by nooby on 2007-09-29
> **Johnny3 said:**
> I think I went to System/Administration/Synaptic Package Manager and search for firestarter?
New at this Johnny3
Gainesville, FL

Thanks to both of you. 


por100pre1 you have to remember I'm a total noob here so to do commando things is beyond me. I don't know how to activate that feathure and how to get out of it. I would only do such things in case of utter despair. if the program Ubuntu toally failed to use the Gui. I don't criticize you, I kindly remind you about me being a another kind of user. I know a lot of people like the commando style. It allows them to take control over things. But it makes me loose any control. To stay within the GUI would at least allow me to slowly learn. I have no way to remember such things you wrote. I'm kind of dense or dim. 

Had I been into such I used a distro totally concentrated to such approaches. 

Johnny3, yes I thought of Synaptic too but texts says that is an advanced tool so I had hoped there was an easier way. 

Shouldn't Nautilus be of help? Now I need to find that tool. I guess nautilus is easier than Synaptic but how to I find it? 


I still have to know about upgrading to Gutsy when the official version comes out next month. 

I'm on WUBI here so no usual install on my computer. I have to go to wubi site and learn if it is possible to upgrade from Fiesty to Gutsy in an easy way of it one has to start all over from beginning? 

How do I know if a port is open using the GUI without starting Firestarter

---

### Post by Sunforge on 2007-09-29
How do I know if a port is open using the GUI without starting Firestarter?

First things first: firestarter is a GUI for firewall management in Linux.
If you want to know if you have any ports open, try using the built in port scanning tool:
System - Administration - Network Tools - Port Scan
Input your IP address 127.0.0.1 (this always scans your own computer) and take a look at what it tells you.
Ubuntu is pretty secure if you're using a default installation, so you shouldn't have too much to worry about.

Getting new programmes:

My experience is that Ubuntu works best if you try to install programmes in the following order of preference. This is my order of preference other posters will, I am sure, have other orders of preference.

1. Search the distributions programme repositories using the following menu options:
    a) Applications - Add/Remove. Just look through the programme categories, check the         check box and apply the changes.
    b) System - Administration - Synaptic Package Manager. You will be prompted for your         login password which is a "security check", don't panic. Search for a specific         programme name or description, right click on your software selection, select "mark         for installation" and then hit the "apply" button at the top of the window
    c) The command line (apt-get install <packagename>). You've said that you aren't keen         on the command line and it is foreign if you're used to windows, but you can simply         cut and paste commands from a lot of the "how to" guides and they just work. There is         no real need for the command line for 90% of your tasks.
2. Downloading a .deb (debian binary file) and using gdebi package installer
3. Downloading an RPM and using alien
4. As a very last resort compiling from source which can be a very frustrating experience if you're not very sure about what you're doing.

Nautilus

Nautilus is the same as Windows explorer, it's the application that you use to browse files when you open your home folder. Right clicking on any file will bring up a list of options for that file, the same as Windows.

How do I upgrade from Feisty to Gutsy?

Remember that Feisty will continue to be supported until at least 2008 so you don't have to worry about upgrading as soon as Gutsy arrives. 

I know that you're not keen on the command line, but cutting and pasting this command will help you greatly:

gksu "update-manager -c"

This will fire up the update manager with sudo privileges (in effect you're acting as root for a few minutes). The above command was taken from a how to guide for upgrading Edgy to Feisty: the princinples are the same for upgrading Fesity to Edgy:

[http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/](http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/)

I have to confess at being a little paraniod about any automatic update so generally download an entire distro, wipe my machine and start from scratch *having backed everything up*. You definitely don't have to be as extreme as me though.

And finally here are two pretty solid reference guides:
Ubuntu Beginners Guide:
[https://help.ubuntu.com/community/Beginners/Guide](https://help.ubuntu.com/community/Beginners/Guide)

Ubuntu Feisty Fawn Starter Guide:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_IP_calculator_for_GNOME_desktop_environment](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_IP_calculator_for_GNOME_desktop_environment)

I think that should do it for now. I'm off to worry my computer with some dodgy software :-P

---

### Post by por100pre1 on 2007-09-29
> **nooby said:**
> Thanks to both of you. 


por100pre1 you have to remember I'm a total noob here so to do commando things is beyond me. I don't know how to activate that feathure and how to get out of it. I would only do such things in case of utter despair. if the program Ubuntu toally failed to use the Gui. I don't criticize you, I kindly remind you about me being a another kind of user. I know a lot of people like the commando style. It allows them to take control over things. But it makes me loose any control. To stay within the GUI would at least allow me to slowly learn. I have no way to remember such things you wrote. I'm kind of dense or dim. 

Had I been into such I used a distro totally concentrated to such approaches. 

Johnny3, yes I thought of Synaptic too but texts says that is an advanced tool so I had hoped there was an easier way. 

Shouldn't Nautilus be of help? Now I need to find that tool. I guess nautilus is easier than Synaptic but how to I find it? 


I still have to know about upgrading to Gutsy when the official version comes out next month. 

I'm on WUBI here so no usual install on my computer. I have to go to wubi site and learn if it is possible to upgrade from Fiesty to Gutsy in an easy way of it one has to start all over from beginning? 

How do I know if a port is open using the GUI without starting Firestarter

Sorry for any inconveniences. That's a command for installing Firestarter. You can use Add/Remove to add Firestarter, think in that command as a shortcut to have the job done. Just copy, paste and ENTER any command in Terminal (Applications> Accesories> Terminal). Again, sorry for any inconveniences.

---

### Post by nooby on 2007-09-29
Thanks to both of you. I try it out in due time. 

Maybe I am already in Nautilus when I use the Gui? Or that program start when one open things or click on meny? Kind of is open by default. I am a bit worried to use command line interpreter cause it is too powerful. People could give advice that start things that corrupt the set up, them not realizing I use wubi. 

Maybe I should go over to UNetbootin instead so but I failed to get if that one deleted the windows OS? The text is too geeky to get for me as a  noob. It is possible to read it to say that one replace win xp with the linux distro OS. That is not what I want. I have to read more so I get what it actually says. 

[http://lubi.sourceforge.net/unetbootin.html]("http://lubi.sourceforge.net/unetbootin.html")

I know I most likely could use LVPM to make the WUBI into a regular installation with both win xp intact and ubuntu easily upgradable using the commandline? 

Ok I take a pause from it now I guess. Have to get the bookmarks for firefox migrated.

---

### Post by por100pre1 on 2007-09-29
We are glad to help. You can get specific Wubi advice in the [Wubi sub forum]("http://ubuntuforums.org/forumdisplay.php?f=234") right here in the Ubuntu Forums. I'm sure they will be glad to help too. :)

---

### Post by nooby on 2007-09-29
Another guy with same error as me posted august 8? but none answered him so hope it is ok if I take it here too? I'm not cross posting by intent. 

After upgrading using the little symbol in upper right corner that prompted me to ugrade some 118 such fixed things. 

Then it failed to shutdown. The power of the computer was still on and harddisk spinning and fan reeling and so on but no error text on screen. 

So I had to pull plug on it. The power button did not respond. 

Is that a known bug and that explains why nobody answered him for som long time? 

I'm very happy you folks respond. I do relaize one should find proper place and as a noob this is the place?

---

### Post by Sunforge on 2007-09-30
I've never known why people don't respond to some posts. That would be a subject of a post itself. I've found 

Your power problem is an interesting one and something that I have experienced myself on different computers. There are plenty of bugs registered on launchpad and several (technical) workarounds for some situations.

(Sample bug listings for power down problem on launchpad):
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104868](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104868)
[https://launchpad.net/ubuntu/+bug/43961](https://launchpad.net/ubuntu/+bug/43961)

I'm far from expert on power down problems but it might be worth starting with what hardware you're running?

---

### Post by nooby on 2007-09-30
Sunforge, much appreciated. Wow show that I am not alone. Surprising that nobody respond. 

They know about it don't they? 
Hope they solve it in the Gutsy version or I have to look for another version of linux unless it is the Kernel cause that one are same for all distros? 

funny thing is that before the update it world good. 

Depressing to read here , the admin?writes they have not decided the importance of it. To not be able t oshut down and the program corrupt files is very serious. Highest importance for a noob like me. 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104868]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/104868")

I love Open Source and Linux as a concept but functionality is A and O. If it even fail to shut down and even corrupt files that is disaster for us noobs. I've had enough of that in windows. :)

PS  ooups maybe I break a rule going too OT? I ask to know how to avoid such shut down things. If diffferent installations are different in being sensitive to it? 

suppose I use UNetbootin instead of WUBI. Would that solve the no shut down bug? 
I see your a tester of Gutsy. What kind of installation do you have. Have you kept Windows and made three new partitions or dedicated an older puter to be  Linux exclusive?

---

### Post by Sunforge on 2007-09-30
Gutsy: I've got my main Dell PC with Gutsy on it and no other OS. I've been using it since tribe 2, just wiped it to put the Gutsy beta on it. If you want to try Gutsy please wait until the official release. I'm too lazy to dual boot but do keep backups of all important stuff.

The Gutsy alpha release definitely has issues with powering down some machines, even variants of the same machine (Dell Optiplex for example), so I can't recommend going to Gutsy when it is finally released as, at time of writing, it may not solve your problem.

Power down issues: There are a few proposed fixes on Launchpad so it might be worth looking at them or asking further in the forums, as I'm no expert. It may be worth taking a look at your BIOS and seeing if there are any settings that enable or disable support for power management; there are a few threads which mention this:

[http://ubuntuforums.org/showthread.php?t=307643](http://ubuntuforums.org/showthread.php?t=307643)

---

### Post by nooby on 2007-09-30
Thanks yes it could be something with Bios, I thought about it too but not being good at computers I didn't dare to change things. It usually crash when I do such things. Ok I look into it when they have released the official version of Gutsy. 

Ah it had Linux on it already. Dell Sweden has hesitated for years but have finally maybe decided to try it on a few laptops. I have enough computers aöready so such have to wait for me.

---

