---
title: "Macromedia download snafu"
date: 2006-08-17
forum: Absolute Beginner Talk
---

### Post by smoaky on 2006-08-17
Hi,
I am a noo'b to installing programs on Linux. I need to install Macromedia Flash Player onto Ubuntu but the instructions on the download page are completly Greek to me......See below:

Installation Instructions


1. Click the "Download Now" button. A dialog box will appear asking you where to save the Installer.

2. Save the Installer to your desktop and wait for the file to download completely. 

3. Unpackage the file. A directory called install_flash_player_7_linux will be created. 

4. Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s).

5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

Can someone please explain to me (In simple terms) how to do these steps.I have no clue how to do what they are saying and would need someones clear step-by-step explanation.
I would greatly appreciated one of you Ubuntu experts out there that have the time a patience to help a new ubuntu user convert from Windoze,to what I think is the best distro in the whole world......Ubuntu   :-]
thanks for your help and understanding!!!

---

### Post by wilstrup on 2006-08-17
Flashplayer is a not open source, and therefor not available by default in ubuntu.
If you wish to install it, may I recommend that you enable the multiverse repository, by editing /etc/apt/sources.list (the file contains instructions for enabling multiverse).

Once this is done you can use synaptics package manager to install the 'flashplugin-nonfree' package.

Alternately, if you'd rather proceed with your downloaded flash plugin, I think you need to state which of the steps in the list is actually causing you trouble.

Good luck, and welcome to Ubuntu.

---

### Post by huygens on 2006-08-17
You can install Flash without dowloading it, and with a nice neat interface :)

Just go to your Ubuntu Application menu (it is on the top-left of your screen, with the nice Ubuntu logo)
You will see an entry at the bottom of this menu named "Add/Remove Applications"
You will have a [nice interface]("http://people.ubuntu.com/%7Emvo/gnome-app-install/new-look/gai--new-look.png") displayed :)

Check the two checkbox named "Show unsupported applications" and "Show proprietary applications". These two checkbox are located in the middle of the window on the right side. Then, type in the search box (the white rectangle in the top-right corner) the following word: flash
You will be displayed a list of application after a short while, and you should be able to identify one as being the Macromedia Flash version. Click on the small rectangle on the left of the Macromedia flash label (it is the checkbox associated with the application). And press the OK button (see at the bottom-right of the window).

:) Well, you're almost done. There will be a wizard at this point, which will take you through the installation. It will ask you to confirm that you want to download the flash package. And you will be done.

:) Do not hesitate to ask further questions if this did not solve your problem.

Huygens

---

### Post by smoaky on 2006-08-17
Hi Huygens,
Thank you  for the detailed info!!!! I will give it a try right now. How about updating Firefox to the newest version? I noticed that the update function is diabled on the dropdownbox. I think the newest is version 1.5.0.5 I have read posts asking the same question. Is this someting ubuntu has to to?
As far as security,I run Windoze XP with all various types of security software. Do I really need any type of security software using ubuntu distro?...I have a cable modem hooked up to a D-Link "NAT" enabled router. Would I need a firewall or anti-virus/spyware progam(s). It would make me feel safer If I did....yea call me paranoid, but i'm used to getting bombarded with all kinds of "nasties" using Windoze.
You suggestions and/or thoughts on all of the above would be great.
Take care and stay web safe   :-]

---

### Post by huygens on 2006-08-17
> **smoaky said:**
> How about updating Firefox to the newest version? I noticed that the update function is diabled on the dropdownbox. I think the newest is version 1.5.0.5 I have read posts asking the same question. Is this someting ubuntu has to to?

Yep, Ubuntu disable the automatic update of Firefox for a simple but good reason: [Ubuntu takes care itself]("http://www.zdnet.com.au/shared/images/news/ubuntu/automaticupdates.gif") of updating Firefox and keeping it well integrated into your Ubuntu. So if you perform an Ubuntu update, you will get the new Firefox version.
To force an update, go simply to the System menu on the top-left corner. Then under Administration you will find something like "Update Manager". Click on it. The [Update Manager]("http://www.flickr.com/photos/charlvn/197246412/") will let you show available updates (since last time he has synchronise), to be sure to have the latest, click the "Check" button in the middle of the window, and it will re-synchronise its list of updates. Then, click the "Install" button to install them. You will get the latest Firefox version.
Note: Ubuntu 6.06 has been shipped with Firefox 1.5 and I guess it will stick to it. So you will only get security and bug fix of Firefox. When Firefox 2.0 will be out, you will need to install it by yourself if you are interested. Or you could switch then to a newer Ubuntu release ;)

