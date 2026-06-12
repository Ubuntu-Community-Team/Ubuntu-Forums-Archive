---
title: "Device drivers and Anti-virus program + ?"
date: 2005-12-14
forum: Absolute Beginner Talk
---

### Post by Fibre on 2005-12-14
Ubuntu noobie onboard-

Ok got it's running, love it, goes well. But I've noticed that in device management there are some area's that are not fully recignised.

eg - motherboard chipset - it knows the brand name but thats all.
       ati sapphire radeon 9550 256mb agp card

Just to name a few- I don't know but is there some way to have my system checked sought of like the wizard in windows or is it as simple as using my motherboard and graphics disc's that came with those pieces of hardware?

Also I'm wondering about an Anti-Virus program and also something like Ad-Aware SE. I'm assuming that I'll still need these items for secure use of the internet.

I've read through forums section at the beginning of the beginners talk (stickies)
but after about 10 pages of that and getting no where well not exactly true the first page did show me a list of firewalls to choice from and an up to date list of alternative software.

I wear glasses for reading and there tuckered out having looked around late last night and having little sleep, then starting again this morning. Not to mention that I'm a slow reader. LOL

Anyhow do I need these internet applications for security and if possible some simple straight forward info on drivers for more system please.

Thanks for the patience and assistance I've received here so far. I appreciate the collective help I'm receiving.

---

### Post by Mustard on 2005-12-14
The drivers are built into the kernel for the most part.  With regards to the ATI graphics card you would need to install ATI drivers.

Here are some links for ati..
[https://wiki.ubuntu.com/BinaryDriverHowto/ATI](https://wiki.ubuntu.com/BinaryDriverHowto/ATI)
[http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10](http://www.ubuntuforums.org/showthread.php?t=24557&page=1&pp=10)

Anti-virus is not necessary unless you have other windows computers that you share files with, as viruses won't affect linux, but you could inadvertently pass a virus on to another computer on your network.  If you have a standalone system then there really is no need for virus protection.

Adaware is not necessary either.  The software you will be using is open source, and won't contain spyware.

About the only thing you would need to do, is if you are running services of some kind. like a web server or ftp server then you could activate the built-in iptables firewall using the firestarter frontend.  Firestarter is installed via synaptic package manager.

---

### Post by Fibre on 2005-12-14
Great thanks,

I've already installed firestarter, but now I've noticed another problem with my sound after I updated last night things where fine but after booting up this morning there is no sound?

I am thinking of running a server on my other machine once I have the hang of the basic's. But I think I'll listen to what you have to say there and go with Ubuntu on that machine also before I start. I'll start off just using it for gaming purposes when I do as far as server aspect goes.

Also if you could suggest an anti-virus, I may place one on anyway just for the security of others. If I send something to another person and it's infected they wouldn't be to happy with me :).

Thanks for the help Mustard much appreciated.

---

### Post by Mustard on 2005-12-14
You could download clamav via synaptic for virus checking.  There is nothing very fancy about clamav.  A lot of the virus checking stuff is going to be command line stuff.

There are a number of different ones that are available.  If you open synaptic package manager and use the keyword 'virus' in the search field using the 'Name and Description' search option, it will list all the packages that have 'virus' in description.

With regards to your sound, what soundcard are you using?

When you say it doesn't work, could you elaborate on what things you have tried and are no longer working?

---

### Post by Fibre on 2005-12-14
oddly enough it works now I re-booted to xp for a while and now am back with ubuntu and the sound is there again?

It's actually intergrated sound, I'm thinking I've got a lot of study to do with this system. I've got a MSI board, a px8 Neo-V with - AC97 intergrated in VT8237
                                                                           VIA 1617 6-channel audio codec
                                                                           compliant with AC97 v2.2 Spec

I was given a site where you enter specific codes relating to installing software/ activating software?([http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php))

So is it the way they state to do it here like this:

I'd type these commands in a **terminal**:

sudo apt-get update
sudo apt-get install (mozilla-thunderbird)- put (clamav) [U]or something similar from the site I'm refrencing to?
[/U]

Or is there a simpler way to do it where you have a bit of a choice and just click on it.

Also there doesn't seem to be any explanation as to the **Terminal** Its probably stairing me in the face but I can't seem to find it.

I know you can go to Applications/Add Applications/Add-Remove and I've tried there before and will try again now with the name you've given me also.
Just rattling off what I've done to give you an idea where I'm at.

Here's the choices I've found but I'm not sure which is best for ubuntu, I've only looked at one, the first one. I'm just not sure which are suited to this system and to save time I was hoping someone might have an idea of the best choice.

Save me going through them all installing / uninstalling etc etc. + they might seem good to me, but what are they missing? whats getting past the program?
It took me sometime on windows to decide which application was best but if I could narrow it down with you guys it would save sometime for other stuff.

Here's the list of choices I have but exclude the 1st one, it only suits version4 something for ubuntu.

1) Dr. Web. [Prop]
2) Trend ServerProtect. [Prop]
3) RAV Antivirus. [Prop] (Bought by Microsoft?)
4) OpenAntivirus + AMaViS / VirusHammer.
5) F-Prot. [Prop]
6) Sophie / Trophie.
7) Clam Antivirus.
8) Kaspersky. [Prop]
9) YAVR.

