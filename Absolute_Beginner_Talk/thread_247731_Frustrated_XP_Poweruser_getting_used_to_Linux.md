---
title: "Frustrated XP Poweruser getting used to Linux"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by ehonda on 2006-08-31
I had a nice transition to Ubuntu. I ordered the cd's almost a year ago and let them sit on my desk for quite some time. A couple of friends tried to install it b/c I was afraid of it and let them be the guinie pigs. No one could get it to install right so I had never been into it at all. I use Photoshop and game all the time so I had no reason to switch. Recently however, I aquired a laptop and since I hate windows I thought I'd give those ubuntu cds I never threw away one last shot. Well, in just a short time I had a new OS installed and had configured my (pain in the a55) LAN W200 as well as setting up all the necessary updates and XMMS, themes, all the cool stuff that I thought I wanted Linux for in the first place. Then I bought two card readers that were rendered worthless. I thought I'd skin XMMS, no go. Its telling me I don't have permissions to write in the skins folder. Then I try to install WINE and some other Windows proggies like BF2 and Winamp, just random stuff. I tried to install a dock. No go. Then lastly I thought well, I'm going to try Xgl. That was a waste of time too. I know it can be done and I'm not going to give up, I'm just extremely frustrated and don't really know where to turn now. Is there anyone out there that can point me in some right directions? I'm ](*,) here.:-? 

Thanks ahead of time. 
Marshall

P.S. I have a lot of experience in Windows from 95 and up. I was into reghax and customizing it to no end. I guess you'd call me a power user. I have had absolutely no experience with Linux until this semester though. I also haven't used DOS in YEARS, so learning commands was a guessing game. I'm running drake on a Compaq N610c, 2g Intel, Radeon 7500, 1g RAM. Runs much better than XP did, but I'm ready to see the real Linux eye candy.

---

### Post by grte on 2006-08-31
If you're having problems with permissions, then most likely you need to start putting sudo in front of your commands.

Or if you're using the gui, you'll need to open those files with a sudo-enabled nautilus.

Open a terminal, type gksudo nautilus, you should then be able to open pretty m uch anything you want.

Basically, in Linux, you aren't logged in with administrative privileges at all times.  Sudo stand for 'superuser do', and allows you to temporarily gain administrative priviledges.

Oh, and for xmms, try the /home/$USERNAME/.xmms/skins directory instead of the one you were attempting to use.  The .xmms folder is in your home directory so you always have permission to edit what's in it.

---

### Post by _simon_ on 2006-08-31
If your cd's are over a year old which version did you install?

The current version is 6.06 (Dapper Drake)

---

### Post by Mimsy on 2006-08-31
> **ehonda said:**
> Well, in just a short time I had a new OS installed and had **configured my (pain in the a55) LAN W200** as well as setting up all the necessary updates and XMMS, themes, all the cool stuff that I thought I wanted Linux for in the first place.

How did you do that!?! Tell me, please, I beg you!

---

### Post by OffHand on 2006-08-31
Just use it as much as possible. Within a few weeks you are starting to know linux/ubuntu and things will become easier. Also use the excellent documentation to search for specific guides and solutions.

[https://help.ubuntu.com/](https://help.ubuntu.com/)

---

### Post by 3rdalbum on 2006-08-31
> **ehonda said:**
> Then I bought two card readers that were rendered worthless...I tried to install a dock. No go. Then lastly I thought well, I'm going to try Xgl. That was a waste of time too...

...I ordered the cd's almost a year ago and let them sit on my desk for quite some time...

"Well there's your problem!"

I've got three pieces of advice for you:

1. Get the latest version of Ubuntu and clean-install that.
2. Don't be afraid to take your time learning everything. (XGL and Compiz isn't important, so try it only when you're comfortable with Linux).
3. Temporarily forget everything you know from Windows. It's not going to help you.

I'm very very surprised the card readers don't work. Have you tried going to the Places menu and down to "Computer"? The reason I'm surprised is because card readers are generally USB Mass Storage devices, which have been supported in the Linux kernel since version 2.4.0 (even early versions of Ubuntu have shipped with more recent kernels).

The integrated card reader on my computer actually works BETTER than in Windows, and an external one I bought for my Mac also works fine. As long as your card readers are plug'n'play with Windows, they should work.

---

### Post by toasted on 2006-08-31
Also, don't lump all your troubles into one and view them as one big trouble. Break them down into individual troubles, prioritize, and sort them out one at a time. It's much easier on the brain ;)

