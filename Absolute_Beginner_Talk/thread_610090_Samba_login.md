---
title: "Samba login"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by BLTicklemonster on 2007-11-11
I just set up Gutsy on a new hard drive. 

I went to network, and accessed an XP box. Whee. I know better than to think the linux gods will smile on me as far as letting the XP boxes connect to my machine... so I didn't waste my time doing it.

Then, suddenly, without warning (this is why I don't waste my time trying to get my XP machines to access this box, thank you), I have to put a password in to connect to the network. Gee, nothing has changed here. No reboots, no installing, just walk away for a few hours, try to connect, and everything is different than it was before.

(I have to freaking email my wife upstairs pictures I want to share, by the way. Real swift way to run a railroad, huh? I was going to drop it in her shared folder, but no no no no no Ticklemonster!!!)

Same thing happened before. Every time I have ever gotten the network set up to where the XP boxes can access this machine, either I do an update that wrecks everything, or it just changes all by itself.

I follow just about every guide here, and I have yet, to this day, gotten a useful network set up.

Now I'm no networking wizard in Windows, but sharing files and folders in windows blows this crap away. Why? What about "it just works" says "unless you want to network"? 

I'm having a hard time getting the better half to look at Ubuntu as anything other than an oddity here. (and several other friends who would use Ubuntu if they could sit down at any machine in my house and connect to my machine. they all have home networks, and refuse to "waste time on that junk OS" I use no matter how awesome I tell them it is.)

Reason for posting:

Come on guys, give us networking that "just works". Look at all the unanswered threads here where people have posted that they have networking problems. Look at all the people who say they want easier networking. Figure out how to make this junk work without having to open an editor and change a single line of code, please! You've spent more time playing with getting compiz working than you have with networking. 

On another note, guess what Windows also does rock solid every time you try it? Boots if you drop a new hard drive in. Yeah, in Ubuntu, you have to boot to the live cd and set grub up again. Windows just magically boots with the drive ready to go! And you don't have to mount the drive, either! AAAARRRRGGGGHHHH!!@!!!

But for all of that, I love Ubuntu, and refuse to give up on it!

That is all, please forgive my ranting, but good God all Mighty I was p*ssed off when I sat and thought about all the time wasted on compiz that could have been spent getting a reliable networking system going, and an auto grub setup. What's more important, "it just works", or "it just almost works, but look at all this eye candy crap we did?", Priorities, fellas, priorities.

Whew.

Thus sayeth the troll.

lol

---

### Post by Daveski on 2007-11-11
> **BLTicklemonster said:**
> Now I'm no networking wizard in Windows, but sharing files and folders in windows blows this crap away. Why? What about "it just works" says "unless you want to network"?

Windows is OK at sharing files and printers with other Windows machines (although XP Home can get a bit funny sometimes, and you might have to wait 15 minutes for all Windows machines to appear in the list of network computers). I think you are trying to fileshare between Linux and Windows. This requires a little bit of setup as Microsoft File and Printer sharing is a proprietory system. You would have to do extra work to get Windows to share with OSX or with Linux native system NFS.

Also, Windows sharing does work for Windows 'out-of-the-box', but unless you are careful you can find your shares are visible from the Internet. The XP firewall blocks File and Printer sharing by default to try to shore up the security a little.

---

### Post by matthewcraig on 2007-11-11
After two years and two thousand forum posts, aren't you more of a veteran than a "Absolute Beginner"?  I would look to someone like you to help get the networking you want that "just works"!  Hope this isn't a bad sign having someone with your expertise appealing to the newbies for networking code.

---

### Post by BLTicklemonster on 2007-11-11
This is where the absolute beginners post for help. 

When it comes to networking, I've never gotten it to work, so I consider myself to be a beginner in it. And trust me, I've tried and tried and tried. Had it working a few times, and every time, it stops working. Now I know that it can be done, because people do it, but I don't understand why one must go to all the garbage to get it set up. And once it's set up, why does mine always stop working? Does this happen to anyone else ever? It drives me bonkers. (er)

---

### Post by TadH on 2007-11-11
what is the longest period of time is was working for?

---

### Post by ant2ne on 2007-11-11
[http://ubuntuforums.org/showthread.php?t=292006](http://ubuntuforums.org/showthread.php?t=292006)
Read the part about the password expiring. Might be the solution to your problem

---

### Post by Bigbird999 on 2007-11-11
OP has a valid point.  I am a Linux noob (2wks).  I have a home network with a Mac (Panther), 2xWin XP, 1xWin2K and a NAS server (NASLite - which is a Linux on a floppy that turned an old P1 into 750 GB of windows share storage).  I have a couple of Home Theater PCs so lots of large file transfers and/or remote playing of recorded shows.

To allow Windows to share files on the Mac, I had to click 'enable windows sharing' in the Mac's network configuration screen.  To log on to Windows from the Mac I had to go to the connect to server window and type in the Win box IP and password and I was connected. another tick and it mounts on startup. The Mac can access all of the drives on the NAS.  Windows, well, like the OP said, it just works.  Click on explore in Network neighborhood find the Mac or NAS or other windows shares, double click enter a password and it's connected.  Map the shares and Windows gives them a drive letter and mounts them automatically at startup.  

 
I can play a recorded TV show or even live TV, as it is being recorded on the Mac or any of the Windows boxes. (Same for photos or music).    After a couple of days (really - about 12 hours) of screwing around I was finally able to get Ubuntu to mount the windows shares so I can play music or videos on my Ubuntu laptop, but I cannot get them to mount automatically  (maybe because it is wireless) so I have to do a "sudo mount -a" to mount the shares listed in /'etc/fstab  For some, as yet unknown, reason it won't connect to the Win2k box unless I use a different mount command from the terminal.  To me it is inexplicable that you can transfer a file from the Network>Workgroup>Share but you can't play it unless you mount the drive???WTF!!!!  

After all this, Ubuntu can't see any of the NAS drives and although it sees the Mac, it can't see any files (maybe I need to enable something on the Mac, but I haven't had time).  Once I go through the BS of mounting the Windows shares they work fine.  

As for the Mac or Windows boxes  even seeing my Ubuntu Laptop - I haven't been able to figure this out (saving this for my next 12 hrs of learning Ubuntu).  It is not a killer issue, because I use the laptopmainly  to play media and manage the windows boxes via VNC, but,as my friend would say,  it is very "aggrannoying " (I know it isn't a word, but it should be)

My opinion is the same as the OP's, networking is  wwwwwwwwwwwwwaaaaaaaaaaaayyyyyyyyyyyyyy to hard in Linux, 
 Networking should be as easy as it is on other operating systems. 

I read in CPU magazine that approx 0.36% of the world's computers are running Linux, vs 2.8% for Mac and >96% for Windoze.  I don't see this changing unless Linux gets a lot more user friendly, especially on things, like networking, that even the noobiest noob can do easily in other OS's

Thats my 2.16 cents (Canadian):guitar:

BB

---

### Post by HermanAB on 2007-11-11
The Ubuntu networking wizards suck.  However, it is OK on most all other distributions.  So you have a choice:  You can either learn how to configure networking yourself - which is not difficult, or you can switch to another distribution with better wizards.

Cheers,

Herman

---

### Post by BLTicklemonster on 2007-11-11
Yah now, Herman, I've attempted other distros, but I Ubuntu is the easiest one to install. Put the disk in, before you know it, you're spammin' away like a pro.

I"ll try that ant2ne. Thanks.

---

### Post by ant2ne on 2007-11-12
> Networking should be as easy as it is on other operating systems.And I'm gonna argue that Windows XP-Home's default simple sharing is, simple. Simple to set up, and simple to crack. Weak and insecure, but simple. You could argue that Samba needs a "Simple" File sharing version just as XP-Home uses. But I wouldn't want to use it.

The Windows Server / XP-Pro sharing is more complicated, and I'd say it was based off of the unix / linux sharing ideals. (Learn about Linux/Unix and Samba sharing, and you learn about XP-Pro and Server-03 sharing) Yes linux to Windows sharing is complicated but, you don't see MS making any effort to be more Windows to linux friendly. 

Perhaps, on install, samba should ask the user if it should set up a "Simple" share and if 'yes' is selected, then by default; a guest share is created, and relatively lax permissions are set. For Simple home network sharing; "life is good". I wouldn't want to use it though.

Between linux to linux you could use an NFS share. It is a piece of cake to set up. I set up an NFS share a long time ago. I have NEVER had any problems with it compared to learning and using SAMBA. NFS works every time with no problems. I am still struggling with my samba shares! 

Having said all this, I feel that samba is part of Linux's future. Linux (Ubuntu) needs to learn to thrive in the Windows dominated world in order for it to take a bite out of that market. Anyone who thinks otherwise is.... {edited} ! !  For this reason I've taken on this Samba guru challenge. (I Just don't know enough yet.) And perhaps, for this reason, your argument of Samba Simple Sharing is valid. 

Yet... I'm reminded of my favorite Linux analogy... " Linux is free, as in free kittens." You can have the kittens for free, but keeping them healthy is the owners responsibility. You must educate yourself on how to keep you kittens (Linux OS) healthy.

Don't quote me on any of this, I'm still a newb  ;-)

ASIDE NOTE: Why are you spammin?

---

### Post by Peter09 on 2007-11-12
as a matter of interest can you ping any other machine by host name from Ubuntu. Are you using DHCP?

---

### Post by TeaSwigger on 2007-11-12
Now, I had a you-know-what of a time getting my home network up, but it is up, and rock solid reliable now. I had similar struggles with Windows - to - Windows.

Since we're in a community cafe subforum mode ;) ...Why lay the issue at ubuntu's doorstep? They didn't make Windows, they just try to help you in your desire to make Linux based ubuntu work with an incompatible and closed-source system. Windows is doing nothing to help on their end, of course; they don't want you having the option at all. Linux to linux networking is much more like windows to windows in possible simplicity to the end user. Incidentally have you tried Kubuntu? They have some networking methods (which windows doesn't offer) such as zeroconf which can make networking a breeze. As for questions of superiority, which one is doing the majority of the file sharing in the world? Linux, being as the majority of web servers won't use windows as a server, which is basically what a home network is. Web serving is often of course a lot more demanding. So apples and oranges, as usual.

Now that's all hashed out - if you'd like to get your network running right, I'll be glad to help if I'm able to. Specify the setup and let's see.

---

### Post by BLTicklemonster on 2007-11-12
I don't understand how the steps one takes when setting up the network can't be all in one place where one can just get it over with. Are you saying that if a secure network is simple to set up, the hack fairy jumps out of the bushes on it and humps it's leg?

Fort Knox still has a front door. You don't have to compile one when you show up.

---

### Post by ant2ne on 2007-11-12
> **BLTicklemonster said:**
> I don't understand how the steps one takes when setting up the network can't be all in one place where one can just get it over with. Are you saying that if a secure network is simple to set up, the hack fairy jumps out of the bushes on it and humps it's leg?

Fort Knox still has a front door. You don't have to compile one when you show up.
That is pretty funny. Fort Knox does have a front door, So does my house, but it is more secure than a windows share LOL!

---

### Post by ed_d on 2007-11-12
I have found the only way to make the windows shares work without issues is to do static networking. Only way I have gotten it to work.

---

### Post by ant2ne on 2007-11-13
> **ed_d said:**
> I have found the only way to make the windows shares work without issues is to do static networking. Only way I have gotten it to work.

what is static networking?

---

### Post by BLTicklemonster on 2007-11-13
After playing around with Ubuntu for around 2 years now, and never getting networking down rock solid (as in: once I get it working, it invariably stops working at next upgrade, or for no apparent reason. Case in point: I could connect to the network and see other computers, then I couldn't, then last night I could, then I couldn't. all since last Friday), and now having problems getting a "this one works for Ubuntu" printer to work (as in it doesn't work at all), I'm pretty much burned out on this all. Period.

Look, if ubuntu were ready for the masses, then anyone could install it, then share a folder, fill in a few blank spaces (user name, password), then click okay/close, and the networking would work. Period. Same with a printer. But that doesn't happen, and after putting up with a "it's really neat, but all I can really do with it is get online and read emails, chat in a less than stellar functioning chat program, make some really neat graphics, etc." operating system for 2 years, I really don't feel that it's been worth the hassle at all. Not one bit.

Ubuntu severely inhibits my PCs functionality.

There's no other way of looking at it.

So I'll leave it installed, but I'm going back to the functional OS for now, as much as I hate to. I'm sure that Ubuntu will one day be ready, and that the developers will quit wasting time on eye candy, and work on the nuts and bolts:

auto grub: I ought to be able to drop a slave HD in, and boot to the desktop without having to reconfigure grub from a live cd.
Networking Wizard: I ought to be able to use a gui that asks me what I want to share, what user name, and password, and if it's windows share, and be done with it.
Printer: I think you're getting the idea now.

And this really pains me because I've been going around telling everyone about how good ubuntu is. Now I'm a bit of a laughing stock with 5 of my friends who couldn't get (ubuntu ready) printers or networking going either.

See you all around.

---

### Post by Daveski on 2007-11-13
> **BLTicklemonster said:**
> Ubuntu severely inhibits my PCs functionality.

You have got to be kidding.

Well, I am sorry you feel that way.

---

### Post by BLTicklemonster on 2007-11-13
My Pc's functionality, not yours.

If I can't get a reliable network after dicking around with this for 2 years, it's time to hang it up.

---

### Post by Naipes on 2007-11-13
In 2 years I'm sure you've seen this YouTube video, but just in case you missed it.  The video says it's for Ubuntu 6.something, but it works for later versions too.

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

This is how I set up my Ubuntu file server and it seems to work just fine. No problems talking to my Ubuntu boxes from my XP boxes and vice versa.  I also use Ubuntu as my print server. 

However, I  agree with you.  Linux is not for the masses, but Ubuntu is just about the closest thing to being ready for prime time as I've come across in a long time.  Ubuntu resurrected a 6 year old computer in my house  to serve as my file/print server.  

For a *free* operating system, I think it works pretty good and  the community around it is outstanding.  Help is always just a post away.  Of course, you already knew that... ;)

Good Luck!

---

### Post by BLTicklemonster on 2007-11-13
Yes, Naipes, and that's the hard part. I love Ubuntu, I just don't have the time to fiddle fart around with it any more.

A little haitus is in store, I guess.

I'll watch the video, see if that's any help.

---

### Post by BLTicklemonster on 2007-11-13
lmao, shared folders crashes now. Won't even come up.

Wheeee!

I knew better, I swear.

*edit:

Okay, rebooted, now I see shared, and yes, the folder I'd shared is ... shared. At least it says it is.

But: after going through all the stuff, if I click on places, network, I see windows network, but I click that, and I see nothing. No swirly icon showing I'm loading the several files which I could see ... an hour ago when I was using XP.

So whatever.

I go to the XP box across the room. I can see my computer. (will miracles never cease) I try to access it, and I am told I don't have permissions, to contact the administrator to see if I have permission. I ask myself, I do, yet dog gone, I still can't connect to it. (oops, no miracles tonight)

So ... yeah. Stick a fork in me, I'm done.

I do want to thank all the wonderful people here who have tried to help me.

I'll be seeing you all around later. I'm just too tired of all of this.

I'm going to kill the auto email for this thread subscription, so leave me out of any further voodoo here, thank you.

If, however, you feel that you have the key to the golden monkey's fruit jar, please PM me. I'm thinking I'd have to totally undo everything network-wise and start from scratch, though.

---

### Post by BLTicklemonster on 2007-11-16
Installed a fresh ubuntu. Went to video. Did the first step. Tried the second one, but shared folders won't open. Went back to see if I'd done something wrong in the first step, but now that won't open now.

Aaaaaargh. 

No, I can't leave it alone. This is eating me alive. 2 fricking years I have been messing with this!

*edit: Okay, logged out, back in, and I got to the end fine. I can see the XP machines.But, I can't access my machine with the username and password I entered. Of course. So I tried to add a new user name and password, and it won't accept it.

bill@ubuntu:~$ sudo smbpasswd -a dad
New SMB password:
Retype new SMB password:
Failed to modify password entry for user dad
bill@ubuntu:~$ 

I'm not making a mistake with the password, either.

Any way to remove the password?

---

### Post by jwrezz on 2007-11-18
This video tutorial was fantastic. Finally sharing w/ my Mac, and it's a piece of cake!

---

### Post by jwrezz on 2007-11-18
> **Naipes said:**
> In 2 years I'm sure you've seen this YouTube video, but just in case you missed it.  The video says it's for Ubuntu 6.something, but it works for later versions too.

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

This is how I set up my Ubuntu file server and it seems to work just fine. No problems talking to my Ubuntu boxes from my XP boxes and vice versa.  I also use Ubuntu as my print server. 

However, I  agree with you.  Linux is not for the masses, but Ubuntu is just about the closest thing to being ready for prime time as I've come across in a long time.  Ubuntu resurrected a 6 year old computer in my house  to serve as my file/print server.  

For a *free* operating system, I think it works pretty good and  the community around it is outstanding.  Help is always just a post away.  Of course, you already knew that... ;)

Good Luck!

This is what I meant to say was a piece of cake. It made it really easy. Should be a sticky.

---

### Post by BLTicklemonster on 2007-11-18
That just figures. Everybody can network but me, and I follow every tutorial to the letter. I don't think it's a problem with my router, because the network has worked before.

---

### Post by Daveski on 2007-11-18
BLTicklemonster, I know this sounds a bit simplistic, but are you SURE there is no security software on the Windows or Linux machines which might be causing problems? 9 times out of 10 if there is odd network behaviour, I normally end up discovering that a firewall or even antivirus software is blocking certain ports to certain addresses or subnets.

---

### Post by BLTicklemonster on 2007-11-18
The router has it's firewall, but that's never stopped me before. And I don't have firestarter going in ubuntu.

This is the same setup I've used before and gotten it going. That's what messes me up. It works once, then stops, never to work again.

---

### Post by BLTicklemonster on 2007-11-19
!!! suddenly, as if by magic, and with no changes made by me, I have to log in to access the XP boxes. And no, the user name and password I supplied don't work.

See why I have such a problem with this? It's like little unix gremlins running around complicating things or something.

---

