---
title: "no panel, and a virus"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-11-18
this is bad.
I was doing the usuall thing on my Xubuntu partition talking to friend with gaim listening to music.I take a picture of myself with a digital camera plug it in via usb over top of my usb flash drive computer screws up.  Panels are gone,  I think ill just restart i did when i booted up there it was all the windows i had at the time came no panels at all.  I go to the settings (via right click system --> settings) guess what.  I click on the panel button nothing happens.I turn off my Xubuntu partition only to find before it shuts down it say :
You do not have the lasted Version of clam anti virus, don't panic get it at [http://www.clamav.net](http://www.clamav.net)
lucky my windows partition works fine.what should i do in my Xubuntu partition i installed Clam anti virus via terminal(I think) i suspect i have a virus I need help badly.  Is there any way to possibly get rid of this Threat can i get back my panels?

---

### Post by lordvolo on 2006-11-18
i could really use help please

---

### Post by Swab on 2006-11-18
I don't think it's likely that a virus has broken your system.  Clam may well have spotted a Windows virus.  Boot into Linux and run clamscan manually, it should tell you which file it believes is the virus.

Edit: Actually, it's perfectly normal for Clam to complain as the repository version is not the latest I believe.  There is probably no virus at all.

---

### Post by turbojugend_gr on 2006-11-18
PLZ do not get offended but my sayings here...:mrgreen: 

WHAT on earth stroke you and you installed an anti-virus on a linux Machine????

Seriously now, it's one soOOooo unneeded and dangerous thing to do. Those creating an anti-virus for Linux, are imho the only ones dreaming of a Linux virus, and your incident just supports me with it.

Search all these forums I don't think you will find more than 10/15 people that complain for a virus and chances are that all where using an anti-virus...

The only thing I could suggest is un-installing such software, and waiting for someone else to answer in a better manner ;)...

I really, don't wish do sound offensive here, if only you could hear to the sound of my voice, to confirm that. 

Best Wishes ;), TJ.

EDIT: By dreaming a virus, I mean to point the fact it is a rare thing to appear, not a wish on their behalf...

---

### Post by lordvolo on 2006-11-18
unfortantly i dont know how to scan or i would every day i thought i installed it with this command:

Sudo apt-get install clamav

and how do you explan my panels

---

### Post by Swab on 2006-11-18
> **turbojugend_gr said:**
> PLZ do not get offended but my sayings here...

WHAT on earth stroke you and you installed an anti-virus on a linux Machine????

Seriously now, it's one soOOooo unnedded and dangerous thing to do. Those creating an anti-virus for Linux, are imho the only one dreaming of a Linux virus, and your incident just supports me with it.

Search all these forums I don't think you will find more than 10/15 people that complain for a virus and chances are that all where using an anti-virus...

The oinly thing I could suggest is uninstalling such software, and waiting for someone else to answer in a better manner ;)...

I really, don't wish do sound offensive here, if only you could hear to the sound of my voice, to confirm that. 

Best Wishes ;), TJ.

I have to disagree.  The point in installing anti virus in Linux is to make sure you don't pass anything on to Windows users.

I have a Samba server that has 25 Windows desktops connected to it.  Anti virus is essential on the server.

Even if you don't network directly with Windows machines, it's still good practice to have Clam installed.

---

### Post by loell on 2006-11-18
you can start your panel again
by running

xfce4-panel 

in the terminal

don't exit the terminal, just restart, and hopefully your panel will go back

ps: you don't need an anti virus, imho :)

---

### Post by Swab on 2006-11-18
> **lordvolo said:**
> unfortantly i dont know how to scan or i would every day i thought i installed it with this command:

Sudo apt-get install clamav

and how do you explan my panels

I don't know what's going on with your panels... 

clamscan is the command to manually run a scan.

man clamscan will give you all the details.

---

### Post by lordvolo on 2006-11-18
listen before this becomes a huge debate can someone help me?!?!

---

### Post by Swab on 2006-11-18
> **lordvolo said:**
> listen before this becomes a huge debate can someone help me?!?!

Did you try what loell suggested?

---

### Post by turbojugend_gr on 2006-11-18
@Swab: I would agree with you, if I wasn't that stubborn ;)...

