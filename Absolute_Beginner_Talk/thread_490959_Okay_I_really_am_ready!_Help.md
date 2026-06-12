---
title: "Okay I really am ready! Help?"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by RD4UBN2 on 2007-07-03
I have been reading up on Ubuntu and your community. Looks like it's worth the leap. Here's where I am now... I don't hate Windows, but for me it has become too expensive to maintain - given the stability I am currently getting from it.

I am used to Windows. I know enough about keeping it operating smoothly to be the one my family and friends call when they crash their system, or have a virus.

I know *nothing* about Linux. No thing. Nada. I love the idea of choices, but am not too proud to admit that I am intimidated by the very many choices there are here. I find myself overwhelmed with questions. Do I need a virus scanner? Malware scanner? How do I uninstall Windows? Will internet connection be an issue? And on. And on.

I am very willing to learn but I am finding it hard to determine where square ONE is, because it seems square one is different for everyone. My biggest concern is being sure I remain connected to the internet so that I can come here and resolve any problems I encounter. So... I imagine it's best to give my hardware and let a more seasoned user help me pick a path.

I have:
HP Pavillion a450n
Intel(R)
Pentium(R) 4CPU 3.00GHz
512 MB of RAM

Canon PIXMA MP600
I can provide info on any other hardware if you tell me where to look for it.

The only software I really use is:
AdAware
Yahoo Messenger
Apophysis
Paint Shop Pro

I'm sure I can fall in love with Linux equivalents if I cannot continue to use these.

I want to make smart choices about what Linux programs will cooperate best with what I have to work with. I am also interested in having Windows completely off my hard drive once I know Ubuntu will work for me. Is this possible?

Any and all help is welcome and greatly appreciated!

Mad love,
Jeannie

---

### Post by lisati on 2007-07-03
I suggest you start with a desktop version of the "Live CD" which you can get from [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)  - have a play with it before you commit yourself to installing it. If you're comfortable "burning" CDs you can download a copy, otherwise theres the "Request Free CDs" option.

---

### Post by RD4UBN2 on 2007-07-03
ty muchly, I will try to find a clean cd to do that.

---

### Post by lisati on 2007-07-03
I forgot to add: if you start the CD with Windows running, it gives you a chance to play with Windows versions of some of the software on the disk. Otherwise, if you boot from the CD, it lets you run Ubuntu without having to install.

---

### Post by GeeZor on 2007-07-03
PaintShopPro will become an issue for you i am afraid. But other that that be prepared to get swiped off your feet and fall in love with Linux..

---

### Post by Inxsible on 2007-07-03
GIMP which comes installed with Ubuntu, does a lot of things that Paint Shop Pro does, if not all.
 
Substitutes for Yahoo Messenger are a plenty. Kopete, GAIM/Pidgin, GizmoProject, GyachI and many others

---

### Post by RD4UBN2 on 2007-07-03
It all sounds wonderful!

I hate to be so needy right from the gun, but doing this install... can i save that to a cd from the download site, or do I need to save it to my desktop and then burn things from that to a cd. It sounds like the latter, but 700 MB? Yikes? I can delete that once I've burned what I need if it goes to the desktop, yes?

---

### Post by GeeZor on 2007-07-03
Gimp covers it quite, but not if you are in to professionaly editing photo's...

installing software is done in the terminal,
```
sudo  apt-get install kopete 
``` for instance....
or 
```
sudo apt-get install amsn
```
or 
```
 sudo apt-cache search <package>
```


You dont need to store these files, they are all available from the Ubutnu repository.

see /etc/apt/sources.list for a list site's that provide the packages for you....

---

### Post by hyper_ch on 2007-07-03
at first you don't have to use the terminal to isntall software.
You can use synaptic/adpet (depending on whether your run Ubuntu or Xubuntu or Kubuntu).

you can access them somewhere in the menu "Install Software" or maybe they are called Adpet or Synaptic... I don't really remember... it's been quite a while since I used a graphical interface to install software.

What GeeZor has written is for the terminal. I find it, like him, quicker to use that... In the end, adept and synaptic and apt-get (command line) and aptitude (command line) use all the same backend.

gimp should do a marvellous job at replacing Paint Shop Pro, however it handels some things differently than PSP does.

What is Apophysis?

---

### Post by sailor2001 on 2007-07-03
I think what the lady is refering to is the live cd disk of ubuntu....I suggest you download the iso of feisty to someones computer that is dsl.......burn the iso image at 4x speed to a disk. It's a live disk that you can boot into and play with....... When you'r e ready, you can install from that in a dual boot setting... Have fun. a great adventure.

