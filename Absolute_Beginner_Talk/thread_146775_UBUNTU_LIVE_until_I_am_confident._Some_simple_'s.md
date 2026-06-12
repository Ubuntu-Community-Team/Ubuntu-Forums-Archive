---
title: "UBUNTU LIVE until I am confident. Some simple ?'s"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by C_P on 2006-03-19
Hello All,
Hopefully someone can help with these simple questions on this person that is too apprehensive to format to UBUNTU and running the Live version someone sent me.

I am having some issues trying to figure this out before I finalize the big step.
1. When I put the UBUNTU installation disk in, will it ask me to format my hard drive or will I have to type in some series of commands to get this OS installed?
2. Will this OS pick up most of my devices or do I have to install drivers for them? The Live disk seems to see all.
3. The device manager sees my scanner but how do I choose to use it as it does not load when clicking the scanner button on my Canon 660U
4. This Live disk has Thunderbird email client on it and I can see it but when I double click the executable of Thunderbird to begin the install I get a error:
Couldn't display "/cdrom/programs/thunderbird/Thunderbird-1.0.2.exe".
5. Someone told me that I should use KDE desktop because it is better graphics, etc. This appears to use GNOME. How do I switch this or is this only done by a series of impossible to remember commands I have to enter somewhere?
6. How do I create a short cut on my desktop? I can see how to add to panel but not desktop?
7. How do I find my primary files like C:/program files/ etc.?
8. How do I install programs that I download? Double click? Because this did not work with Thunderbird email client.
9. I cannot find a way to set up Hotmail with this Evolution Email client. I could set it up in Outlook under HTTP settings. 

That should get me started. I really am not an idiot but never used another OS other than Winders.
I too have a forum and know what a pain it is for people to keep asking the same thing so maybe if someone was where I am at one time and could help?

Thank you VERY VERY much
FYI, I am on MSN, AOL, ICQ, and Yahoo cat if anyone wants to chat.

---

### Post by C_P on 2006-03-19
FYI, I am running Ubuntu Linux 5.04 : The Hoary Hedgehog Release.

---

### Post by NeghVar on 2006-03-19
Ok, I have some answers for you:

> 1. When I put the UBUNTU installation disk in, will it ask me to format my hard drive or will I have to type in some series of commands to get this OS installed?

When you first put it in it will ask Boot from CD ROM? (atleast on this machine it does) From there it will come up saying Install, hit enter, then it will go through language options, time zones, eventually yes you will have to either format or partition off a piece of your had drive, the details depend on what you want.

> 2. Will this OS pick up most of my devices or do I have to install drivers for them? The Live disk seems to see all.

If the live disk picks them up then they SHOULD work on the install, my computer hasn't had any problems with hardware yet. Things like additional hard drives will require an entry into fstab (the file that tells your computer where to find your disks)

> 4. This Live disk has Thunderbird email client on it and I can see it but when I double click the executable of Thunderbird to begin the install I get a error:
Couldn't display "/cdrom/programs/thunderbird/Thunderbird-1.0.2.exe".

If Im not mistaken you can access Thunderbird by going: Aplications>Internet and it should be there, although Im not entirly sure since Ive never run the live cd.

> 6. How do I create a short cut on my desktop? I can see how to add to panel but not desktop?

If you are referring to things in your applications list then right click on it and hit add this launcher to desktop. For files Im not sure.

> 8. How do I install programs that I download? Double click? Because this did not work with Thunderbird email client.

