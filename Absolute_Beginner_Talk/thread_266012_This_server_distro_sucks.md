---
title: "This server distro sucks"
date: 2006-09-26
forum: Absolute Beginner Talk
---

### Post by Validimir Putin on 2006-09-26
Sorry guy's but I was sucked in by the hype .... However 3 long evenings later and several attempts trying to successfully load the server version in a VMWare environment I have failed to get a working server with a gui desktop environment and I'm a computer techie for a job!....I hate windows with a passion...but this is sad..If you want this to ever get past geek porn then you have to make the install work first time and be managable from the first keystroke, not be inpenetrable command line tosh..I was angry at first now I'm just dissapointed..thought it would be better than this...

---

### Post by xpod on 2006-09-26
WOW...Any particular reason you opted for the obviously more complicated server install as apose to the desktop one???mho

I dont know about you but i would`nt have a clue what to do with nothing bar a "prompt" either.

EDITNOT as my first go at least

---

### Post by bluefuse on 2006-09-26
Well everyone is entitled to there opinion, ofcourse. me personally I think any deb distro is a excellent server distro. my second choice for a server distro would be "debain" now if you want simple and easy to maintain out of the box try CentOS system with the Bluequartz server its a all in one ftp/dns/mail/http/https/ and more...................

[http://www.nuonce.net/bq-cd.php](http://www.nuonce.net/bq-cd.php)

[http://www.nuonce.net/bq/Nu-CentOS-BQ-4.5.iso](http://www.nuonce.net/bq/Nu-CentOS-BQ-4.5.iso)

NuOnce Network is also offering commerical
Applications as well for OUR CentOS/BQ CD!

NuOnce Commerical CentOS/BlueQuartz Offering

# Bandwidth Monitoring (purchase)
# NuOnce Security Package (purchase)
# MailScanner /w ClamAV (purchase)
# PHP v4.4.0 (purchase)
# PHP v5.0.4 (purchase)
# Open Web Mail (purchase)
# osCommerce Installer (purchase)
# SpamAssassin w/ DCC (purchase)
# phpMyAdmin (purchase)
# AwStats (purchase)

---

### Post by Wilb on 2006-09-26
> **Validimir Putin said:**
> Sorry guy's but I was sucked in by the hype .... However 3 long evenings later and several attempts trying to successfully load the server version in a VMWare environment I have failed to get a working server with a gui desktop environment and I'm a computer techie for a job!....I hate windows with a passion...but this is sad..If you want this to ever get past geek porn then you have to make the install work first time and be managable from the first keystroke, not be inpenetrable command line tosh..I was angry at first now I'm just dissapointed..thought it would be better than this...

Why do you want a desktop environment if you're installing a server? Waste of resources... However, if you do then:

 sudo apt-get install ubuntu-desktop 

is your friend.

---

### Post by bodhi.zazen on 2006-09-26
> **Validimir Putin said:**
> Sorry guy's but I was sucked in by the hype .... However 3 long evenings later and several attempts trying to successfully load the server version in a VMWare environment I have failed to get a working server with a gui desktop environment and I'm a computer techie for a job!....I hate windows with a passion...but this is sad..If you want this to ever get past geek porn then you have to make the install work first time and be managable from the first keystroke, not be inpenetrable command line tosh..I was angry at first now I'm just dissapointed..thought it would be better than this...

Here is my Ubuntu server running X.

[[color=blue]Bodhi's Server[/color]](http://img177.imageshack.us/img177/6242/200609242354061600x1200scrotkk0.png)

(It's OK)

If I can do it, why can't "a computer techie for a job" ?. Linux is not windows.

Now, is there a question?

---

### Post by skymt on 2006-09-26
The server install is CLI-only, by definition. That's what it's for. If you want a GUI, do a regular install and add server packages. The only reason they offer a separate server version is because most Linux server admins prefer not to waste resources on a GUI.

---

### Post by xpod on 2006-09-26
> Here is my Ubuntu server running X.

:cool: ;)

---

### Post by Validimir Putin on 2006-09-26
Like I said I'm a pooter techie for a job and if I have to stand in a another machine room and look at another win3k server install I'm gonna scream..Thats why I thought ahh something different..I can run this at home, no issues with ferociously overpriced licensing, and it come loaded with all the stuff I want..Cha..as if..I trawled the forums even remembered how to use vi "yes I've admin'd UNIX boxes too both SGI and Sun". It just looked so promising and delivered so little in what you'd call a mature market...Ok you can get stripped down software and O/S's but peoples expectations are so much higher these days and well you just expect that a question at the start like do you want a gui interface might be a good call for those looking to have a machine up and running in short order without having to have a compuetr science degree...If this distro is to trounce the likes of red hat and Suse and present itself as a viable option for people who can't afford windows systems its gonna have to do better..Sad but unfortunately true

---

### Post by xyz on 2006-09-26
Hello Mister Putin,
Sincerely sorry things don't work "better than this" and that "3 long evenings later and several attempts" it didn't work past the "geek porn" and that you can't "penetrate the command line first time" ...I must say you are a strange computer techie...was it ever easy at first!

I don't know what to say because some folks (high % don't) barge in saying "it doesn't work.period" and so many things do work here in the Linux "gang".

If something doesn't work for me, most part it's I don't know how or compatibility problems...aside from that I try to ask questions in such a way that I don't put people off, the same ones who can help me!

Free distribution doesn't mean it is a freeway!

Your post is interesting.
No offence at all intended. Welcome to this great world!

---

### Post by whizbaby on 2006-09-26
Why X on a server? Each process on a server is a potential security risk so minimize the number of proc's down to what is vital for the services and leave out the rest. Perhaps on a private server it's "safe" (though not recommended) to run X, but definitely not on business servers (unless you patch your system to death).

Enough brainy-smurf talk, nice desktop, bodhi!

---

### Post by bodhi.zazen on 2006-09-26
Validimir Putin:

You have a point, kind of.

Linux is not Windows. Ubuntu is not SUSE.

If you want enterprise level Linux, IMO, go with Red Hat, Centos, or SUSE. Or even Unix. If you have as much experience as you claim you should know this.

Ubuntu has been marketed, IMO, to users new to Linux. The server install you looked at is a minimal install and, IMO, a Porsche. Your windows server is, <EDIT> (almost got meself banned):evil:.

At any rate, you need to learn to drive :twisted:.

I for one do not want a gui on my server. That server I showed you is being used as a desktop workstation. It is a minimal install, minimal GUI, and it will out perform almost anything (OS that is, not the best hardwaer mind you... :mrgreen:) except for Gentoo. :twisted:

---

### Post by Validimir Putin on 2006-09-26
OK I'm shamed...I'll give it another go, why do I do this to myself? 

The install seems to go OK but I want a desktop..just to see if I can..I've done the Sudo get update stuff but still the x server wouldn't start.

NO nothing is easy at the start but then it doesn't have to be designed difficult either..there is a lot of computing history now and like I said expetctations are higher now...How many of you have kids with IPOD's and mobile phones they didn't exist when I was a kid but now even 9yo's can't live without them? Things change and the command line was a system console presentation of the late 70's...rant over now back to a new VM...

---

### Post by xpod on 2006-09-26
I aint no "poohter techie" and had`nt even seen one till march but found it all relatively simple.....Of course i aint doing real complicated stuff like installing the server version..........:-k :rolleyes: 