---

### Post by RD4UBN2 on 2007-07-03
> **hyper_ch said:**
> What is Apophysis?

Apophysis is a free fractal generator. I'm not very good at it yet, but with patience you can get some amazing art out of it. I am convinced the universe is one big fractal now.

You can see the products of APO here [http://apophysis.deviantart.com/gallery/]("http://apophysis.deviantart.com/gallery/") and follow links there to get it if you're interested.

---

### Post by RD4UBN2 on 2007-07-03
> **sailor2001 said:**
> I think what the lady is refering to is the live cd disk of ubuntu....I suggest you download the iso of feisty to someones computer that is dsl.......burn the iso image at 4x speed to a disk. It's a live disk that you can boot into and play with....... When you'r e ready, you can install from that in a dual boot setting... Have fun. a great adventure.

I have a decently fast cable connection, I think I will give it a shot. Fiesty is the 7.04, yes? And this huge file goes to my desktop? And then I burn, but I have never burned an ISO image - so do I need a special burn program for that? And after I have burned it I can delete the 700MB file?

---

### Post by RD4UBN2 on 2007-07-03
Okay I think I got it... downloading now.

Woohoo!

---

### Post by hyper_ch on 2007-07-03
For burning:

[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

Have a look at this site. It's really good for beginners :)

Maybe that fractal program runs with wine...

---

### Post by DrMega on 2007-07-03
2 things:

1. When you download the CD image, and burn it to a disk, you'll need to burn it as an ISO image (most good burning software will have such an option), rather than simply burning the ISO file onto the disk.
2. Not all hardware is supported. Particularly printers. I think you'll be OK though. Take a look at [http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600]("http://www.linuxprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600")

---

### Post by sailor2001 on 2007-07-03
k3b is a great burner (in synaptics) A caution.. before installing ubuntu on a dual boot.........defrag your windows......

---

### Post by Rhumbline on 2007-07-03
Here's my experience, it may help.

Like you I was interested in getting out of windows, because even for simple everyday stuff it's just too much and all the commercial stuff bugs me.

I downloaded Ubuntu and also a disk burning program Infra Recorder. I burned the ISO.

I had two Windows machines, a recent Dell and  a computer I bought in Malaysia.
The Ubuntu wouldn't run on either for different reasons. One to do with clock speed, and the other (Dell) something to do with the display.

My original plan was to partition one to try Ubuntu but as they wouldn't run it I abandoned that idea... I still wanted to play with Ubuntu but was reluctant to wipe either of the machines I had.

I got an old computer from work which was being thrown out. I put in the Ubuntu disk and it loaded and was up and running in less time than a windows installation. All the software I looked at was easily understandable.

I bought a cheap wireless card and put it in and it worked first time ( I tested it with one of my other cards first).

I ditched the old clunky monitor and bought a new flatty and it worked fine (I tested it with one of my other screens first).

Today I tried my printer, a Canon ip2200 and it didn't work. There isn't a driver for it in the list. So I'm going to get an old deskjet which is being thrown out and I'll try that. Old stuff seems to work fine with Linux.

I've been using windows since the late '80's and DOS before that so I'm not afraid to try things. But some of these guys have been to university to learn how to use Linux. I'm content to use the GUI like windows and I don't plan to get into programming. These guys are doing a great job making it easy for beginners so stick with it....

---

### Post by ITdrummer on 2007-07-03
I agree, InfraRecorder is a great, light-weight burning program.  

Check this out on burning an image using InfraRecorder:
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by RD4UBN2 on 2007-07-03
Thabk you all SO much! I am really loving the community here, and am even more determined because of it to make Linux work for me. I've a hunch it's less of a making it work for me thing and more a get over myself and just DO it thing. Ha!

I've downloaded Fiesty to desktop. Then found that I was out of cds. :p
I defragged yesterday... but I am having more problems with this machine all the time. I went from:

Random shutdown past 2 weeks, progressively worse(Windows blaming *everything* via error reporting).
Updated NVIDIA drivers per prompt yesterday
Then they wanted me to upgrade - Vista! No thanks. :-| SP2! No thanks. :-|
Now Yahoo stopped working, several programs won't work...
Did a recovery. Now shutdowns have ceased, but several programs still dont work.
Desktop seems dead, no shortcuts work.

I was running NAV suite with AdAware and doing all my updates. I don't understand what went wong or where. Things seem to take turns not working. I'm pretty sure that if I got to the guts of it I would find a software culprit, but I am totally fed up with the time it takes to maintain a machine that isn't even used for much more than browsing. I do have another functioning CPU. If I knew Ubuntu was going to work for me on this one, at this point I'd probably just wipe this whole damn thing and go fresh. Can you network a Linux OS to XP to share a connection? And if I do decide to install it side by side, can I then wipe the Windows side completely if I like?

I am very likeminded to the threads I've been reading around here, and am almost certain I'm going to love everything about being free. Even the trial and error stuff!

Okay, I'm off to buy cds! Woohoo!

---

### Post by ap3rtis on 2007-07-03
wait, you don't have SP2 installed on XP?! Might expain some of your issues. It's a service pack which fixes alot of issues with xp. a windows xp sp2 install should not be giving you many problems.

---

### Post by ITdrummer on 2007-07-03
Wow, you dont have service pack 2 and your JUST NOW having issues?! Lucky you!

That service pack is essential and has been around for almost 3 years.

Good luck with Ubuntu/Linux
(Im going through the same process you are right now!)

---

### Post by ResumeMan on 2007-07-03
You may want to play with [Wubi]("http://wubi-installer.org/"). You run it through Windows, and it installs Ubuntu in a "virtual partition." From Windows it looks like just a file folder, but Linux sees it as an actual partition. It's a great way to step from just playing with a Live CD to having a real Ubuntu installation on your machine, without going through the hassle of partitioning.

If you decide you want to stick with the dual-boot, you can either retroactively create a real partition (I haven't done this), or uninstall Ubuntu (by running an uninstaller in Windows).

I did this a couple weeks ago, and it worked well. Over the course of the next week-10 days, I played around with the OS and screwed a couple things up. Don't know if they were related to Wubi or not. But I had gotten the feel of things, and decided to do a more fundamental install. So I uninstalled Wubi and went through the partitioning process, and have been running that way since.

Even though I didn't keep the Wubi install, I'm glad I started that way to make the initial plunge easier.

---

### Post by RD4UBN2 on 2007-07-04
Well I had all the updates automatically for 3 years and no problems. Then the random shutdown crud etc. Before the recover yesterday I was prompted to try Vista. After the recover i was prompted to try SP2 *or* Vista. I saw either as a temporary and expensive fix to only eventually arrive at the same frustrating situation. Went through it with 98. Going through it with XP. Not willing to go through it with Vista. Twice burned and all that...

*Aaaaaaaanyway*, I am very pleased and proud to announce that I am using my boot up cd now!

***[COLOR="DarkOrange"]**does the crazy happy dance**[/COLOR]***

I haven't been playing with it long but I am so excited that it worked! Will it be the same if I install it or should I expect to then encounter hurdles? So far I am just thrilled to have my sound back! Going to go play now and see what happens.

!!!YaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaYaY!!!

---

### Post by buuntuu! on 2007-07-04
you wouldn't have to pay for SP2, so if you want to keep dual booting windows and ubuntu i'd go with that!
installing shouldn't create problems with your specs, but you can never be totally sure of course.
anyways i would give it a go!  there is nothing to loose (as your xp seems really buggy now a fresh install would probably be necessary anyhow) just be sure to back up important data!
see[ this link ]("http://www.winsupersite.com/showcase/windowsxp_sp2_slipstream.asp")for how to create a xp-cd with sp2 already installed if you don't want to bin xp just now (i found it handy being able to dual boot during my first weeks with ubuntu - gives you that extra feel of security having a second OS to boot into if you mess things up - wasn't really necessary though)
and read up on installing before you get going, if you run into problems it will be less stressful if you have done your homework;) the link to psychocats posted by hyper_c is kind of the basing point for beginners, if you read it thoroughly it will help you install and you'll  learn your first things about how linux works and how to find your way around.
have fun!

---

### Post by ndefontenay on 2007-07-04
Hi!

Good to see someone doing the plundge.

I've switched to Linux totally cold turkey from one day to another.
I decided I would find alternative to what I'm currently using (such as photoshop) because in the end I'm being just too lazy to try something new.

So I installed Linux Kubuntu Feisty Fawn (because I like KDE).

What you get when booting from the live CD is what you'll get when installing Linux completely on your PC.
The best configuration in my opinion is to have a dual boot on 2 different hard disk first.
I didn't throw windows away directly because I need to pay my bills through internet banking and Thai websites uses solely IE.

After I found out I could run IE on Linux (IE4Linux), I threw windows away completely.

Things like skype not having a webcam on linux version sometimes makes me a bit sad but I'm so happy to have a working, stable system that I don't complain too much about the few things that upset me.

If you are happy with what you see live (Try to use internet for example), install linux.

You don't need to download softwares on the internet. Linux do it for you.

Go to add/remove programs in your GUI and simply select the apps you want to try. Then apply. Linux downloads, install and stick an icon somewhere.

---

### Post by RD4UBN2 on 2007-07-04
I am reading through [http://www.psychocats.net/ubuntu/iso]("http://www.psychocats.net/ubuntu/iso") in the next couple of days, and I plan to do the dual boot thing and keep Windows until I am truly comfortable in the Linux world. One quick question:

My fans seem to kick on using any application, is this still going to happen after install, or will having Ubuntu installed be less stressful on my system than running the live cd?

May I say again and again and again that you guys ROCK.

---

### Post by sailor2001 on 2007-07-04
running on a cd is always slow.........and hard on resources

---

### Post by happy-and-lost on 2007-07-04
Good to see a new user who's willing to try alternatives :)

If all you really use in Yahoo and Paint Shop, you're going to *love* the next release (due Oct). The Yahoo equivalent (Pidgin, GAIM in the current Ubuntu) and PSP equivalent (GIMP) have had major facelifts and usability overhauls, they're simply *beautiful*. Welcome to the rapidly-improving world of Ubuntu :)

---

### Post by punkybouy on 2007-07-04
I don't know how comfortable you are changing hardware but If you know how to change a hard drive and if yours is a year or older you might want to buy a new hard drive and install Ubuntu to that.  That way you don't have to worry about messing up a Windows installation by accident, you have a whole hard drive to play with and should you decide you don't want Linux you need only pop your old drive back into your PC and off you go.  Even retailers have weekly hard drive specials for $50 or so.
I went that route with a Dell laptop and bought a 7200 rpm drive for $80 dollars that was bigger and faster than the 4200 rpm drive I had been using.  Ten months later the Windows drive still sits in my laptop bag unused and I feel like I have a new laptop.

---

### Post by anurgo on 2007-07-04
There are plenty of places that can get you started, just google it up and you're ready to go. I'm also a noob but have been able to become familiar with some ubuntu, and in general linux, features. For starters, the terminal windowe is like the MSDOS command prompt on windows. After youre installation, any other programs can be installed accesing the terminal. Oh and if you happen to encounter any trouble like a BLANK screen when your try to install, just try the safe graphics option and if it still doesn't work try typing F6 and then on the boot command line: live vga=771 noapic nolapic irqpoll noirqdebug

(that's what worked for me anyways) i'm sure you will also start to love ubuntu

---

### Post by R_U_Q_R_U on 2007-07-04
> **punkybouy said:**
> I don't know how comfortable you are changing hardware but If you know how to change a hard drive and if yours is a year or older you might want to buy a new hard drive and install Ubuntu to that.  That way you don't have to worry about messing up a Windows installation by accident, you have a whole hard drive to play with and should you decide you don't want Linux you need only pop your old drive back into your PC and off you go.  Even retailers have weekly hard drive specials for $50 or so.
I went that route with a Dell laptop and bought a 7200 rpm drive for $80 dollars that was bigger and faster than the 4200 rpm drive I had been using.  Ten months later the Windows drive still sits in my laptop bag unused and I feel like I have a new laptop.

Good points. I just ordered a brand new Dell 1521 laptop that comes with Vista on a 5400 RPM 8o GB drive. I also bought, from NewEgg, a 7200 RPM 100GB drive and 2 GB of ram. I plan to pull the Vista drive and install the new drive and install Fiesty on it. I had to buy the machine with Vista because of the Employee Purchase Plan. Ubuntu is not offered pre-installed with the employee discount deals. You can also get, for $30, an external enclosure for your old drive and use it for backup. I bought one of those too.:D

---

### Post by RD4UBN2 on 2007-07-05
I am _really_ looking forward to the October release now! It will be 07.10 right? ;)

Buying the new hard drive is an excellent idea. I cannot afford it at present, but I think I will run a dual boot until October and then treat myself to a system that just runs the good stuff! I should be pretty comfortable with Linux by then I would hope. Is there any other hardware that can be recommended that typically cooperates better with Ubuntu?

---

### Post by hyper_ch on 2007-07-05
Read first the vista end user licence agreement... it is possible, that you can get reimbursed for Vista...

---

### Post by moredhel on 2007-07-05
By the way, apophysis works in wine, I use it all the time ;)

