---
title: "How different is Ubuntu from openSUSE?"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by Bullfrog245 on 2007-06-10
Hi guys,

THIS IS MY VERY FIRST POST USING A LINUX OS!!  Yeah for me.  Now for my question.

I tired for several days to install Ubuntu, but I kept getting the "tty" error.  After searching this forum for several hours and looking for a work-around, I gave up.  Instead of going back to Windows and begging for forgiveness, I downloaded openSUSE instead.  The install for it went great, and I've even figured out how to network it with my Windows computers.

How different are the different distros of Linux?  In the future, I'd like to switch to Ubuntu once a version comes along that I can install.  Will all the stuff I lean using openSUSE be valid for other distros of Linux?  Is it like the switch between Windows XP Home and Windows XP Professional, or like the switch from Windows XP to OS X?  Are all the shell commands the same?  I don't even know enough know to know what could be different.

Any insight would be helpful.  Thanks.

---

### Post by steveneddy on 2007-06-10
Ubuntu has a better community.

AND - I don't get beans by posting on openSUSE forums.

---

### Post by Bullfrog245 on 2007-06-10
The community is one of the reasons I wanted to install Ubuntu so bad in the first place ^_^

---

### Post by koshari on 2007-06-10
on thew serface the main differences are between gnome and kde, under the hood the packaging systems rpm yast and apt are prolly the most different, the nbasic file structure and user concepts are very similar.

also sudo is another area that not all distributions offer

---

### Post by ramjet_1953 on 2007-06-10
Both distros are very slick.

However, there are differences, also.

1. Ubuntu is Debian based and in my opinion has a vastly superior package management system, with Synaptic. Open SUSE is Fedora based and uses the RPM syste, which is OK, but doesn't have the dependency sorting power of Synaptic.

2. By far the biggest advantage with Ubuntu are these forums and WIKI's. There is just nothing else out there like it.

3. As good as SUSE is, it is now owned by Novel, who have recently signed an agreement with Microsoft. Many people view this a "dealing with the Devil" and goes against the Open Source philosophy.

Regards,
Roger :cool:

---

### Post by Bullfrog245 on 2007-06-10
What is the alternate to the RPM style.  To me, the RPM's seem to be the equivilant of .exe in windows.  You download a RPM, double click on it, it magically gets installed somewhere (I haven't figured out where yet *shame on me*)  How are things installed in Ubuntu?

What exactly was the deal Novell signed with Micro$oft?  I am trying to make the switch to Linux to get as far away from Windows as I can...

*Forgive the windows lingo, I'm a recent migrant after all ^_^

---

### Post by ThinkBuntu on 2007-06-10
[LIST]
[*]Ubuntu boots faster and launches its package manager faster
[*]Ubuntu searches packages slower once in the manager
[*]OpenSuSE has more usability tweaks
[*]OpenSuSE looks nicer from a fresh install
[*]OpenSuSE's installer offers more customization, but takes loner (it's a DVD)
[*]Ubuntu's community is better, faster, and most importantly, largely centralized
[*]The same goes for its repositories, which are overall more reliable and easier to use
[*]OpenSuSE takes a more agressive free software stance
[*]Ubuntu is more popular and gets more press these days
[*]OpenSuSE has a very robust control center called YaST
[*]OpenSuSE comes with extra security features, such as AppArmor, but both can be equally secure
[*]OpenSuSE largely depends on itself (and SUSE, of course), while Ubuntu depends heavily on Debian
[*]The Ubuntu wiki is more comprehensive
[*]OpenSuSE could, just maybe, be affected by the Microsoft-Novell deal. But that remains to be seen.
[*]Ubuntu, largely due to Debian, has a much, much larger package base.
[*]Both are about the same as far as being up-to-date
[*]Both have near-equal performance
[/LIST]

Personal note: Also, my avater would be lame with a chameleon in the hat. And SuSEPad/ThinkSuSE doesn't sound nearly as slick as ThinkBuntu. Because, I think Buntu on my ThinkPad.

---

### Post by Bullfrog245 on 2007-06-10
Thanks for the information ThinkBuntu.  I quess I didn't make too bad of a choice for a temporary Ubuntu substitute.  It does seem that I ended up across the street as far as the behind-the-scenes stuff is concerned.

How did you make a bulleted list with HTML code being turned off?

*side note*
Can anyone tell me which directory software is installed to if I double clicked on an RPM and told it to install?

---

### Post by ramjet_1953 on 2007-06-10
RPM's and deb's are just different ways of putting files together that are then installed.

Under Ubuntu, you have 4 ways to install software.

1. Applications>Add Remove. A simplified way to install common softwarepackages.

2. Synaptic Package Manager a greatly exhanced GUI for installing packages.

3. Use the command line with a text package installer called apt

4. Roll your own. This is where you dowload sourcefiles and go through a process of compiling and installing a piece of software manually.

Of course, with SUSE you can do the same things, especially compiling from source.

I'm not an expert on the political manouverings of Microsoft, but from what I understand Microsoft is on one of its FUD crusades, at present and is claiming that Linux impedes on hundreds of its patents. However they have been repeatedly asked to "Put-up, or shut-up" and they haven't been forthcoming with the proof.

