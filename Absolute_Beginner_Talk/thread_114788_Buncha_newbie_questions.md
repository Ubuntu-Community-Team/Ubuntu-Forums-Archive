---
title: "Buncha newbie questions"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by Quinch on 2006-01-09
Well, fresh from Win98SE and new to Ubuntu.... 'ello.

Anyway, I have a few problems. Well, chances are I have a truckload, but these are the more prominent ones.

1} Croatian user. Croatian keyboard. Croatian characters. English layout when I type. How do I change it to what I want? I went to keyboard/preferences/layout and set it to Croatian, but nothing's changed. What am I doing wrong?

2} Taskbar. Windows. Is there a way to have the open windows listed on my taskbar a la MSWindows, or some other way of switching windows without having to constantly alt-tab between them?

3} How do I install software? That's a biggie. 

4} How can I rearrange mz hard drives in the file manager? I've three hard drives with four partitions, and like to put the more commonly used one on top, rather than the one with W98 installation. 

Regards and thanks in advance,

Quinch

---

### Post by Arktis on 2006-01-09
1.)  I'm an en_US user, so I don't need to switch layouts and wouldn't know.  Sorry. :???: :( 

2.)  There is a panel applet which does this.  In english, the instructions to make use of it are like this: Right-click the panel > Add to Panel > scroll down and select "Window List".  Position it wherever you like.

3.)  For most software, you'll use synaptic.  You can also use apt-get from the command line.  Synaptec is in the system > Administration menu.

4.) I don't know how they are ordered... *checks fstab*
Nope, no clue.  :rolleyes:  maybe someone else can help.

---

### Post by TikkiRo on 2006-01-09
[COLOR="Purple"]On #4 - all I can think of if FStab doesn't sort it for you, is to use the desktop ordering of icons perhaps - you know the "sort by" and then rename your drives so that they can be sorted by name - I did this and it works quite well - takes a bit of working tho when you've got 10 partitions like me!!!  

On #3 if you're using the Breezy version of Ubuntu which is the latest one, then you can also put another program called Automatix to good use - if you do a search on the forums here you'll find all the posts relating to that one - it takes a bit of getting used to as well initially but an easier interface than Synaptic and seems to install stuff much easier too :)[/COLOR]

---

### Post by Arktis on 2006-01-09
Automatix is bad!  Naughty.  Evil.  No!!!  :rolleyes:

---

### Post by Quinch on 2006-01-09
Alrighty, #2 is nailed down {funnily enough, I saw that same solution looking on the forum, but couldn't find it.... because I didn't notice the scroll bar on the side. Duh.} Thanks. 

#3} Arktis, thanks, but I should have been a bit more specific - it's more of a "okaz, I've downloaded the Mozilla installation onto my desktop, I've figured out that the Synaptic had something to do with software installations, but damn if I can figure out how to combine the two and the help file is as helpful as a barbecue on a raft."

#4} Where is Fstab, maybe I can take a look at it myself? I've managed to tweak Grub to rearrange the boot options, so it can't hurt to look it over. On a related note, does the File Manager have a search function, and if so, where do I find it?

Regards,

Quinch

---

### Post by Qrk on 2006-01-09
3) Synaptic doesn't act like an installer... it is much more. When you open up synaptic, you can double click on a program/package you want to install and then select "apply" It will automatically download and install the program and everything it depends on. 
But for synaptic to be truely useful you have to add the non-free/universe componate. Do that by selecting Settings-->Repositories.

4) fstab is in /etc

---

### Post by welsh_spud on 2006-01-09
For search you may be interested in the Beagle search tool. I think it's called 'best' in Synaptic.

Heres more info: [Beagle]("http://beaglewiki.org/Main_Page")

---

### Post by s6dalane on 2006-01-09
[QUOTE=Quinch]

1} Croatian user. Croatian keyboard. Croatian characters. English layout when I type. How do I change it to what I want? I went to keyboard/preferences/layout and set it to Croatian, but nothing's changed. What am I doing wrong?

Quinch[/QUOTE]

Open the terminal and type:
> sudo gedit /etc/X11/xorg.conf
Then change the the following line:
> Option		"XkbLayout"	"xx"
xx marks your country code (for me it is 'ee').

Then restart your computer and when a dialog box comes up press the button to use X settings.
Atleast that worked for me, hopefully for you too!

---

### Post by Arktis on 2006-01-09
[QUOTE=Quinch]

#3} Arktis, thanks, but I should have been a bit more specific - it's more of a "okaz, I've downloaded the Mozilla installation onto my desktop, I've figured out that the Synaptic had something to do with software installations, but damn if I can figure out how to combine the two and the help file is as helpful as a barbecue on a raft."

#4} Where is Fstab, maybe I can take a look at it myself? I've managed to tweak Grub to rearrange the boot options, so it can't hurt to look it over. On a related note, does the File Manager have a search function, and if so, where do I find it?

Regards,