see [http://en.wikipedia.org/wiki/WINE](http://en.wikipedia.org/wiki/WINE) for an explanation of what it is ;)

---

### Post by Rhumbline on 2007-07-05
Yes you can share a connection, but you'll need a router of some sort. Your connection provider will have them or you can buy one. Wireless or hard wired? Up to you.

My suggestion is to use your other machine just for Ubuntu. Then you can learn as you go with no pressure.

In my house my kids have a mac laptop, 2 windows desktops and my wife has a windows laptop and I have my Ubuntu desktop all using the same wireless router.

---

### Post by lisati on 2007-07-05
> **Rhumbline said:**
> Yes you can share a connection, but you'll need a router of some sort. Your connection provider will have them or you can buy one. Wireless or hard wired? Up to you.

My suggestion is to use your other machine just for Ubuntu. Then you can learn as you go with no pressure.

In my house my kids have a mac laptop, 2 windows desktops and my wife has a windows laptop and I have my Ubuntu desktop all using the same wireless router.

Ditto - we have a dual-boot laptop (Ubuntu 7.04/XP Home) hooked up through wireless, a dual-boot desktop (ditto the config) and occasionally the neighbour's laptop (NT? via wireless) all sharing a connection. The wireless portion of our setup is protected by WEP+access control by MAC ID (so only people who have the right passphrase AND who I know to tell the router to let through can connect), and our router has its own built-in firewall.

---

### Post by coolen on 2007-07-05
Another new recruit...I mean, user :P
Don't worry about not knowing things. You get used to it real quick. When I was looking to try out Linux (Debian), I read up on it and heard that Linux has a steep learning curve...and it's true. The thing is, it's rather easy to follow, since most things in Linux make sense (if you're at all technically minded, which, by the sound of it, you are).
My first Linux install landed me at the command line with only a vague idea of where to proceed. I soon got Enlightenment installed, and found my screen size set to four times my resolution, requiring me to scroll to the bottom of the screen.
Needless to say, I was having a blast. You won't run into those issues with Ubuntu, but whenever you do, you learn, and more importantly, you learn the truth. It's not just click this, select that. You get to issue real commands at the terminal, decrypt error output, edit configuration files by hand...
I miss Debian, in a way. Everything in Ubuntu just works...

