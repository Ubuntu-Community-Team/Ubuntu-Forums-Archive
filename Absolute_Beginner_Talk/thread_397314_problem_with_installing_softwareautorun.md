---
title: "problem with installing software/autorun"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by dmsymr on 2007-03-30
Im very new to Ubuntu, having just got my cd today, Im very happy so far with it, but I cant install software from my cds. Ill be specific in a mo but I will say Im a complete layman, I dont understand computer speak! So if anyone can help, please be patient with me!
Ok, so We have a network at home, the main pc is still windows, and my laptop has been using a WLAN card (ADD-GWK140) so after installing ubuntu, I proceded to put the driver cd for my wireless network card into laptop and it wont autorun. I opened the file on the cd but every .exe file I click on says "couldnt display xxxxxxxxx/xxxxx/xxxxx/xxxxx.exe"
I hope this is enough information for anyone that knows how to rectify my problem!

---

### Post by Zuuswa on 2007-03-30
First off welcome to GNU/Linux and Ubuntu!  The most important thing you should learn now is that linux is not windows . . . so your cd that has .exe's on it is made for windows, but linux will not run .exe's (for the most part . . . there is a program called wine that will run some .exe's but that is not the solution you are looking for)  I would using the search function at the top of the page in the forums and entering your specific wireless card, and hopefully some answers will pop up!  "ADD-GWK140" does not give me enough information to know what make/model your wireless card is, so I cannot quite begin to help you.  Although, if your wireless card did not work right away, you will need that cd with the driver on it, it will prove usefull, but trying to use it like you do in windows will not work (i.e. autorun or double-clicking on the .exe)

As for installing other software, there is a little tool called add/remove programs, that will automatically download, install and set up most of all the software you will ever need for linux!

---

### Post by dmsymr on 2007-03-30
Thank you for the welcome, also for the advice, the search is coming up with nothing so far but i know what Im looking for now so thankyou....am I right in thinking i cant install any software from cd with ubuntu then?

---

### Post by Zuuswa on 2007-03-30
that all depends on what kind of software it is you are trying to install.  Most software for Linux (and especially Ubuntu) is held in online 'repositories' that programs like Add/Remove and Synaptic connect to to download and install them automatically.  I havnt heard of any software for Linux that comes on a cd, though I could be wrong.  I am assuming the cd is for Microsoft Windows, so it will most probably will not work in linux.  If that is the case, try finding an Open Source alternative to the software, as many alternatives for popular software exists and is sometimes much better than non-free alternatives.  What type of aplications are you trying to install?

---

### Post by dmsymr on 2007-03-30
Its the driver for my network card. its on cd. Im on the computer at the mo, its the laptop ive installed ubuntu on so I cant get online to download it directly!

---

### Post by Zuuswa on 2007-03-30
Try connecting with the ethernet cable.  Honostly I have yet to configure my wireless card to work with Ubuntu 6.10, but I dont really need to because it is almost always sitting at the desk right next to the router, so I always just have it plugged into the ethernet.

---

### Post by dmsymr on 2007-03-30
Ok that would certainly save alot of hassle!!! thankyou so much for your help id still be trying to click on the .exe files now otherwise! 
out of curiosity....what about the driver for my wireless mouse etc, that on disc, will i be able to instll that?

---

### Post by Zuuswa on 2007-03-30
As far as I know your wireless mouse should work automatically, if it is USB (i dont know why it wouldnt be) although I havent tried any wireless mice myself.

---

### Post by GSF1200S on 2007-03-31
> **dmsymr said:**
> Ok that would certainly save alot of hassle!!! thankyou so much for your help id still be trying to click on the .exe files now otherwise! 
out of curiosity....what about the driver for my wireless mouse etc, that on disc, will i be able to instll that?

Youre mouse should work automatically... mine does and its wireless...

The wireless card is a little more tricky. You have two options, and I will help you to the best of my ability.

One is a program called ndiswrapper. Basically it installs a compatibility layer between linux and your wireless card. Then, you install your windows driver and it should work. Honestly, this one didnt work for my wireless card. You can try it. 

Your second option, and its the one that worked for me, is to use madwifi. Madwifi are linux drivers that are made to use with your wireless card. Simply go to the Synaptic Package Manager and search for madwifi, then install. Once installed, I restarted my system and my wireless card worked flawlessly.

I must say I couldnt get my wireless card to work with Edgy, but as soon as I downloaded and installed the Feisty Fawn distribution, plus the madwifi drivers and a restart, my card worked flawlessly. While you might be tempted to do this, keep in mind Feisty is still in BETA, and thats not always the best place for someone new to be. I took a chance because I wanted my wireless, and so far Ive found Feisty to be stable and functional..

Let me know which route you want to take and Ill start posting terminal codes. I would suggest using madwifi as it seems to be a bit easier. 

Despite me being a bit new to Ubuntu, im already trying to collect some information on a how to thread for getting wireless working.. I know how important this is for laptop owners... Welcome!!

---

### Post by dmsymr on 2007-03-31
Ill look for MADWIFI this evening, Im online using the ethernet cable at the mo which is fine but it defeates the purpose of having a laptop, so ill keep you updated!
Veering off a little, Ive been looking into anti-virus and firewall for ubuntu. any reccomendations? I have downloaded AVG so will see how that works out but should I install a firewall, or is their one installed already?

Thanks

---

### Post by hyper_ch on 2007-03-31
You don't need an antivirus program on linux. The concept of Linux is totally different... in order to get a virus you would actually have to install it yourself. As long as you use the repositories of software you shouldn't have a problem.

However if you host an email server or if you are sharing files with other people in your home or other people in general who use windows, then you may think about install an antivirus program for deleting windows viruses so your family/friends don't get them...

And by default you have a firewall installed. It's called iptables which normally has all ports closed... There is however a gui for it (not advanced) called firestarter. You coud install that to "modify" your firewall.

Further I recommend you to have a read here: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

It covers a lot of basics :) Linux is not Windows :)