Give it another go.Im sure the boy`s here will have you up in a flash.Might even get you "flash"..Go with the gui;)

---

### Post by lapsey on 2006-09-26
good luck

---

### Post by bodhi.zazen on 2006-09-26
> **Validimir Putin said:**
> OK I'm shamed...I'll give it another go, why do I do this to myself? 

The install seems to go OK but I want a desktop..just to see if I can..I've done the Sudo get update stuff but still the x server wouldn't start.

NO nothing is easy at the start but then it doesn't have to be designed difficult either..there is a lot of computing history now and like I said expetctations are higher now...How many of you have kids with IPOD's and mobile phones they didn't exist when I was a kid but now even 9yo's can't live without them? Things change and the command line was a system console presentation of the late 70's...rant over now back to a new VM...

I knew you'd see it my way ! :)

Now on to the fun stuff.

Start with an old box you are not useing for anything else.

boot it with the live CD, install to HD.

Now boot ubuntu and break it proper !!

LOL :lol:

If you need help, PM Bulldog.

---

### Post by RobsterUK on 2006-09-26
What I'm left wondering is, if at any point during the "3 long evenings" you posted the problems you were having on this forum. Perhaps if you had done so you wouldn't be so frustrated.

---

### Post by bodhi.zazen on 2006-09-26
> **whizbaby said:**
> Enough brainy-smurf talk, nice desktop, bodhi!

Thanks.

---

### Post by xpod on 2006-09-26
> If you need help, PM Bulldog.

Great idea
Line them up:mrgreen:

---

### Post by bodhi.zazen on 2006-09-26
Another Windows user rescued I'd say.

I'll bet Bulldog's collar Validimir 'll b teachin us noobs how to Ubuntu by tomorrow.

---

### Post by Validimir Putin on 2006-09-26
OK thanks for the support I'll report back this time tomorrow and let you know how I get on..

---

### Post by xpod on 2006-09-26
Good luck:D 
Dont give up...you might just be suprised;)

---

### Post by az on 2006-09-26
> **Validimir Putin said:**
> 

The install seems to go OK but I want a desktop..just to see if I can..I've done the Sudo get update stuff but still the x server wouldn't start.


Enable the online repos and install ubuntu-desktop.  That being said, all those desktop packages will not help you one bit.  By and large, there is no GUI to server applications.  You don't need it.  

You will find that managing your servers a lot easier if you just accept that to begin with.  Probably the biggest reason why there is not GUI is that nobody who runs a LAMP server (or any other linux-based server) really thinks it would make their life easier.

---

### Post by kerry_s on 2006-09-26
Let's talk you through it just in case your not doing it right.

server install
sudo su  <makes you root
nano /etc/apt/sources.list
comment(#) out the cdrom and uncomment all the other repo's(they start with deb)
ctrl and x and y and enter to save
apt-get update
apt-get install (you choose here) choice's are ubuntu-desktop(gnome) kubuntu-desktop(kde) xubuntu-desktop(xfce4)
reboot

or you can go custom

apt-get install x-window-system-core gdm xterm (WM here)<fluxbox, icewm, wmaker, openbox... are good light weight WM's.

---

### Post by bodhi.zazen on 2006-09-26
> **kerry_s said:**
> Let's talk you through it just in case your not doing it right.

server install
sudo su  <makes you root
nano /etc/apt/sources.list
comment(#) out the cdrom and uncomment all the other repo's(they start with deb)
ctrl and x and y and enter to save
apt-get update
apt-get install (you choose here) choice's are ubuntu-desktop(gnome) kubuntu-desktop(kde) xubuntu-desktop(xfce4)
reboot

or you can go custom

apt-get install x-window-system-core gdm xterm (WM here)<fluxbox, icewm, wmaker, openbox... are good light weight WM's.

Please use and advise aptitude over apt-get.

Here's why: [[color=blue]Aptitude[/color]](http://ubuntuforums.org/showthread.php?t=37736)

---

### Post by kerry_s on 2006-09-26
You can advise aptitude. I hate aptitude and always uninstall it. If you screw up in aptitude your screwed, If you have problems with apt-get there are more solutions. I trust apt-get alot more than i would trust aptitude. Even in that how-to it dosen't tell you what to do if something goes wrong. Why? Cause your screwed.

---

### Post by Paul133 on 2006-09-26
Well, I don't understand why you installed the server if you wanted a GUI. The regular install contains everything in the server, plus much more. As others have suggested ```
 sudo aptitude update 