Quinch[/QUOTE]3.)  Synaptic isn't going to help you with stuff you downloaded with your web browser.  Synaptic connects to online software repositories, grabs software packages you request and installs them, and handles system updates in the same manner.  If you're looking for Firefox 1.5 install instructions, you can get them [here]("https://wiki.ubuntu.com/FirefoxNewVersion").  Firefox has not been backported into the software repositories for breezy because of reasons outlined in [this]("http://ubuntuforums.org/showpost.php?p=529570&postcount=1") post.

4.)  It's located at /etc/fstab.  ```
sudo gedit /etc/fstab
```Don't bother messing with it though; it's not going to help you re-order the drives list.  I checked it on my system and the order of my fstab vs the order of nautilus's drive list doesn't match.  Mine isn't in alphabetical order either... strange, no?  If you find a solution to this, I'd be interested.

Also, you can search for files using the command ***gnome-search-tool*** or launching it from the panel menu (Places > Search for Files).

---

### Post by Quinch on 2006-01-09
[QUOTE=s6dalane]Open the terminal and type:

Then change the the following line:

xx marks your country code (for me it is 'ee').

Then restart your computer and when a dialog box comes up press the button to use X settings.
Atleast that worked for me, hopefully for you too![/QUOTE]

Jackpot. Thanks, this was driving me nuts down the golf course.

Qrk and Arktis: Okay, wait, so how do I install applications that aren't in the repository? I.e. the downloaded ones?

---

### Post by etc on 2006-01-09
If you download a .deb package all you have to do is in a terminal
```
sudo dpkg -i packagename.deb
```
And it's installed.

If you're building from source (usually a .tar.gz archive), then USUALLY (not always, you might have to configure some stuff so read the README that comes with it) all you have to do is
```
./configure && make && sudo make install
```

But if you want to make a nice .deb from the source you should use checkinstall
```
sudo apt-get install checkinstall
./configure && make && sudo checkinstall
```
And checkinstall will make a .deb and install it for you

---

### Post by Arktis on 2006-01-09
I'm about to give you a lot of information.  It's not as complicated as I might make it sound.

If you downloaded a package (*.deb) then you can use dpkg from the command line.```
sudo dpkg -i packagename.deb
```

Here's where I get all long winded:

If you downloaded a tar.gz or similar archive, it's a source code tarball, and you need to compile it.  Not as hard as it sounds.  first you should install the build-essential package.```
sudo apt-get install build-essential
```The usuall commands (after extracting the archive and going to it's folder from the command line) to execute the proper scripts are **./configure**, then **make**, then **make install**.  Everything is done automaticly for you.  If you're missing anything you ned to compile, the configure script should alert you.  If you are, then it's probably a development package, so go ahead and use synaptic to search for it.  It takes some getting used to, but eventually, you'll get the hang of it.  Sometimes you may need to use google or clusty or some other search engine to figure out what package(s) you need.  But always be sure to get them from synaptec or apt-get.

Then you have to figure out what the name of the binary executable it installed was so that you can run the program... what makes things easier is to install a utility called checkinstall, and subsitute it for the make install command, like this: **./configure**, then **make**, then **checkinstall**.  It makes you a nice debian package and installs it for you.  Then later if you want to remove the program, you don't have to hang onto your source code just so you can execute the make uninstall command.  Many times, uninstall rules aren't included anyways and so you have to manually go hunting around your system.  Yuck!  With your checkinstall created package, all you have to do is either use sudo apt-get uninstall packagename or use synaptec to uninstall it.  Once it is installed, from synaptec you can get a package specific list of all the files installed by any particular package.  You can use that to find the name of the binary executable and therefore know what command to execute to run the program.  Then you can make yourself an applications menu entry for your newly installed program using smeg.  (Right-click the applications menu, then click "Edit Menus")

Using checkinstall also has the benefit of giving you a nice package that you can put wherever you keep your backup files, for later reinstallation should you ever do a fresh install again.  But beware, checkinstall does not handle package dependancies.  You'll have to manually satisfy those but only if you ever reinstall a checkinstall package onto a fresh installed copy of breezy where those dependancies have not already been met.

Once again, it's not as complicated as I might make it sound.

**Edit:** Aw geeze, I took all the time to write that out and somebody beat me to it.  :razz:

---

### Post by aysiu on 2006-01-09
[QUOTE=Arktis]
**Edit:** Aw geeze, I took all the time to write that out and somebody beat me to it.  :razz:[/QUOTE] Next time, save yourself some typing and just link to the second link in my sig.

---

### Post by jonathanm on 2006-01-09
checked the order of my partitions and mine seem to go:
from top to bottom:
hdb1
hda1
hda5
hda7
hda10
that says to me that they go alphabetically upwards and numerically downwards.  Soz, don't know how to change them tho

---

### Post by aysiu on 2006-01-09
Do they appear alphabetically in the file manager? I'm confused as to what you're trying to change exactly... you open Nautilus and see your partitions somewhere...?

---

### Post by Arktis on 2006-01-09
In the places menu, the tree on the left pane in nautilus, and the (normal) file open dialogue.  All three of these share the same order.  For mine, they aren't displayed alphabeticly or in the order in which they appear in fstab.

And yeah, next time I'll just link to that page from your sig.  Nice one. ;)

---

### Post by lindejos on 2006-01-09
RE: Qrk and Arktis: Okay, wait, so how do I install applications that aren't in the repository? I.e. the downloaded ones?

This depends what kind of file you have.  So far I have sort of got the hang of tarballs, bzip2's, .debs , and auto-installing files.

If it's a tarball you can use:

tar -xzvf /path/of/file/filename.tar.gz

to get it to unroll.  Now you'll have a directory which will usually have a readme file in it that will tell you what to do next.

I've also seen a lot of filename.something.bz2 packages.  These are explaned [here]("http://www.linuxheadquarters.com/howto/basic/bz2.shtml")

if you have something that ends in .deb (a Debian package) you can [unpackage]("http://linuxhelp.blogspot.com/2005/12/concise-apt-get-dpkg-primer-for-new.html") it with:
dpkg -i /path/of/file/filename.deb

Sometimes, if you get an install package that is "auto opening" like the debian distro of java that I got last night you have to just type the filename into the command line.

/path/of/file/filname.bin

or you can browse to the directory that the file is in, and run it there:

cd /path/of/file
./filename.bin

I'm still pretty new to this myself so if there is anything here that is wrong, somebody correct me before I send anyone on a wild goose chase. Specifically I'm not sure which of these commands needs to be called by root.  

Question (sorry if this doesn't really belong in this thread):

If apt-get is supposed to get [all the dependencies]("http://www.psychocats.net/linux/installingsoftware.php") then if you find that you can't install a package by using apt-get is that because you don't have the right repositories?  I've had to "apt-get backwards" a few times so far.

---

### Post by TikkiRo on 2006-01-10
> Qrk and Arktis: Okay, wait, so how do I install applications that aren't in the repository? I.e. the downloaded ones?

[COLOR="Purple"][FONT="Comic Sans MS"][SIZE="3"]I was totally stuck at the outset of using Linux to do this very thing - hadn't a clue about installing tar files for starters - but found some excellent help at Tuxfiles - [http://www.tuxfiles.org/linuxhelp/software.html]("http://www.tuxfiles.org/linuxhelp/software.html")

Still using it regularly to install quite a few files, but still run into the odd problem which has usually been sorted by just hunting through directories to locate exactly where programs are.  One tip you may find useful is that when it comes to typing in the install code (that tar xvzf bit) and it wants the package name/location - I usually try doing a right click on the downloaded file in Firefox downloads and copying the final download directory location - then pasting that in watching out to ensure there are / in the right place.  So one e.g. might be tar xvzf /home/username/Torchlight_0_2_0_tar.gz.  Not sure if you need to stick sudo in front of that or not but think it will tell you if you do.  For whatever reason I never had any success with the next bits of that command - the configure and make install - the program seemed to install just by running the tar command itself.  No doubt I've missed something somewhere aliong the way on it, but it's worked that way for me at least.  

If you get an error on the directory as I often did, you could try relocating the package into an easier directory to get into - I found it almost impossible to use the My Downloads directory in the tar command, so pulled each file into my Home directory instead.   Hopefully tho the info on the tuxfiles site will be as useful for you as it's been for me (I'm only into my 2nd week and have installed everything I could lay my hands on now using that info plus the awesome help given on the forums here!).  Just keep asking - that's my best advice.  I'd a lot of very simple problems that were solved by just putting up the query and when I saw the answer realised I knew it but had just missed one slash or something.  Good luck!  :) [/SIZE][/FONT][/COLOR]

---

### Post by aysiu on 2006-01-10
[QUOTE=TikkiRo][COLOR="Purple"][FONT="Comic Sans MS"][SIZE="3"]I was totally stuck at the outset of using Linux to do this very thing - hadn't a clue about installing tar files for starters - but found some excellent help at Tuxfiles - [http://www.tuxfiles.org/linuxhelp/software.html]("http://www.tuxfiles.org/linuxhelp/software.html")[/quote] Or you could see the second link of my sig, which is a set of instructions tailored specifically for installing software *in Ubuntu*.

> 
One tip you may find useful is that when it comes to typing in the install code (that tar xvzf bit) and it wants the package name/location - I usually try doing a right click on the downloaded file in Firefox downloads and copying the final download directory location - then pasting that in watching out to ensure there are / in the right place. You could also un-tar the .tar.gz by simply double-clicking it and then clicking "extract."

---

### Post by TikkiRo on 2006-01-10
[QUOTE=aysiu] You could also un-tar the .tar.gz by simply double-clicking it and then clicking "extract."[/QUOTE]

[COLOR="Purple"][FONT="Comic Sans MS"][SIZE="3"]Ah but that was where I seemed to always come to a sticky end.  Had no problem doing that, but for some reason the program never appeared anywhere, and half the time I couldn't figure out how to actually get it to run - always ran into errors and found it hard to know what was what - I know, newbie blues - but there you go - that's really why I ended up going for that other method.  Great tho that there are different ways to get to the solution in the end tho.  Thanks for those links - kept forgetting to check on them, and just wish I'd had them last week when I was at the outset myself of all these issues :D [/SIZE][/FONT][/COLOR]

---

