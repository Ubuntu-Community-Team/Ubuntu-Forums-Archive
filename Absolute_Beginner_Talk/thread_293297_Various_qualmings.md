---
title: "Various qualmings"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by freshofftheufo on 2006-11-05
Ok, hi. I recently converted to Ubuntu after realizing that everything I was using in XP was originally created for Linux anyways (i.e. Gimp, Firefox, music players, etc.) and I am fortunate enough to be able to waste a load of time on my computer while getting accustomed to the system.

I'll admit that I have a very XP-centric view of the way OSs should work (I've been with MS since old versions of DOS... I was like 6 years old), but I'm having trouble understanding the logic of how a few things work in the GNU/Linux and Ubuntu worlds.

First of all, the problems that I am immediately facing:

My first goal with a new comp is usually to get the A/V functionality up and running, so after figuring out that Rhythmbox and Totem weren't for me, I've been looking for alternatives. I used XMPlayer and QMP in XP, but I wasn't really satisfied with either of those (XMP has weak music library support and customizability, and recent QMP builds crashed a lot on my computer), so I'm trying out a bunch of others.

Of course, everybody has their own needs, but I can't really figure out how Ubuntu handles file extensions. I'm used to the whole "programs go in "program files" on drive x and are executed from the .exe file, music files go into your arbitrary customized space (in my case on a dedicated partition) and have extensions like .mp3 and .ogg, and those .mp3 files are linked to those .exe files by going into the preferences and clicking "preserve file associations" thing, but I'm having trouble grasping this concept in Linux.

_Where am I supposed to be looking for my installed programs, or how can I predict where they will end up?_ _How is the filesystem arranged in Ubuntu?_ _Do I always have to wade through folders filled with hundreds of other folders?_ It all seems like a big mess to me, one who never has folders with more than 20 files, unless they are all of the same or related file types.

_Is there a tool for handling file associations easily?_

Also, though I have a fair amount of HD space, I intend on filling it up soon with media unrelated to the OS, so while I understand Ubuntu comes packaged with a plethora of useful and reliable tools, programs, and media, I'm going to need to be getting rid of a lot of it to free up space. I will never be using PalmOS, nor Remote Desktop, among many other utilities, but _will I run into any troubles if I try uninstalling them?_ _Are program dependencies difficult to predict/work around?_

Now a question or two of a little deeper nature... and I admit I really shouldn't be asking this at such an early stage, with such an elementary understanding of Ubuntu, but I can't help but wondering. Why are Linux users happy with the way installing works in Linux? Do they not wish to be able to download a single automatically extracting file that knows how to install itself correctly, and does so? If they want more customizability, do they not want that same system to be just a little bit more flexible, instead of putting the responsibility entirely in the hands of the user? I understand the need for some users to have very high levels of control over the workings of their programs, so I don't mind huge confusing dialogs when browsing through a programs preferences, but I don't understand what necessitates everything else to be so involved. There are benefits to streamlined OSs like MacOSX (which I have never used, and never will) that I don't think are unattainable even with a very complex and customizable system. Are Linux users against such streamline-ism, or is there some other logic that I haven't grasped yet? I'm sorry if I sound critical, I really do like many things about Ubuntu, but I'm just hoping someone will come to the defense of Linux here and set me straight.