Primary installtion is down through Apt-get or synaptic (apt-get's friendly user interface) You can't install with the live cd because the live c is running off ram, you will need to do a full hard drive install to install programs.

Hope that helps with some questions

---

### Post by johnybot on 2006-03-19
i am kinda a new user, but i can help 
1.the installer will have onscreen instructions for partitioning
2. It should, mine did
5. If you install ubuntu it comes with Gnome
if you install KUBUNTU it comes with KDE
you can manually install both and switch from the login screen
6. I do so by holding down middle button(wheel) and dragging
7. You have to modify /etc/fstab
sorry i cant help with this but perhaps someone can link to a tutorial
8. It is best to use synaptic package manager, but how you install file is based on what type it is (rpm,deb,source)

Sorry i can't help with the other questions

---

### Post by Sef on 2006-03-19
> 1. When I put the UBUNTU installation disk in, will it ask me to format my hard drive or will I have to type in some series of commands to get this OS installed?

[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")    <---An excellent tutorial

> 2. Will this OS pick up most of my devices or do I have to install drivers for them? The Live disk seems to see all.

If your live cd picked up your devices, then they should be picked up upon install.

> 3. The device manager sees my scanner but how do I choose to use it as it does not load when clicking the scanner button on my Canon 660U[QUOTE]

[http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=660U&bus=any&v=&p=]("http://www.sane-project.org/cgi-bin/driver.pl?manu=canon&model=660U&bus=any&v=&p=")
In a nutshell, works good.

[QUOTE]4. This Live disk has Thunderbird email client on it and I can see it but when I double click the executable of Thunderbird to begin the install I get a error:
Couldn't display "/cdrom/programs/thunderbird/Thunderbird-1.0.2.exe".

Someone else will have to answer.

> 5. Someone told me that I should use KDE desktop because it is better graphics, etc. This appears to use GNOME. How do I switch this or is this only done by a series of impossible to remember commands I have to enter somewhere?

Gnome or KDE? It is your choice.  I prefer Gnome to KDE.  You should try both and see which one you like better.

> 
6. How do I create a short cut on my desktop? I can see how to add to panel but not desktop?

Highlight the application > right click >Add this launcher to desktop.

> 
7. How do I find my primary files like C:/program files/ etc.?

Click on the Computer Icon > Go to files

> 8. How do I install programs that I download? Double click? Because this did not work with Thunderbird email client.

[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")
<----- Another excellent tutorial

> 
9. I cannot find a way to set up Hotmail with this Evolution Email client. I could set it up in Outlook under HTTP settings.

Don't know if that is possible.  Someone will have to tell you if it is possible.

---

### Post by IYY on 2006-03-19
> 1. When I put the UBUNTU installation disk in, will it ask me to format my hard drive or will I have to type in some series of commands to get this OS installed?

You will not have to type any difficult commands. The installer is nearly as intuitive as that of Windows XP. More intuitive if you are not planning on dual-booting.

> 2. Will this OS pick up most of my devices or do I have to install drivers for them? The Live disk seems to see all.

Whatever the live disk sees, you will have.

> 3. The device manager sees my scanner but how do I choose to use it as it does not load when clicking the scanner button on my Canon 660U

I've never used a scanner in Ubuntu, but why don't you try Applications > Graphics > Xane image scanner.

> 4. This Live disk has Thunderbird email client on it and I can see it but when I double click the executable of Thunderbird to begin the install I get a error:
Couldn't display "/cdrom/programs/thunderbird/Thunderbird-1.0.2.exe".

This file is Thunderbird for Windows, and will not run in Linux. Thunderbird is not included in your initial installation, but is very easy to download from the repositories. 

> 5. Someone told me that I should use KDE desktop because it is better graphics, etc. This appears to use GNOME. How do I switch this or is this only done by a series of impossible to remember commands I have to enter somewhere?

Switching is very easy. You won't need any commands unless you want to use them (it's actually faster to copy/paste one line of code into the terminal than go through 5 icons). However, KDE does not have better graphics than Gnome, it's just more customizable. 

> 6. How do I create a short cut on my desktop? I can see how to add to panel but not desktop?

If you have the icon somewhere (in your menu or panel), you can just drag it to the desktop. If you want to create a new one: right click on the desktop, select 'create launcher' and fill in the textboxes. 

> 7. How do I find my primary files like C:/program files/ etc.?

The file hierarchy is a bit different in Linux. It's basically like one big tree where **/** is the root. All other directories and files have a path which starts from there. Many executable files, for example, go in **/usr/bin/** whereas configuration scripts go in **/etc/**. If you don't want to, you don't have to browse this tree often. Adding and removing software is all quite automated, and you can just use icons and launchers. When you want to run a program and you know the filename of the executable (often it's just the name of the application in lower case), you can just type this name into the terminal and the application will run. 

> 8. How do I install programs that I download? Double click? Because this did not work with Thunderbird email client.

Installing programs in Ubuntu can be done in 3 different ways:
**apt-get:** the easiest method. You don't have to open the browser and download anything. Just run the Synaptic package manager, search for the program you want and double click. Everything is automated.
**.deb:** these files can be installed using one line of code in the terminal, but you shouldn't worry about it now since you'll find everything through apt-get. The next release of Ubuntu has a graphical installer for these files.
**source:** it's possible to compile the programs from source, but that usually takes more time and skill and is very rarely needed. 

For example, say you want to install Thunderbird. Run System > Administration > Synaptic Package Manager. Search for "Thunderbird", double click on "mozilla-thunderbird", and click apply. Done. 

The same can be done via terminal if you know the exact name "mozilla-thunderbird". Just type **sudo apt-get install mozilla-thunderbird**.

---

### Post by dueY on 2006-03-19
[QUOTE=C_P]
1. When I put the UBUNTU installation disk in, will it ask me to format my hard drive or will I have to type in some series of commands to get this OS installed?
2. Will this OS pick up most of my devices or do I have to install drivers for them? The Live disk seems to see all.
4. This Live disk has Thunderbird email client on it and I can see it but when I double click the executable of Thunderbird to begin the install I get a error:
Couldn't display "/cdrom/programs/thunderbird/Thunderbird-1.0.2.exe".
5. Someone told me that I should use KDE desktop because it is better graphics, etc. This appears to use GNOME. How do I switch this or is this only done by a series of impossible to remember commands I have to enter somewhere?
6. How do I create a short cut on my desktop? I can see how to add to panel but not desktop?
7. How do I find my primary files like C:/program files/ etc.?
8. How do I install programs that I download? Double click? Because this did not work with Thunderbird email client.
9. I cannot find a way to set up Hotmail with this Evolution Email client. I could set it up in Outlook under HTTP settings. 

[/QUOTE]

Looks like a lot of these have been answered already but here's my reply anyway:

1.  You will have to format a partition.  If you're dual booting there are Windows programs out there to partition a drive (Partition Magic, for example) if you feel more comfortable using Windows and having the space ready and waiting.  But the Ubuntu installer can also partition if you are feeling confident (it's not hard)