No seriously you have a good point there, but I don't see Lordvolo administrating a cluster there, he seem like a desktop user to me ;)

@lordvolo: I am sorry for making this a short debate m8. I hope loell's answer is what will get your panels back (I never used XFCE).

---

### Post by lordvolo on 2006-11-18
i clamscaned it only scan the home directory, second probleum i got my panels  back but if i exit the terminal i lose them again.*ugh*

---

### Post by loell on 2006-11-18
i told you, ;) , don't exit the terminal, just restart

---

### Post by lordvolo on 2006-11-18
how do i get my applications menu back?

---

### Post by lordvolo on 2006-11-18
well im here how do i scan my intire Xubuntu partition and not just the /home directory?

---

### Post by adam.tropics on 2006-11-18
I don't use xfce, but doesn't <Alt><F2> bring up a 'run' dialogue for you guys? then do the xfce4-panel thing from there.

---

### Post by Swab on 2006-11-18
> **lordvolo said:**
> well im here how do i scan my intire Xubuntu partition and not just the /home directory?

sudo clamscan -v /

---

### Post by loell on 2006-11-18
> **lordvolo said:**
> how do i get my applications menu back?
im in ubuntu/gnome but i think

in the panel where you like to add the menu, right click it, add to panel, 
theres a menu plugin, just add it

---

### Post by catlett on 2006-11-19
If you are considerate of the people you send emails to etc, then you should have an anti-virus agent installed on linux. You can easily be a "carrier" of a windows virus and clamav (or the others) will keep you from infecting people you correspond with. Also many people dual boot and a linux anti-virus is very effective for checking their windows' partitions.
Since Dapper has been released there have been many turbojugend's around and I really dislike the forum because of it. These "know it alls" with their condescending attitudes would have had no place in the Ubuntu forums I joined.
This forum is to HELP people who have Ubuntu issues, NOT to run at the mouth about how "smart" you are or to iject your personal opinion. (Which I guess is what I just did so I think it is best I left this forum)

---

### Post by loell on 2006-11-19
> **catlett said:**
> If you are considerate of the people you send emails to etc, then you should have an anti-virus agent installed on linux. You can easily be a "carrier" of a windows virus and clamav (or the others) will keep you from infecting people you correspond with. Also many people dual boot and a linux anti-virus is very effective for checking their windows' partitions.
Since Dapper has been released there have been many turbojugend's around and I really dislike the forum because of it. These "know it alls" with their condescending attitudes would have had no place in the Ubuntu forums I joined.
This forum is to HELP people who have Ubuntu issues, NOT to run at the mouth about how "smart" you are or to iject your personal opinion. (Which I guess is what I just did so I think it is best I left this forum)

the first paragraph is helpful,

but, :-k  to whom are you reffering to, in the second paragraph?
and is the second paragraph beneficial to the current topic?

perhaps, you should start a thread in ubuntu cafe, with that line of topic.

---

### Post by adam.tropics on 2006-11-19
> **catlett said:**
> If you are considerate of the people you send emails to etc, then you should have an anti-virus agent installed on linux. You can easily be a "carrier" of a windows virus and clamav (or the others) will keep you from infecting people you correspond with. Also many people dual boot and a linux anti-virus is very effective for checking their windows' partitions.

Valid point, that for some reason has escaped me till now. With the last part though, if Linux checks a Windows Partition and finds a virus or whatever, does it deal with it in a 'windows safe' way? I presume it must because it wouldn't have an environment in which it could function (as a virus) would it?

---

### Post by adam.tropics on 2006-11-19
> **loell said:**
> the first paragraph is helpful,

but, :-k  to whom are you reffering to, in the second paragraph?
and is the second paragraph beneficial to the current topic?

perhaps, you should start a thread in ubuntu cafe, with that line of topic.

I believe it was this...

> **turbojugend_gr said:**
> PLZ do not get offended but my sayings here...:mrgreen: 

WHAT on earth stroke you and you installed an anti-virus on a linux Machine????

Seriously now, it's one soOOooo unneeded and dangerous thing to do. Those creating an anti-virus for Linux, are imho the only ones dreaming of a Linux virus, and your incident just supports me with it.

Search all these forums I don't think you will find more than 10/15 people that complain for a virus and chances are that all where using an anti-virus...