Lastly (god this is long, so sorry), the default System Monitor consistently takes up about 10% CPU time and 4 mibs on my laptop (it's shitty, I push it to the max), which basically makes it useless to me because that distorts the CPU figures for all other applications. Are there any other system monitoring applications similar, that have at least as much functionality as the XP equivalent without being such a system hog (on my poor little lappie)?

Thanks to anyone patient enough to read this whole thing. I've underlined the important parts so you can skip over the rest if you like.

---

### Post by hegenious on 2006-11-05
> Lastly (god this is long, so sorry), the default System Monitor consistently takes up about 10% CPU time and 4 mibs on my laptop (it's shitty, I push it to the max), which basically makes it useless to me because that distorts the CPU figures for all other applications. Are there any other system monitoring applications similar, that have at least as much functionality as the XP equivalent without being such a system hog (on my poor little lappie)?

Thanks to anyone patient enough to read this whole thing. I've underlined the important parts so you can skip over the rest if you like.

type "top" in a terminal window, it is a non-graphical task-viewer, 1,2MB on my system.

there is no such thing as file associations through filename extensions in Linux.

however, there is a feature similar to "open with..." just right-click the file and choose properties. there you'll find a tab "open with" 
also see this thread: [http://linuxfud.wordpress.com/2006/09/03/ubuntu-linux-file-associations/](http://linuxfud.wordpress.com/2006/09/03/ubuntu-linux-file-associations/)

---

### Post by Bartender on 2006-11-05
I've read several comments on these forums from guys who are obviously competent with their Linux machines that they don't know what 99% of the files do.  All you need to worry about is your home folder, unless you need to chase down something more obscure, like a ppp dialer file or some such.
Try to avoid translating everything into what it might be in Windows.  You'll make progress faster that way.
EDIT: I found the same thing with my old PIII 450.  System Monitor bumps CPU usage about about 10% so I don't worry about it anymore.  Top works fine to get a feel for what's going on.

---

### Post by Portable_Jim on 2006-11-05
> 
Now a question or two of a little deeper nature... and I admit I really shouldn't be asking this at such an early stage, with such an elementary understanding of Ubuntu, but I can't help but wondering. Why are Linux users happy with the way installing works in Linux? Do they not wish to be able to download a single automatically extracting file that knows how to install itself correctly, and does so? If they want more customizability, do they not want that same system to be just a little bit more flexible, instead of putting the responsibility entirely in the hands of the user? I understand the need for some users to have very high levels of control over the workings of their programs, so I don't mind huge confusing dialogs when browsing through a programs preferences, but I don't understand what necessitates everything else to be so involved. There are benefits to streamlined OSs like MacOSX (which I have never used, and never will) that I don't think are unattainable even with a very complex and customizable system. Are Linux users against such streamline-ism, or is there some other logic that I haven't grasped yet? I'm sorry if I sound critical, I really do like many things about Ubuntu, but I'm just hoping someone will come to the defense of Linux here and set me straight.

Symaptic is a centralised place to install files. You can search it for files, then, (downloding and) installation is only 2 or 3 clicks away (provided you have the internet). So you can install a program without opeining your web browser. 
For example, to install Skype:
1. Open Synaptic Package Manager
2. Click search.
3. Sype in "Skype"
4. Click on the box in the first column in the line where it says "Skype"
5. Click "Apply"
6. Click "Apply" in the dialog that comes up.
7. Wait
8. GO to Applications -> Internet -> Skype

and you are running Skype.

---

### Post by Bartender on 2006-11-05
Good point, P_Jim.  The first time I watched Synaptic do its thing my jaw dropped.  There's lots of stuff I don't understand about Linux, but already pretty sure I don't want it to become Windows. 
Besides, it's pointless to criticize some facet of Linux as it is today.  It's moving too fast.  
Make a folder in your "home" folder called "Music" and start piling your .ogg files in there.  That's what The Official Ubuntu Book says to do.  You can make folders for each band, or each album, or however you want to do it.
You wanna talk about simple?  I helped a friend Ubuntu-fy his old Dell a few weeks back.  I brought a spare hard drive with me that had Ubuntu already on it from when it was residing in a different PC.  By mistake I booted his computer to the HDD instead of the CD.  It started up and ran fine.  You know what would happen if you tried that with Windows, don't you?   
He bought a Belkin USB PCI card to give him 4 more USB ports, and a network card.  Both came with drivers that woulda been needed with Windows.  With Ubuntu, we plugged the cards in, turned it back on, BAM both of them worked.  HAH!  Try that in Windows!

---

### Post by freshofftheufo on 2006-11-05
Thanks for the replies guys.

> type "top" in a terminal window, it is a non-graphical task-viewer, 1,2MB on my system.

there is no such thing as file associations through filename extensions in Linux.

however, there is a feature similar to "open with..." just right-click the file and choose properties. there you'll find a tab "open with"
also see this thread: [http://linuxfud.wordpress.com/2006/0...-associations/](http://linuxfud.wordpress.com/2006/0...-associations/)

I tried top, but the thing is, it's running through terminal, so it's actually taking closer to 20mibs, though the CPU usage is much lower, so it's more useful for me at the moment.

And thanks for that link, makes it a little bit easier to handle my file types, and I don't mind setting them up manually. I still don't know where to find the core programs though... I mean if I want to add VLC media player to the list of options, where would I find it on my file system? 

> I've read several comments on these forums from guys who are obviously competent with their Linux machines that they don't know what 99% of the files do. All you need to worry about is your home folder, unless you need to chase down something more obscure, like a ppp dialer file or some such.

So I should just... let my hard-drive get smaller and smaller, with no control over the amount of junk files that are left over in areas not related to my user area? The truth is, I'm running a 4 year old Thinkpad P2, 128 RAM and a 10 gig harddrive. I'm not planning on doing anything hardcore with it this year other than music and Gimp editing, but I do need to streamline this system somehow; I was running XP with a 600MB OS partition, and though I know that's not going to be possible with Ubuntu, I at least want to get rid of all the unnecessary stuff.

> Symaptic is a centralised place to install files. You can search it for files, then, (downloding and) installation is only 2 or 3 clicks away (provided you have the internet). So you can install a program without opeining your web browser.
For example, to install Skype:
1. Open Synaptic Package Manager
2. Click search.
3. Sype in "Skype"
4. Click on the box in the first column in the line where it says "Skype"
5. Click "Apply"
6. Click "Apply" in the dialog that comes up.
7. Wait
8. GO to Applications -> Internet -> Skype

and you are running Skype.

Yes, I've been using Synaptic and I used Automatix to get me started out. I think it's a great idea to have one central utility that can gather all installs from the internet and handle it automatically (it makes it easier to tell someone else to install a program, you don't have to give them a trusted link to the file), but I still have problems with it. Synaptic doesn't list all available programs, and so if you just want to install something that your friend made up it's not going to be available. It also took me 10 minutes to complete a search for "VLC" while my harddrive grinded and an additional 10 minutes to actually complete the installation after downloading the files, compared to a typical 2 minute installation (on a low-end system) with a typical XP installer utility. I can't pretend to know why it's so complex, and I've heard that this "easy way out" is only available for devian systems... so why do other Linux users go through the steps? Do they actually like it that way?

---

### Post by Chayak on 2006-11-05
Files in linux are grouped by function just like unix systems.  That and everything in a linux system is a file, even devices.  The structure is explained here [http://www.tuxfiles.org/linuxhelp/linuxdir.html]("http://www.tuxfiles.org/linuxhelp/linuxdir.html")

---

### Post by hegenious on 2006-11-05
to locate programs in your filesystem, you can use the "whereis" command.

$ whereis vlc
vlc: /usr/bin/vlc /usr/lib/vlc /usr/bin/X11/vlc /usr/share/vlc /usr/share/man/man1/vlc.1.gz

$ whereis whereis
whereis: /usr/bin/whereis /usr/bin/X11/whereis /usr/share/man/man1/whereis.1.gz

:p

and to find out which one is used, use the "which" command.

$ which vlc
/usr/bin/vlc

$ which firefox
/usr/bin/firefox

---

### Post by zek725 on 2006-11-05
> **freshofftheufo said:**
> My first goal with a new comp is usually to get the A/V functionality up and running, so after figuring out that Rhythmbox and Totem weren't for me, I've been looking for alternatives. I used XMPlayer and QMP in XP, but I wasn't really satisfied with either of those (XMP has weak music library support and customizability, and recent QMP builds crashed a lot on my computer), so I'm trying out a bunch of others.

Try **gxine**.

> **freshofftheufo said:**
> I will never be using PalmOS, nor Remote Desktop, among many other utilities, but _will I run into any troubles if I try uninstalling them?_ 
Nope.

---

### Post by Bartender on 2006-11-06
With 128 MB RAM you'd probly be much happier running Xubuntu.  You can download only what you need via Synaptic - Search "Xubuntu-desktop".  I think (not sure) you have to enable some of the extra repositories.  Although I haven't pursued it, have read some posts that described how to clean up the archives or somethign like that...when you download/install to update something thru Synaptic it keeps a copy of the original programs in some folder.  After a while the folder gets out of hand.

---

### Post by Bartender on 2006-11-06
According to Official Ubuntu Book downloaded packages are stored in  /var/cache/apt/archives.
```
sudo apt-get clean
``` empties out this cache

---