``` and ```
 sudo aptitude install ubuntu-desktop 
``` will get you the regular desktop verison of Ubuntu. I installed the server since the regular install kept freezing, and then installed the desktop, and it works fine. Good luck.

---

### Post by az on 2006-09-27
> **bodhi.zazen said:**
> Please use and advise aptitude over apt-get.

Here's why: [[color=blue]Aptitude[/color]](http://ubuntuforums.org/showthread.php?t=37736)

Actually, you should just say "use any method you want to install ....."  and provide a link to the package management wikipage. ([https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware))

People may end up thinking that certain packages need to be installed using one package manager frontend or otherwise won't work - that's not the case.  

You should not tell people that one method is incorrect - that is another issue entirely and you should not confuse the issue at hand with your personal preferences.

---

### Post by shat on 2006-09-27
It's actually pretty easy to get confused by the different ubuntu offerings.  

I installed ubuntu about a year ago, on it's own partition (breezy), and never really played with it.  

So a few months ago, I wanted a pure ubuntu laptop, so I went to make the CD.. and downloaded the server (I didn't want a Live version! Duh! Server was the only other choice.. and before when I downloaded Ubuntu, the choices wern't there.. Hm.) And needless to say, was confused by the CMI I recieved.  Fortunately, I figured out what I did, and the desktop install was sleek and simple!

So anyways, easy mistake to make!

---

### Post by Gladimhere Valdimir on 2006-09-27
Hi xpod, kerry, Bodhi..yeps its me under a new psudeonym ..

Well I gave it another go and after following Kerry's instructions and after the 

"apt-get install ubuntu-desktop" command 

I got a screen full of scolling 

"Depends...but is not installable"

I don't suppose for a moment thats correct..

Any suggestions?

---

### Post by xpod on 2006-09-27
Vlad the installer

---

### Post by Gladimhere Valdimir on 2006-09-27
Y..I might be Vlad the flamin uninstaller soon tho'

---

### Post by xpod on 2006-09-27
Good eveining mate .
Sorry the best i can offer you is my corny humour and mabey some of the basic basic`s:-? ...but Im sure these good folks will manage to help you with the rest