> **smoaky said:**
>  As far as security,I run Windoze XP with all various types of security software. Do I really need any type of security software using ubuntu distro?...I have a cable modem hooked up to a D-Link "NAT" enabled router. Would I need a firewall or anti-virus/spyware progam(s).

I know what you mean. I still have Windows in parallel, and I understand you ;)
If you are behind a NAT router, then you do not need a firewall in my opinion. Especially if you run Linux ;) Well, as you said, I'm also a bit paranoid, and even though my firewall/router is a PC with [Linux IPCop]("http://www.ipcop.org/"), I still have a firewall on my Windows and Linux PC behind. But actually, when looking at the logs of them, I really do not need them.
If you still want a firewall, you could install Firestarter, it is available like I did described it before for 'flash' (by using the [Add/Remove Application]("http://www.flickr.com/photos/charlvn/197243108/")), just look for firestarter instead and install it :)
There is a guide explaining [how to use Firestarter]("http://doc.gwos.org/index.php/Firestarter_Guide") (at least the bare minimum). There is also an entry about [Firestarter in the Ubuntu 6.06 Documentation]("https://help.ubuntu.com/ubuntu/desktopguide/C/networking.html"). And finally the forums have an interesting [how-to start automatically firestarter]("http://www.ubuntuforums.org/showthread.php?t=187899").

For spyware or anti-virus... I use none on Linux. Anti-virus softwares on Linux mostly check for Windows viruses :p they are intended to be used on Linux router, so that what is going via the network and is arriving on a Windows machine is safe!
As for spyware, I wish I new a software for Linux doing a similar job as Spybot... 'Cause eventhough I do not think there are spyware programs under Linux yet, we do have the same cookies crap with our internet navigators... So perhaps a bit of clean-up in your coockies once in a while would be required under Linux.

For [security on Ubuntu]("https://help.ubuntu.com/community/Security"), there are some entries in the [Ubuntu documentation]("http://help.ubuntu.com/"). It is rather technical and not all is for beginners, but you could get some idea.


Huygens

---

### Post by smoaky on 2006-08-17
Thank you Huygens,
What great information and very detailed!!! I now have Flashplayer installed and working. I also added firestarter.
Keep in mind I am doing all this as a test before I install this onto my HDD. Yes... I am doing this all on the "Live CD". All my programs and setting get wiped out everytime I re-boot,thats a good thing for me. I practice using all the various settings, trying out Terminal,etc,etc, before I commint to a dual boot with Win XP.
BTW I wanted to install Opera 9 browser,so I navigated to the add/remove, looked for it and it is not listed even though several how-to posts on Ubuntu say that it is there. Any possible reason why it is not listed? I have performed all updates to Ubuntu.Could it be that I'm running the Live CD?
I have sucessfully installed Opera 9 onto Ubuntu using the Opera web site, I am just curious as to why it is not listed on the add/remove. I checked both boxes as I had done for firestarter and flashplayer.....no luck. Not a big deal just like talking to a helpful person who enjoys working with Linux.Maybe some of your knowledge will rub off on me.
ttys

---

### Post by huygens on 2006-08-18
Hi Smoaky,

Thank you for your compliment :-) It made me feel happy to have helped you !

As for Opera 9 ... It is a bit weird what happen to you. I had no problem seeing it in the list of Add/remove Applications. Perhaps, you need a refresh of your package list (but as you said, if you have performed all Ubuntu updates, it should be already OK). But let's just try it, just to be sure.
Once you opened Add/remove Applications, there is an "Advanced" button at the bottom of the window. Click on it, and you might get a small window prompting your password. Enter it and then you get to Synaptics.
Once there, you have in the toolbar an icon to "reload" the package list. Click on it. You should see a small window showing you the refresh progress...
Then, you could quit Synaptics and go back to Add/remove Applications (I prefer that way, because I do not need to know in which repository Opera is located, Add/remove App will just ask me if I want to add the correct repository once I have selected Opera). There you could look once more for Opera, and hopefully find it :-)

The next time I will reboot my computer, I will try to boot on the Live Ubuntu version and check it out... Apart, if you solved your problem before that! ;-)

Huygens

---

### Post by paul_h on 2006-08-18
Hi Huygens,

Thanks for your guidance on installing Macromedia Flash. After installing Ubuntu only a week ago I'm wrapt in it. I've neen using MS OSs since the year dot but that is ended now as Ubuntu does everything for me.  Installing Macromedia Flash was one of my last hurdles, but you have fixed that.

