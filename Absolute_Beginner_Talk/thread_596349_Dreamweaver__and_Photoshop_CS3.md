---
title: "Dreamweaver  and Photoshop CS3"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by ohmycar on 2007-10-29
Anyone know how well Dreamweaver CS3 and Photoshop CS3 work under wine?

Also anyone know of a good alternative to Dreamweaver that runs native on linux, kind of like how Gimp is the alternative to photoshop?

---

### Post by Maestro23 on 2007-10-29
You can check the Wine App DB for info on how well those 2 programs run under Wine.
[http://appdb.winehq.org/](http://appdb.winehq.org/)

For a Linux alternative to Dreamweaver, there is Kompozer (formerly NvU). It's pretty close to DW.  It's available thru Synaptic.
[http://www.kompozer.net/](http://www.kompozer.net/)

---

### Post by ohmycar on 2007-10-29
Awesome! Thank you , I will try it out.

---

### Post by mlentink on 2007-10-29
They say support for Photoshop is improving. But don't expect too much.

I'd take a look at Bluefish as well, if you're going to look at Kompozer.

---

### Post by brennydoogles on 2007-10-29
> **ohmycar said:**
> Anyone know how well Dreamweaver CS3 and Photoshop CS3 work under wine?

Also anyone know of a good alternative to Dreamweaver that runs native on linux, kind of like how Gimp is the alternative to photoshop?

Aptana!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by Maestro23 on 2007-10-29
I use Bluefish as well.  Haven't tried Aptana.

---

### Post by mdpalow on 2007-10-30
Hi Ohmycar and All,

For many of us, Photoshop and Dreamweaver are a must have and in many cases will either deter someone from using Linux or at least cause them to keep a dual boot option.

I don't use either programs AS MUCH as most professionals, but on the occasion I do use it - I use it at the professional level. So, bottom line is that I too know what it means to need these two programs.

Here's probably the best solution I've found to have these two and any other Windows programs you want working perfectly.

However, before I begin - let me just say to many of those reading this that want to immediately jump in and recommend Gimp, Kompozer, etc.,etc. that I know they exists and I have tested them and others. Yes, they are pretty good, but unfortunately they don't compare to the market leaders at this point. If they did, I would be using them because I would prefer to be completely Linux.

Ok, enough said.

Here's the deal, I've spent the past few days installing Wine, Photoshop, and Dreamweaver. Do they run in Wine? Yes. I did have success with Photosop CS in Wine once, but couldn't reproduce it a second time. Something made me think to try Photoshop 7 and it loaded fine. However, it was a little buggy and it took the form of a Win 98 appearance, which might not be a show stopper for some, but I know we all like our programs to look good while they're running if they can.

Yes, I know you can change the user.reg file in Wine to display some colors better and yes, I know you can add a theme in Wine and have it work in the applications. However, Of all the themes I tested, I only liked three of them and those three slowed Dreamweaver down significantly due to all the colors and things it was changing within Dreamweaver. So, it's an alternative, but not the best.

There's a much better alternative if you don't want to have a dual boot system, but also don't mind installing Windows XP or Vista INTO Ubuntu.

It's called VMware and it basically creates a fully functional Windows XP/Vista OS within your Ubuntu system. Because it's an actual OS loaded; everything works and perfectly.

I followed the very good instructions for installing the FREE VMware application into Ubuntu and within a few minutes, I had VMware installed and running. I then installed Windows XP and then Photoshop CS, Dreamweaver, and MSN Messenger. All work perfectly.

Attached is a pic of it running on my system. Please note that I could only get the Ubuntu snapshot to work if I was NOT in full screen mode for windows. Meaning, you can click the Full Screen button and have Windows using the entire screen to where you wouldn't even know you were still using Ubuntu. It's REALLY REALLY nice and if you are one of those users who simply needs Photoshop and Dreamweaver (any versions) to work and work well - then this might be your best option.

I'm going to add some install comments for anyone that wants to give it a go because the tutorial is really good, but I had a couple minor questions (newbie) during the install.

1. Follow the instruction from TOP to bottom. I wasn't scrolled all the way to the top and missed the "build-essential" download, so the VMware install didn't work. Made that install and VMware installed like a champ.

2. In the terminal - during install, you're asked a lot of default questions about where you want VMware to install. When you see the recommended directory, just copy it like you see it and press ENTER. Same with all.

3. Few times it asked me if it should do something that I wasn't sure. The default answer it showed was [yes]. When you see the default answers, just go with them by typing in what they displayed as the default.

4. When I began to install Win XP there's always that part about formatting your HD. It's only formatting that 8 or 10 gigs you allocated during setup; nothing else. More importantly, when you are asked to begin formatting that drive you have to hit the SPACE BAR to select it. I hit space bar, but nothing. That's because you have to mouse click INSIDE the window where you see Windows XP to make the keyboard work in that screen and not in Ubuntu. Later learned that when you open a VMware window you're still in Ubuntu UNTIL you mouse click inside that window. To get out of window and back to Ubuntu, you simply press CTRL + ALT keys. 

5. After you install Windows, find the "Install VM Tools" option in the VMware menu options.  These small tools will make your mouse movements much more smooth.

EDIT: 1 Nov 2007: USB Flash Drive wasn't recognized in Windows XP when I plugged it in. I simply edited the settings to recognize the drive as a hard drive instead and it showed up in My Computer. You have to know what physical drive it is in order to do this, so you can type " mount " in terminal and find it. I imagine you could right click on it in Ubuntu as well and click on properties to see which drive it is. Either way, it works.

Want your Windows to load up in 5 seconds? SUSPEND windows when you're done with it and don't do the normal Windows shut down. Next time you need Windows, it'll come up that quick. 

Gimp, Kompozer, and the likes of these programs will get much better in the future. Until then, you can use this option to keep you going.

Here's the link to the HOW TO Tutorial for installing VMware. I'm a newbie myself and got it in a matter of a few minutes:

[http://ubuntuforums.org/showthread.php?t=183209]("http://ubuntuforums.org/showthread.php?t=183209")

Good luck,

Edit:

By the way, I have Dreamweaver MX, Photoshop CS, Nero (for Light scribe function only), and one little Win Utility I like to use still.

---

### Post by timmyw29 on 2007-10-31
+1 for this, I did something similar using VirtualBox rather than VMWare, both are excellent in my opinion and for anyone with a computer strong enough to handle the extra OS and overhead I'd say virtualization is one of the best solutions around to use native Windows applications on Linux.

---

### Post by mdpalow on 2007-11-01
timmyw29,

Thanks - and perfectly said....

Your post couldn't have come at a better time as I was JUST reading about Virtualbox and wondering how it compares to VMware. My question is related to sharing files between the virtual Windows XP and my Ubuntu 7.10.

I see there are some How To's for file sharing between the two, but I was wondering if you have any experience with this in VB?

If you do, I'm really interested in knowing if the setup sharing is more simple than:

[http://ubuntuforums.org/showthread.php?t=296668&highlight=vmware+sharing+files+with+windows]("http://ubuntuforums.org/showthread.php?t=296668&highlight=vmware+sharing+files+with+windows")

If so, can you provide a simple/quick overview as to how it's done? Not expecting a how to, just some simple comments that will give me an idea of what's involved.

Thanks...


P.S. For those reading this who have not installed VMware yet, but considering it because of Photoshop/Dreamweaver - everything works great. I'm simply trying to file share between both systems since I do a lot of pre-photoshop and pre-dreamweaver things in Ubuntu. If I did all this in my Windows XP I wouldn't need to file share, so don't think this comment/question is a problem with VMware running those Windows apps. They run fine and everything works perfectly. I'm simply trying to take things to the next level. :)

As mentioned in previous post - I don't use either application that much unless I'm working on a project, which isn't often - but I was using them both last night full out and they work(ed) flawlessly. I was working in full-screen mode and couldn't even see Ubuntu, but could still here my aMSN Messenger ringing when a friend sent me a message. Simply hit CTRL + ALT keys and was back in Ubuntu to answer the message. Just doesn't get much better than that. :)

---

### Post by timcredible on 2007-11-01
kompozer is the linux replacement for dreamweaver.  i have a short article about website development with linux if you're interested: [http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=16&Itemid=32](http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=16&Itemid=32)

---

### Post by timmyw29 on 2007-11-01
I havn't actually done file sharing between them. Mostly because there hasn't been any need. I remember a quick attempt (about 5 minutes, maybe?) at networking, but since it wasn't critical at the time I just moved on. Sorry I couldn't be a bit more help in that regard.

I can, however, say that Samba will be needed. Even on a normal network, to access Windows shares you need to use Samba.

---

### Post by mdpalow on 2007-11-02
thanks...

You actually told me all I need to know when you said I need "Samba" since it's also required in VMware to share files.

---

### Post by mdpalow on 2007-11-02
timcredible...

As much as I hate to say it - Kompozer is currently the Linux wanna-be equivalent to Dreamweaver. It's not there yet.

That's OK though.. as I said, having VMware installed gives me the ability to use Dreamweaver until Kompozer grows up and I can switch.

I would love to be all Linux apps., but right now it's not possible.

...

---

### Post by timcredible on 2007-11-02
> **mdpalow said:**
> timcredible...

As much as I hate to say it - Kompozer is currently the Linux wanna-be equivalent to Dreamweaver. It's not there yet.

That's OK though.. as I said, having VMware installed gives me the ability to use Dreamweaver until Kompozer grows up and I can switch.

I would love to be all Linux apps., but right now it's not possible.

...

i agree that kompozer isn't as good as dreamweaver.  but joomla is better than dreamweaver, frontpage, and kompozer put together.  so you can go all linux if you want quite easily.  i've got 3 websites, and they're better and have more features (calendars, photo management, polls, weather, etc.) than anything 95% of dreamweaver users could do, and i did them with 100% linux apps on both the server and client.

---

### Post by the_rajah on 2007-11-02
Joomla is very nice, without a doubt. I've installed and used it on a couple of sites so far. In fairness, though, it's not the same thing as Kompozer, Dreamweaver or any of the web page editing software. 

The big difference is that iJoomla is a content management system (CMS) that actually runs on the server for the web site you are developing and requires MySQL and PHP while the others mentioned are editor applications that run on your own local machine and can edit pages anywhere, while Joomla can edit pages only on the site that it's installed on. Joomla is very powerful and useful, I'm not sure that Joomla installation is for the newbie. Anyway, I just wanted to clear up the difference.

I continue to be somewhat disappointed in the web authoring/editing tools available for Linux, but the situation is clearly improving as we go forward. I've been using Nvu, but the development picture for it and its offshoots is a little cloudy at the moment.

---

### Post by junjan on 2007-11-03
I also run Photoshop CS3 on Gutsy using Virtualbox. Smooth...

---

### Post by eagledrc on 2008-03-12
I can share files on VIrtualbox, but it is very slow.  Here is my post
[http://ubuntuforums.org/showthread.php?t=718060](http://ubuntuforums.org/showthread.php?t=718060)
any help would be appreciated.

---