2.  If the LIVE disc sees them then you shouldn't have a problem really.  

4.  Not really sure what that is, but once you have the actual desktop installed you shouldn't have that problem.

5.  I think more people prefer GNOME, and it's probably easier for a beginer.  Personally I've never used KDE.  But if you want to use it then you should download Kubuntu and not Ubuntu.

6.  Right click > add launcher

7.  The filesystem is a little different on Linux than Windows.  It would be hard for me to write a good explanation here, you're better off googling for one.

8.  You can install programs either through the terminal or Synaptic.  Synaptic is the gui for apt-get.

---

### Post by C_P on 2006-03-19
Wow, I am amazed at the replies I received and the help! I would have thought there would be a "oh no, another noobie with dumb questions" stagnation here. Thank you all for the help!
I have gotten the scanner to work via Applications > Graphics > Xane image scanner
I am having a weird issue on the Live CD where I lose my DSL connection after a while, not sure what that is.
Also, will I need firewall and Anti Virus software while running the new Ubuntu OS? I am soo used to turning this on immediately before anything under Windows.
I am assuming all these commands you are referring to are listed somewhere and are a requirement in Ubuntu to run certain things correct?
Also, I thought about getting Fudora and it was said I should download Kubuntu and not Ubuntu but man, there are like 17 different .iso files and they take forever to download. Then I download all the files to a folder, then what? I am not sure what to do with them after that.
Thank you ALL very much for your help thus far.

---

### Post by Sef on 2006-03-19
> Wow, I am amazed at the replies I received and the help! I would have thought there would be a "oh no, another noobie with dumb questions" stagnation here. Thank you all for the help!

We love noobies here.  They are always welcome with any question about Ubuntu.

