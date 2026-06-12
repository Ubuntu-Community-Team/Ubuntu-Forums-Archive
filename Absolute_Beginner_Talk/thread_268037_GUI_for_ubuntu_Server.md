---
title: "GUI for ubuntu Server"
date: 2006-09-29
forum: Absolute Beginner Talk
---

### Post by jbru on 2006-09-29
Hi, I'm a bit new to linux so i'm trying to get the hang of things.  I just recently installed Ubuntu server on one of my computers to get familiarized with it.  The problem is, it installed without a GUI and I really don't know where to begin from the command line.

I heard it was possible to install KDE using the apt get command set but i also heard that by default some things like GUI installs are disabled and their settings need to be edited. 

I looked through the wiki and couldn't find any specific articles dealing with this issue, so I thought I would turn here.

What do I need to do in order to set up ubuntu server with a gui?

---

### Post by Klaidas on 2006-09-29
in short:
> sudo apt-get install ubuntu-desktop

---

### Post by Marsolin on 2006-09-29
Installing ubuntu-desktop will get you Gnome and a lot of other apps. Installing kubuntu-desktop will get you kde and a lot of other apps.

If all you want is the KDE without too much extra baggage then use the following command:

sudo apt-get install kdebase kdm x-window-system-core

That has everything you need to get KDE running.

---

### Post by Matt_BLah on 2006-09-29
hi, I am new to ubuntu server as well.

what I am getting from the first reply is this-

type in that command (have ubuntu server install CD in) and it will install the GUI right there or do we have to do something else as well?


Edit: this is what happenes when I type it in--

Reading Packare list.... Done
Building dependency tree.... Done
E: Couldnt find Package ubuntu-desktop


ummmm not good I think. Hope you can help me out.

thanks,
Matt_BLah

---

### Post by nthdegree on 2006-09-29
If you wanted a GUI then you want the **Ubuntu Desktop CD** or the **Ubuntu Alternate CD** because the Ubuntu Server CD is for a non-GUI system.

Servers aren't meant to have GUIs because they are a serious waste of CPU clock cycles.  Perform a **desktop** install and **NOT A SERVER INSTALL**.

---

### Post by Matt_BLah on 2006-09-29
well I am a XP user and I didnt know that it wouldnt come with a GUI plus I installed the server for the preconifed html, mysql, php stuff..... so if all I want to do is install the GUI into the server edition what sould I do?

---

### Post by Abhi Kalyan on 2006-10-24
sudo apt-get install ubuntu-desktop
works fine,
After install type
startx at the root prompt

I have a problem and it would be great if someone could help 
My problem is after installing ubuntu desktop in server, am not having the add/ remove option?

---

### Post by brentoboy on 2006-10-24
abhi,  pick a thread, and stay there -- ask all your questions in one place so that people can stick with you and walk you through.

what add/remove option are you looking for?
add/remove programs?  or remove the ubuntu-desktop? or users? ...?

---

### Post by dmizer on 2006-10-25
> **Matt_BLah said:**
> well I am a XP user and I didnt know that it wouldnt come with a GUI plus I installed the server for the preconifed html, mysql, php stuff..... so if all I want to do is install the GUI into the server edition what sould I do?

if all this machine is going to be is a server, don't install a gui.  if you install a gui, you'll kick yourself for it later.  there are other tools available to you to give you a point and click interface and management.