---

### Post by RD4UBN2 on 2007-07-05
I never bought Vista - thank the gods! I was bent on not doing that from the moment they announced its existence. 

Did a SP2 update and my XP side is still a little buggy, but not crashing.

Installed Ubuntu! It was pretty easy. Connection wasn't a problem, I had the routers all set up from the XP network and just never touched them. The other comp is still connected. I don't know if that will change should I uninstall XP, but I will burn that bridge when I come to it. Ha!

Since the install I am glad to report my fans don't seem overworked, I have my mail set up, and well that's all I've had time for this afternoon. Have to work. :( I am so looking forward to reading about wine, it seems to be something that will interest the artsy fartsy in me. I will have a look at that when I get home from work, thanks so much for all the great help I'm getting here!

So I haven't used the terminal yet. I've looked at it, kind of reminds me of being a kid programming my old Commodore 64 to do all kinds of fun things. I like that. I am unsure of what to do here, but I know I need to use it to get java (I like to pogo.com). When I go to java download I get the choice of 4 dls for Linux and I don't know which to choose or how to install it. Anyone know which path I should take here?
			
	Linux RPM (self-extracting file) filesize: 17.67 MB 
	Linux (self-extracting file) filesize: 18.15 MB
	Linux x64 * filesize: 17.15 MB 	Instructions
	Linux x64 RPM * filesize: 16.75 MB 	Instructions
        * Please use the 32-bit version for Java applet and Java Web Start support.