> Also, will I need firewall and Anti Virus software while running the new Ubuntu OS? I am soo used to turning this on immediately before anything under Windows.

Firewall is yes.  Anti-Virus is no.  

Get Firewall:   Applications >  Add Applications > System Tools > more programs >click on firestarter > apply > apply again.  

No viruses in the wild for Linux.  If you run a mail client, you might want to use an anti-viurs, so a windows virus don't sit upon your linux and infect your friends who run windows.

> I should download Kubuntu and not Ubuntu but man, there are like 17 different .iso files and they take forever to download. Then I download all the files to a folder, then what? I am not sure what to do with them after that.

Download Kubuntu: Applications > Accessories > Terminal > then in terminal type sudo apt-get update >after update finishes > sudo apt-get install kubuntu-desktop.  

Then you will have the choice of which desktop to use.   Choose in sessions in the log in window.

---

### Post by C_P on 2006-03-19
Sef you rock bud! Where are there a list of commands for Ubuntu and do I allways run those commands from the method you suggested: Applications > Accessories > Terminal > then in terminal type ?

---

### Post by NeghVar on 2006-03-19
> do I allways run those commands from the method you suggested: Applications > Accessories > Terminal > then in terminal type ?

Yep pretty much, altho Kubuntu might use something different. You cant do the change to Kubuntu until you install to the hard drive though.

---

### Post by C_P on 2006-03-19
Thank you, do you have a list of those commands? Also, I have been told some people modify the code so it loads quicker and does not do the "unnecessary" stuff. Are there sections for this kind of advice for tips and tricks?
Also, do members seem to prefer Ubuntu, Kubuntu, or Fudora? Are there polls somewhere and the breakdowns of each of why they like it. I know I can search and read but sometimes getting direct feed back from the users that actually have used the products are the best reviews.
Thank you ALL again.

---

### Post by NeghVar on 2006-03-19
I don't know of any complete list of commands. As for what people prefer, Fedora is a completely different project supported by a completely different company. As for KDE or Gnome its all a matter of preference really. Some prefer KDE I prefer Gnome, why I don't really know I just do.

---