---

### Post by Donnut on 2006-08-31
You probably have version 5.04, Dapper has come a long way since then, when I first tried to install 5.10, I got a flashing terminal.  But under 6.06, my SD slot even works!  I could not ask for a better Version of desktop linux...

---

### Post by ehonda on 2006-08-31
Ok. kewl. Thanks for all the help. I am going to retry the readers and see if I can get them to work. All I really did to use the readers was plugnplay like windows b/c I didn't know how to mount or anything like that. 

I installed an older version. I don't know exactly which one, but when I was conriguring WNIC I had to update everything to Dapper and the update everything in Synaptic sure helped with that. It downloaded and installed the new OS. So, to the best of my knowledge it is Dapper. Is there a way I can check for sure though?

As for configuring the WNIC. All I did was search the ubuntu forums and the wiki and there was a walkthrough on how to install that NIC. Apparently everyone has trouble with it.

[https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200](https://help.ubuntu.com/community/WifiDocs/Device/CompaqW200)

There's the link for the NIC. Hope that helps ya Mimsy.

All in all its been a good experience. Again, thanks for the help and I feel better about it today. So my freetime will be spent sorting things out one at a time. I'm also going to see about this Nautilus.

---

### Post by The_Apprentice on 2006-08-31
ehonda - just wanted to say stick with it.

I am a Microsh@ft trained consultant who got bored with Windows.
Or more to the point got bored of paying for bloatware.
I have just got rid of my Windows server hosting a website and Exchange.
It is still really hard to beleive that everything on the Ubuntu box is free.  In fact I feel guilty declaring that.  :oops: 

Anyways, the biggest advice is to stop thinking Windows.
I had the mentality of trying to "clone" what I had on my Microsoft box, and I wanted it yesterday.
Now I am taking it one step at a time, dealing with one problem at a time.  It is a real pleasure, I mean bloody hell I have not even played BF2 for a week :shock: 

Ooo, another bit of advice is to backup after you have a success - [http://www.compentux.org/index.php/Backup_%26_Restore_guide](http://www.compentux.org/index.php/Backup_%26_Restore_guide)

Now where's my PuTTY gone :)

---

### Post by ehonda on 2006-08-31
Ok, updated. The nautilus trick worked splendidly. I'm able to dragndrop the skins in the proper folder now. So check one prob down. Thanks for helping. Now on to the more serious of issues. OpenGL haha. :D

---

### Post by Mimsy on 2006-08-31
Thanks for the link, ehonda! I've read that document before, and I tried configuring the W200 once again after the directions, but for some reason, as I get to the part about downloading firmware, I get a message in the terminal that says the file is not available, and everything goes downhill from there. I have started over several times, as I learned to do in That Other OS, with a reboot before each time, but still no luck. I made a new thread and p[osted about my problem, and I'm now keeping my fingers crossed that a nice and friendly forum member will be able to help me out.

But thanks anyway, I appreciate the effort to help as much as anything else. :)

/Mimsy

---

### Post by bodhi.zazen on 2006-08-31
How does it feel to be in a foreign country? If you liked Windows wait to you see what you can do with Linux.

Learn the Linux command line.

---

### Post by Mimsy on 2006-08-31
> **bodhi.zazen said:**
> How does it feel to be in a foreign country? If you liked Windows wait to you see what you can do with Linux.

I'm still adjusting, thank you. And I hope Ubuntu doesn't take me more than two years to get used to! :confused: That would su... ahem. Not be good.

---

### Post by ehonda on 2006-08-31
Its definately a foreign land to me. I just tried to install Xgl and thought I had everything right until I rebooted. I got some pretty wierd stuff going on after I tried to log in with the Xgl session.

Sorry the link didn't help mimsy. Maybe its something to do with your NIC b/c it worked on the first try for me.

---

### Post by Fedz on 2006-08-31
I've been using 6.06 for a few weeks.

At 1st it's abit daunting but, after a few weeks you learn heaps thanks to this forum.

 tried putting codecs and things below my home directory and wondered why it wouldn't work but then realised that your home directory has hidden folders but, goto view ? hidden folders you can see **.**xmms and then into skins folder and you put your skins in it.

**[Gnome-Look](http://www.gnome-look.org)** has some outstanding Ubuntu themes and backgrounds and to me using one of these alters your whole way of thinking towards Ubuntu as for some reason the effect of an appealing theme makes for greater learning patience ;

I missed Window$ XP as I've used Window$ since 95 but, in all honesty once past the shock of a new OS and played around with Ubuntu and installed some software and themes ...etc. you do realise that Window$ is just another operating system but, with major flaws after flaws and problem after problem.

Ubuntu you are actually free and can make an OS  the way you want it and have input which is a far cry from Window$.

In a nutshell stick with it, it's certainly worth the change too Ubuntu and after awhile you'll laugh at yourself for loving Window$ and wonder why :D

Kind regards

---

### Post by Toxicity999 on 2006-08-31
Windows POWER USER? haha... Maybe if you mean that in the sense of it eating up my battery life ;)

Okay the thing with XMMS is simple. You probably attempted to install to the computer wide skins directory when you need to install it in the local home directory... I think .xmms in your home folder contains the local skin directory. Correct me if I'm wrong... Sorry if that was already answered just trying to plow through some threads and help out before my battery dies! (Shakes fist at Dell for poor battery performance in the Inspiron 5100)

---

### Post by toasted on 2006-08-31
What I did was make a folder called skins in my home directory. Then inside of that is sub folders for XMMS and whatever else uses skins. Then its just a matter of pointing the app to the right place to use the skin.

---

### Post by bodhi.zazen on 2006-08-31
> **Mimsy said:**
> I'm still adjusting, thank you. And I hope Ubuntu doesn't take me more than two years to get used to! :confused: That would su... ahem. Not be good.

Welcome to Linux (Ubuntu). Ask and thou shall be assisted. You can become very comfortable with Linux in a few short weeks. DO NOT USE WINDOWS AS A CRUTCH. Running back to the comfort of your familiar OS will hamper your learning.

Tweak, break, post, fix, learn.

---

### Post by ehonda on 2006-08-31
okay, so maybe I'm not a power user in your eyes. I got what I needed to get done though. Not a programmer by any means. Until I installed ubuntu the only thing I needed the command line for was telnet stuff. My boring windows experience is a thing of the past though. Thanks to you guys and this board the transition has been surprisingly simple. Thanks again.

---

### Post by bodhi.zazen on 2006-09-01
> **ehonda said:**
> okay, so maybe I'm not a power user in your eyes. I got what I needed to get done though. Not a programmer by any means. Until I installed ubuntu the only thing I needed the command line for was telnet stuff. My boring windows experience is a thing of the past though. Thanks to you guys and this board the transition has been surprisingly simple. Thanks again.

Not so, you are an experienced power user migrating to Linux. You will be a power Linux user. I see an Ubuntu server install in your future.

---

### Post by Mimsy on 2006-09-01
> **ehonda said:**
> okay, so maybe I'm not a power user 

Of course we are. *In Windows.* In Linux I am a completely lost novice, and I have no problem admitting that. Why would I be posting in the Absolute Beginners section if I wasn't well aware how ignorant I am of this, for me, entirely new operating system?

/Mimsy

---

### Post by ehonda on 2006-09-01
> **bodhi.zazen said:**
> Not so, you are an experienced power user migrating to Linux. You will be a power Linux user. I see an Ubuntu server install in your future.

Ubuntu server eh? Anytime I get to play with new software count me in. What is the purpose for Ubuntu Server though? How would I use/benefit from it?

*2nd edit - Aw man. You shouldn't have shown me that. I always talked about owning a server. Not too sure what I could do with it at this point of my life, but....

> 
Of course we are. In Windows. In Linux I am a completely lost novice, and I have no problem admitting that. Why would I be posting in the Absolute Beginners section if I wasn't well aware how ignorant I am of this, for me, entirely new operating system?

/Mimsy

+745874685 on that one.

---

### Post by bodhi.zazen on 2006-09-01
1. Server is a "minimal install". Install X and a light desktop (Fluxbox, Icewm, Openbox). Install only applications you need. Now you have a lean, mean desktop.

2. Buy a "high end" box (does not hvae to be all that high end). Install Ubuntu + applications. Log onto ubuntu from Windows. Run applications on Ubuntu -> export output to windows box. More then 1 user can use Ubuntu at once (unlike windows) and you only need to maintain software on the server, not individual workstations. Works ubuntu -> ubuntu as well.

Ex: Do not let windows onto the internet. Install 2 10/100 cards on Ubuntu server -> 1 to internet, 1 to local network. Windows boxes access internet on Ubuntu. (log onto ubuntu -> run firefox with output to Windows). Now your windows boxes have the security of Linux.

3. Run a server. ftp, apache, mail server at home.

There are several variations on these themes, but this should open your eyes to possibilities.

---

### Post by ehonda on 2006-09-01
Wow, that's only the coolest thing I've heard all day. I think I will end up doing that. All the goodies without all the garbage. :)