The only thing I could suggest is un-installing such software, and waiting for someone else to answer in a better manner ;)...

I really, don't wish do sound offensive here, if only you could hear to the sound of my voice, to confirm that. 

Best Wishes ;), TJ.

EDIT: By dreaming a virus, I mean to point the fact it is a rare thing to appear, not a wish on their behalf...

---

### Post by misfito on 2006-11-19
> **loell said:**
> you can start your panel again
by running

xfce4-panel 

in the terminal

don't exit the terminal, just restart, and hopefully your panel will go back

ps: you don't need an anti virus, imho :)

escuse my ignorance but I've seen this IMHO many times allready, I know this has nothing to do with the thread but what does it meens anyways?

---

### Post by adam.tropics on 2006-11-19
In my humble opinion

---

### Post by kvonb on 2006-11-19
```
Quote: If you are considerate of the people you send emails to etc, then you should have an anti-virus agent installed on linux. You can easily be a "carrier" of a windows virus
```

...is MS Windows considerate to Linux problems?  How hard do I hear you laughing?

With respect, Linux is not the "world police" of Windows' shortcomings!  Tough luck on the part of MS I say :)

---

### Post by Mimsy on 2006-11-19
This is turning into something very ridiculous... hate Windows all you want, and laugh at those you stll use it if you like. But go do it outside of a thread started by someone who needs help. The Backyard comes to mind. 

/Mimsy

---

### Post by bikeboy on 2006-11-19
If it's still not working after the restart, try looking for some log files that may give hints about why it's not coming back. The ones to start with IMO are /home/youruser/.xsessionerrors and /var/log/messages .

Good luck.

---

### Post by gn2 on 2006-11-19
> **adam.tropics said:**
>  if Linux checks a Windows Partition and finds a virus or whatever, does it deal with it in a 'windows safe' way? I presume it must because it wouldn't have an environment in which it could function (as a virus) would it?

The difficulty is write support for the Windows partition....

Linux is great on it's own, but dual-booting Windows with shared partitions could be a recipe for disaster.

---

### Post by Buck2348 on 2006-11-19
> **gn2 said:**
> Linux is great on it's own, but dual-booting Windows with shared partitions could be a recipe for disaster.

I'm a new Linux user.  I installed NTFS-3G and so far no problems at all writing to Windows partition.  gn2, is there some risk I'm not aware of?

Thanks,
Buck

---