### Post by steve.horsley on 2006-03-19
Here is a series of pictures of an install being done:
[http://www.mrbass.org/linux/ubuntu/install/](http://www.mrbass.org/linux/ubuntu/install/)

If there is unused disk space, the installer will give you the option to use that, so you don't necessarily have to enter the custom partitioning dialog.

---

### Post by C_P on 2006-03-19
Woah, thanks Steve! GREAT shots there! I think I like the looks of Kubuntu with KDE Desktop. VERY nice look.
I sure could use Mr.Bass to show up at my house and explain these things and be there when I have questions. There are some nice tutorials on his site. 
 If I install Ubuntu with Gnome desktop, according to the previous post, I can change my desktop to KDE correct? Or is it better installing Kubuntu with KDE Desktop? If it is better to install Kubuntu, does anyone have the steps on downloading this and how to put it together since I am on a Windows XP OS I have looked for these things and all seem to have like 15 files and some .iso files. Let&#8217;s say I download all the Kubuntu with KDE Desktop files to a Kubuntu folder on my Windows OS, what is the best method/steps on getting these files to a bootable CD? Copy the files to a CD and boot from it?
Thank you all again, I am getting closer to a Linux user and former Windows user....

---

### Post by NeghVar on 2006-03-19
[http://us.releases.ubuntu.com/releases/kubuntu/breezy/](http://us.releases.ubuntu.com/releases/kubuntu/breezy/)

click the 1st link on that page unless u are using a 64 bit AMD processor or a mac. Once you have the ISO downloaded you need to use a program which will burn an iso, so nero type of program will do it.

---

### Post by mcmillan on 2006-03-19
It shouldn't really matter which version you install first.  Once you have one just install the other as already described,. The way to switch is when you logon there'll be a button somewhere saying sessions, click this and choose whichever you want to use that time. 

If you download the file NeghVar told you burn it the same way you did for the liveCD

---

### Post by C_P on 2006-03-19
I am trying to find the Firewall but no luck. SEF stated: Get Firewall: Applications > Add Applications > System Tools > more programs >click on firestarter > apply > apply again. There is no Add Applications, nor can I find a More Programs.

---

### Post by NeghVar on 2006-03-19
The problem is you need to do a hd install to get any option to add programs. once you do that it is Aplications>Add Applications and i think it is in the internet or system tools one. But you need to do a hd instal first.

---

### Post by C_P on 2006-03-19
Thank you for the reply and suggestions but it may not come with this version.
My father just did a HD install and we do not see these options you are referring to. We are running Ubuntu Linux 5.04: The Hoary Hedgehog Release and have run the 127 Updates.
I wish the screen shot program could show you that these options are not in my list. We also did a search for firestarter on the file system and only found a .html file called firestarter.html

Also, his Epson 825 Stlus Photo printer is in my printers list and I have selected it and added it as my printer but nothing prints when sending to it.

---

### Post by NeghVar on 2006-03-19
I don't know, Ive only worked with Breezy, sorry. Although id imagine that if you use synaptic you can download firestarter.

---

### Post by C_P on 2006-03-19
Thank you again, it must be included with Breezy then. I looked through Synaptic and there is MUCH pkgs there but I did not see firestarter. I have ordered Breezy, I wonder how long it takes to ship.

---

### Post by Jedeye on 2006-03-19
it takes around a month

---

### Post by NeghVar on 2006-03-19
did you do a search for firestarter, it really should be there. Your best place for answer is probly going to be the actually Hoary forum.

[http://www.ubuntuforums.org/forumdisplay.php?f=49](http://www.ubuntuforums.org/forumdisplay.php?f=49)

---

### Post by mcmillan on 2006-03-19
You might need to enable some extra repositories to be able to get it. There's some instructions on how to do this at ubuntuguide.org. This is one case that it may be an advantage to have hoary, since that page wasn't updated for the new version. I don't know if all the repositories are still active, but I'd bet it should still work. That page is actually a good source for a lot of information how how to get ubuntu working.

---

### Post by C_P on 2006-03-20
Thank you for the replies. I will look around. I actually just downloaded Kubuntu also and looked at it last night. It has very nice graphics and different applications. I do have issue with adding or even seeing my printer with that though. I posted the question in Kubuntu forum. I am testing both out to see which I like but Ubuntu seems to have found all my stuff but Kubuntu does not seem to see my printer though. Weird.

---

### Post by C_P on 2006-03-20
Ok, now I am getting addicted! I just downloaded my third flavor called PCLinux and BOY I am getting hooked! Having some media player error and it never plays my Metallica CD (.cdr files) that plays fine in my truck.
Also,
1. How do I change the default Konquer browser to Fire Fox?
2. How do I find my CD rom? When I had live disk in, it did not see it.
3. I put a CD with .cdr files on that I play in my truck and it errored out then started picking up my microphone?
It never played the CD.
4. How hard is it to install programs? Example: I have Nero 7.0 on a CD as a  zip file.
I load the CD in, do I browse to the CD ROM and double click the Nero executable to install? Also, how about the zipped file? Can I double click it and choose extract to say my folder and then double click the .exe to activate or install?

---

### Post by mcmillan on 2006-03-20
1. Not real sure about KDE, but I think there's something in control center (I think that's what it's called) that has this setting. 
2. When you have the liveCD in you shouldn't be able to access the cd drive, unless you have multiple drives. Once it's installed it's in /media/cdrom. To access it you need to mount the drive. That just means making it active, and needs to be done for all drives and partitions, though for your hard drive partitions you can set things to be mounted when the computer boots. To mount the cd-drive you type into a terminal "sudo mount /mnt/cdrom" If you need to mount something else you will have to have a different mount point, and replace the last part of the command. There's also ways to mount drives through the file driver. I can't remember how konquerer does it though. Also Ubuntu automounts drives normally, not sure about kubuntu.
3. No idea, hadn't even heard of .cdr file format before
4. For the most part installing things is real easy, no need to even use that cd, especially since it wouldn't work if it's for windows. Install using a program called Synaptic in Ubuntu, Kubuntu uses something else by default (kynaptic?), but I liked Synaptic better anyway. These are all just graphic frontends for a command in the terminal called apt-get. Using these you can install anything in the repositories, though you'll need a few more repositories to be enabled to really find everything you need. By the way you should already have something for burning CDs, in ubuntu there's gnome-baker, and kubuntu has K3B. 

For a lot of this information you should check out [this guide]("http://easylinux.info/wiki/Ubuntu")

---

### Post by C_P on 2006-03-21
As usual, this forum has fantastic help! Are these "repositories" a type of peer 2 peer files sharing that connects somewhere outside of my PC?
What I mean is people are referring me to the Synaptic repositories like this is the place that stores all the programs I need. When I go there do I do a search for lets say "firewall" and it will show me all firewall programs then I use the terminal and type apt-get (name of firewall program) and hit enter and it gets this program from the "peer 2 peer repository" and installs it for me?
Sorry for sounding like a typical noobie here, but I am currently at work and do not have the live CD to test this and actually not sure it would work with Live CD anyway.

---

### Post by LordBug on 2006-03-21
[QUOTE=C_P]As usual, this forum has fantastic help! Are these "repositories" a type of peer 2 peer files sharing that connects somewhere outside of my PC?[/quote]
peer 2 peer - No.  Outside the PC - yes. The repositories are more like websites or FTP sites, you download from them only.  No uploading on your part to them.

> What I mean is people are referring me to the Synaptic repositories like this is the place that stores all the programs I need. When I go there do I do a search for lets say "firewall" and it will show me all firewall programs then I use the terminal and type apt-get (name of firewall program) and hit enter and it gets this program from the "peer 2 peer repository" and installs it for me?
Sort of correct.  Synaptic is a graphical front end for apt-get.  You can search it, like for "firewall" as you stated, and then you can install the program(s) directly from synaptic.  Just right click and check "Mark for Installation".  Once you have all the marks you want made, click the "Apply Changes"(?not at home, this might be wrong?) up top and it'll do the appropriate apt-get commands for you.

---

### Post by mostwanted on 2006-03-21
[QUOTE=C_P]As usual, this forum has fantastic help! Are these "repositories" a type of peer 2 peer files sharing that connects somewhere outside of my PC?
What I mean is people are referring me to the Synaptic repositories like this is the place that stores all the programs I need. When I go there do I do a search for lets say "firewall" and it will show me all firewall programs then I use the terminal and type apt-get (name of firewall program) and hit enter and it gets this program from the "peer 2 peer repository" and installs it for me?
Sorry for sounding like a typical noobie here, but I am currently at work and do not have the live CD to test this and actually not sure it would work with Live CD anyway.[/QUOTE]

The repositories are basically download sites set up by Ubuntu, Debian or whoever is offering a lot of packages. You'll probably never need to enable more than the 4 official Ubuntu repos (main, restricted, universe, and multiverse). It's not peer-to-peer as you don't upload anything yourself - think of it as a more comprehensive version of Windows Update.

---

### Post by C_P on 2006-03-21
Are these paid programs to download? I guess I am used to Window$ where you have to pay for ALL programs.

---

### Post by mcmillan on 2006-03-21
No need to pay. That's the nice thing about linux, almost everything is available for no cost.

---

### Post by C_P on 2006-03-21
Is there a product in this "repository" that will allow you to view Windows documents such as .doc and .xls files?

---

### Post by Brunellus on 2006-03-21
[QUOTE=C_P]Is there a product in this "repository" that will allow you to view Windows documents such as .doc and .xls files?[/QUOTE]
depends on which version.  OpenOffice.org Writer and Calc (the wordprocessor and spreadsheet programs included in ubuntu) will read and write .doc and .xls files.  the MS Office 97 format files are quite well-understood and easily-managed.  Office 2000 and XP files are supported, but there are a few formatting gotchas.  

My father, incidentally, runs OpenOffice 2.0 (on Windows) and was largely satisfied with the file compatibility.

---

### Post by C_P on 2006-03-21
Ok, let me get this straight:
1. This OS appears to be safer, faster, and more reliable.
2. It is free and customizable.
3. If you need a program go get it in the repository (for free) and install it.
4. This OS is not just an OS but these packages come with the OS and also run Window$ files (or some anyway)
5. Everything you need is built in, free, safe, and secure and if you need help the Ubuntu forums replies are so quick and eager to assist there is no need to worry?

I have one more question, WHY USE WINDOWS?   
I realize I sound like a pitchman or salesman for this OS and it's packages but this just seems too good to be true.

---

### Post by Brunellus on 2006-03-21
[QUOTE=C_P]
I have one more question, WHY USE WINDOWS?   
[/QUOTE]

In the interest of fairness and balance, I'll answer this, too:

1) Device compatibility.  Some devices don't have drivers for them in Linux, but have windows-only drivers.  Main offenders:  wireless LAN adaptors, printers, webcams.  If you're thinking of installing, I recommend you look at what hardware you'll be using, and the degree to which it is supported natively (i.e. 'out-of-the-box'.  Study now to avoid pain later.

2)  Commercial software. Let's get this out of the way right now:  there is no iTunes for Linux.  There is no MSN for Linux.  There is no MSOffice for Linux.  There is no Dreamweaver for Linux.  There is no Macromedia Flash for Linux.  There is no Adobe Photoshop for Linux.  There is no Call of Duty for Linux.  There is no World of Warcraft for Linux. 

If you are dependent on commercial software, by all means keep a windows machine or partition so you can run the software that you need.  But don't migrate and then complain bitterly about the lack of well-known commercial applications.  You have been warned.

3)  Multimedia codec support.  This is a trick question, since Windows has no codecs "out of the box" either, but since most users simply use the preinstalled windows image they bought from their computer manufacturer, they have no way of knowing that the OS really ships "stripped."  This is trivially added to ubuntu, but requires some actual effort.