---

### Post by 3rdalbum on 2007-03-31
> **hyper_ch said:**
> 
And by default you have a firewall installed. It's called iptables which normally has all ports closed... There is however a gui for it (not advanced) called firestarter. You coud install that to "modify" your firewall.

I don't want to start an Ubuntu firewall flame war... :-)

The iptables firewall is installed but does not block any ports by default. This isn't anything to worry about, as none of the software that comes with Ubuntu actually listens on any ports by default. If nothing is listening, then no worms can get in (not that there are any worms for Linux currently anyway!).

On Windows, yeah, definately run a firewall. Windows, and Windows programs, often listen on remote ports when there's no need to. Linux and Ubuntu have been designed for security, so you don't need a firewall yet.

---

### Post by GSF1200S on 2007-03-31
> **dmsymr said:**
> Ill look for MADWIFI this evening, Im online using the ethernet cable at the mo which is fine but it defeates the purpose of having a laptop, so ill keep you updated!
Veering off a little, Ive been looking into anti-virus and firewall for ubuntu. any reccomendations? I have downloaded AVG so will see how that works out but should I install a firewall, or is their one installed already?

Thanks

Yeah, madwifi might work for you. I know this is new to you, but you may not have success with the madwifi drivers. It really depends on what wireless card you have. Mine for example, wouldnt work on Edgy because of the HAL, but it worked flawlessly as soon as I installed Feisty.

As for antivirus.. I asked the same question a few days ago. Linux is a very secure OS, and there are very few viruses that will even work on Linux. Almost anyone on this forum will tell you that antivirus is unnecessary for Linux, and that youd just be wasting system resources running it. If youre still set on running AV, AVG free is a pretty good one. Clam AV is regaurded as one of the best, and its open source. 

As for firewalls, im currently using firestarter. Ive had no problems with it, but it doesnt seem like it would do much unless you knew how to write rules. One of the best... ahhh... intrusion prevention/ firewall systems seems to be Snort (do a quick google search). Its open source as well, and seems to be highly regaurded.

Youll quickly see that many things for Linux are free, but try to look past that. Open source is a really great approach to .. well anything... but especially computers. These communities work hard to make quality products because they want other people as well as themselves to benefit from it. Welcome to the land of the penguin...

---

### Post by dmsymr on 2007-04-02
Thanks so much for all the info guys, Im learning slowly, so thanks for being patient!
I just have a couple of points that im still struggling with....but cant find yet on the forums! Most websites about ubuntu and linux dont seem to be (complete) beginner friendly!

1, **REPOSITORIES**...where are they? how do I access them? Is the add/remove program in my applications menu the repository or is it the synaptic package manager? If so Its a mine field!
2, **AVG** is running fine (I think) but Am I right in summarising that I dont need to worry about a **FIREWALL?** alot of my friends are still on windows so Im concerned about exchanging files via email with them.
3, **MY PRINTER** is attached via usb and I can see it in my folder but it wont connect, would I find the driver in the repositories (if so......point 1)
This takes me back to the original point to my thread...why cant I download programs from the internet? A friend recommended limewire for p2p, will that work with ubuntu or is their a linux equivalent?

Im trying to find the solutions to these points, but at the risk of soundinf lazy and oafish, any help would be so much appreciated!

---

### Post by hyper_ch on 2007-04-02
Repositories:
[https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

Regarding your printer:
What printer have you got?

Regarding exchanging email:
Windows viruses can't harm your linux... as said, av is only used to filter out windows viruses which are aimed at windows computers/users...
You shouldn't worry about your firewall...

---

### Post by dmsymr on 2007-04-02
The printer is hp psc 2510! any suggestions? Thanks for the other info!

---

### Post by hyper_ch on 2007-04-02
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

---

### Post by dmsymr on 2007-04-02
That seems to have done the trick! many thanks! :KS

---

