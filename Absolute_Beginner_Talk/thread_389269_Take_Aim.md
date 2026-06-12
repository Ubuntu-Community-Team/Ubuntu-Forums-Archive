---
title: "Take Aim"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by PhillD on 2007-03-20
Is Linux/Ubuntu viable for the average user?

Being fairly new to linux and ubuntu, I have decided to really see what people think of it.  Let me explain a little about the situation I am in before I go further.  I am, (by force) a new Linux user.  My company director decided (due to licensing) to rolling out Linux boxes to end users and use it as a remote desktop terminal to connect to a Windows terminal server.  This gives him a 'free' windows box and keeps him from having to pay for anti-virus software on each machine.  He also says that the 'unfriendliness' of Linux will prevent users from messing around with it and stop them from screwing up their machines...

I am the IT guy who has been assigned to make this happen and so far it’s not been a good journey!  From the very beginning I had problems with learning how to install programs and navigate the file structure (I guess I can write that off as learning curve. (I am not afraid to try new things)).  But in starting to setup the PC for a business environment, I have never encountered so many PC problems in my life.  First off, the touch screen monitor didn’t work (and still doesn’t), 2nd wireless and 3rd a printer.  Ok, so I suppose it’s my job to figure out this stuff and I should know about kernels, terminal command and the inner workings of the X system.  I have read so many articles about how people come away from ubuntu (and linux for that matter) thinking that they have to use the console,,,,,well sorry to say that I did and if you think about the average user who may want to install a printer, web cam, scanner etc….. then chances are they will too.

Is this too much to expect of an average user?  And would the average user expect it to be too much of them to understand this stuff?  After all, I don’t have to know the inner workings of an ipod to connect it to my PC/Mac – “it just works”

Phill

P.S. I'm probably going to get bashed out of existance for this post.

---

### Post by Crakie on 2007-03-20
I understand your frustration, but Linux or Ubuntu is not to blame actually. Most manufacturers just do not supply Linux drivers for their hardware. The result: outsiders have to make them, often while not having access to the detailed specifications of the hardware. Knowing that, I think Linux supports an amazing amount of stuff.

I know, it does not solve your problems. And yes, it does mean Ubuntu is not quite there yet as an alternative OS for the average user. But the Linux 'unfriendliness' you mention is not by choice. If anything, you should complain to the manufacturers of the hardware you mentioned. Really, you should! If people keep nagging about it, maybe things will change for the better.

---

### Post by jvc26 on 2007-03-20
Hi there,
I would say that when I started using ubuntu I was just an 'average user' I have learnt a lot from the experience, and now to be honest would choose to use it over windows any day due to the ease of install, reliability, lack of viruses and spyware, and the lack of having to pay for the software or wait for months for a security fix that should be patched within a few days of it being noticed. There is a learning curve, but for the most part its not that horrific, and if its something you need to do, and will have to do over the coming months (especially if your business is migrating) then its something that you will pick up pretty briskly. From HOWTOs on the forum and from the wiki there is a wealth of information to solve pretty much every problem which comes up (except where as has already been mentioned there are driver incompatibilities because for some unapparent reason hardware companies are not that keen on releasing their drivers).

If you give us an idea of the stuff you're trying to set up, it would be fairly simple for us to assist you as best we can, just telling us there is a problem won't get us very far at all. Secondly, CLI isnt that bad, and as you're an IT person, theres a fair chance you will have used it yourself. To be honest the majority of things you can do without CLI, its just often the CLI is faster (compare the quick commands sudo apt-get install with trawling through synaptic to find everything you need).

I'm not sure whether your post was asking for help or just outlining a list of issues/problems and leaving it at that.

EDITL:: Forgot to answer your question. Linux (or ubuntu in this case) is fine for the use of the average user. But to be honest, if you have no need to use it - why use it? Basically, if XP/Windows works and you're fine with it then there is very little reason to change to be brutally honest (beyond curiosity/want to be out of the proprietary software loop/support opensource/find a nice OS which is reliable) There is a learning curve and it is NOT windows, but it is possible to do it if you want to/have to, and if you don't want to or have to, then dont feel obliged to try to grapple with it. :)
Hope we can help,
Il

---

### Post by sad_iq on 2007-03-20
I think Crakie just about tells it all...but let's take another point of view...take a new computer...without any CD's (no drivers...no nothing, just the Windows CD)...and let's see how the "average user" can manage to install Windows and all the drivers that windows needs, without knowing what's inside the computer's case, then compare the time it takes to do it in Linux!!!