In sum:  this is a great OS.  I love it, and prefer it to Windows.  But it is NOT WINDOWS.

---

### Post by C_P on 2006-03-21
Well said and points taken. So dfar my hardware all seems to be picked up and working.. so far that is.
I do not game nor really care to.
If it does what I need it to do and runs safely so I do not have to worry when I boot if my firewall is stopping idiots, my AV is up to date by the second and always running in the background, the system does not require a reboot when it gets tired, and I do not have to pay $300 to $400 just for an OS and aproximately the same amount for MS Office, etc... it sounds good to me.

---

### Post by LordBug on 2006-03-21
> 4. This OS is not just an OS but these packages come with the OS and also run Window$ files (or some anyway)
Ubuntu isn't an OS.  It's a distribution of an OS (Linux) that also gives you a boatload of applications so you can do things.  Windows isn't much different, honestly.

> 5. Everything you need is built in, free, safe, and secure and if you need help the Ubuntu forums replies are so quick and eager to assist there is no need to worry?
Ubuntu installs 95% of what people need.  Another 4% is available in the repositories.  The last 1% may or may not exist in Linux (yet).  These forums are wonderful for asking questions, but are not 100%.  Sometimes an answer just isn't out there right away.

---

### Post by C_P on 2006-03-21
[QUOTE=LordBug]Ubuntu isn't an OS.  It's a distribution of an OS (Linux) that also gives you a boatload of applications so you can do things.  Windows isn't much different, honestly.[/quote]
Thank you very much for the clarification.
I understand and I am now aware of the distribution reference with the OS. I am just used to Windows basicly only including the OS.