Thanks.

Paul_h

---

### Post by Ambimom on 2006-08-18
if you're concerned about cookies, both Opera and Firefox will remove cookies at the close of each session.  The advantage in Opera is that it has a password manager built in.  It is a simple matter of clicking on it's "magic wand" to input passwords.  That way, sites can put as many cookies as they like because they're gone the minute you close your browser.  Check the preferences menus.

---

### Post by smoaky on 2006-08-18
> **huygens said:**
> Hi Smoaky,

Thank you for your compliment :-) It made me feel happy to have helped you !

As for Opera 9 ... It is a bit weird what happen to you. I had no problem seeing it in the list of Add/remove Applications. Perhaps, you need a refresh of your package list (but as you said, if you have performed all Ubuntu updates, it should be already OK). But let's just try it, just to be sure.
Once you opened Add/remove Applications, there is an "Advanced" button at the bottom of the window. Click on it, and you might get a small window prompting your password. Enter it and then you get to Synaptics.
Once there, you have in the toolbar an icon to "reload" the package list. Click on it. You should see a small window showing you the refresh progress...
Then, you could quit Synaptics and go back to Add/remove Applications (I prefer that way, because I do not need to know in which repository Opera is located, Add/remove App will just ask me if I want to add the correct repository once I have selected Opera). There you could look once more for Opera, and hopefully find it :-)

The next time I will reboot my computer, I will try to boot on the Live Ubuntu version and check it out... Apart, if you solved your problem before that! ;-)

Huygens
Thank you Huygens,
I live on the East coast U.S.A. Where do you Live? It is 5:30 PM here and I just got home from work. I work Tomorrow probably until 6PM. I will try out your great suggestions on Sunday,and I will get back with you as to my results then.Keep on the lookout for my reply. Until then take care my new friend and I will talk to you Sunday.

---

### Post by huygens on 2006-08-19
> **smoaky said:**
> Thank you Huygens,
I live on the East coast U.S.A. Where do you Live? It is 5:30 PM here and I just got home from work. I work Tomorrow probably until 6PM. I will try out your great suggestions on Sunday,and I will get back with you as to my results then.Keep on the lookout for my reply. Until then take care my new friend and I will talk to you Sunday.

Hi Smoaky,
At the moment I live in Germany near Francfort, but I'm actually from France. Tough job to work on Saturdays :( I did not do anything today ;) it is now 22h49, just checking my e-mail and getting some more rest in a few seconds...
I'll check this thread tomorrow for news from you, and perhaps I will have found the time to try Opera from the Live CD...
Take care you too and see you online in the coming days.

Huygens

---

### Post by huygens on 2006-08-20
Hello Smoaky,

I'm back online and using the Live DVD of Ubuntu at the moment.
As you said, I am not able to find the Opera entry in Add/Remove Applications :(
But do not worry, if you plan to install Ubuntu, you do find it :)

To install it none-the-less under the Live version, you could try this:
Go to the Applications menu and select "Add/Remove..." at the bottom of the list.
On the bottom of the newly opened window, click on the "Advanced" button. It will open Synaptics.
There you need to add the correct [repository]("https://help.ubuntu.com/community/Repositories/Ubuntu") for Opera. For this, you go to the Settings menu and select the Repositories entry. A new smaller window will appear. Then, you see the list of available "channels" (or type of repository) you are already subscribed to, or that you can add. However, the one interesting us for Opera, is not in the list. You need to click on the "Add" button which is on the right-end side.
You will get a new window where there is a "Custom" button which you have to click on. It will ask you for a line, which is: ```
deb http://archive.canonical.com/ubuntu dapper-commercial main
``` Click on "Add channel".
Then click on "Close". A information message will appear that state that has your channel subscription is different, you need to update it. To update it, click on the "Reload" button in the toolbar.
Now, you can find 'Opera' (strangely, it did not appear in Add/remove Applications on the Live CD) and install it. :)[LIST]
[*]You can still use Synaptics:[/LIST]Inside the window, at the bottom-left corner, there is a "Section" button. Click on it. In the left part of the window, you have now some kind of "directory" or "section" list. You need to scrolldown to the bottom and select the section "World Wide Web (non free)". On the right side, you will now see Opera. Select it, and click in the toolbar on the "Apply" button. To select it, you need to click on the left of the Opera line, there is a small symbol (a white square with a small star), then a small menu appear where you need to select "Mark for installation". You're done :)