Would`nt you be better just burning the desktop cd for starters m8?
I think i understand why you might "want" a server but i reckon what you "need" is something you can at least use........for now of course:) 

Obviously if thats not an option then you`ll need to do things the hard way

---

### Post by Gladimhere Valdimir on 2006-09-27
Yeah I'm really frustrated with this. Reckon I'm going to toast it and go fo a suse download and see how that goes..

---

### Post by xpod on 2006-09-27
Why give up on ubunto so quick...just cause you`ve had a bad experience with one "cd"...
I had quite a few problems trying to find the right one for the 2 pc`s sitting here....Ubunto went on this ok but i had to try a few different ones to eventually find that the Kubunto alternate was the one for the second pc.

I really think you should give it another go with the desktop alternate installer mate and i think you`d be ok...

Of course thats just my own very humble opinion my friend:D 
Good luck regardless

EDIT...Many folks give up just cause "that" cd would not load or run.They dont know what their missing IMO

---

### Post by Gladimhere Valdimir on 2006-09-27
Xpod all I wantd was a server I could stick in my garage with my web sites on and bits and pieces ... I have 2k box there and it was up and running doing everything I wanted in an hour...This has taken ages and what have i got to show for it? A lot of new forum mates.. :) which is not a bad thing but not where I want to be. Shame really. I will try the desktop but its the server thing I want. I'm gonna toast the Server VM now and check the desktop.

---

### Post by xpod on 2006-09-27
I understand mate.sorry
At least you`ll get a better feel for things with the gui`s and more ..you wanted:D

---

### Post by Gladimhere Valdimir on 2006-09-27
Xpod if u'r around I'm gonna start the ubuntu desktop install now and see how long it takes to the first login..k?

---

### Post by bulldog on 2006-09-27
Uhhmmmm,what is that pm Bulldog stuff??

If you both stay that way I have a days work with all the pm's that I got.

Thx bodhi.zazen en xpod ofcourse,I asked the admin's for a bigger postbox.:D :D :D

---

### Post by bodhi.zazen on 2006-09-27
If it is not too late:```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by Gladimhere Valdimir on 2006-09-27
to latemate installing the desktop now