However, Novel signed a deal with Microsoft, which I believe indemnifies them and their customers from legal action from Microsoft, if they are successful in their bid for patent infringement. Of course, money has also changed hands.

Many people in the Open Source community are uncomfortable with this deal and have given SUSE the flick, on moral grounds.

Regards,
Roger. :cool:

ps, if anyone is more familiar with this subject please feel free to correct me, or clarify things.

---

### Post by ThinkBuntu on 2007-06-10
I don't know too much about RPM installation, as I largely stuck to the repos when I used openSuSE 10.2. It'll install it where it needs to be, I suppose. You could always move the .rpm file to a cache folder of your choice, I suppose. And as for the bullet list, click the bullet list icon when you're posting. Right between the numbered list icon and the unindent icon.

---

### Post by ukripper on 2007-06-11
Well if you are forced to use rpm packages in ubuntu u still can convert them to deb packages by using app called - Alien which is in repository does it all for you in conversion. i rember when i had to convert Office 2.2 in deb Alien was my best mate.

---

### Post by Dedoimedo on 2007-06-11
Hello,

I'm using both, as I like both.

My results are:

Ubuntu is gentler, more community oriented, softer.
SUSE is rough, a bit cold, but more professional.

Ubuntu has a bit more compatibility and stability problems with various programs.
SUSE, having a much larger default pool of programs, is better tailored but less friendly.

Synaptic is far, far friendlier than YaST / ZENWorks.

SUSE has better internal affinity for graphic drivers.
SUSE has a higher level of tweakability but is more difficult to setup.

Overall, both are superb, roughly equal in terms of performance.

Dedoimedo

---

### Post by ukripper on 2007-06-11
> **Dedoimedo said:**
> Hello,

I'm using both, as I like both.

My results are:

Ubuntu is gentler, more community oriented, softer.
SUSE is rough, a bit cold, but more professional.

Ubuntu has a bit more compatibility and stability problems with various programs.
SUSE, having a much larger default pool of programs, is better tailored but less friendly.

Synaptic is far, far friendlier than YaST / ZENWorks.

SUSE has better internal affinity for graphic drivers.
SUSE has a higher level of tweakability but is more difficult to setup.

Overall, both are superb, roughly equal in terms of performance.

Dedoimedo


Stability problems??????? Please could you give us some instance of instability?

---

### Post by Dedoimedo on 2007-06-11
I had both Amarok and Beryl die on me in Ubuntu. But I resurrected them.
Plus some minor glitches here and there.
Dedoimedo

---

### Post by Nekiruhs on 2007-06-11
Most of the shell commands will be the same. The shell commands arn't done by the operating system, its done by the BASH interpreter (see my sig for a BASH joke). BASH is pretty standard on most modern POSIX compliant OSes. Many of the commands (cd, mv, cp, stat, locate, grep, find, cat. sudo, su, alias, function, etc.) will be the same, but some of the more tailored ones may not be. So if your not doing anything too advanced with the command line, that knowledge will apply to Ubuntu as well.

---

### Post by ThinkBuntu on 2007-06-11
P.S. Don't let politics or business concerns steer your decision about which free (as in cash) distro you select. The Novell deal is suspect, but unless you're developing for openSuSE, providing a ton of support and bug reports, or donating money, this doesn't need to be a real concern to you, as you'll know well that you're not contributing to any immoral practices.

---

### Post by Bullfrog245 on 2007-06-11
Thanks alot guys (or possibley gals).  my biggest problem so far has been installing programs.  Everywhere I look I can find how to install under Ubuntu, but I have to look harder to find how to install with openSUSE. This will probably change after I get used to the way things work.  I have, afterall, only been using Linux for 3 days.  You have no idea how much I wish I could use apt-get in SUSE ^_^

As for the command line, are the commands for mounting drives the same?  In SUSE it was
mount -t //host/folder /destionation/folder

Also, does samba work the same?  It took a while for me to set up a network with a windows computer, but I think I understand the process now.  In Ubuntu, does modifying the fstab file follow the same syntax as Ubuntu?  Sorry for the poor terminology, I'll learn the "linux" words for windows functions soon enough.  This probably isn't the best forum for these questions either...

*another side note*
Did anyone else get excited when checking their website statstics and seeing that a Linux computer had visited the site, and knowing that the computer was yours?

---

### Post by Dragonbite on 2007-08-29
I've been using openSuse for a little while now and I think there are a number of differences between Ubuntu and openSuse and that they could actually learn from each other (some).

**INITIAL LOOKS**

openSuse appears to me a bit more professionally polished overall. 
[LIST]
[*]don't know if part of it is the theme (font, windows, wallpaper) they use but it looks slicker and more "professional" (I prefer green over brown, but it seems their wallpaper choices span more colors)
[*]Yast centralizes managing almost the entire system (similar to Windows Control Panel, and Administrative Tools sub folder)
[*]KDE and KDE apps appear more integrated for a seemless feel.
[*]It takes a bit of getting used to it but their modified Main Menu (K Menu) is a little slicker than the base KDE.
[*]Firefox uses the Firefox icon  (not sure of Thunderbird, I went with KMail)
[/LIST]