---

### Post by PhillD on 2007-03-20
Hi,

Not that this was some kind of clever trap but I was venting partly due to my frustration with the touch screen monitor which I have made serveral posts about but not gotten any help.  The link to my post is [http://www.ubuntuforums.org/showthread.php?t=382937&highlight=gunze+touch+screen](http://www.ubuntuforums.org/showthread.php?t=382937&highlight=gunze+touch+screen)

Some things are fast with the command line I admit (apt-get) being one of them (when the software you want is available) but I don'ty ever think I'll get used to using the command line to copy/replace system files.  Anyone know how to do it using Thunar?  Also does anyone know how I can connect to a windows share from ubuntu with a command similar to //192.168.1.105 etc

---

### Post by eric5656 on 2007-03-20
I also don't think Linux is ready for the average user.
May that you need 20' to install Ubuntu but after that you need 10 nights to have your camera, your printer, your wireless working...
And my Wacom will never work on it...
In XP you need 1 hour but everything works...
Hope this will change one day whoever's responsibility it is...
But don't sell Linux for the average user like me. It's just for people willing to spend hours on the terminal and reinstalling the OS....
Eric

---

### Post by 23meg on 2007-03-20
> 
Is this too much to expect of an average user? And would the average user expect it to be too much of them to understand this stuff? 


There's no such thing as the average user, none that we can put our finger on.

Non-technical users typically get their operating systems preinstalled. Linux isn't popular enough to ship preinstalled on a mass scale. One of the things we're trying to do is make it that popular, trying to fix [bug #1]("https://launchpad.net/ubuntu/+bug/1"), and until it's fixed, *we're* helping them (those who care enough to sort out their own problems) get their systems up and running. In the preinstalled OS paradigm, it's the system vendor, or the IT admin (you) that does this.

---

### Post by srt4play on 2007-03-20
Try /dev/ts0 instead of /dev/gunzets in your /etc/X11/xorg.conf

---

### Post by PhillD on 2007-03-20
Hi,

Thanks for the suggestion, I will give it a try though ts0 would suggest a serial connection but I am connectibg via USB.  The /dev/gunzets entry was specified in the manual for the gunzets driver.  But I will give it a try and see what happens, and thanks for making a suggestion.

---

### Post by jvc26 on 2007-03-21
With the windows server - how are you trying to connect to it - if you have ssh installed for instance, you could connect via Places -> Connect to server -> Input details, or via CLI with ssh [email]user@xxx.xxx.xxx.xxx[/email] if you're after the samba connection, I'd take a look at samba (sharing drives between windows and linux):
[http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/)
[http://doc.gwos.org/index.php/Share_files_using_Samba](http://doc.gwos.org/index.php/Share_files_using_Samba)
[http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18](http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18)
Hope they point you in the right direction,
Il

---

### Post by cowlip on 2007-03-21
> **PhillD said:**
> Hi,

Not that this was some kind of clever trap but I was venting partly due to my frustration with the touch screen monitor which I have made serveral posts about but not gotten any help.  The link to my post is [http://www.ubuntuforums.org/showthread.php?t=382937&highlight=gunze+touch+screen](http://www.ubuntuforums.org/showthread.php?t=382937&highlight=gunze+touch+screen)

Some things are fast with the command line I admit (apt-get) being one of them (when the software you want is available) but I don'ty ever think I'll get used to using the command line to copy/replace system files.  Anyone know how to do it using Thunar?  Also does anyone know how I can connect to a windows share from ubuntu with a command similar to //192.168.1.105 etc

Just so you know, Thunar doesn't support SMB yet (....I know *sigh*).  A good solution is to use fusesmb, so that you can access your windows shares on the filesystem without using a vfs, and you can access them from the terminal as well

[http://ubuntuforums.org/showthread.php?t=304131&highlight=fusesmb](http://ubuntuforums.org/showthread.php?t=304131&highlight=fusesmb)

---

### Post by slimdog360 on 2007-03-21
not much of an IT guy if you had trouble with linux now then are you.

---

### Post by PhillD on 2007-03-21
Is it really necessary for comments like that?

---

### Post by PhillD on 2007-03-21
Thanks to everyone else on their useful comments.  Still no luck on the monitor though.

---