You're done :-) I hope it works for you too...

Huygens

PS: I have been using this help page to get information [where to find the Opera repository]("https://help.ubuntu.com/community/OperaBrowser").

---

### Post by huygens on 2006-08-20
> **smoaky said:**
> As far as security,I run Windoze XP with all various types of security software. Do I really need any type of security software using ubuntu distro? [...] Would I need a firewall or anti-virus/spyware progam(s).

Sorry to go back to this topic, but I have found a forum where they talk about activating an anti-virus also for a Linux desktop user (like you). They also state that it is not really needed, but in case you are just interested to try it out, here it is: [http://www.ubuntuforums.org/showthread.php?t=136064](http://www.ubuntuforums.org/showthread.php?t=136064)

Huygens

---

### Post by smoaky on 2006-08-20
> **huygens said:**
> Hi Smoaky,

Thank you for your compliment :-) It made me feel happy to have helped you !

As for Opera 9 ... It is a bit weird what happen to you. I had no problem seeing it in the list of Add/remove Applications. Perhaps, you need a refresh of your package list (but as you said, if you have performed all Ubuntu updates, it should be already OK). But let's just try it, just to be sure.
Once you opened Add/remove Applications, there is an "Advanced" button at the bottom of the window. Click on it, and you might get a small window prompting your password. Enter it and then you get to Synaptics.
Once there, you have in the toolbar an icon to "reload" the package list. Click on it. You should see a small window showing you the refresh progress...
Then, you could quit Synaptics and go back to Add/remove Applications (I prefer that way, because I do not need to know in which repository Opera is located, Add/remove App will just ask me if I want to add the correct repository once I have selected Opera). There you could look once more for Opera, and hopefully find it :-)

The next time I will reboot my computer, I will try to boot on the Live Ubuntu version and check it out... Apart, if you solved your problem before that! ;-)

Huygens

Hello Huygens,
My guess is that it is around 02:10PM at your house right now? Early Sunday Morning here.Yea I don't like working Saturdays but I'm off Sun,Mon and Tue each week!!!!
Anyway I tried all of the above after re-boot.Ran add/remove 
and performed all your instructions...still doesn't show Opera listed ??? PLEASE do not worry about it, as I said before I am able to install Opera via the web site with no problems.It's still kinda strange huh? I burned this CD from an iso image,could there have been a glitch in burning the CD? Haven't encounterd any other possible problems with this distro. as of yet.
BTW I am buliding a PC that I will give myself for Christmas. It will have an AMD Anthlon64 3800+ processor,Asus mobo,ATI,2Gb Ram, 250Gb SATA Western Digital HDD,DVD/CD burner optical drive.
I will be installing Ubuntu on that comp with no other O/S. Will there be a need for a disk defrag program like i run on windows? (I use Diskeeper 10 pro)  
I would love to have someone such as yourself,to talk to about computers and Windows/Linux O/S on an occasional basis If you don't mind. I am a self-taught computer junkie for just the past three years, and would enjoy to continue to learn all that I can.
Would there be a way to exchange email addresses without having everyone else see them? (for privacy.)
If you would prefer to keep this thread going instead of using email address's that fine too. And If you don't want me to bother you that cool also.
I just hate to bother people if they don't want to be bothered. Remember I always have lots of questions and Iam always willing to listen and learn.
Take care and I'll ttys I hope.

---

### Post by smoaky on 2006-08-20
Thanks I will give that a try.
Also I will be installing Ubuntu on that comp with no other O/S. Will there be a need for a disk defrag program like i run on windows? (I use Diskeeper 10 pro) 
I would love to have someone such as yourself,to talk to about computers and Windows/Linux O/S on an occasional basis If you don't mind. I am a self-taught computer junkie for just the past three years, and would enjoy to continue to learn all that I can.
Would there be a way to exchange email addresses without having everyone else see them? (for privacy.)
If you would prefer to keep this thread going instead of using email address's that fine too. And If you don't want me to bother you that cool also.
I just hate to bother people if they don't want to be bothered. Remember I always have lots of questions and Iam always willing to listen and learn.
Take care and I'll ttys I hope

---

### Post by huygens on 2006-08-20
> **smoaky said:**
> Hello Huygens,
My guess is that it is around 02:10PM at your house right now? Early Sunday Morning here.Yea I don't like working Saturdays but I'm off Sun,Mon and Tue each week!!!!
Almost, it was 03:10PM at that time :) now getting close to the end of the day, planning to get a DVD to rent and watch it :) with my Girlfriend and a martini... How much "time shift" do we have then between the East Coast and Central Europe?