for example: webmin ... [http://www.ubuntuforums.org/showthread.php?t=195093&highlight=webmin+dapper](http://www.ubuntuforums.org/showthread.php?t=195093&highlight=webmin+dapper)

try to step away from the "i need gui" thinking process.  particularly with a server, you'll end up doing everything in the command line anyway (with very few exceptions).  ssh and webmin are your friends, and frankly ... i'm not sure what would be available to you in a gui for server administration.

---

### Post by tubasoldier on 2006-10-25
You can not install a gui with your server installation disk. Simply because it is not there.
Assuming that your software repositories are set up correctly the apt-get ubuntu-desktop command should work. But from the looks of your "error" you got your repositores are not set up properly. I would reccomend looking at ubuntuguide.org It will give you information on how to add more software repositories so you can install a gui. 

Hope this helps.

---

### Post by dmizer on 2006-10-25
there is not a problem with the repositories, and nothing is preventing you from installing a gui desktop from the server cd.  in fact, you don't need a cd at all to install the ubuntu-desktop meta package (just comment out the cd line in sources.list).

```
sudo apt-get update
```
before installing ubuntu-desktop will fix the problem.  but again, if you want a server ... don't install a gui.  if you have problems doing something, search here on the forums. nearly ALL howto's are forumlated in command line directions anyway.  in a server environment, there is absolutely no need for a gui.

edit: actually, i'll take a step further ... in a dedicated server environment a gui is useless.

---

### Post by Abhi Kalyan on 2006-10-26
> **brentoboy said:**
> abhi,  pick a thread, and stay there -- ask all your questions in one place so that people can stick with you and walk you through.

what add/remove option are you looking for?
add/remove programs?  or remove the ubuntu-desktop? or users? ...?
1. Sorry about going to lot of places.
2. I was under the impression that a thread deals with only a certain scope, hence am looking around to get the doubts cleared
2a. am constantly checking the threads and am not randomly creating threads.
2b. After being here for a while i feel that i need to give as much as i take,
2c. Where ever possible i keep quite and only quote or drop in links and information that more experianced users had passed on to me ( with referance/credits to them off cource )
2d. have been passing on the information ( your posts are so good that am not able to stop myself from giving it to others who or on the look out - Thank you , and super Job brentboy [ i have even memorised you name and the names of a great many who have been helping me in this forum])
3. add/remove
pick on "applications" on the top of the screen
in the drop down menu, the last line has "Add/Remove"
Am not having this in the desktop installed on a server.

Thank you Brentoboy, you have helped me a lot and i felt i owe you an explanation atleast with regard to my behaviour,
Hope you understand that i respect everyone in this forum and do not intend to be disruptfull in any way.

Thank you.
Sincerely
Abhi Kalyan

---

### Post by brentoboy on 2006-10-26
I didnt mean to be harsh,  I just figured you would be more likely to get consistant help if those people who decide to help you only have to watch a couple of threads.

often times, people will pick up on a person who is struggling with something that they have some experience with, and they subscribe to that thread to keep a heads up on it and be more helpful.  I was just noticing that your questions were spread all over, and often times they were in other threads that started with different issues.

I'm not so worried about you "cluttering" up other threads, heck, most threads dont stay on topic for more than 5 or 6 posts anyway.  I was looking at it more from the standpoint that a single thread with your whole story, one question at a time will likely help another guy who is starting in the same place as you and ends up going through a lot of the same stuff.

---
anyway,  I'm not sure why the Add/Remove Applications option isnt working.  But, the "real" way to add remove packages is to use synaptic.  Look in System->Administration->Synaptic Package Manager.


The stuff in the "nice" Add Remove Applications area is mostly just user applications anyway, the services are added through synaptic.

---

### Post by Abhi Kalyan on 2006-10-27
Not at all brentoboy, I did not take any offecne on what you had posted.
I just keep learning from every post.
Am currently working on the milestones, and also on opening certain key threads which could document all the problems and solutions which were encountered during this project.
Thank you once again.

As for the add/Remove it came up after we installed " Configuration editor"
under Applications->system tools->Configuration editor.

Have started using the synaptic pretty much, but am not able to uninstall program's now.

Will keep posting.
Thank you once again

---

### Post by neill on 2006-10-31
just to pick up on a couple of points re GUIs for servers

i agree of course that in the ideal scenario a server should be CLI only

however i guess a lot of people, myself included, are XP converts and find the CLI an extra barrier to usage - not an insurmountable one by any means, but present nonetheless

i have seen elsewhere on the forums suggestions that some sort of minimalist server GUI might be useful (cf OS-X server admin GUI) - after all AFAIK it's just a matter of constructing a list of packages and then you could apt-get it after the server install or it might be an install option up front. the GUI could be ***very ***minimalist and lightweight (XFCE, fluxbox or IceWM based) and contain [FONT="Arial Black"]only [/FONT]those GUI tools which you would need for server admin

personally i think this is a good idea - it would certainly cater for those people running servers for small home or work networks who have hardware options which will compensate for the 'wasted' clock cycles - but who lack the full set of skills/confidence needed to administer it all from the CLI

what d'you think ? :-k 

on a side note - if i install the server CD and get to the CLI, how do i proceed to use webmin ?

thanks

neill

---

### Post by brentoboy on 2006-10-31
something like this...

[http://www.guibuntu-server.org/guibuntu.html](http://www.guibuntu-server.org/guibuntu.html)

---

### Post by dmizer on 2006-10-31
> **neill said:**
> on a side note - if i install the server CD and get to the CLI, how do i proceed to use webmin ?

you simply browse to it with a computer and internet browser of your choice (firefox), by entering [https://serveraddress:port](https://serveraddress:port) in the address bar.

this can be done from any computer attached to your local network.  also, if you open the port (usually 10000) through your firewall you can even access it remotely ... but this is VERY insecure, as the only thing that will prevent system wide access to your server is a password.

this means ... you don't even need a monitor, keyboard, or mouse attached to your server in order to administrate it.  and this is why a gui is unnecessary.

---

### Post by MetalMusicAddict on 2006-10-31
If you want to use a machine as a server with a GUI I recommend using Xubuntu. Its what I use. You still get some unneeded things but its lighter than K/Ubuntu. Or you can do a server install and install Fluxbox along with the tools you need.

Feel free to PM me if you want more info. I have a small 5 machine home network. It has win, linux and sometimes OSX machines.

---

### Post by JayTee on 2006-11-01
I think it's ok to install a GUI on a server but if I was going to run one dedicated I'd shutdown GDM and X-server when not "needing" the GUI. I agree though that for the most part the better way to learn the server and get the most out of it is from the CLI. Even Microsoft is taking a step in this direction with Windows Server 2003. There are way more command-line options in it than there are in Windows 2000 Server so that admins can use scripts and automate tasks easier. Still, just having the GUI running on a Windows Server is alot of memory overhead that would be better off freed up for MSSQL (memory hog) or file and print sharing services. Linux servers have an edge in this department and in most cases can outperform a Win2K3 box even running on slower hardware. Less overhead + more efficient kernel = better performance.

---

### Post by neill on 2006-11-01
> **brentoboy said:**
> something like this...

[http://www.guibuntu-server.org/guibuntu.html](http://www.guibuntu-server.org/guibuntu.html)

exactly like this ...... :D 

(in the interim i'm playing around with webmin to see if i can do all the things i need to with that)

neill

---

### Post by stalker145 on 2006-11-01
> **neill said:**
> (in the interim i'm playing around with webmin to see if i can do all the things i need to with that)

neill

I've been tinkering with WebMin for a couple of weeks now and haven't come across much of anything server-wise that I can not do. I have been very much impressed by this software.:D

---

### Post by louieb on 2006-11-01
Just my 2 cents worth on installing a GUI on a server machine.:twisted: 
  I have installed Ubuntu Brezzy on an old P1, 200 mhz, w/128 mb memory. The Gnome Desktop is very functional if abbetly slow on this machine.
  If I am running a server it is going to be a P4 or better w/a couple gig of memory or better. I doubt the installation of a desktop on such a machine is going to make a measurable diffrence in performance on that machine. 
  It is my feeling the server adminstrator can use the GUI to be more productive and get things done easier. Sure there will always be a need for the CLI (even widows has one) but with the speed and price of todays hardware give me the a GUI for day to day tasks and save the CLI for when its needed. :rolleyes:

---

### Post by bsussman on 2006-11-01
> **nthdegree said:**
> If you wanted a GUI then you want the **Ubuntu Desktop CD** or the **Ubuntu Alternate CD** because the Ubuntu Server CD is for a non-GUI system.

Servers aren't meant to have GUIs because they are a serious waste of CPU clock cycles.  Perform a **desktop** install and **NOT A SERVER INSTALL**.

If one has worked hard to install server, that would have the undesirable effect of wiping out all that work.

According to my system monitor, very little cpu is used when I am not using the gui.  So the convenience of the gui MIGHT outweigh the cost when I am using it.

installing xxxxxx-desktop or or only the two specified packages should have the desired effect.

---

### Post by atomix on 2006-11-02
If you really want to install **ubuntu-desktop** (or any other package) from **cd** on your server, use the **"Ubuntu Alternate CD"**.

 sudo apt-cdrom add 
[sudo apt-get update] 
sudo apt-get install ubuntu-desktop 

 It works fine!"

---

### Post by mmadsen on 2006-11-11
If, when you type "apt-get install ubuntu-desktop" and it cannot find the package, it may be likely that:

1.  You have the server CD-ROM in the drive
2.  You have the CDROM line uncommented (i.e., default situation) in /etc/apt/sources.list.

If you comment out the CDROM (assuming you have internet access) line in /etc/apt/sources.list, type "apt-get update" as root, and then try the install of "ubuntu-desktop" again, APT will look for the package in the Ubuntu repository online instead of looking on the server CDROM and the install should work.

---

### Post by Abhi Kalyan on 2006-11-13
> **mmadsen said:**
> If, when you type "apt-get install ubuntu-desktop" and it cannot find the package, it may be likely that:

1.  You have the server CD-ROM in the drive
2.  You have the CDROM line uncommented (i.e., default situation) in /etc/apt/sources.list.

If you comment out the CDROM (assuming you have internet access) line in /etc/apt/sources.list, type "apt-get update" as root, and then try the install of "ubuntu-desktop" again, APT will look for the package in the Ubuntu repository online instead of looking on the server CDROM and the install should work.
you could try apt-caher after installing apache2, it does a great job of bringing down internet bandwidth usage by caching packages locally.
Once we get the packages from the repository, its stored locally and we could play around how much ever we want with out having the need of downloading the packages numerous times.
Sorry if this is a repeat. If it is not a repeat i would love to illustrate the procedures and uses.
Sincerely
Abhi Kalyan

---

### Post by aml on 2006-11-17
> **nthdegree said:**
> Servers aren't meant to have GUIs because they are a serious waste of CPU clock cycles.

I agree  - but only if they're running. 

I always install a GUI and only have it launch if I start it manually. If the OP wants a gui on the Server than installing the Server CD may still be appropriate - if only because it installs such a minimal set of packages by default.

---

### Post by jvtexas on 2007-04-28
I am a newbee and installing 6.10 server edition.  I am also trying to get ubuntu desktop installed (to help ease the learning curve a bit).

If I use the commands posted by ATOMIX above, but use the 6.10 desktop CDROM, will that work?

Right now I am having trouble getting the IP settings to work.  If I do a fresh server install (not LAMP) and use DHCP, I get an IP address and can reach other devices.  Once I try to change to a static (*sudo nano /etc/network/interfaces*...edit file), it breaks.  Then if I try to revert back to DHCP, I not longer get an IP address assigned.  
I tried to install/configure resolvconf, but no luck (can't remember right now the errors, but it's basically not installed).
My next plan of attack is to get DCHP working again and leave it alone until I get the desktop installed and packages updated, then try to tackle the static IP.

My goal for this server is to host virtual machines using VMServer.

---

### Post by brentoboy on 2007-04-28
what you have there is a "plethora" of issues to work out.

you should post the ones that are not related to server gui's (like the dhcp stuff) in its own thread.  Partly because it is unlikely you will get help for that in this one.  People who have already read through this thread and decided that it no longer interests them wont see your question.

The sort answer to your dhcp question though is that you should use the network settings screen to set it to use dhcp then deactivate your network interface (in edgy and before there is a deactivate button, but feisty has a check box next to the interface.)

give it a few seconds to bring down the interface, and then reactivate it (or recheck the checkbox in feisty).  give it a few seconds to catch up, and then see if you have a functional browser when you are done.

then, open a terminal window and type this command:

sudo ifconfig

write down your gateway IP address, and dns servers and anything else in there that looks interesting.  (some of that shows up in the network tools application.

then when you disable dhcp, make sure and fill in all those settings so that your computer knows how to "see" the world.

if you have trouble beyond that, start a thread for it, or look for a thread with a very similar problem.
--
as far as getting a gui on a server, the answer seems to be to install from the regular desktop CD and then add the stuff that was recommended earlier (I think Az gave a quick command line that adds the lamp stack on your PC.

Good luck with that
For people looking to get a small office server or LAMP system up and going, I seriously recommend this excellent book:
"Linux Quick Fix Notebook" by Peter Harrison
Its part of the Bruce Perens' Open Source Series -- all of which are quite excellent.

---

### Post by jvtexas on 2007-04-30
Thanks for the reply, but I figured out what went wrong with the IP config.  Once I fixed it I was able to get the GUI installed.

To fix the IP config: I didn't notice that a line became un-commented in the interfaces file.  I replacing the missing '#' and it fixed the dhcp problem.  
I then updated aptitude and ran the install for the GUI.  The first pass failed because there was something missing or not updated, but it did offered a suggested fix (to update apt), which I did.  The GUI installed fine after that.

Now I need to do more research on changing the desktop to only load/start manually and installing VMServer.

Thanks for the suggestions on where and how to post to the forum.

---

### Post by RuRat on 2007-08-28
so how do i use my ubuntu server with webmin to print jobs off my network.  I have tried webmin and it says i need CUPS.  I have not been able to find a CUPS version that only runs from text based obviously so how do i do print jobs from ubuntu server w/o installing gui

---

### Post by pheedme on 2007-10-09
> **Klaidas said:**
> in short:

Cheers Very Helpfull... I installed server because running a Ultrasparc 5 I did not have the luxury of a desktop Distro.

If this sparcstation setup is a success, I think ubuntu will run very nice on sun enterprise server. Now I just need new power lines in my house ... Lol

Now Lets see if this thing can run beryl :)

---

### Post by perlDude on 2008-06-29
I have installed Kubuntu on my server and I sitting on the command line trying to start Kubuntu, any suggestion on how to start the GUI?

---

