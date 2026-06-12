---
title: "Uninstalled Ubuntu"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by linuxian on 2007-03-11
Hi,

I was running Ubuntu 6.06 (Dapper Drake) and ended up uninstalling it.

Why? 

Several reasons:

Installation process is confusing - for instance, can I run KDE apps under Gnome or do I have to get Kubuntu to do this? When you're looking in Synaptic for a program you can install, how can you tell if it will run under your version of Ubuntu (or Linux, generally?). There also seems to be too many ways you can install programs - i.e via Synaptic, aptitude (using apt-get command) or via Add/Remove programs menu list. 

For instance, I tried installing the eboard chess program. No matter what I did trying to install it, uninstalling it, then reinstalling it, it refused to show up in my programs menu. I still have no idea what I did wrong here. An attempt to install Wine didn't work very well either - that is, it did install, but some Windows apps I tried to run under Wine simply refused to work.

The help function in Ubuntu 6.06 didn't seem to work very well either. I'd click on the life-preserver icon and get... nothing.

Trying to configure Ubuntu to one's personal taste is time-consuming and not very clearly explained. I also found that while CUPS recognizes my old Canon s600 printer, some of the apps I installed did not have a driver for the printer.

I'm really disappointed. I had such high hopes for Ubuntu. I really have some moral and ethical objections to the way Microsoft is working lately, and saw Ubuntu as a chance to break free of the chains that the Redmondians are trying to put on millions of people with Vista. With so many distros out there and so many people working on providing Linux apps and support (your work is genuinely appreciated) I wonder if the reason why Linux is having some difficulty becoming mainstream could be a lack of co-ordination between all the developers and distro makers.

Maybe I need a distro that doesn't require a lot of command-line pokery-jiggery and works more like Windows. I just want something that is easy to use, and lets me do what I want to do. 

Maybe someone can point me in the right direction here. *sigh* :confused:

---

### Post by v8YKxgHe on 2007-03-11
> Installation process is confusing - for instance, can I run KDE apps under Gnome or do I have to get Kubuntu to do this? When you're looking in Synaptic for a program you can install, how can you tell if it will run under your version of Ubuntu (or Linux, generally?). There also seems to be too many ways you can install programs - i.e via Synaptic, aptitude (using apt-get command) or via Add/Remove programs menu list.

Yes you can run KDE apps under Gnome, and Gnome apps under KDE. Every single software in the Ubuntu repositories will work in the version of Ubuntu you are using, why would they put them in there else? Install software with the method you prefer the most, and the one you find easiest to use. 

> For instance, I tried installing the eboard chess program. No matter what I did trying to install it, uninstalling it, then reinstalling it, it refused to show up in my programs menu. I still have no idea what I did wrong here. 
The game you installed is a terminal based, which means it has no GUI. If you were to run it from Terminal it would work. What you want to install is 'xchess' I guess, or any of the other chess games there.

> An attempt to install Wine didn't work very well either - that is, it did install, but some Windows apps I tried to run under Wine simply refused to work.
Windows applications are programmed to work on MS Windows. Linux does not have native support for Windows applications, you really can not expect a project that is reverse engineering load of files, to run Windows applications flawlessly in Linux. Its far easier for you to just use Linux alternatives, instead of running Windows apps in Linux - if you're gonna run most of you're applications in Wine then you may as well just be using Windows.

Also, you only have 2 posts. This community is the largest and nicest I know of, post any, absolutely any question you may have - and I'm sure someone will come a long and help you.

Good luck, keep at it =)

---

### Post by HereInOz on 2007-03-11
Funny, I was poking about Vista yesterday, and I found it - confusing.

Why?  Simply because it is different from XP.  I have grown used to XP, having initially thought it confusing after 2000.  Why?  Because it was different.

Example:  In Windows 2000, there is a lovely dialog box that lets you access all you want to with regard to setting up users.  It is called the userpasswords control, and you get to it through Control Panel.  But in XP, you need to open a command terminal and type "control userpasswords2" to get that box.

So frustration was the order of the day until I eventually found how to do it.

So too with Vista.  I am still not sure how to configure users and networking in Vista, but with perseverance, it will become natural, and easy.

So too with Ubuntu.  XP is not 2000.  Vista is not XP.  And certainly Ubuntu is not Windows.  They are all different.

When I first encountered Linux (Fedora 3 actually) I was confused.  But with some effort I achieved a degree of comfort that allows me to use Linux (now Ubuntu Dapper) with contentment.  Still no expert though

If you wish to move house, then the moving requires research, investment and learning.  Put in that investment, and you will be free of Bill.  However, if you want to stay in the house in which you currently live, that is fine.

