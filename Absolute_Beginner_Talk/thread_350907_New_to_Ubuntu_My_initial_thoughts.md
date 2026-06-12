---
title: "New to Ubuntu: My initial thoughts"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by Armor on 2007-02-01
I'm currently dual booting XP and Ubuntu Edgy. So far, here are my thoughts:

1) Working with Ubuntu is not as easy as it is with XP. In XP, I can save, create, delete, move, or change any file I want without having to open up a command prompt and run a string of commands to do it or open up a different file browser. I've seen people say that "If you want to break Ubuntu it doesn't try to stop you" - how is this possible? Please tell me how long it took most of you to figure out that if you wanted to create and save a file in a restricted directory before you figured out you had to run something like "gksudo gedit filename.extension" from a terminal.

2) Installing things is not as easy. Sure, if it's in the repositories it's not too bad. Forget trying to do anything else that isn't in a repository. I recently tried installing Beryl and making that work. Uh uh. Wasn't happening. I understand Beryl is very much beta, but how much of a pain in the *** is it to screw with all that other stuff like trying to make a new xgl session? I have found that by and large, installing things in Ubuntu required looking at directions or installation notes, using the terminal all over the place to get things JUST SO before I tried to do something, and looking at the Support Forums of whatever it was I was trying to install.

3) Little things here and there don't work. STILL can't get embedded Quicktime or WMP videos to play in Firefox. Some pages don't load correctly in Firefox if I'm running Ubuntu, although they will just fine if I'm running XP. Not sure what the problem is. GAIM is ok, but it's not great. Limited functionability. The side buttons on my mouse don't work and I have no idea if they ever will in Ubuntu. Small things here and there that you notice

4) If you have an ATi video card and want hardware acceleration, be prepared with a bottle of Advil and a good hour of free time trying to figure out how to make the "fglfx" drivers work.

Does anyone share my frustrations? Does anyone have any advice to help me get over this hump? Is it because I'm so new I'm doing EVERYTHING the really, really hard way? I WANT to like Ubuntu, I WANT to use it as my primary OS, but it's just discouraging.


As far as installation being a pain in the ***, here's exactly what I'm talking about (quote from another thread):
> Lime wire is available for Ubuntu, i installed it and it works perfectly fine. You just need to have anything alteast near to the latest version of Java eg: Java 5 update 10 or 9. I picked up the following instructions from ubuntu guide website, its what i followed:

Enter the following in Terminal, when you are prompted to install Dash, select &#8220;NO.&#8221;

Code:

sudo dpkg-reconfigure dash

Now download LimeWire(Linux RPM) from site [http://www.limewire.com/english/cont...oadfree2.shtml](http://www.limewire.com/english/cont...oadfree2.shtml)

To convert the package to a Ubuntu *.deb file you must have alien installed:

Code:

sudo apt-get install alien

Then type the following into Terminal to convert the package from the *.rpm to a *.deb file:

Code:

sudo alien -d LimeWireLinux.rpm

Once it has been converted, double-click the new *.deb file to install LimeWire and that&#8217;s it, you&#8217;re done.

That should be all.

In Windows, the instructions to install something like Limewire would be as follows:
1) Download file
2) Double click setup file.

---

### Post by gh0st on 2007-02-01
> **Armor said:**
> I'm currently dual booting XP and Ubuntu Edgy. So far, here are my thoughts:

1) Working with Ubuntu is not as easy as it is with XP. In XP, I can save, create, delete, move, or change any file I want without having to open up a command prompt and run a string of commands to do it or open up a different file browser. I've seen people say that "If you want to break Ubuntu it doesn't try to stop you" - how is this possible? Please tell me how long it took most of you to figure out that if you wanted to create and save a file in a restricted directory before you figured out you had to run something like "gksudo gedit filename.extension" from a terminal.

2) Installing things is not as easy. Sure, if it's in the repositories it's not too bad. Forget trying to do anything else that isn't in a repository. I recently tried installing Beryl and making that work. Uh uh. Wasn't happening. I understand Beryl is very much beta, but how much of a pain in the *** is it to screw with all that other stuff like trying to make a new xgl session? I have found that by and large, installing things in Ubuntu required looking at directions or installation notes, using the terminal all over the place to get things JUST SO before I tried to do something, and looking at the Support Forums of whatever it was I was trying to install.

3) Little things here and there don't work. STILL can't get embedded Quicktime or WMP videos to play in Firefox. Some pages don't load correctly in Firefox if I'm running Ubuntu, although they will just fine if I'm running XP. Not sure what the problem is. GAIM is ok, but it's not great. Limited functionability. The side buttons on my mouse don't work and I have no idea if they ever will in Ubuntu. Small things here and there that you notice

4) If you have an ATi video card and want hardware acceleration, be prepared with a bottle of Advil and a good hour of free time trying to figure out how to make the "fglfx" drivers work.

Does anyone share my frustrations? Does anyone have any advice to help me get over this hump? Is it because I'm so new I'm doing EVERYTHING the really, really hard way? I WANT to like Ubuntu, I WANT to use it as my primary OS, but it's just discouraging.

Ubuntu isn't perfect and I don't think anyone here would claim that it was but windows certainly isn't perfect either.

1. The reason you can't just create files and delete files all over the system folders is for safety really. Ubuntu doesn't log you in as administrator like XP and this has been the source of many a virus or malware problem for Windows. In fact Vista has copied the Linux user model and doesn't log you in as administrator either you have to enter a password to do admin stuff like Linux.

2. Installing things with a ".deb" file shouldn't be any harder than using an ".exe" in windows. Compiling from source isn't easy though and I would accept that point. If you add the restricted repositories to Synaptic though there shouldn't be much you could need from outside the repos and installing is easy.