Ubuntu gets you started easily and quickly
[LIST]
[*]Easy means to get proprietary graphics drivers
[*]Clean layout which is easy to get used to
[*]Good initial selection of applications
[/LIST]

Ubuntu, while it does look good please don't get me wrong, but it doesn't seem to have the "spit and polished" or "professional" feel that openSuse does.  I see openSuse as looking like what a non-Linux user would consider an operating system, while Ubuntu has more of a piecemeal look.

_DISCLAIMER: _I may say different things if I ran openSuse under Gnome.  The issue may not be so much Ubuntu vs openSuse as it is KDE vs  Gnome.

**UNDER SKIN-DEEP**

Once you get past initial looks, though, Ubuntu includes a number of user-friendly aspects that openSuse can take some notes from.

openSuse also lacks in some very user-friendly aspects
[LIST]
[*]Yast does not include any of the repositories pre-listed. When you are done installing you are left with the CDs/DVD as a repository only.  You have to look online, at their wiki to find out how to add repositories and then what address to manually add
[*]Yast crashed when trying to update all of my repositories even though I set every one of them to not refresh (since I'm on dial-up). After the crash I was left with 1 repository and my CDs/DVD again.
[/LIST]

Ubuntu, in comparison, 
[LIST]
[*]Includes the necessary repositories automatically so right after install you can update everything (handy if you are installing a couple versions old)
[*]Easy means to install proprietary drivers (like Graphics) with the system auto-checking what you have for hardware
[*]Quickly get up-and-running without going through lists of lists of applicatons.
[*]Hides icons for applications you are not authorized to access (not sure if openSuse does something like this or not). For example when my kids goes into the System/Administration menu, they see very few icons while I get the full list.
[/LIST]

With both of them, they do make it easier to run Linux as a desktop between drivers/hardware recognition, most operations can be done with a GUI of some sort (minimal to no command line required) and their dial-up support is lacking somewhat.

**IT'S THE COMMUNITY**

You hear and read about it that the Ubuntu community is a big asset of Ubuntu.  It's true.

FORUMS:

Ubuntu has this forum which is a great source of information on any subject (Linux, technical and otherwise) and the posters here are really good about not throwing around a lot of attitude (I'm guilty of once-in-a-while) or ignoring/berating anybody. I have fun reading the Cafe' for just about any offbeat subject, but I also watch many of the others to try and help (if I am able to).

Now I have only found the openSuse forum(s) to be plesant but I have only really seen 2 of them.  While maybe they could focus on different levels of technical ability, they aren't that organized. So to answer your question you have multiple forums to search through and then when you want to ask.. do you ask in one or all of them (since so many people are in multiple forums)?  What happens if your favorite username is taken in one but not the other?

WIKI:

The Ubuntu Wiki are well organized, detailed and easy to search through for what you are looking to do.  Also, being a member I am able to make any changes if I find errors or alternative means (haven't yet.. but it's possible).

The openSusse Wiki just doesn't seem that way plus you have the "official" one (on opensuse.org) and then there is the (unofficial) wiki associated with one of the forums.  Neither of them have fully impressed me, but the one thing I like is they use more visuals than I usually find in the Ubuntu wiki's (I'm a visual guy, in case you haven't noticed yet ;) )

I'm not sure, though, what I'd have to do to be able to modify the Wiki's yet so I also cannot comment on the Wiki coding.

LOCO TEAMS:

Ubuntu has them, openSuse doesn't. 'nuff said :lolflag:

**OK, TIME TO GO BACK TO WORK**

So in summary, it seems openSuse is more sporadic and spread out while Ubuntu is centralized and well thought out.

This difference (unified vs fragmented) also applies to the repositories available which is both good and bad.  I'm not touching the whole RPM vs DEB argument because as long as I can download and install my programs they could be coming in as XYZ files for all I care.
[LIST]
[*]The bad part is knowing which repositories you want to use in openSuse and the conflicts that can occur (maybe they need to be able to prioritize the repositories?).
[*]The good part, though, is that certain projects (Mono, KDE, VLC, etc.) manage the repositories themselves sometimes and so stable upgrades make it into the repositories quickly instead of waiting for a single group of packagers to go through testing new versions before putting them into the repositories.
[/LIST]

Both distros are good and they focus and excel in different matters very nicely. Like I said, a blend of the two would be idea (at least for me :) ); openSuse's eyeball interface with Ubuntu's attention to detail and underpinnings (not sure about the DEB vs RPM yet though).

---

### Post by viciouslime on 2007-08-29
I think one important thing is also whether you prefer gnome of kde, suse's implementation of kde is far far far superior to kubuntu (the version of ubuntu that uses kde). Gnome is about equally well implemented in opensuse as it is in ubuntu, but ubuntu's package management, the massive selection of packages (many more than opensuse) and the community definitely cause me to pick ubuntu over opensuse any day.

The philosophy driving ubuntu is also a great plus!

---