---

### Post by toasted on 2006-09-01
So, using a server install and a light desktop is the most lightweight you can get? Seems like there would be some server stuff that would not be needed in a desktop environment.

---

### Post by bodhi.zazen on 2006-09-02
> **toasted said:**
> So, using a server install and a light desktop is the most lightweight you can get? Seems like there would be some server stuff that would not be needed in a desktop environment.

Although you can not tell form the name, the server install is minimal. CLI only, no GUI.

You have to install all the "server stuff" yourself starting with apt-get install aptitude.

Rather then setting up a server -> Install a light desktop and only the applications you need. You can run gnome, kde, or xfce applications in fluxbox/icewm/openbox. Also there are light weight applications for everything. dillo, mousepad, abiword, rox, vim, xchm, d4x, evince, xarchiver ... This with firefox, K3b, xmms, streamtuner, and gaim give a very functional desktop.

Install Openoffice or other heavy programs as needed.

Install applications first -> then X and light desktop and all your applications should be in the menu. Otherwise use menumaker:
[http://menumaker.sourceforge.net/](http://menumaker.sourceforge.net/)

---

### Post by ehonda on 2006-09-02
I may just stick with what I have for now. I'm really enjoying playing with what's installed now. I've got it pretty much set up the way I want. If the weighted proggies were enough of a bother or I get bored enough I can just go through and take em out one at a time right?

---

### Post by bodhi.zazen on 2006-09-02
> **ehonda said:**
> I may just stick with what I have for now. I'm really enjoying playing with what's installed now. I've got it pretty much set up the way I want. If the weighted proggies were enough of a bother or I get bored enough I can just go through and take em out one at a time right?

good choice for now. Explore your new OS, install away. You will find you will settle into a few proggies.

Once you know what you want, learn how to get it (ie become comfortable with CLI).

Then server away, if you have the space use a new partition (perhaps the windows partition???), fall back to your 1st Ubuntu install.

You can un-install, of course. If you ever want it back (or break Ubuntu) re-install (proggies).

---

### Post by ehonda on 2006-09-02
> **bodhi.zazen said:**
> good choice for now. Explore your new OS, install away. You will find you will settle into a few proggies.

Once you know what you want, learn how to get it (ie become comfortable with CLI).

Then server away, if you have the space use a new partition (perhaps the windows partition???), fall back to your 1st Ubuntu install.

You can un-install, of course. If you ever want it back (or break Ubuntu) re-install (proggies).

This is my first time to ever use any kind of multi-desktop switching. I'm really enjoying this. I don't feel so cluttered like I did in XP. I like to run a lot of things simultaniously and even though its a drain on the machine it feels easier for me to switch back and forth. Sometimes with XP I had the res @ 1200x1600 and had 3 lines of windows open in the tray. This makes it easier for me to organize and know where everything is.

---

### Post by bodhi.zazen on 2006-09-02
lol...

DO NOT TRY DUAL MONITORS THEN......

---

### Post by ehonda on 2006-09-02
> **bodhi.zazen said:**
> lol...

DO NOT TRY DUAL MONITORS THEN......

Funny you said that, haha. I was just shopping newegg for a second monitor for my windows machine. I like the idea of having a second monitor to see my digital work in full while I'm organizing or editing in the other. Guess 2 monitors could lead to very bad things tho if I'm not careful.

---