3. The reason WMP and Quicktime don't work for you is because the codecs are propriatory and Ubuntu doesn't install them by default. You need to get them from the restricted repositories. Things like mozilla-totem-zine and Mplayerplug-in can do all the things you can do on XP. I watch quicktime trailers and wmp vids all the time in Firefox. You need to install the Flash Player 9 plugin to watch videos in YouTube and sites like that.

4. I have an Nvidia graphics card so I can't comment on ATI but I know a lot of people complain about setting up ATI cards on Ubuntu. You may have a point there I dunno, I'll let someone more qualified comment.

If you want an easy way to install all the extra restricted software you need you should run Easy Ubuntu or Automatix they'll have you watching videos in no time. I have been told off in the past for recommending Automatix because it's not an official part of Ubuntu and could install some broken packages or whatever but I've used it for a quite a while and it hasn't caused any problems for me. It basically just adds the repos you need installs all the software you select at once. It's not for everyone but I like it, only you can decide. Try this link [www.getautomatix.com](www.getautomatix.com)

The fact that Ubuntu doesn't do everything you might want out of the box can be a problem for newcomers and you make some valid points. Don't forget though Windows doesn't come with all the software you need installed either. They both need some setting up. Last time I installed XP I had to spend ages installing and Office suite, picture editors, firefox, media players and all kinds of other stuff.

---

### Post by Tomosaur on 2007-02-01
Well yes, you're used to Windows, so you shouldn't expect Ubuntu to just 'work'. If it's brand new to you, then you need to get used to how things work around here. As for installing stuff outside the repositories - it's not too hard. Yes, you need to compile stuff quite a bit, and download extra dependencies to get it working, but all of this runs into the open-source philosophy and such. When you install a program in Windows - the reason it works first time is that each program has its own dependencies built in to the setup file. Over time, you end up with a lot of files and libraries (.dlls) on your computer which do much the same thing. On Linux, you have one library. You may prefer 'the Windows way', and that's your choice, but you need to understand the reasoning behind it.

As for saving files in restricted directories - it's still possible. Yes, Nautilus currently lacks a 'sudo up' feature, which can be pretty irritating, and kind of forces you to use the command line (which can be daunting if you don't like it, I guess), but then again you shouldn't be creating stuff outside of your home directory anyway. Windows sets everyone as admin by default, and the directory structure is such that it's not immediately obvious which files are system and whatnot. Linux' directory structure is pretty obvious (despite initially cryptic directory names), and its permissions scheme means you won't delete something vital by accident.

Firefox plugins - yes, it's very annoying. You may be better of scrapping the 'built-in' firefox and just downloading and compiling from source, since it makes following HOWTO guides a bit easier. You won't be able to use the plugins in the repository though. I don't know why these issues with Firefox haven't been resolved yet, it's a total pain in the backside getting all the plugins to work properly.

ATI card are just not built for Linux, and ATIs support for Linux users is terrible. You may be better off switching to nVidia to be perfectly honest.

---

### Post by rejser on 2007-02-01
As many have said before, linux isn't for everybody and mostley it wasn't created to be easy, it was created to have control over the computer. Even if it is getting more and more comfortable.
But the linux desktops where not intended to be an equal alternative to xp, it's for those who feel that they need a little bit more control over their computer.
I installed win xp the other day and I have to say I found it really hard to use. To get keyboard to work go there download.... and so on. Had to spend 3hours getting all the drivers just to get started. I linux I just change a couple of lines in xorg.conf and it's perfect.

---

### Post by Armor on 2007-02-01
> 3. The reason WMP and Quicktime don't work for you is because the codecs a propriatory and Ubuntu doesn't install them by default. You need to get them from the restricted repositories. Things like mozilla-totem-zine and Mplayerplug-in can do all the things you can do on XP. I watch quicktime trailers and wmp vids all the time in Firefox. You need to install the Flash Player 9 plugin to watch videos in YouTube and sites like that.
THANK.
YOU.
God!

In what ways does Ubuntu offer more control over my computer? It just seems that I can do less and less with Ubuntu because ATi doesn't support it, Firefox is a pain in the butt to make work, et al.

---

### Post by rejser on 2007-02-01
Well aside from Ati (which is ati's problem since they won't release proper codecs). It's easier to optimise, no unecesary things running in the background, more options to shape a workspace as you would like.
Easier to maintain, don't get junk-files laying around after removing software as windows often leaves behind. 
To start optimize you should always start by compiling your own kernel for your computer. Apt-get get alot of glory, but compiling the software yourself get much better performance when you start to realise what you are doing. 
Gentoo's merge system is one of the best easy systems to getting a well run computer that only does what you tell it to and nothing more.
Take a look at all services running in windows, do you know what they do? Do you need them, what is taking up 5-10% of your bandwidth? There is to much going on that I don't know about, and then I don't propably need it.
But I have been using linux since 96 or 97 now so.....

---

### Post by hyper_ch on 2007-02-01
In the beginning I just thought like you... because so many things were different I tended to think that linux is more complicated... it's not really more complicated if you understand the reasoning behind it and then you start asking yourself "why doesn't windows do it the same way..."

Anyway, it has been pointed out, that normally you shouldn't be required to create files outside the home directory... that's true... but most configs to demons are located in /etc and it's quite nice to be able to edit those directly. What you can do is create a new menu entry (for example in the system section) that executes "gksudo nautilius" --> then you will be prompted for the sudo pwd and then you can edit the files as sudo... however I would really not use that by default... hence my suggestion to put it into system section :)

And rejser has a point regarding the drivers... it's a pain on windows... I have created now myself a install shell script that will do the following:
(1) copy "my" sources.list to /etc/apt/sources.list
(2) Add the necessary keys to apt
(3) Download and install skype and Java
(4) Download and install everything else