---

### Post by xpod on 2006-09-27
Bigger kennal you need m8

EDIT:sorry i meeant "kernal":-\"

---

### Post by xpod on 2006-09-27
40 mins......tick tock,tick tock

---

### Post by Gladimhere Valdimir on 2006-09-27
Well got a desktop with a disk icon with install written on it does than need to be clicked on?

---

### Post by xpod on 2006-09-27
By god that was quick......You got a "red button" you pushed there????
Cant wait to see how long the insatll takes once you`ve clicked that install icon

---

### Post by Gladimhere Valdimir on 2006-09-27
remeber I'm doing this in VM ware with a virtual CD working of the downloaded iso

---

### Post by bodhi.zazen on 2006-09-27
> **bulldog said:**
> Uhhmmmm,what is that pm Bulldog stuff??

If you both stay that way I have a days work with all the pm's that I got.

Thx bodhi.zazen en xpod ofcourse,I asked the admin's for a bigger postbox.:D :D :D

Well if I ask they PM me they all think I'm arrogant. :confused:

Besides you have a more inviting avatar.... :biggrin:

---

### Post by lapsey on 2006-09-27
> **Gladimhere Valdimir said:**
> Well got a desktop with a disk icon with install written on it does than need to be clicked on?

if you want to install ubuntu....





...yes.

---

### Post by Gladimhere Valdimir on 2006-09-27
Quick question...how demanding is this on hardware..I might knock a PC together from bits for my mum if its not to heavy on resource.

---

### Post by xpod on 2006-09-27
> remeber I'm doing this in VM ware with a virtual CD working of the downloaded iso

That might as well be chinese to me:confused: 

I barely know the real thing never mind the pretend ones

EDIT> Quick question...how demanding is this on hardware

Mines are all bits.. And i aint got many resources to start with:D

---

### Post by Gladimhere Valdimir on 2006-09-27
Xpod, I'm running Win Xp on a reasonable quick box and using a application called VMWare (google it) it allows you to load and run operating wsystems like linux and others in aVirtual Machine (VM) so you can sort of run a machine in a machine..its pretty cool and llows you to play without toasting the host machine..BTW 93% done..whoo hoo :)

---

### Post by podunk on 2006-09-27
Quote from bondi:
Now boot ubuntu and break it proper !!
~~~~~~~~~~~~~~~~~~~~~~~~~~

Heard that! :-D

Nice desktop!

---

### Post by xpod on 2006-09-27
hehe...i know what it is m8 without googling it.It just aint something i know jack about.....Neither is much else come to that but yer trying again which is the best i could dae

---

### Post by Gladimhere Valdimir on 2006-09-27
I'm at a login screen now...

---

### Post by vinnn on 2006-09-27
Why don't you just install the regular Ubuntu CD if you want an easy to setup  GUI'd distro to store your files or run Apache or whatever?
You can still do all the same stuff on the desktop distro as what you can with the server distro but with more noob friendly tools.

I administer hpux & linux servers as part of my job, I find it puzzling that you would want X running on a 'server' as it's a just a big security vunerability.
One more niggle... just because x86 server software can usually run on a PC, remember that a PC is not a server.

---

### Post by lapsey on 2006-09-27
> **vinnn said:**
> I find it puzzling that you would want X running on a 'server' as it's a just a big security vunerability

explain. also maybe you can tell me if one can block the vnc port from certain interfaces

---

### Post by bodhi.zazen on 2006-09-27
> **Gladimhere Valdimir said:**
> I'm at a login screen now...

Well, what is that blue screen behind? No wonder you are complaining about a lack of resources & runnin so slow! :lol:

Welcome.

---

### Post by bodhi.zazen on 2006-09-27
> **podunk said:**
> Quote from bondi:
Now boot ubuntu and break it proper !!
~~~~~~~~~~~~~~~~~~~~~~~~~~

Heard that! :-D

Nice desktop!

How did you find me here?

Thanks. :cool:

---

### Post by Gladimhere Valdimir on 2006-09-27
Bodhi.. I'm running VMware on a XP host so I can play without toasting my main machine..its not so bad..

---

### Post by xpod on 2006-09-27
Your more likely to "toast" it just by"using" it than what you would be if it was tucked up safe on it`s own partition while you just run the cd from the cd-rom......