> 
Ubuntu installs 95% of what people need.  Another 4% is available in the repositories.  The last 1% may or may not exist in Linux (yet).  These forums are wonderful for asking questions, but are not 100%.  Sometimes an answer just isn't out there right away.
Windows does not offer a "repository" for its users and is a great feature of Linux.

---

### Post by Brunellus on 2006-03-21
[QUOTE=C_P]Thank you very much for the clarification.
I understand and I am now aware of the distribution reference with the OS. I am just used to Windows basicly only including the OS.


Windows does not offer a "repository" for its users and is a great feature of Linux.[/QUOTE]
...of Ubuntu.

Linux is just the kernel;  the rest of the OS is a bunch of other programs that runs on the kernel.  

Ther are linux distros that don't use the central repository method.

---

### Post by C_P on 2006-03-21
[QUOTE=Brunellus]...of Ubuntu.

Linux is just the kernel;  the rest of the OS is a bunch of other programs that runs on the kernel.  

Ther are linux distros that don't use the central repository method.[/QUOTE]
OUCH, thank you again for this info. Do you know if Kubuntu or PCLinux offers the "central repository method"?

---

### Post by Brunellus on 2006-03-21
[QUOTE=C_P]OUCH, thank you again for this info. Do you know if Kubuntu or PCLinux offers the "central repository method"?[/QUOTE]
Kubuntu is just Ubuntu with KDE (different desktop environment).  as in it Komes with programs whose names Kommence with the letter K.  Konsistently. :-)