I just keep adding programs that I installed through the repos to thise little script.. I have used it meanwhile 2 times and I can get my computer up and running in less than 1 hour with 95% of all I had on before... this is only possible because I have /home on a seperate partition

That little script will auto-download the newest bits and pieces upon each re-install... I even modified it for use with Feisty... same script... within one hour feisty was running fine...

I have to admit that windows is "more convenient" for some things... but for other things I keep asking myself what the winodws programers were thinking... Windows has its advantages in a few things and Linux has its advantages in other things... in the end it is up to the individual user to decide which one he likes more :)
--> Have a guess what I like more :)

---

### Post by jkeyes0 on 2007-02-01
The biggest difference I've seen between Windows and Ubuntu is that I can actually get support when I don't know how to do something in Ubuntu...

I can't tell you how many times I've found a problem in Windows and spent the better part of a working day looking for an answer, only to find nothing, whereas when I have problems with things in Ubuntu, I can come here, to a dedicated forum, and receive help (or at least guidance) in a matter of minutes. Free, useful, and it doesn't involve me calling India to speak to Ronald McDonald (yes, I've had to do that before, and that was the actual tech's name... it was for my internet service though).

---

### Post by Patrick-Ruff on 2007-02-01
you need to keep an entirely open mind.  both OS's have benefits, ubuntu has particular benefits to those who like to know precisely what is going on in their system. over all you learn a lot more about how your computer works (with the exception of being a programmer, we truly know how a computer works.)

you're going to run into many users on here who will preach the ubuntu philosophy here, but you're not hearing it from me.  yes it can be a pain, and yes some things wont work. this is all dependant upon your hardware. 

if you have an nVidia you're set, if you have an ATI welcome to a world of frustration and pain.  though, that's not much different from the world we live in now, is it?

---

### Post by Armor on 2007-02-01
Well the thing is I don't WANT to repalce my ATi card. It's a good card! x1800XT Radeon, it's a powerhouse. Good points all around...I guess for the next X length of time I'll be making regular "How do I..." posts. Thanks much for the support

---