EDIT:it would`nt touch your main setup or even go near it:D

---

### Post by Gladimhere Valdimir on 2006-09-27
OK I'm won over...let me play with it ..oh err... and I'll get back to you all..thanks for the support I was pretty p'd off but now all smiley..

---

### Post by vinnn on 2006-09-27
> **lapsey said:**
> explain. also maybe you can tell me if one can block the vnc port from certain interfaces

Well remote desktop wasn't what I was talking about, the X11 protocol is the biggest insecurity attributed to running an X server.
But the answer to your question would be to block port 5900 for the adapter that you want deny VNC using **iptables**
```
man iptables
```

---

### Post by xpod on 2006-09-27
> OK I'm won over...let me play with it ..oh err... and I'll get back to you all..thanks for the support I was pretty p'd off but now all smiley..
Reply With Quote

Successfull infection???
Good stuff........wait for the rush:mrgreen:

---

### Post by bodhi.zazen on 2006-09-27
> **Gladimhere Valdimir said:**
> Bodhi.. I'm running VMware on a XP host so I can play without toasting my main machine..its not so bad..

Very easy to fix this, no.

Install Ubuntu, run Windows vmware !! :biggrin: And don't let that windows partition out on the net... [-X

---

### Post by JeevesBond on 2006-09-27
Go for it, install the desktop then open Synaptic and get yourself: Apache, PHP, MySQL and all the other stuff you might want.

It works perfectly for me, think they were all setup 'out of the box' (or installer rather ;) ).

As for VMWare, am doing exactly the same in reverse, just to run IE7 for testing (don't worry I wouldn't actually do any browsing with it *chortle*) and Eve-Online.

Let's hope [ies4linux](http://www.tatanka.com.br/ies4linux/index-en.html) gets the former and [Cadega](http://www.transgaming.com) gets the latter fixed soon. :)

A hatred for Windows is where it starts, it ends with Ubuntu Linux.

---

### Post by 52rockwell on 2007-06-10
Is there a Title for that artwork Bodhi  . Im a buddhist and got booted from a Southern Baptist church for the sin of Syncretization... Its an old sin and Im kinda proud to have learned it on my own..Not braggin understand but for a po whiteboy from North Texas it is an accomplishment.
  It looks to me like a beautiful angel from heaven comforting a burned up(out}fallen star.
Maybe a white version of Guanyin for the Christian psyce?

---

### Post by alecz20 on 2008-03-11
> **Gladimhere Valdimir said:**
> I'm at a login screen now...

What...? I thought WM was Window Manager you were talking about.
There is blasphemy in this picture! :D:D:D:lolflag:
In any case, install on a PIII is about 20 min I guess. and you need at least 256MB to run Ubuntu Desktop decently.
CPU wise... at least PIII.

---

