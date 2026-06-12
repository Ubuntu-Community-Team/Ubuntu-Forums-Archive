---
title: "Complete and utter newbie with lots of questions"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by GTdriver2012 on 2007-09-16
First off, I would like to just say thank you in advance to everyone who contributes to linux and open source in general.  I am simply amazed at the quality of the community that I have seen just from my (months) of research on linux and ubuntu.  

I will try and keep this short, but I believe this small history might help.  I have been a windows user since 95, and after 12+ years of frustration and growing contempt for windows and its "upgrades" I have finally decided to take an alternate route (I know, I know, its about dang time)  I know windows well, it has taken years to learn how it "works" and despite what so many people believe, Windows is not easy, nor is it user friendly in the least.....IMO   But i'm sure that I don't have to go into detail about that.

Anyway I am very interested in running ubuntu as my primary OS.  I just recently purchased a new laptop   in which I intend to wipe clean of Vista :) and install ubuntu.  I have a desktop that will still stay XP for a few reasons, but this laptop will be a clean slate, a fresh start.

Where to begin........ I guess with a few questions

1. Where can I find definitions to terminology used in ubuntu and linux in general. Is there a source that lists these words and plain english explanations of what they mean, and what they are referring to.

2. I have seen plenty of references to commands that need to be typed into the terminal (I think) for installation, setting, etc.... where, when, how do I do these commands, and what is it exactly that I am doing by using these commands?  I know this is vague, and I am sorry for that, but it is my lack of knowledge showing its true colors.


I am not afraid to learn, and I do not expect this to be painless or frustration free, after all I did use Windows for a long time..... maybe I am a glutton for punishment :twisted: 

Thank you in advance again, I look forward to joining this community, and hope to someday become a contributing member!

---

### Post by mikewhatever on 2007-09-16
> 1. Where can I find definitions to terminology used in ubuntu and linux in general. Is there a source that lists these words and plain english explanations of what they mean, and what they are referring to.

2. I have seen plenty of references to commands that need to be typed into the terminal (I think) for installation, setting, etc.... where, when, how do I do these commands, and what is it exactly that I am doing by using these commands? I know this is vague, and I am sorry for that, but it is my lack of knowledge showing its true colors.


Hi and welcome. 
I am not aware of any list of words of terminology for linux, but here is a good site to start with [http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php).
It also answers the question about the Terminal [http://psychocats.net/ubuntu/terminal](http://psychocats.net/ubuntu/terminal)

---

### Post by aysiu on 2007-09-16
Don't forget that you can **copy and paste** commands. You do not need to *retype* them.

---

### Post by GTdriver2012 on 2007-09-16
thank you so much mike, after a quick view of those sites, they have already been bookmarked :D

---

### Post by Paul133 on 2007-09-16
And note that Crtl-C and Ctrl-V work with most programs, but not the terminal. You'll have to right-click to copy and paste. As far as Linux commands, try wikipedia. Google UNIX commands. Do 'man command' in the terminal to look at the manual for the command (though the manual isn't always easy o understand). Here's a pretty good site for commands and Linux info i plain English: [http://www.linfo.org/](http://www.linfo.org/) Definitely check out Asius site ([http://www.psychocats.net](http://www.psychocats.net)). The terminal is located in Applications -> Accessories -> Terminal. I personally have my terminal key-binded to the useless Windows key so it's easy to bring up,but you don't have to do that (keybindings are in System -> Preferences -> Key Bindings by the way). 

In Ubuntu, we install programs (packages) not from random Intenet sites, like in Windows, but through repositories, servers containing thousands of programs that have been checked to work with Ubuntu and have no malware. In order to access the default repositories, go to System -> Administration -> Synaptic Package Manager. It lets you search for and install programs.

Any other questions? And remember, if ou have any problems, just post on the forums and we'll try to help you. Good luck with Ubuntu!

---