### Post by Henry Rayker on 2007-02-01
1) took me about 5 minutes...I remember googling something to the extent of linux file permissions and BAM! done. This is a protection. This allows certain files and folders (which are incredibly important, due to the fact that the OS uses a LOT of files for settings etc. (as opposed to binaries or dlls that include their data)

2) Installing is different...I wouldn't say harder. For the most part, it is as easy as ```
./configure
make
sudo make install
```

The only things that could be easier is for Ubuntu to install build essential and the kernel headers by default...I STILL don't understand why they don't do that.

As for your installation example, I don't see what the problem is...not sure what the part about Dash is about, but that aside, this is essentially like downloading a program whose .exe is zipped (so you convert from .rpm to .deb) ...alien must be installed before you can do this...then you double click it. Different != harder.

3) Proprietary codecs...install them yourself. If you have a problem with that, go choose an OS with a different philosophy concerning that. You wouldn't join an Islamic mosque and then complain about the fact that they don't have Jesus, would you? As for the buttons on your mouse, if there aren't drivers out there for it, complain to the manufacturer about the fact that they don't have drivers for Linux based OSes.

4) Complain to ATi. This is their shortcoming, not ours. You wouldn't complain to Microsoft about Photoshop being difficult to learn, would you? The Linux community would be MORE THAN happy to fix/modify/branch the fglrx driver, if we could look into the source.....but they won't let us.

Have you ever tried to install anything from source in Windows? THAT sucks. Oftentimes, there is NO documentation (or when it exists, it has little information concerning dependencies etc.) You have to be willing to look at similar situations, though...
a) using alien to convert from .rpm to .deb - similar to having to unzip the .exe first
b) installing from .deb - similar to just using the .exe
c) installing from source - similar to installing from source (only WAY easier in Ubuntu)
d) installing from repos - almost as easy as contracting viruses/spyware in Windows

One other major thing people don't seem to understand...imagine trying to get your hardware to work in Windows if the manufacturer didn't provide drivers on disk or on the internet...You'd have to rely on a community (who seems to delight in infecting one another's computers with viruses and whatever else) to get your stuff working....good luck!

---

### Post by rejser on 2007-02-01
I thought of something, most usuall thing to do to solve a problem in windows is to install yet another program to have running that takes this care for you. Most I know running windows that are a little more advanced than a surfing/mailing user has about 20-30 icons for programs doing stuff in the taskbar.

---

### Post by TrendyDark on 2007-02-01
I'll just say, the only directory you should be editing files in is your home folder, the rest are needed system files and such, which means you shouldn't be cluttering them up with "MyMomsBirthdayParty.jpg" files. Also, when did we start having to move files using the terminal? Last I check, I can drag and drop just fine.

As for software installation, how hard is using Synaptic to find software? Or Gdebi to install a debian file? As for Beryl, if you installed your video driver (simple with ati cards, even simpler with nvidia) then you should just add the beryl repos and do "apt-get install beryl-manager emarald-themes".

The mouse you have has support, trust me, I have a 6 button mouse and use it in Firefox on Ubuntu all the time. Do a little searching on the forum and you'll find guides for your mouse to have full support (and don't give me "but it works easier under windows" because I know, but mouse companies don't make pretty installation software and drivers for linux).

:) All around, your complaints are really just that you are trying to do things and don't seem to want to take time and get the grasp of Linux.

---

### Post by Armor on 2007-02-01
No no, I've been working with Ubuntu for a couple weeks now, it's NOT that I don't want to take the time. Trust me, I've spent hours. Just gets frustrating

---

### Post by Patrick-Ruff on 2007-02-01
I know how you feel, but you must remain patient.  otherwise ubuntu and linux is not for you (I know you probably hate it when people say this.)  you just have to accept the fact that things are less efficient GUI wise, well, I think we must face the facts here when I say that the GUI sucks.  Mac OS X has done so many things right in that sense. 

it depends on what you really want in an OS, you will never get everything in one, but you will get most of what you want out of one.  find that OS and you will be content, and if you're not, I suggest you look into buddhism ;).

---

### Post by hyper_ch on 2007-02-01
Btw, if I remember correctly ATI on windows isn't all to great either :)

---

### Post by Frazer on 2007-02-01
[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

when I first started this helped me a lot

and automatix hasnt give me any problems, but personaly I like instaling everything myself.

of automatix I have the browser swiftfox and the pluggins all work fine for me.

---

### Post by Patrick-Ruff on 2007-02-01
> **sjau said:**
> Btw, if I remember correctly ATI on windows isn't all to great either :)

it's a whole lot better then on linux.

---

### Post by TrendyDark on 2007-02-01
> **Armor said:**
> No no, I've been working with Ubuntu for a couple weeks now, it's NOT that I don't want to take the time. Trust me, I've spent hours. Just gets frustrating

Trust me, it's hard at first. You just need to understand LINUX IS NOT WINDOWS. Things may seem hard, which some are, I still HATE to have to compile something from source, but vendors don't support Linux like the redmond giant and we just have to live with that and continue to use ./configure.

I've been using linux for about a year and a half now and I still break things, specifically x.org (a lot). It takes patience, and a lot of trust that the community will help.:D

---

### Post by lyceum on 2007-02-01
I really don't use the terminal much myself, just cut and paist when I need to, following how-to's etc... 

anyhow, to help you along, have you been to this site?

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

And I would 2nd getting Automatix2. It is great!

---

### Post by Frazer on 2007-02-01
achually for me lol ATI was a lot easyer on Linux,  In my laptop I cant use the official ATI drivers without a lot of messing about.  I have to use the hp ones.  They cause LOTS of problems playing games.  

On Ubuntu it took less than 5 mins.

---

### Post by Torajima on 2007-02-01
Windows users always seem to forget how much initial setup it takes to get XP running:

You can't view PDFs until you download Acrobat Reader.
You can't view DIVX or Quicktime until you install the proper codecs.
You can't view some webpages until you update Flash and/or Shockwave.
You can't even view email attachments, until you change your security settings.

And if it's a brand new machine with new software, you've got to register/activate most every piece of software before it will even work.

So of course you can expect a bit of initial setup when switching to Linux.

---

### Post by gh0st on 2007-02-01
> **Armor said:**
> THANK.
YOU.
God!

In what ways does Ubuntu offer more control over my computer? It just seems that I can do less and less with Ubuntu because ATi doesn't support it, Firefox is a pain in the butt to make work, et al.

I did tell you how to install the codecs and things you need to get your system setup in that post. 

FROM PREVIOUS POST: *If you want an easy way to install all the extra restricted software you need you should run Easy Ubuntu or Automatix they'll have you watching videos in no time. I have been told off in the past for recommending Automatix because it's not an official part of Ubuntu and could install some broken packages or whatever but I've used it for a quite a while and it hasn't caused any problems for me. It basically just adds the repos you need installs all the software you select at once. It's not for everyone but I like it, only you can decide. Try this link [www.getautomatix.com](www.getautomatix.com)*
---------

Have you tried automatix?

1. It will install some of the core windows fonts, that will stop some of your pages looking weird in Firefox.

2. It will install all the codecs and media players / firefox plugin's you could need. That will have you watching WMV and quicktime.

3. It will also install some scripts for Nautilus that will give you the option to use gedit as root when you right-click a file, it will also open a location in Nautilus as root with a right-click.

That's 3 or your problems sorted in one fell swoop. I was trying to help you, not being funny. Automatix isn't the answer to everything and a lot of people don't like it but it might help you.

NO.
PROBLEM.
;)

---

### Post by glabouni on 2007-02-01
1) you're wrong about xp. if you try to access say windows directory from explorer using a non administrator account, you'll have nothing but a message saying this not allowed. If you were logged in ubuntu with root account (kinda equivalent to administrator account under xp) you would have no problem at all editing any files. I'm not gonna go length on this matter so I'll just say that being able to mess with each and every files in your system is a design flaw.
it didn't spent any time searching this, as I've read guides, tutorials and documentation *before* I installed ubuntu, I knew about sudo and gksudo and kdesu. I had previous knowledge of UNIX system though and already knew of su. 
spending time learning about something you don't know is part of the process.

2) installing beryl the first time was really easy, I just added the beryl repository to my repositories and got it installed with a couple apt-get command (you can do this with synaptic if you want a GUI) then added beryl-manager to start with my session and I was done. second time was on a different computer with ATI radeon 9800pro card, (did I mention first time was with a nvidia card?) and that was not as easy as the first time, but all I had to do was following this guide: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu). 
having experienced  both ATI and nvidia, I think the blame should go to ATI. 

Seems to me you want to install some exotic stuff too soon. You should get familiar with your new system before trying to go wild. 

3) if you wan't to fix most of these little annoyances, have a look at [ubuntu guide]("http://www.ubuntuguide.org/"). gaim limited functionality comes from proprietary networks not willing to release their software under linux and not willing open source client to use their network. I fixed this by switching to [jabber]("http://www.jabber.org/") ([wikipedia entry for jabber]("http://en.wikipedia.org/wiki/Jabber")). 

4) I agree that having ATI card to work under linux can be a hassle, but I believe complaint should go toward ATI, and there are a bunch of guides out there to try such as:
[3D Desktop (Beryl and Xgl) on Ubuntu Edgy Eft with ATI card.]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
a good thing is by the time you succeed (or fail and get your ATI back to the store and ask for a refund) you have learned some about your new system and become better at understanding it.

> **Armor said:**
> Well the thing is I don't WANT to repalce my ATi card. It's a good card! x1800XT Radeon, it's a powerhouse. Good points all around...I guess for the next X length of time I'll be making regular "How do I..." posts. Thanks much for the support

this is your call, but remember that you can't have it all.
btw I fail to see the point of having 3D acceleration under linux, unless you wan't to run unstable beta software such as beryl or kiba dock. In your position I'd prefer to drop hardware acceleration under linux just to avoid the related stress and frustration.
but maybe beryl was the reason you tried ubuntu in the first place.

> **Armor said:**
> No no, I've been working with Ubuntu for a couple weeks now, it's NOT that I don't want to take the time. Trust me, I've spent hours. Just gets frustrating
I totally understand this. that's what pushed me to try other linux distros.

from my own experience, my advice to you would be to switch from gnome to kde (ubuntu to kubuntu). I suggest you first try kde, you only need to install kubuntu-desktop or kde-base packages. (xubuntu-desktop package will give you access to xfce, you might also want to give enlightment a try).

I followed this advice and it improved my linux experience, cutting on simplicity to give me lots of features I missed.
[QUOTE=Linus Torvalds]I don't use GNOME, because in striving to be simple, it has long since reached the point where it simply doesn't do what I need it to do. I personally just encourage people to switch to KDE.[/QUOTE]

this one just made laugh while expressing the way I felt about gnome (and to a certain extent about OSX).
[QUOTE=Linus Torvalds]Often your 'fixes' are actually removing capabilities that you had, because they were 'too confusing to the user'. GNOME seems to be developed by interface Nazis, where consistently the excuse for not doing something is not 'it's too complicated to do', but 'it would confuse users'.[/QUOTE]

---

### Post by sean222 on 2007-02-01
Oh man...I feel your pain...although I haven't really experienced it :)

I just dual-booted XP and Ubuntu last week and it's AMAZING...I can't believe what I've been missing...and all this for free! Unreal.

I guess I'm just blessed to have compatible hardware.

As for codecs and what not, **Automatix** should give you almost all the codecs you need.

As for software...the repository is huge, you almost never need outside software. I always thought 'oh no my iPod and WinTV tuner card are screwed'...and yet the Ubuntu repositories have software for both! GAIM is fine...you're right not great like MSN Live...

...but in the end you just gotta remember, you're making a whole operating switch...you can't expect to leave windows, and still be in windows...gotta make some sacrifices :D

---

### Post by Armor on 2007-02-01
Automatix hooked me up, Firefox plugins work great now

Thanks SO MUCH for all the support here. This is a HUGE reason I felt safe making the switch, because of the incredible support (NOT offered by Windows)

---

### Post by vishnuke on 2007-02-01
> **sean222 said:**
> As for codecs and what not, **Automatix** should give you almost all the codecs you need.

I've been having a lot of problems lately getting WMVs to work. I installed everything through Automatix and Keffeine still chokes and dies on WMVs. I haven't tried anything else yet mostly because I'm not too worried about it.

---

### Post by hyper_ch on 2007-02-01
VLC plays the WMVs just fine... at least the last ones I tried...

---

### Post by gh0st on 2007-02-01
> **sjau said:**
> VLC plays the WMVs just fine... at least the last ones I tried...

Yeah thats a good point actually I forgot to mention that. VLC is amazing it will play anything it seems. I have yet to find a file it won't play. I'm probably tempting fate saying that though :D 

You can install it from Synaptic I think. I dunno what repository it's in though.

---

### Post by tyler_roach on 2007-02-01
About your ATI card:
I couldn't get mine to work until, IN ADDITION to following the instructions on the Ubuntu wiki I added the package mentioned here:
[http://jdanger.wordpress.com/2006/09/11/woohoo-ati-accelerated-dri-on-ubuntu-edgy/](http://jdanger.wordpress.com/2006/09/11/woohoo-ati-accelerated-dri-on-ubuntu-edgy/)
(you can search for it in synaptic.)

I also second moving to kde. It's much nicer that Gnome AND XP, IMHO.

---

### Post by pegazuz on 2007-02-01
> **gh0st said:**
> 

3. The reason WMP and Quicktime don't work for you is because the codecs are propriatory and Ubuntu doesn't install them by default. You need to get them from the restricted repositories. Things like mozilla-totem-zine and Mplayerplug-in can do all the things you can do on XP. I watch quicktime trailers and wmp vids all the time in Firefox. You need to install the Flash Player 9 plugin to watch videos in YouTube and sites like that.

If you want an easy way to install all the extra restricted software you need you should run Easy Ubuntu or Automatix they'll have you watching videos in no time. I have been told off in the past for recommending Automatix because it's not an official part of Ubuntu and could install some broken packages or whatever but I've used it for a quite a while and it hasn't caused any problems for me. It basically just adds the repos you need installs all the software you select at once. It's not for everyone but I like it, only you can decide. Try this link [www.getautomatix.com](www.getautomatix.com)



It has been a struggle but I finally got Kubuntu up and running and connecting to my secure wireless network.  My goal now is to add whatever I need to watch videos like those on Yahoo news, movie trailers, listen to music etc.  I have added Automatix to my menu.  Now what add ons or plug in extension are needed to do eveything under Firefox.  Generally i think it is really slick to have these package installers that list many programs. 

 Where though can we find info or reviews about the various programs offered.  Us beginners don't know what we need to get everything working once we figure out how to a things.The next step will be searching for things to replace the programs we are used to using in Windows.

---

### Post by Armor on 2007-02-01
I really can't handle another change right now, I'm JUST starting to barely understand sort of how GNOME works. Can't change to KDE until I understand how this works, that'll throw me WAY off

---

### Post by gh0st on 2007-02-01
> **pegazuz said:**
> It has been a struggle but I finally got Kubuntu up and running and connecting to my secure wireless network.  My goal now is to add whatever I need to watch videos like those on Yahoo news, movie trailers, listen to music etc.  I have added Automatix to my menu.  Now what add ons or plug in extension are needed to do eveything under Firefox.  Generally i think it is really slick to have these package installers that list many programs. 

 Where though can we find info or reviews about the various programs offered.  Us beginners don't know what we need to get everything working once we figure out how to a things.The next step will be searching for things to replace the programs we are used to using in Windows.

Yeah that can be a problem for newcomers I admit. There is so much stuff that comes with Linux it can be a bit daunting trying to find what's right for you. For playing media in Firefox I would say that Mplayerplug-in is the probably my favorite, it works well for quicktime trailers and also WMV. What I did when I first got Ubuntu and Automatix was installed pretty much everything I liked the look of from the list and then played with the different media players until I found the ones I liked.

I'm not sure where you can go to get reviews but I did see a thread on here recently talking about the best media plugin for Firefox and most people seemed to say Mplayerplug-in was the way to go. You can read about it on their Source Forge site: [http://mplayerplug-in.sourceforge.net/](http://mplayerplug-in.sourceforge.net/)

Just looking at the list of apps under Multimedia in Automatix. I installed the following:

Aud-DVD - So I can watch my DVD's on Ubuntu.

Exaile - Because it's great for managing your music and playing it.

Flash Player - For YouTube links people keep sending me

Mplayer and FF Plugin - For watching vids in Firefox

Media Players - There is lots of cool stuff in here like VLC

Multimedia Codecs - You need those to play all your media

Real Player - Not strictly needed cos other players can handle the format but I like to have the official RM player for web streaming and stuff.

I also installed a shed load of other stuff and just played around with it, these are the main apps I use daily though. You will have to see what works for you. This is just my opinion obviously.

Hope that helps in some way. Happy hunting :D

---

### Post by rocknrolf77 on 2007-02-01
Side buttons on the mouse in firefox : [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Activate_side-mouse-buttons_in_FireFox](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Activate_side-mouse-buttons_in_FireFox)

---

### Post by mtibesar on 2007-02-01
I got sick and tired of Windows and all the windows apps vendors wanting my money on a monthly or yearly or release basis (they want to get into your wallet every time!)

So, I decided to abandon Windows and the new Vista two days ago.

I installed Ubuntu Edgy with the GNOME desktop and I have had very FEW problems.

I converted my Microsoft Money accounts to QIF files and imported them without incident into GNUcash - great!

I exported my Family Tree Maker genealogy database into a GEDcom file and imported it without any incidents into GRAMPS

I set up all of my website connections in FireFTP without a hitch.

So far (realizing I'm only on my second day) I have found Ubuntu to be just as easy to work with as Windows. Yes, I am learning but if I had jumped to Vista I would have had to do the same thing.

Just my two cents worth....

After 20 years A ex-DOS and now ex-Windows user with more money in my pocket - no more monthly subscriptions for me!

---

### Post by VorDesigns on 2007-02-01
As an old DOS 2., DRDOS, MSDOS 3. user who was dragged kicking and screaming into Windows 3.1 which included OEM vendor level customer support access direct to Microsoft which gave me intimate understanding the MS Registry, which then Mr. Gates was so kind to make me a consultant because of Windows 95; I'm am always amused by the Windows is better drivel that oozes from the fingers and mouths of the uninformed.
Sure, Windows has come a long way from where it started (at the expense of the Mac product) and there are aspect of the OS that are better than other platforms and yes, the commercially available software is more ubiquitous.
There are also the problems mentioned throughout this post:
1. Default non domain install creates initial users as Administrators (wouldn't want those users pissed off by a little security would we?).  This was a tremendous mistake not made with the release of Windows 2000 and one that should never have been made.  There should only be one god per computer and you should have a really good reason to invoke him.  
2.  Due to the problem listed above, most Windows programmers worked just like most consultants like to work, as Administrators, they got lazy.  This means that about 80% of the software available for Windows platforms won't install properly unless the user is running as, god.  Most Windows programmers are ill trained in the proper development of applications in a "user" environment vs. working as "god".  
3.  There never should have been a "Home" version of Windows and WindowsME was an abortion.  But that had to make things "easier".  
4.  With each release of Window whatever and consequental patching, the OS has become more and more bloated driving the need for newer hardware just to run the OS.
Windows just is, it isn't better, it just is.
This is the second post where I've seen the computer illiterate squeal Microsoft's praises.  Keep talking, you are my bread and butter.

---

### Post by shareMenaPeace on 2007-02-01
Not sure if you if this is fixed but for beryl, what was the error message?

---

### Post by xpod on 2007-02-01
> This is the second post where I've seen the computer illiterate squeal Microsoft's praises. Keep talking, you are my bread and butter.

The first 2 of very many to come no doubt:D 
I`m a "computer illeterate" myself in the sense that i only switched a pc on last year but even little ole me is forever astounded by some of the stuff i see spouted across the web,especially the stuff by those who should in fact  know better.