### Post by Perfect Storm on 2006-11-19
Lets keep the "do-I-need-an-anti-virus" discussion out of this thread. I can refer this thread: [http://ubuntuforums.org/showthread.php?t=131616](http://ubuntuforums.org/showthread.php?t=131616) if people have an urge to discuss it.

Lets keep this thread on track.

---

### Post by gn2 on 2006-11-19
> **Buck2348 said:**
> I'm a new Linux user.  I installed NTFS-3G and so far no problems at all writing to Windows partition.  gn2, is there some risk I'm not aware of?

Thanks,
Buck

It's my opinion that if you are booted into linux on a dual-boot with Windows PC, and have access to the files across OS's, it could be possible to download something unpleasant unknowingly, then encounter problems when you re-boot into Windows.

I have experienced this recently and have stopped dual-booting.

There can be a risk of data loss/corruption writing to NTFS in Linux.

---

### Post by turbojugend_gr on 2006-11-19
> **catlett said:**
> If you are considerate of the people you send emails to etc, then you should have an anti-virus agent installed on linux. You can easily be a "carrier" of a windows virus and clamav (or the others) will keep you from infecting people you correspond with. Also many people dual boot and a linux anti-virus is very effective for checking their windows' partitions.
Since Dapper has been released there have been many turbojugend's around and I really dislike the forum because of it. These "know it alls" with their condescending attitudes would have had no place in the Ubuntu forums I joined.
This forum is to HELP people who have Ubuntu issues, NOT to run at the mouth about how "smart" you are or to iject your personal opinion. (Which I guess is what I just did so I think it is best I left this forum)

First of I am sorry Artificial Intelligence for this post, but I need to make some things clear, as you can see I am criticized for a post of mine. (post #4)

1. **[Since Dapper has been released there have been many turbojugend's around and I really dislike the forum because of it. These "know it alls" with their condescending attitudes would have had no place in the Ubuntu forums I joined.]** --> I don't believe it is your job to "TAG" me, and I don't believe Bostonians are thought to be narrow-minded. I 've been using ubuntu since Breezy (around april) and I don't get what Dapper has to do with "turbojugends" anyway. I haven't read in Dapper release notes ([http://www.ubuntu.com/news/606released](http://www.ubuntu.com/news/606released)) anything saying it's for smart asses like me **(?)**.

2. *This forum is to HELP people who have Ubuntu issues, NOT to run at the mouth about how "smart" you are or to iject your personal opinion.*
--> Helping someone is a subjective matter. For me not having the experience with such apps under linux, I tried to share my opinion regarding the use of anti-viruses under Linux (considering it was supposed to be a linux virus, since the user complained so). Apparently I was right, since the user's problem doesn't seem to be connected to that virus (at least until the moment I wrote that). So the user got panicked, cause he thought the virus made his panels disappear, while had he not used the anti-virus, he would calmly ask for a command to bring his panels back. After all, I've never seen the user confirming neither he is an administrating a cluster nor he confirmed he is massively forwarding e-mails to windows users, so I **suppose** he was just insecure (after using winxp for many years, I guess) about viruses, and thought an anti-virus is needed in Linux too, so that safety is to be secured. I repeat that is only my hypothesis, once bitten twice shy...

3. *These "know it alls" with their condescending attitudes would have had no place in the Ubuntu forums I joined.* Where exactly do you see these? Maybe when I please for the user to not to get offended, maybe when I wish I do not sound offensive, or when I wish he could hear my voice tone, to make sure I 'm positive or maybe when I am suggesting to listen to someone else with better manners (humorous)?

4. In general you should mind your manner my friend, I never gave you the impression you can insult me publicly, I wish you just woke up on the wrong side of the bed, and you've regretted your outburst. Last but not least, I advise you to read to users post more in detail before deciding to insult them. I don't expect you to say you are sorry, if you were that kind of man, you would bother reading my post before posting about it, and also to take the user's actual reactions regarding my post, since he got my spirit, I don't get why you come and ruin this thread.

5. You are welcome any time to contact me via IM, so I can prove my words, as I won't even read any posts of you here, as I would be tempted to be dragged into debate. I really mean you are welcome, I just wish to leave this thread to it's actual purpose, I understand a post can confuse its reader, cause it is not showing the writers attitude.

P.S.: @ lordvolo: I really hope I didn't offend you m8, I tried hard to make sure I didn't. I also hope your are OK with your issues now.

---

### Post by bodhi.zazen on 2006-11-19
> **lordvolo said:**
> this is bad.

What is the current problem?

If I am understanding your post you have a problem with the xfce panel.

I have had this problem with XFCE and switched to an alternate WM because of it.

To debug, open a terminal and type:```
xfce4-panel **&**
```

The & is to run the panel in the background.

post any error messages.

Also do a google search ["xfce panel crash"](http://www.google.com/search?q=xfce+panel+crash)

This behavior is NOT due to some type of virus and, unfortunately, is not uncommon in xfce.

IMO Linux anti-virus programs are helpful if you wish to offer your windows brethern some viral protection by running an antiviral package on a server, (well that is what linux AV does best). It seems to me that scanning Linux file systems, the way you may be accustomed in Windows, results in fasle positives and panic.

files on Linux can contain viral code, but the code has not been described to be able to propagate.

**gn2:** If you have any data or information to support your claim:> It's my opinion that if you are booted into linux on a dual-boot with Windows PC, and have access to the files across OS's, it could be possible to download something unpleasant unknowingly, then encounter problems when you re-boot into Windows.

**I have experienced this recently and have stopped dual-booting.** I would love to see it....

Although this may be a (weak) theoretical risk, I have NEVER seen this claim substantiated elsewhere and if you have any security information please share.

Otherwise I would assume your problem stems from windows or transferring a contaminated file from Linux to windows which then ran on windows. Neither of these scenarios stems from rw access to ntfs or dual booting (as the problem is an infected file and you should scan files from windows before transfering them).

Dual booting is perfectly safe. Just watch which files and how you transfer them to windows.

---