Thanks!
Jeannie

---

### Post by coolen on 2007-07-06
With Java, do we have anything in the repos? RPM packages are for Red-Hat like systems. Debian based distros (such as the Ubuntu box you see before you) use .deb files.
If you get stuck with an RPM package, you can use alien:
```
sudo apt-get install alien
```
I haven't used alien in a fair while...but I imagine you just pass it the name of the RPM package. It converts, and you then install it with this command:
```
sudo dpkg -i name_of_package.deb
```

Java seems to be in the repos, though (I assume you're going for the SDK, to develop?).
Open Synaptic (System -> Administration -> Synaptic Package Manager) and search for Java.
You also have browser plugins for all your browsin' needs, and the runtime environment.
Always go for a repo, if one's available. Easiest to keep your system in line :)

---

### Post by lisati on 2007-07-06
> **RD4UBN2 said:**
> 
So I haven't used the terminal yet. I've looked at it, kind of reminds me of being a kid programming my old Commodore 64 to do all kinds of fun things. 
Your comments reminded me that I have a couple of Commodore 128s + a printer for them sitting upstairs in the spare room that were given to me a couple of years ago. One of the disks is for CP/M - I read somewhere that some of PC/MS-DOS was inspired by the way CP/M was put together.

---

### Post by hyper_ch on 2007-07-06
> **lisati said:**
> The wireless portion of our setup is protected by WEP+access control by MAC ID (so only people who have the right passphrase AND who I know to tell the router to let through can connect), and our router has its own built-in firewall.

Actually this is not really secure. The Mac Address can easily be faked so that someone else's wifi card uses your authorized mac number...

WEP password cracking is a matter of minutes... WPA is a bit tougher but nevertheless also "easily" hackable (there was a demo at the CeBit).
The problem with WEP is that it is not really encrypted and WPA uses for the handshake also a non-secured lined...

WPA2 should be secure (I think) opr using a Radius Server...

---

### Post by quinnten83 on 2007-07-06
> **hyper_ch said:**
> Actually this is not really secure. The Mac Address can easily be faked so that someone else's wifi card uses your authorized mac number...

WEP password cracking is a matter of minutes... WPA is a bit tougher but nevertheless also "easily" hackable (there was a demo at the CeBit).
The problem with WEP is that it is not really encrypted and WPA uses for the handshake also a non-secured lined...

WPA2 should be secure (I think) opr using a Radius Server...

God, I hope ubuntu supports that from the get-go.
I see so many people here having trouble with their wireless connections.

---

### Post by coolen on 2007-07-06
> **quinnten83 said:**
> God, I hope ubuntu supports that from the get-go.
I see so many people here having trouble with their wireless connections.

Feisty was a big step up in terms of wireless. Previously, the only wireless connections that were really supported were either unsecured, or WEP-enabled. You could go and edit the configuration file manually, pray that it worked, restart networking, restart, and then go do it all over again when you got home.
Six months later, the only major issues remaining are drivers. This isn't really up to the Ubuntu team, however. This is an issue far larger than the developers.
WPA is supported, though, and I'm pretty sure WPA2 is, too. Major leaps.

---

### Post by RD4UBN2 on 2007-07-06
> **lisati said:**
> Your comments reminded me that I have a couple of Commodore 128s + a printer for them sitting upstairs in the spare room that were given to me a couple of years ago. One of the disks is for CP/M - I read somewhere that some of PC/MS-DOS was inspired by the way CP/M was put together.

You should go play with it!!! Fun! \\:D/

---

### Post by RD4UBN2 on 2007-07-06
Java is all good now, thanks! It was a sudo apt-get thing. I am so not used to these commands, but I think it will get easier for me as I fiddle with it. Haven't tested the printer yet.

On connections, we are not wireless but should there be specific security settings for me anyway? Should I set something somewhere, or is there a scanner or something? I am so used to the Windows world of alerts! warnings! oh noes!!! Is there really no need to be all vigilant and  uptight here?

---

### Post by lbelloq on 2007-07-06
Somewhere, out in the blue, Debian is waiting for you to come back.
Please, do not fall into temptation. Stick with Ubuntu.

---

### Post by twiceasworn on 2007-07-06
> **RD4UBN2 said:**
> Java is all good now, thanks! It was a sudo apt-get thing. I am so not used to these commands, but I think it will get easier for me as I fiddle with it. Haven't tested the printer yet.

On connections, we are not wireless but should there be specific security settings for me anyway? Should I set something somewhere, or is there a scanner or something? I am so used to the Windows world of alerts! warnings! oh noes!!! Is there really no need to be all vigilant and  uptight here?

As for the Linux commands, they will be second nature soon enough.  I started using linux religiously about 5 months ago when i got a job in a *nix shop.  I had the basic commands down in a week or so.  It isn't difficult, just different :)

---