Don't know about PCLinuxOS.  

In practice, lots of distros can be and have been adapted to the Debian way of doing things (i.e. the way Ubuntu handles programs), either by adopting .deb/apt (as ubuntu, mepis, knoppix, and the other Debian Daughters do) or by implementing apt on top of their usual package management systems (apt4rpm, slapt-get) or by developing equivalent ways of doing things (yum, portage)

---

### Post by Dr. E on 2006-03-21
Yes, PCLinuxOS has a central repository for programs.

---

### Post by C_P on 2006-03-21
As always, you all are simply amazing. This thread seems to answer a typical noobies questions on this subject. Great job all of you!

---

### Post by dvarsam on 2006-03-21
Hello!

I can answer questions 6, 8 & 9:

6.  How do I create a shortcut on my desktop? I can see how to add to panel but not desktop?

Read Article#:144613	- Create a Shortcut to another Partition.
Read Article#: 145991	- How to create a "launcher" (or "shortcut") on the "Applications" Menu?

8. How do I install programs that I download? Double click? Because this did not work with Thunderbird email client.

I have NOT read this thread much (because it is very late in my country) & I believe that probably many people have answered this...
However, let me also suggest you to read my Tutorial on How to Backup programs you install with "Synaptic Package Manager".

Read Article#: 134921	- Tutorial &#8211; How to get those valuable ".deb" Program Files & Back them Up

9. I cannot find a way to set up Hotmail with this Evolution Email client.
    I could set it up in Outlook under HTTP settings. 

I do NOT think you will be able to do this...
Microsoft is pretty strict with this & requires that you USE only its products to access a Hotmail account (e.g. Outlook Express, etc.)...
I suggest you open an E-mail account with another company.
I currently have 3 E-mails: hotmail, yahoo & aol.
Let me suggest that you open an Email account with a Provider that supports IMAP protocol instead of the old POP3 protocol.
IMAP is better than POP3 because you do NOT have to download EVERY Email in your PC to then be able to work on them...
It just shows them (instantly) & you just do stuff without the downloading part - so it is much-much faster...
Unfortunately Microsoft & Yahoo charge this service, so you better NOT select these guys if want to try out a IMAP account...

Have Fun !!!

---

### Post by C_P on 2006-03-22
Thank you for the great info! I am enjoying playing with Kubuntu. If there is a Kubuntu user out there can they please answer this question?
I pluged in my Canon Power Shot USB and turned on my camera. I went to Syste (I believe it was) and it saw my Canon! However, I cannot figure out how to see or import the images from the camera? I went to all of the media options and could not get it to load or import my pictures or figure out how to do this.

---

### Post by Brunellus on 2006-03-22
[QUOTE=C_P]Thank you for the great info! I am enjoying playing with Kubuntu. If there is a Kubuntu user out there can they please answer this question?
I pluged in my Canon Power Shot USB and turned on my camera. I went to Syste (I believe it was) and it saw my Canon! However, I cannot figure out how to see or import the images from the camera? I went to all of the media options and could not get it to load or import my pictures or figure out how to do this.[/QUOTE]
please search the forums and, if you don't find an answer, post a new thread.  that'll significantly increase the chance that your question is answered.

---

### Post by C_P on 2006-03-22
Thanks again, I will do so. Have a great day.

---