> **smoaky said:**
> I burned this CD from an iso image,could there have been a glitch in burning the CD? Haven't encounterd any other possible problems with this distro. as of yet.
As I said :(, I do not see it neither in the Add/Remove Applications. Perhaps a small problem with the Live version of Ubuntu. But it was working properly when installed :) (as I installed Opera via this application just after installing and upgrading my Ubuntu)

> **smoaky said:**
>  BTW I am buliding a PC that I will give myself for Christmas. It will have an AMD Anthlon64 3800+ processor,Asus mobo,ATI,2Gb Ram, 250Gb SATA Western Digital HDD,DVD/CD burner optical drive.
Sounds good :) However, I had a bad experience with my Radeon card not properly configured under Linux. Basically, I have a laptop and the Radeon 9000 mobility is not supported for 3D. Well some 3D applications do work, but forget about Xgl, it is incompatible... So I am quite unhappy with it. Next time, I was planning to look for nVidias or even better Intels. Those last ones are perhaps not great for 3D performance, but they do have an open source driver, and as I am not playing games, this would be a good solution for you.
Perhaps, you should go to the [hardware part]("http://www.ubuntuforums.org/forumdisplay.php?f=138") of these forums and ask people if they had any problem with the ATI card you plan to have. Also, there is a page where [many uncompatible graphic card with Xgl]("http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL#Cards_seemingly_unsupported") are listed, this could help you to choose.

> **smoaky said:**
>  I will be installing Ubuntu on that comp with no other O/S. Will there be a need for a disk defrag program like i run on windows? (I use Diskeeper 10 pro)

On Linux you do not need to defragment your hard drive :) Fragmentation of files do exist, but it is a really slow process and therefore, before it starts to be anoying you will change of OS or hard drive ;)
So this is really not a critical topic under Linux and UNIX OS (I do not know for Mac OS). But fragmentation concerns basically only FAT32 and NTFS file systems (perhaps you've heard about those terms once you installed Windows and it was asking you to format your drive)

> **smoaky said:**
>  I would love to have someone such as yourself,to talk to about computers and Windows/Linux O/S on an occasional basis If you don't mind. I am a self-taught computer junkie for just the past three years, and would enjoy to continue to learn all that I can.
Would there be a way to exchange email addresses without having everyone else see them? (for privacy.)
If you would prefer to keep this thread going instead of using email address's that fine too. And If you don't want me to bother you that cool also.
I just hate to bother people if they don't want to be bothered. Remember I always have lots of questions and Iam always willing to listen and learn.
Take care and I'll ttys I hope.

:) I would be glad to chat with you by other means! You could check my profile (clicking on my avatar) and there you will see: "send a message via e-mail to Huygens". If you put yours in, we could then chat via other medium.

Talk to you later!

Huygens

---

### Post by smoaky on 2006-08-21
I did it !!!!!!!!!!!!!
Thanks again Huygens. Check your Yahoo email. I sent you a brief message so you can accquire my email addy.
ttys

---

### Post by huygens on 2006-08-21
I'm happy it is working for you and thanks for your e-mail, I have received it. I'm leaving in about 10min, so I will reply to it another time if you don't mind :)

But I found an interesting information for you. It was a post on a [French Linux geeky site]("http://linuxfr.org/2006/08/20/21216.html") and it was about disk defragmenting :) So as [Google translation is clumpsy and funny]("http://translate.google.com/translate?u=http%3A%2F%2Flinuxfr.org%2F2006%2F08%2F20%2F21216.html&langpair=fr%7Cen&hl=en&ie=UTF-8&oe=UTF-8&prev=%2Flanguage_tools"), I will summarise it for you:
Basically they say it can defragment a few filesystem types, but as said before, this is not needed on a weekly basis, they precise that you can do it once a year, it is not too often ;)
The project page of Shake is: [http://vleu.net/shake/](http://vleu.net/shake/)
There are some user feedback on it on a Gentoo forum here: [http://forums.gentoo.org/viewtopic-t-463204-start-75.html](http://forums.gentoo.org/viewtopic-t-463204-start-75.html)
And a small post about [why doen't Linux need defragmenting]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting").

The rest of the post is basically what is written in English on the project web page.

Have a nice day still ;) I'm going now to look for a new apartment, closer to work (not that I like it, but I would loose less time going there each day, so moe free time ;) )

Huygens

---