You have had only two posts, and it is a shame that you have decided that the move is not worth it after a short time.  A bit like homesickness - when you move house, you want to go back to the other one, I guess.

Most of what you have grizzled about is eminently sort-out-able.  The Canon printer could have caused you difficulties though - Canon doesn't help the Linux community much at all.

Maybe sometime soon you will have another go, and we look forward to seeing you here with the inevitable questions.

---

### Post by sad_iq on 2007-03-11
Well...you can install install programs with Synaptic...or using the terminal...it's better that way...try installing 15 programs with Synaptic...should take 10 min...try doing the same with sudo apt-get install program1 program 2... program 15 (all in one line)...it should take you 1 min. It's all about choices!!!
 If Synaptic shows a program...than it runs in Ubuntu(Kubuntu, Xubuntu, Edubuntu and the rest to come).
 "Trying to configure Ubuntu to one's personal taste is time-consuming and not very clearly explained" ...hmm...what could you not configure? The printer should work with the install of cupsys-driver-gimpprint (googled the answer)...and if you install a package and it doesn't show in the menu...simply type it's name in a terminal and it should start...if you have more post them!!!
 And wine is not ubuntu...it's just a package that's available for ubuntu(and other distros)...so i don't think that changing distros wil help you run your windows programs...try finding alternatives to your win programs to use with linux.

 You also fail to see the good side of ubuntu...no reinstall every 2-3 months because of windows registry getting messed up, no antivirus needed, no antispyware, no firewall(all that eating resources...computer and economical), no random crashes,it also has over 20000 free packages to install so it should very well cover your needs !!!

---

### Post by perce on 2007-03-11
Hi,

I can't add more to what other have told you, but I'll tell you my opinion

> **linuxian said:**
> 

Installation process is confusing - for instance, can I run KDE apps under Gnome or do I have to get Kubuntu to do this? 



You can run KDE applications under Gnome and vice versa. It doesn't always look pretty from an aesthetic point of view, but you have no loss of functionality.

> 
When you're looking in Synaptic for a program you can install, how can you tell if it will run under your version of Ubuntu (or Linux, generally?). 


It will: Synaptic, or whatever other program you will use, will automatically detect and install all the files you need to run the application.

> 
There also seems to be too many ways you can install programs - i.e via Synaptic, aptitude (using apt-get command) or via Add/Remove programs menu list. 


They are all interfaces for the command-line apt-get. In particular they are all compatible and you can use the one you prefer, and switch freely from one to the other.

> 
For instance, I tried installing the eboard chess program. No matter what I did trying to install it, uninstalling it, then reinstalling it, it refused to show up in my programs menu. I still have no idea what I did wrong here. 


Annoying, you're right, but there is a solution:
1. right click on "applications" on the topmost left corner
2. click on "modify menu" this will open a window called "menu layout"
3. In the window click on games on the left column, then on "new item" on the right.
It will open a dialog windows. Write eboard on the "name" entry and "/usr/game/eboard" in the command entry. 

At this point you will have an entry for eboard in the applications menu under games.
The eboard package doesn't seem to have an icon, so we can't make the menu entry look pretty unfortunately.

I use Edgy in Italian, so the instructions could be a bit different with Dapper.

> 
An attempt to install Wine didn't work very well either - that is, it did install, but some Windows apps I tried to run under Wine simply refused to work.


Does Windows run Linux applications? so why should the converse be true? Linux is not a slightly modified version of Windows, it is a completely different system, like OS X is for example.

> 
The help function in Ubuntu 6.06 didn't seem to work very well either. I'd click on the life-preserver icon and get... nothing.


It works for me. Are you sure you didn't have a broken installlation?

> 
Trying to configure Ubuntu to one's personal taste is time-consuming and not very clearly explained. 


You might be true here, but it's something you have to do it once in your life. 

> 
I also found that while CUPS recognizes my old Canon s600 printer, some of the apps I installed did not have a driver for the printer.


From the KDE printer manager I can find 4 different driver combinations associated to your printer. One of these four (most probably the recommended one) should work.
I don't have that type of printer, so I can't test. Have you tried to ask in the forum with a more detailed description of the problem?

> 
I wonder if the reason why Linux is having some difficulty becoming mainstream could be a lack of co-ordination between all the developers and distro makers.


Partly yes, but most of the reason is an insufficient cooperation from the hardware manifacturers. I bet you wouldn't find Windows easy if you had to install it yourself, then download and install all drivers and applications.

> 
Maybe I need a distro that doesn't require a lot of command-line pokery-jiggery and works more like Windows. 


This is the point: we do NOT want something that works like Windows. Linux has found its own solutions and its own way to handle things. 

> 
I just want something that is easy to use, and lets me do what I want to do. 


Like Ubuntu :D

---