### Post by Maestro23 on 2007-09-16
Few links to get your feet wet with:

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Top 10 Commands for noobs: [http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/](http://blog.lxpages.com/2007/02/25/top-10-linux-commands-for-newbies/)

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

### Post by Paul133 on 2007-09-16
Maestro, who recommends vi to a newbie? I'm perfectly happy with nano. :)

---

### Post by Maestro23 on 2007-09-16
> **Paul133 said:**
> Maestro, who recommends vi to a newbie? I'm perfectly happy with nano. :)

Nano is what I use as well.  It was just in my "Noob" links. :smile:

I started out using vi back in the day on Solaris systems. Bad memories. :lolflag:

---

### Post by GTdriver2012 on 2007-09-16
Thank you aysiu and paul!  Great Great Info


A couple of more questions.....

Do certain packages have restrictions on which hardware they will work with like motherboards, graphics hardware, processors, etc...

I know windows was very prone to these few problems, how is linux with them?  Windows basically self destructs its registry from regular use, which causes the need to re-install every so often to keep the system running smoothly. Does linux allow programs to edit the kernel, moving things around and eventually confusing the core of the system?  How does linux (basic in a nutshell) handle programs, and how they run on your system?  Does linux get bogged down from continuous use and have to be restarted every so often to get things back up to speed, it is to my understanding that this happens in windows due to poor memory management, and basically static memory being used up to store things that  are no longer valid to a certain program or function.

How does linux manage hard drive storage?  is partitioning recommended? Does linux need to defrag the hard drive from time to time?

Sorry about all the questions, but all this info really got me thinking about things

---

### Post by GTdriver2012 on 2007-09-16
How well will ubuntu run theses tasks
1. Word Processing
2. Web browsing
3. Music and video playback
4. Multitasking the above tasks
on these system specs
Intel core 2 duo @1.5Ghz
2gig ram @ 667 mhz
Intel GMA X3100
160GB 5400RPM hdd

I know vista would suck up most of these resources, leaving little for actual productivity :( 
Thank you guys again for being so helpful :)

---

### Post by aysiu on 2007-09-16
> **GTdriver2012 said:**
> How well will ubuntu run theses tasks
1. Word Processing Extremely well, but the compatibility with Microsoft Word documents may be a little off, particularly in page formatting. > 2. Web browsing Excellently. No complaints. > 3. Music and video playback It depends on what formats your music and video are in. If you have DRM'ed iTunes videos and music, forget it. If you have MP3-encoded music, you may have to [install the proper codecs](http://www.psychocats.net/ubuntu/mp3). If you're already using open formats like Ogg, then you'll love music and video playback right away. > 4. Multitasking the above tasks Absolutely no problem. > on these system specs
Intel core 2 duo @1.5Ghz
2gig ram @ 667 mhz
Intel GMA X3100
160GB 5400RPM hdd Those specs are overkill for the aforementioned tasks.

---

### Post by [Alsharifi] on 2007-09-16
> **Paul133 said:**
> And note that Crtl-C and Ctrl-V work with most programs, but not the terminal. You'll have to right-click to copy and paste.!

u can actually ctrl+shift+v to paste, and ctrl+shift+c to copy.

---

### Post by aysiu on 2007-09-16
You can also highlight text (without the Control-C) and then use middle-click to paste (without Control-V).

---

### Post by [Alsharifi] on 2007-09-16
i didnt complete understand that...middle click?

---

### Post by GTdriver2012 on 2007-09-16
Thank You Thank You Thank You

I have actually been using open office for about 3 years, and I find it more intuitive than MS office!
I have all my media on dvd and cd, so using a new format won't be a problem, I was actually hoping that I would need to convert it to something new, because I've always found that doing is the best way to learn.
I hope to eventually get into some programming, and have been playing around with some 3D design, should I be capable to continue learning and practicing these without overtaxing my system?

---

### Post by Maestro23 on 2007-09-16
> **'[Alsharifi] said:**
> i didnt complete understand that...middle click?

Push down on your mouse wheel if you have one.

---

### Post by GTdriver2012 on 2007-09-16
how would you middle click with a touch pad and only two buttons below?..... hot key it?

---

### Post by Maestro23 on 2007-09-16
> **GTdriver2012 said:**
> how would you middle click with a touch pad and only two buttons below?..... hot key it?

Maybe pushing both buttons down at same time?  Don't know.

---

### Post by eph1973 on 2007-09-16
If you want to learn programming, you've come to the right place.  I am still learning, but my personal opinion is that any Linux based distro completely blows Windows out of the water as far as ease of use for programming.  I don't know anything about 3D design, but it's been my experience that if you are looking to do networking or development that Linux beats Windows hands down.  The only possible exception to this (and I am not completely sure about it) is C#, as it is a Microsoft developed language.

---

### Post by GTdriver2012 on 2007-09-16
From all I'm reading and all of the responses I'm getting, I am confident that I have made the correct choice.   As far as programming goes, I am familiar with the concepts of programming... the if, then, else stuff, I've toyed around with cobal, VB and C++ but I am completely unsure where to start in linux.

---

### Post by jon zendatta on 2007-09-16
As far as i know GT no such thing as fragmentation in Linux unleash the power, you'll never look back.

---

### Post by rich.bradshaw on 2007-09-16
Just to let you know, I have

Pentium III 1GHZ,
256 MB Ram
Intel Integrated Graphics
40 GB Hard disk

and can do all the things mentioned above with no problems...

---

### Post by GTdriver2012 on 2007-09-16
That is exactly what I was hoping to do, not look back.
So then the next question is to partition, or not to partition?

---

### Post by GTdriver2012 on 2007-09-16
thanks rich, its good to know that I'll be set for years to come

---

### Post by GTdriver2012 on 2007-09-16
from what I'm reading it is recommended to partition into 3's  /root /home /swap
does this sound correct for a one user full ubuntu install? 
any recommendations that might work better?

---

### Post by hyper_ch on 2007-09-16
In the beginning you may not want do completely ditch windows so I'd recommend dual-booting... defrag the windows partition a few times and then resize the partition so that you can install ubuntu into the unallocated space.

---

### Post by eph1973 on 2007-09-16
Some people like to partition, it's really up to you.  Some people would recommend a small partition mounted at /home, but again it's up to you.  Personally, since I run a dual boot setup, I have a partition that is FAT32 so I can trade files between Windows and Linux, and I have a swap partition, and I have my partition at / and I have some of my HD that I don't use at all in the event I want to make it another partition of some sort later on down the road.  It really just comes down to personal preference.

---

### Post by GTdriver2012 on 2007-09-16
Thanks for the tip Hyper
I am actually planning on keeping my xp desktop at home, just that, potentially adding dual boot.  My wife is not really interested in using/learning linux, and she is the primary user of the desktop pc, but the laptop I order is gonna be just for me, and i'm more than willing to take the full plunge!

---

### Post by hyper_ch on 2007-09-16
what laptop do you want to get? Did you check hardware compatibility?

video cards, wifi, bluetooth can often pose some challenges.

---

### Post by GTdriver2012 on 2007-09-16
what exactly is the swap, and what is it used for?

---

### Post by GTdriver2012 on 2007-09-16
I finally (after weeks of research) chose the inspiron 1520, I saw that someone had posted a how to guide on getting ubuntu up and running with the only hardware conflict being the integrated modem, which I still don't see why anyone even includes anymore, anyway

---

### Post by mocoloco on 2007-09-16
Yes, I would recommend three partitions, makes it easy to re-install and not lose all your personal stuff.  The tricky part is deciding how much space to give to each, remember that all your installed apps and everything will go in your root partition, but all your personal files, music, photos etc will go in your home partition, so you'll have to gage about how much personal stuff you'll need room for.

---

### Post by GTdriver2012 on 2007-09-16
I've got 160Gb to play with..... 
I was debating whether to use 3 or 4 actually..... could I use a fourth part just for programs keeping them separate from the root? or does linux require that programs are on the same part as root?

---

### Post by eph1973 on 2007-09-16
A swap partition is the same idea as swap with Windows.  Except for Windows uses all of your free space for swap, and Linux has a designated partition for it.  It's basically a partition on your hard drive that the OS can put stuff that's not really being used but needs to remain in memory onto your hard drive so it can access it later should it need it, freeing up your actual memory to process things that are active.  The rule of thumb is 1.5 to 2 times the amount of memory as to its size.

---

### Post by GTdriver2012 on 2007-09-16
so if i've got 2 gigs of ram, a 4 gig swap would be more than sufficient?

---

### Post by eph1973 on 2007-09-16
> **GTdriver2012 said:**
> so if i've got 2 gigs of ram, a 4 gig swap would be more than sufficient?

4 gig swap is quite large, yes, more than sufficient.

---

### Post by GTdriver2012 on 2007-09-16
realistically, would I ever use up that 4 gigs of swap???

---

### Post by NovaAesa on 2007-09-16
Probably not, unless you plan to use hibernation. If you use hibernation, I would suggest 4GiB, but if you don't use hibernation just go with 2GiB.

---

### Post by hyper_ch on 2007-09-16
for hibernation it must be bigger than the ram... so 2gb should be ok... I'd go to 2.5-3gb for swap.

---

### Post by philinux on 2007-09-16
I'm running with the spec below and it runs faster than my mates new Advent laptop with vista!
Just my 2pence worth. Welcome aboard.

---

### Post by GTdriver2012 on 2007-09-16
Does anyone know if I use 4 partitions /root /programs /home /swap
How well will that work in ubuntu, having just ubuntu on its own part, having a part for just programs, and them my home for media and of course my swap

---

### Post by aysiu on 2007-09-16
Four partitions is just a mess.

Go with three:
/
/home
swap

---

### Post by GTdriver2012 on 2007-09-16
Thank you Aysiu, it can't get much clearer than that!
so is there a name for /  or is it just /?

---

### Post by aysiu on 2007-09-16
It's called the *root* folder, but it should not be confused with the /root folder, which is inside /

---

### Post by mocoloco on 2007-09-16
> **aysiu said:**
> It's called the *root* folder, but it should not be confused with the /root folder, which is inside /

Which is generally called *slash root*.  Also when speaking out a path I generally pronounce it slash, otherwise call it root.

---

### Post by GTdriver2012 on 2007-09-16
thanks for the definitions, i'm sure that will come in handy when trying to find out where stuff is installed
Does anyone know where there is a resource that explains these things?

---

### Post by Maestro23 on 2007-09-16
> **GTdriver2012 said:**
> thanks for the definitions, i'm sure that will come in handy when trying to find out where stuff is installed
Does anyone know where there is a resource that explains these things?

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

[http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html](http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html)

Just a few... you can google more.

---

### Post by wheredidrealitygo on 2007-09-17
double post. see below.

---

### Post by wheredidrealitygo on 2007-09-17
a resource I found invaluable when learning about Ubuntu is a book called Ubuntu Hacks, an O'Reilly book. It's really comprehensive, and while it was meant for a previous version of Ubuntu (dapper I think), a lot of it still applies and is informative in general, from installing Ubuntu itself, to installing those proprietary .mp3 & whatnot codecs, all the way up to running servers for apache & mail.

I didn't even have to order it online, I found it at a local Chapters.

[http://www.oreilly.com/catalog/ubuntuhks/](http://www.oreilly.com/catalog/ubuntuhks/)

---

### Post by GTdriver2012 on 2007-10-12
Well I finally got my new laptop.....  I set up vista which came pre-installed (and took 4 hours to set up just to get going :confused: )  WHAT A HORRIBLE experience that was.... Vista is everything anyone said bad about it and more, heck I can't do anything on it, on account of it just locking up completely at random, I have done every hardware check that dell offers and can find no problems...... anyway long story short, I was waiting for 7.10 to come out but tonight decided to just install and try it out, and, wow what a difference!!!! 
The fun part is, it has raised even more questions..... It has yet to freeze up on me, which seemingly proved my theory that it was vista, not hardware.

My first question is, while I'm doing random things, or nothing at all, my hard drive makes a clicking noise, it happens about every thirty seconds or so, but I was wondering if it was normal, or indicative of a hd problem?

---