It`s a funny ole game:???:

---

### Post by MSlaveubu on 2007-02-01
I put it on my PC yesterday.  so far I have gotten DVD playback, so I am happy about that.  But as for everything you said, yep.  Its different, its just something you have to get use to I think.  I am going to give it a chance for a while.  

vista is a waste of money and time IMO, this can do whatever vista can do.  Plus all the illegal things (which my not be illegal, vista just to stupid to know the difference) vista cant do, you can do on here.  XP is awesome, you can do anything.  

Ubuntu is better for image editing, I really see it as a OSX for PC.  It appears to use ram more effectivly, and some things can be easier.  Like connecting to a wireless internet.  XP could not hold a connection for me for more than 3 hours.  On ubuntu, I feel like its hardwired, only time my internet has gone out has been when my usb adapter craped out (pos), its just looses the ability to see networks, so I downloaded wifi radar, so I can at least see what the problem is, and unplug my adapter, plug it back in, and walla.

Some things I like better, some things are annoying, but I think its just a matter of what your use to, ubuntu is not as user friendly, give it a month.  

thats what I will do(at least until I buy a macbook)

---

### Post by WinterWeaver on 2007-02-06
On the first point, this works for me

```
sudo nautilus
```

^_^

---

### Post by Cynical on 2007-02-06
1. Yeah, those are called permissions. Get used to them, because they are the main reason we don't have problems with malware.

2. Sounds like you are trying to do things that you don't completely understand. Why not wait for the next Ubuntu release? I hear desktop effects (beryl) will be on by default. 

3. See screenshot below.

4. ATI's fault. Now that they are owned by the linux friendly AMD this may change, but not anytime soon.

[quote=Armor]Does anyone share my frustrations?[/quote]
Yeah at first, then they ask questions on this forum and get their problems solved.



[quote=Armor]As far as installation being a pain in the ***, here's exactly what I'm talking about (quote from another thread):


In Windows, the instructions to install something like Limewire would be as follows:
1) Download file
2) Double click setup file.[/quote]

Really? Did you try [here](http://www.frostwire.com/)? Linux is only as easy as you make it.

---

### Post by kbudurka on 2007-02-06
While Linux isn't as easy as Windows, it does give you a lot of flexibility you would not have had on XP or Vista or whatever.

Only in Linux is there so many beta softwares available to play with.
only in Linux can you search the web for some software to solve your problem and get a FREE copy of something that works most of the way.

I will say that Windows is easier for new people to work in. Micro$oft spends billions researching how to make software easier, but Ubuntu has made it pretty easy for people new to Linux to get a system setup and working pretty quickly. Sure it's not perfect and certainly not optimized, but if a learning curve doesn't scare you, and you want to be on the cutting edge of newer software coming out all the time, Ubuntu is a GREAT choice.


In my own world, I have been frustrated with the Citrix VPN client for the CAG in Ubuntu. I can not get net6$vn working, but it works in other distros. Am I upset, sure, but I haven't passed on ubuntu. Most everything I need to do, I can now do.... Even lotus notes is working!

I say GREAT JOB - and I'm willing to relearn all over again.... Heck I learned commodore, then amiga, then tandy (yes - it is different from IBM compatibles... heheh) and finally IBM. DOS, Windows, and everything from 95 on....

---

### Post by Armor on 2007-02-06
> 1. Yeah, those are called permissions. Get used to them, because they are the main reason we don't have problems with malware.

2. Sounds like you are trying to do things that you don't completely understand. Why not wait for the next Ubuntu release? I hear desktop effects (beryl) will be on by default. Or, god forbid, you could try learning more about computers in general and linux in particular. 

3. See screenshot below.

4. ATI's fault. Now that they are owned by the linux friendly AMD this may change, but not anytime soon.


Quote:
Originally Posted by Armor 
Does anyone share my frustrations? 

Yeah at first, then they ask questions on this forum and get their problems solved.




Quote:
Originally Posted by Armor 
As far as installation being a pain in the ***, here's exactly what I'm talking about (quote from another thread):


In Windows, the instructions to install something like Limewire would be as follows:
1) Download file
2) Double click setup file. 

Really? Did you try here? Linux is only as easy as you make it.


As you put it, God forbit you try to understand the frustrations of someone new to the OS. I guess I'll extend to you the same advice you ignorantly gave to me: do a little research, click on my name and see all the posts I've put up, you'll see that I AM making a serious effort to learn.

---

### Post by Cynical on 2007-02-06
What I mean to say is, you will read lots of installation instructions and ask many questions because modern desktops aren't intuitive. (for example, many new OSX users have a hard time figuring out how to uninstall applications, even though it involves just dropping an icon into a wastebasket) You may think that windows didn't require you to learn anything, but thats only because of how long you've been using it. You are learning how to do things in a completely different way, keep an open mind and you might see why we think this way is better.

---

### Post by lagomorph on 2007-02-07
I agree with you 100%.  The problem with computers is that they are everywhere.  The first thing you do when you come into office is turn the machine on and when you leave you turn it off.  However the functionality of these machines has changed precious little since the days of DOS 3.2 and Wordstar and Lotus 123.  Today substitute that with XP, Word and Excel - the output from the machine is almost the same.  And the  machine is probably a few hundred times as powerful - Digital imaging and certain other apps are a step forward - but for the basic functions, the computer vendors have concentrated on whizmos and gizmos rather than on common sense.  Common sense would have led to software which switched on instantly and was immune to virus threats - hard wired like your digital camera.  The advances would have been in the direction of data protection and organisation.  

Windows IS easy but that's because they have to be or else they would go the way of the dodo.  Linux has never been easy - but it certainly is  a better pastime than chewing television fodder.  Having a spare Acer laptop at home, I tried out Dapper Drake,  Edgy Eft and the Feisty Fawn Herd 3.  Amazing as it may sound, the Dapper Drake was the only one which proved to be the most stable and the 'easiest'.  Ofcourse one had to use 'Windows' drivers for the wireless - Ndiswrapper using the Neti2220 driver.  The Canon Pixma IP1600 stubbornly refuses to print, though taking the community advice I installed the IP2200 driver.  But what is worrying is that the 'later' releases of Ubuntu actually proved more difficult to work with my hardware.  

That said, I can still see Dapper Drake as a completely viable alternative to xp/vista.  The major problem here would be the software.  Gimp for instance is a programmers programme - unlike Bibble Lite or for that matter Capture One - which process images sensibly.  You can get Bibble Lite  for Linux - but you'd be paying for it again.  

Perhaps it might be sensible to take up gardening - the Microsoft monopoly seems to be impossible to break.  While the Linux community is brilliant, it is very simillar to Microsoft in its blinkered approach - new versions for new hardware - the underlying job remains the same.  A sea change needs people who can think out of the groove and the IT people are hardly capable of that.

---

### Post by xpod on 2007-02-07
I see quite a few comments about Windows being easier but i have to disagree with that statement as it might well be true for all you I.T experts but go tell my friends,family & neighbours about how easy it is and they`ll probably throw the thing at you.

