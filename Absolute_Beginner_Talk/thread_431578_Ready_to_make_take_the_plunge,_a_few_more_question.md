---
title: "Ready to make take the plunge, a few more question, however."
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Pirate_King on 2007-05-03
So here we go. Im sick of windows and all that rot. My desktop specs are as follows.

AMD Athlon 3200+ Processor
1 GB DDR SDRAM
160 GB 7200PRM HD
256 MB Geforce FX Video Card

My computer is mainly used for listening to and burning music, Chatting with friends, and playing games(World of Warcraft, Steam games, Guild Wars). I've never partioned a harddrive before, but I'm not however, new to computers. I hear all this talk about dual-booting, but if it can be managed with the way I use my computer, Id really rather have all traces of Windows removed. I am however, very afraid of ruining something permanently, as this is the only computer I have, and I cant exactly afford a new one. 

Some other subjects I would love to have someone shed some light on are:

If i've never touched a system with a Linux OS, is it going to be terribly hard to get the hang of using it?

As far as the installation goes, am I going to be able to manage it myself, or would you reccomend I find someone who knows what their doing?

If I end up deciding that maybe linux isn't for me, will it be easy to reconvert?

Thanks in advance.

---

### Post by jkblacker on 2007-05-03
Hi there,

I had no experience either before installing. I recommend using the LiveCD for a few days, hanging around here just reading up on what's going on (and recognising that if something should go wrong, there's a lot of people here who'll have a workable solution!).

I don't know about compatability of your games - someone else?

I'd stick with a dual boot for now, as I have done. Make sure everything is backed up from your windows system, just in case something goes hideously wrong; plan any partition changes before making them; don't be afraid to ask for help!

For music and so on - I have an external hard drive (cheap these days - my 250GB MyBook was £60 from amazon.co.uk) that's ntfs from my windoze days, and I can play all my music from there in Ubuntu with no problems (also saves on hdd space!). 

Partitioning can be daunting (it was for me, I was nervous about it!), but if you take good advice and are careful to defrag/back-up beforehand, you probably won't have any problems.

Hope this is helpful!

---

### Post by pay on 2007-05-03
Linux is different to Windows
For gaming Linux isn't the best platform. there are tools like wine and cedega but they don't work 100% of the time.
Nothing should go terribly wrong to the point where you have to buy a new computer. The worst that can happen is you will have to re-install Windows.
You don't need to defrag Linux partitons, only Windows ones.

---

### Post by antoz on 2007-05-03
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

A couple of good links

---

### Post by Stephen Howard on 2007-05-03
I don't know of anyone who's managed to brick their computer just by installing a new OS, so you're quite safe on that score.

Given that this is your first time with linux, its probably best not to delete MS-windows but instead dual boot both operating systems.  The usual pattern of adoption is that new users start by dual booting so that if they can't get something working in linux they have the security of reverting back to windows.  Once you are familiar and confident with linux, then its time to start thinking about deleting MS-windows.

> If i've never touched a system with a Linux OS, is it going to be terribly hard to get the hang of using it?

It can be difficult to get your bearings and to become familiar with the unix jargon - talk of filesystems, mount points, X11, gnome, kde etc will confuse the hell out of you to start with.   Its like learning a new language - it takes time and patience.

> As far as the installation goes, am I going to be able to manage it myself, or would you reccomend I find someone who knows what their doing?

You should be okay - millions have been there before you.  Start by downloading the live-cd version and verify that your computer will run it without difficulty (the live-cd version doesn't touch your harddrive - it runs entirely in RAM - and that means that you can experiment with it without worrying about hurting your MS-windows installation).

If the live-cd works (check browsing etc), then click on the installation icon and follow the prompts.  The only problem you might have is if your harddrive is full, in which case linux won't be able to install - but the installer will warn you.

> If I end up deciding that maybe linux isn't for me, will it be easy to reconvert?

As I said at the start, the advantage of dual booting is that both OSs are on the harddrive at the same time, and you get a menu that pops up at boot time from which you can choose which OS to boot.

Remember, have patience.

good luck.

---

### Post by tact on 2007-05-03
definitely download a ubuntu LiveCD...  boot from the CD and actually use it for a while.  It runs slower as you will expect when running from a CD instead of a HDD.  The up-side is that this changes NOTHING on your HDD until you are ready to double click the tempting "install to HDD" icon on the ubuntu LiveCD desktop.

Doing this will let you see that all your hardware is properly detected and useable.  

Before you succumb to temptation to hit the "install to HDD" icon you might want to boot back into windows and do a full HDD defrag/cleanup.  Then do a nice clean windows shutdown.

Next step down the committment road is to boot from the LiveCD again and hit that "install to HDD" icon.  After a few simple questions you will be presented with basically 2 choices:
- format the drive (wiping out all thats on it now including windows etc) and install ubuntu clean ..or..
- use some freespace on the HDD and install there 

Choose the second option.  This will install ubuntu on whatever portion of the HDD freespace you permit it to take.  It will repartition your HDD and install a bootloader (GRUB) automatically.  You will then be able to dual boot - choosing either windows or ubuntu at boot time.

Assuming complete happiness after a few weeks or months of using ubuntu with the dual boot safety net  you might then take the next step down the road of committment - booting from the LiveCD one more time to use Gparted (partitioning tool) to delete the windows partition totally, and resize the ubuntu partition to take up the entire HDD.

Thats what I did.  ;)   Apparently if you are a gamer you might want to keep windows around longer term.  I am not and so there was no pain for me in getting rid of my windows partition totally.   

I still have a kind of safety net:
- the windows divelog software I use has no suitable replacement in Linux but it runs fine under WINE.
- Windows software applications that I sell on behalf of the company who tosses cash at me every month all runs just GREAT in Virtual Machines (VMs) under Linux.   (I can have applications running on  Windows Server 2003 in a VM .....PLUS applications running on WindowsXP in another VM on the SAME laptop and see the applications talking to each other....  each one on a different side of a cube courtesy of Beryl.)

---

### Post by Stephen Howard on 2007-05-03
Can I say that I'm continually amazed at how helpful people are on this forum.  

Group hug

---

### Post by Stephen Howard on 2007-05-03
> Tact said:  the windows divelog software I use has no suitable replacement in Linux but it runs fine under WINE.

Hmm, sounds like a useful project!

---

### Post by Pirate_King on 2007-05-03
> **Stephen Howard said:**
> Can I say that I'm continually amazed at how helpful people are on this forum.  

Group hug

First off, let my echo this statement. Thank you all. I never expected to recieve such overwhelmingly informative answers to my post, without seeing at least one post commenting on my inferior Linux skill. Thank you all, youve given me the courage to try Ubuntu. I will definitely take your advice.


> **antoz said:**
> [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

A couple of good links

Id especially like to thank you for these links antoz, as i am a visual person and the guides on psychocats are just what I am going to need.


Once again, Thank you all for your help. I am overwhelmed by the kindness everyone has shown, and I think I'll be around for good.

---

### Post by tact on 2007-05-03
> **Stephen Howard said:**
> Hmm, sounds like a useful project!

offtopic alert!  (but its just a little one)  :)

Hey Stephen..  :)  cool go for it.  The specific divelog I use is called "Internet Dive Log" (IDL).  The website is "immersions".

Its unique because the divelog software run on the local PC is a client to their internet server.  The user can select some (or all) records of dives, equipment and divesites to be uploaded to the server and then be accessible even when you do not have your PC with you.

---