what does [Prop] stand for ?

I value the opinions of you guys, your more advanced than I and there's no need to re invent the wheel as one of my irritating teachers once use to tell me LOL.

Thanks for getting back to me Mustard. :)

I've also just found this :-

If you're using Ubuntu (Gnome):
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

But how do I open up a terminal LOL

So easy the Terminal is in Applications/Accessories and there it is far out LOL

Also if you want to put the Terminal on the right click menu of your mouse here's the script if I'm wording it correctly:-

Type 'sudo apt-get install nautilus-open-terminal'

---

### Post by Fibre on 2005-12-14
Your not wrong when you said :-

There are a number of different ones that are available. If you open synaptic package manager and use the keyword 'virus' in the search field using the 'Name and Description' search option, it will list all the packages that have 'virus' in description.

I put in virus as you suggested and man 40 choices - see you in a month LOL.

If there is anyone out there with some good recommendations on an Anti - Virus it would be helpful there are just to many to choose from. Preferably one that doesn't involve scripting constently to use it.

Thanks a lot though Mustard your direction and advise has opened me up to a lot of new area's now that I didn't know. LOL

Whether that makes me any the wiser though.

When trying this step on this site - [http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

If you're using Ubuntu (Gnome):
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

for Enabling Extra Repositories it would ask me for a password but wouldn't allow me to enter my password or anything for that matter.

Does this mean I'm all up to date ? and it won't allow me to do it?

I tried copy and pasting a line at a time as well as both lines but it just came back with password? and a black rectangled cursor that I couldn't write in?

And I only did a standard instalation not advanced.

---

### Post by mcmillan on 2005-12-15
When it asks for your password type it in and hit enter. Nothing will show up, but it still registers, better security since even if someone can see the screen they can't see the number of characters in the password. 

What those commands do, is the first makes a backup of your apt sources in case you screw something up. The second will open the source file with a text editor, which you then can edit as described on the website. Easy enough. 

Don't know much about the anti-virus. I installed Clam but don't really use it very regularly. It seems to work easily enough. I think I may have tested Dr. Web but had some trouble getting it to work, can't remember for sure.

---

### Post by earobinson on 2005-12-15
great AV/Security thread [http://www.ubuntuforums.org/showthread.php?t=98912](http://www.ubuntuforums.org/showthread.php?t=98912)

---

### Post by Mustard on 2005-12-15
I don't use anti-virus much myself either.  I installed clam but I rarely ever have a need to use it.  Any viruses I get are usually in my email, and its pretty obvious they are viruses, so there is never much need to test them, other than for curiousity value.  Occasionally I save a virus or two so I can show friends that it won't do anything when you double click on it in linux.

From the sounds of your above posts, Fibre, you have found the terminal.  Just in case I misread what you have been doing though, it is found in the Applications>>Accessories menu.

Might I also suggest that if you want join the ubuntu IRC support channel you can ask as many questions as you like in there.  The x-chat irc client for ubuntu is installed already, and can be found in the Applications>>Internet menu.  When you start that up you can join the Ubuntu servers and it should automatically take you to the #ubuntu channel where a lot of people hang out and assist others in learning how to set up and use ubuntu.

Ubuntu IRC server: irc.freenode.net
Channel: #ubuntu

Below I have included some links that explain some of the basic funtions of the Terminal (also known as the command line interface or cli).
[https://wiki.ubuntu.com/BasicCommands](https://wiki.ubuntu.com/BasicCommands)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://www.tuxfiles.org](http://www.tuxfiles.org)

---

### Post by Fibre on 2005-12-15
Mcmillan thank you for your help that did the trick all is better now :) well almost my sound isn't working again LOL. Looks like i have a slight problem there.

Earobinson thanks for the info. I got past the first persons comment in the thread and will go back to it as soon as possible and depending on the final outcome of the comments, I will make a choice whether to install an Anti-Virus or not. It's more of a concern for others, that I was wanting to install it. Say I send an email with something in it and it has a virus it won't hurt me but I don't see it and pass it on and well you get the picture.

Mcmillan thanks for the choices you gave me. I'll hold of for the moment and see how it pans out with this thread I'll read later. If I'm not satisfied I'll just install anyway, which may be the case. I'd rather be safe than sorry, even if it isn't for me.

All replies are appreciated.

And if someone has a solution for me about this sound problem please drop me a message. The info is on message #5 of this thread.

Thanks for all the help I'm getting of everyone :)

---

### Post by Fibre on 2005-12-15
Great Mustard I think it might be the go.

I'm going to give it a break for tonight though and perhaps get into it again tomorrow sometime.

I've put sometime into it over the last 24hrs or so and feel it's time to give it a nights rest for now. But chating probably would speed things up and any extra help would be great.

Thanks for the offer mate. 

I got about 5hrs sleep last night so I'm dying to crash.

Just wanted to see what was going on in the forum and have another stab at it before I went to bed.

---

### Post by Mustard on 2005-12-15
I'm off to bed myself soon.  I'm winding down for the day just looking over the forums. ;)

---

### Post by bscbrit on 2005-12-15
Everyone is correct in saying that you don't need an anti-virus, but that doesn't mean that it is of no use.  Imagine, you could forward an email containing a virus to a friend who uses windows.  You would not know until he 'thanked' you.  
I use clamav all the time, it integrates well with evolution, and it catches a couple of viruses a day which, although they are harmless to me, I wouldn't want to send to anyone else.  But I think that any of the AV programs in the repositories will do an adequate job.
I'm not much good at sound problems - I've managed to get my own working reliably but it is not the same system as yours and I suspect there is not much to read across to your own circumstances.

---

### Post by kingsidy on 2005-12-15
As far as as program similar to adaware, there is a program that i use that checks for rootkits, i think that the program name is "chkroot" look it up in synaptic.

---

### Post by Fibre on 2005-12-15
Excellent thanks for the sites Mustard now what to poke my stick at LOL.

I'm thinking I'll try to hook up to the - Ubuntu IRC server: irc.freenode.net - although something makes me think I'm going to have problems there because of my sound problem that still exists.

I'll start a new thread for that first then once I've got it going I'll try and hook up, got a head set so I'm set that way.

---

### Post by Fibre on 2005-12-15
Thanks for the info and feed back bscbrit,kingsidy and Mustard.

I just posted then and all of a sudden your 3 posts popped up before mine, just so you know I'm not ignoring LOL.

Yeah I think I will go with the Anti-Virus then and also this other program you suggested kingsidy.

But first of all I've gotta get my sound soughted? Which I'll start a new thread on so that people can see it is specifically related to sound.

Thanks guys. :)

---