Most of them have had computers for quite a few years but yet practically none of them know how to do even the most basic of tasks.
Nevermind removing viruses and replacing dodgy drivers or corrupt dll`s most of them could`nt clear their private data if you asked them to.

How long does the average XP install take before it could do with being re-installed??especially XP users who dont have a clue about safe browsing habits etc etc
Prior to getting into all this pc\os lark myself last year the folks i know with pc`s would just go buy a new one every couple of years when the present one became unusable.

Even clean installs of XP with all the usual security apps and stuff set up dont last too long though before someones on the phone again with their  next calamity.

I know if i was to set up Ubuntu for most of them and install all the codecs,java,flash etc i`d probably receive no where near as many phone calls as i sometimes still get.

It dont matter what OS a person uses i reckon cause if they aint going to learn how to use it then it`s always going to be hard .

---

### Post by VorDesigns on 2007-02-12
I just gave my brother a Dell 4600 that I got with WindowsXP Pro, 768MB of RAM, an 80GB drive and MSOSBE from a friend of mine who only bought it a year ago.  The reason, he kept getting viruses and I would keep cleaning it up for him.  Four times I did this and the fifth time, he said screw it and went out to buy a Mac.
My brother is very happy with his dual booting system (Windows and Ubuntu).  Since my brother is a Mac person, I told him to try Ubuntu.

---

### Post by mitanc on 2007-02-12
Seems like the issues you stated are mainly dealing with propietary formats problems.  Since the drivers aren't open source you will have a tougher time getting vid cards set up etc.  But I view hardware issues like that as a one time thing, kind of like upgrading Win XP to SP2, I gotta it once after I use my old Win XP CD to reinstall a system

Other than that, getting used to the OS is exactly that, getting used to the OS.  I recently purchased a macbook and I have never used OS X.  I still dont' get why the app doesn't actually close when I hit the X button, or why the app doesn't show in my alt-tab window if it is minimized.  I have learned to accept it, but I prefer linux and mac over windows for the simple reason that if the app doesn't respond every once in a while, I close it and start over with a simple click of a few buttons.  In Windows, my printer or webcam which worked for 3 months without fail now has some device driver error which is impossible to debug.

Anyways, be patient, you may actually like what you see.

---

### Post by tehkain on 2007-03-31
to the OP.

You know just enough to get yourself in trouble. Sure you could 'sudo nautilus' but this is implemented for a reason. You should not be messing with those files. If you do need to mess with them then you damn better be able to use the terminal. If you can't use a terminal then you shouldn't be anywhere out of your home directory. 

Installing is only hard because you are making it hard and it is no worse then windows. If you find a program that is not available in a repository or as a .deb file then you are over stepping the boundaries(the limit windows held you to). In windows did you compile software from source? No you probably did not. So if something is only available in source form then can you really compare that to windows? Not everything in windows is in a simple installer format. Not everything in ubuntu is in the repositories or .deb format either.  So maybe you should stick to the deb and repos like you did with the exes.

All in all you can't compare installing in windows with compiling from source in ubuntu.

Hope you give ubuntu a good chance. Your single os mentality(not a bad thing..not your fault) has given you a challenge. You wont find windows here and you will find at the end of the day it is not GNU/Linuxs fault for many of your issues. Maybe you will one day feel that the ways we do it here actually make more sense.

---

### Post by Robynsveil on 2007-04-01
> **jkeyes0 said:**
> The biggest difference I've seen between Windows and Ubuntu is that I can actually get support when I don't know how to do something in Ubuntu...

I can't tell you how many times I've found a problem in Windows and spent the better part of a working day looking for an answer, only to find nothing, whereas when I have problems with things in Ubuntu, I can come here, to a dedicated forum, and receive help (or at least guidance) in a matter of minutes. Free, useful, and it doesn't involve me calling India to speak to Ronald McDonald (yes, I've had to do that before, and that was the actual tech's name... it was for my internet service though).

My experience exactly. Years ago, I tried Red Hat Linux... not much in the way of support, so I kinda gave up after a few weeks. OTOH, there's heaps of support for Ubuntu, so much that I can't help but feel like I'm part of a growing, energetic community. At this point, I am still having a few issues in getting things like e-mail and NFS working properly, but the problem seems to stem more from having a closed, myopic OS like Windows to tap-dance around instead of finding the right conf file to modify or the right driver to apt-get. I'm staying the course this time... she'll be right!!

Windows has its place. I'm migrating away from it slowly but surely... as I get one feature working properly in Ubuntu, I remove it from Windows. My desktop and my laptop are both dual-boot WinXP / Ubuntu, but I hardly ever boot to Windows on my desktop anymore.

I guess I just love the idea of having a clean OS to work in, having control over my PC that runs faster because I don't have to have all those TSRs running in the background to protect me, and - most importantly - be part of a totally cool, larrikin group of people who are sick of being held to ransom by an industry that has its coffers as a focus. The fact that double-clicking a Setup.exe file installs a program does not stack up very well against the fact that Windows does a deplorable job of housekeeping and so you end up with several gig of junk sitting there to ssssllllllloooooooowwwww things down... even after you uninstall because of all the residual stuff left over in your \windows\system32 folder. Not to mention the gazillion *.tmp files generated by shoddily written programs like MSN Messenger that slows down Windoze even more. Interestingly, it was the Vista rollout that finally decided me to have another look at Linux.

---

