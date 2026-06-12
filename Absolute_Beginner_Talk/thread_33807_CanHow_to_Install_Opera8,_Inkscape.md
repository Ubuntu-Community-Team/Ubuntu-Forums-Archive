---
title: "Can?How? to Install Opera8, Inkscape"
date: 2005-05-12
forum: Absolute Beginner Talk
---

### Post by SirCoistrel on 2005-05-12
[FONT=Garamond]I publish websites in SVG format and thus make use of Inkscape.  In addition I just love Opera8 which is cross-platform and lists Ubuntu as one of its optional homes.  I am an experienced newbie, meaning I know Win XP and DOS but almost nothing about Linux.  No problems whatsoever were encountered in dual booting, but now I need Help!!!! in setting up the file manager tree and downloading and installing Inkscape and Opera....if this can be done.  Cheers, SirCoistrel aka Muzz[/FONT]

---

### Post by Arjen on 2005-05-12
I don't know anything about Inkscape, so I can't help you there.
However, in the case of Opera I can help. In your other post I read that you already downloaded the Ubuntu version. This should be a file with the .deb extension.
The easiest way to install this is from a terminal. You first go to the directory where you downloaded the file to and then type the following:
```
sudo dpkg -i filename
```
Where you replace filename with the actual filename of the downloaded file. This is the way you can install all .deb files, so if Inkscape provides one as well you could use this to install it.

After this you start Opera with the command opera. It doesn't appear in the menu, so you'll have to make a launcher for it on your desktop.

---

### Post by bored2k on 2005-05-12
This is quite simple, but first, we need to enable a few things.

After performing what's said [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) (it's really easy, just copy/paste), go to [in your panel] System > Admin > Synaptic. -- If you find this hard, there's another way, open Synaptic Package Manager > Settings > Repositories > In its settings make it show unselected repositories; after they are displayed, checkmark all of them and click ok then reload. Then continue to the next step --
There search for Inkscape, right click > install > Apply. That's INkscape :D.

For opera, open your web browser and paste
[http://www.opera.com/download/get.pl?id=26666&location=15&nothanks=yes&sub=marine](http://www.opera.com/download/get.pl?id=26666&location=15&nothanks=yes&sub=marine)

After you save it, you need to open up a terminal window.
First, watch where the file is being downloaded. To make things easier, move the downloaded file to your HOME directory.

In the terminal paste this commands:
```

sudo dpkg -i opera_8.0-20050415.5-shared-qt_en_sarge_i386.deb; sudo apt-get -f install
```

It will ask for your password, and then it will get installed.

---

### Post by 23meg on 2005-05-12
in fact both are in the repositories. you can just type "sudo apt-get install opera inkscape" to install them if you have the universe repository enabled.

---

### Post by bored2k on 2005-05-12
[QUOTE=23meg]in fact both are in the repositories. you can just type "sudo apt-get install opera inkscape" to install them if you have the universe repository enabled.[/QUOTE]
 I didn't even know opera was in universe. So yes it's just an apt-get away.. nice.

---

### Post by SirCoistrel on 2005-05-12
Opera sings like a siren.  You don't stand a chance.  You shall be wooed and crawl into the chamber on your knees to view the wonder of the universe.

And after you have been let go, SVG shall enter your life and you shall forget that you ever heard of Flash.  SVG sits under XML as an official (good and bad) standard for vector based graphics.  It is good. Very, very good.

Back to business. Please take me by the hand and lead  me down the garden path.  I have lived with DOS for 15 years and now on an alien though wonderful planet.  How PRECISELY do I enable the universe repositrie?

Thanks for the support.  I am truly delighted to be here.  Muzz aka SirCoistrel

---

### Post by bored2k on 2005-05-12
[QUOTE=SirCoistrel]Opera sings like a siren.  You don't stand a chance.  You shall be wooed and crawl into the chamber on your knees to view the wonder of the universe.

And after you have been let go, SVG shall enter your life and you shall forget that you ever heard of Flash.  SVG sits under XML as an official (good and bad) standard for vector based graphics.  It is good. Very, very good.

Back to business. Please take me by the hand and lead  me down the garden path.  I have lived with DOS for 15 years and now on an alien though wonderful planet.  How PRECISELY do I enable the universe repositrie?

Thanks for the support.  I am truly delighted to be here.  Muzz aka SirCoistrel[/QUOTE]
 Wow. Jdodson's got a poetic competition :-|

a) Upper panel > admin > synaptic > settings > repositories > settings > show disabled sources > ok > add > checkmark every single window from every single panel [hoary / security / updates ] > ok > reload > there you go.

or

b) [http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by SirCoistrel on 2005-05-12
Got Inkscape though 2 versions out of date (quit complaining) but Opera 8 was not to be found.  You can only fly on a magic carpet so far.  Thus I shall try poke around Ubuntu Linux and start learning the true fundamentals.

I will say this, and with much sincereity.  After my recent experiences in the alternate universe, it is an utter joy to have discovered Ubuntu.  You folk are a class act all the way.  I'll go further: you embody the principles which I have long assumed the kernal was designed to serve --- about which I shalll say nothing further.  Don't change your current approach to this endeavour one iota.  Congratulations on an effort that derserves a standing applause.   ,,,,,Too thick?  Not a chance!!!  Cheers, Muzz

---

### Post by bored2k on 2005-05-12
[QUOTE=SirCoistrel]Got Inkscape though 2 versions out of date (quit complaining) but Opera 8 was not to be found.  You can only fly on a magic carpet so far.  Thus I shall try poke around Ubuntu Linux and start learning the true fundamentals.

I will say this, and with much sincereity.  After my recent experiences in the alternate universe, it is an utter joy to have discovered Ubuntu.  You folk are a class act all the way.  I'll go further: you embody the principles which I have long assumed the kernal was designed to serve --- about which I shalll say nothing further.  Don't change your current approach to this endeavour one iota.  Congratulations on an effort that derserves a standing applause.   ,,,,,Too thick?  Not a chance!!!  Cheers, Muzz[/QUOTE]
 No more poems? :-(

---

### Post by 23meg on 2005-05-12
maybe you'll get opera 8 if you enable the *multiverse* repository as well... maybe...

---

### Post by bored2k on 2005-05-12
I did a search for opera, it wasn't there. Just download it from opera's website.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=opera&searchon=names&subword=1&version=hoary&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=opera&searchon=names&subword=1&version=hoary&release=all)

---

### Post by SirCoistrel on 2005-05-12
As is obvious, I am much given to taking ten lines to say even the simplest thing.  Yes, there shall be more songs from the sirens:  after all, "A little learning is a dangerous thing; Drink deep or taste not the Pierian spring."

I shall repeat the whole procedure and see if I missed something with regard to opera.  I have nothing whatsoever against Mozilla, but Opera offers the only genuine full screen viewing in the business.  As for SVG, Mozilla have just starting offering it in their nightly builds and it should reach version 1.1 in Native Format.  Opera already offers Native SVG viewing as of version 8.  SVG  is now positioned to go mainstream; and murphy are there a pile of folk working overtime on Inkscape.  Ulysses would have fallen, and hard.   Cheers, Muzz

---

### Post by bored2k on 2005-05-12
[QUOTE=SirCoistrel]As is obvious, I am much given to taking ten lines to say even the simplest thing.  Yes, there shall be more songs from the sirens:  after all, "A little learning is a dangerous thing; Drink deep or taste not the Pierian spring."

I shall repeat the whole procedure and see if I missed something with regard to opera.  I have nothing whatsoever against Mozilla, but Opera offers the only genuine full screen viewing in the business.  As for SVG, Mozilla have just starting offering it in their nightly builds and it should reach version 1.1 in Native Format.  Opera already offers Native SVG viewing as of version 8.  SVG  is now positioned to go mainstream; and murphy are there a pile of folk working overtime on Inkscape.  Ulysses would have fallen, and hard.   Cheers, Muzz[/QUOTE]
 You should post more often. Your words are really relaxing :-o..

---

### Post by SirCoistrel on 2005-05-12
Hmmm,   Ambiguous, but I'll go with the "tone it down" angle.

---

### Post by SirCoistrel on 2005-05-12
Forums historically were a place for discussion and debate.  Now they are the domain of the one line reply.  I bow out gracefully.   Pardon me for my enthusiasm.  Muzz

---

### Post by SirCoistrel on 2005-05-12
I shall re-work it Meg, thanks.

---

### Post by SirCoistrel on 2005-05-12
[QUOTE=23meg]in fact both are in the repositories. you can just type "sudo apt-get install opera inkscape" to install them if you have the universe repository enabled.[/QUOTE]
 > you can just type "sudo apt-get install opera inkscape" to install them

It may be a trivial thing Meg, but WHERE do you type that?  At no time has a field opened up where it was clear that instructions could be inserted.

---

### Post by 23meg on 2005-05-12
[QUOTE=SirCoistrel]It may be a trivial thing Meg, but WHERE do you type that?  At no time has a field opened up where it was clear that instructions could be inserted.[/QUOTE]

a field shall only be opened up should you request one to be opened up, brother. to open a such a field as one where you may insert instructions, you should click in the correct order "applications / system tools / terminal".

[QUOTE=bored2k]I did a search for opera, it wasn't there. Just download it from opera's website.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=opera&searchon=names&subword=1&version=hoary&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=opera&searchon=names&subword=1&version=hoary&release=all)[/QUOTE]

weird; i'm sure i installed it from the repositories, and i just checked synaptic to see if it's still there, and it is. by the way, is there a way of learning which repository a particular package is in within synaptic? or from the terminal?

---

### Post by SirCoistrel on 2005-05-12
[QUOTE=bored2k]I did a search for opera, it wasn't there. Just download it from opera's website.
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=opera&searchon=names&subword=1&version=hoary&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=opera&searchon=names&subword=1&version=hoary&release=all)[/QUOTE]
 I have already tried this twice.  It poses its own problems which take more than one line to describe.

---

### Post by bored2k on 2005-05-12
Complementing 23meg's post, below are some basic commands for the terminal window [or bash prompt]. Though the may look complicated and useless, they're not, so get used to these commands, specially "man".

--
*Getting Help
man ls : Manual for the ls command
whatis command : Description of command
apropos keyword : Search for Linux commands that match keyword

*APT
apt-cache search filename : searches for a file with that name or description
apt-cache show : displays information about a given file
apt-get update : updates its download database
apt-get upgrade : upgrades ..
apt-get dist-upgrade : system wide upgrade
apt-get clean : clean download cache

*Dealing with Compressed Files
.tar.gz : tar xvzf
.tar     : tar xfv
.bin     : chmod +x _.bin
         ./_.bin
.rpm    : alien -d _.rpm (.rpm to .deb)
.deb    : dpkg -i _.deb
.rar      : rar e

*Directories

-Listing
ls path : Show normal files
ls -l path : Long listing, with date, size and permisions
ls -a path:Show all files, including important .dot files that don't
otherwise show
ls path | more : Show listing one screen at a time

-Changing
cd {dirname} : There must be a space between
cd ~ : Go back to home directory
cd .. : Go back one directory

-Others
pwd : Show where you are as full path. Useful if you're lost or exploring
mkdir {dirname} : Creates a directory
rm -rf dirname : Remove all files and subdirs
rmdir dirname : Removes (only works if {dirname} is empty)

*Working With Files

-Copy a file or directory
cp oldfile newfile
cp -r old-directory new-directory : Recursive, copy directory and all subdirs

-Move (or rename) a file
mv oldname newname : Moving a file and renaming it are the same thing

-Find files on system
find filename : Works with wildcards
slocate filename : This searches a database, rather than the actual
directory tree, which makes it much faster than find

-Make an Alias
alias name='command' : For example: alias cdrom='mount -t iso9660
/dev/cdrom /cdrom', now you can mount your cdrom by just typing cdrom
(put the command in 'single quotes')
--

---

### Post by SirCoistrel on 2005-05-12
root@ubuntumuzzmarmot:/home/sircoistrel # sudo apt-get install opera inkscape
Reading package lists... Done
Building dependency tree... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate
root@ubuntumuzzmarmot:/home/sircoistrel #

That is the message I received.

---

### Post by bored2k on 2005-05-12
[QUOTE=SirCoistrel]I have already tried this twice.  It poses its own problems which take more than one line to describe.[/QUOTE]
 Post the problem here with no worries, we would know what to do.

-- Do not apt-get install opera

> For opera, open your web browser and paste
[http://www.opera.com/download/get.pl?id=26666&location=15&nothanks=yes&sub=marine](http://www.opera.com/download/get.pl?id=26666&location=15&nothanks=yes&sub=marine)

After you save it, you need to open up a terminal window.
First, watch where the file is being downloaded. To make things easier, move the downloaded file to your HOME directory.

In the terminal paste this commands:
```

sudo dpkg -i opera_8.0-20050415.5-shared-qt_en_sarge_i386.deb; sudo apt-get -f install
```

It will ask for your password, and then it will get installed.

---

### Post by Malicine on 2005-05-12
the manual and repository installs have both worked for me.
I did manual download and terminal install, I noticed it in synaptic after.
However, also being a noob... 
Should opera have an icon somewhere now? I cannot seem to find the installed program anywhere ](*,) 

great thread btw, covering a number of areas.


cancel that, just noticed the 'run app~' button and typed "opera", works sweet.
Imported all my bookmarks,contacts,setup etc from my win partition. \\:D/

---

### Post by bored2k on 2005-05-13
It should not have an icon. I had to make on myself in KDE [right click on panel > menu editor]. On gnome it is possible, but it isn't nearly as friendly as KDE.

---

### Post by SirCoistrel on 2005-05-13
Hi.  Sorry if I mistook something as an innuendo.  Onwards.

Now, from my perspective, though it doesn't carry much weight, the straightforward approach in order to get the most recent version of a program is the download.

I have downloaded both Opera 8 for Ubuntu in tar.gz and attempted to implement the most recent update of Mozilla.  Opera offers two variations on the the Ubuntu download.  Now I am (obviously) used to calling in a program to open an archived file.

But what I see are two options: "Open" from the File Menu .... which in both the case of Opera and Mozilla did indeed open a ton of files in, I believe, the tmp folder.  I looked for some sort of executable or setup file but nothing seemed to meet the criteria.  

Now it is quite possible that I have not set Ubuntu up correctly for although I located Inkscape without difficulty, I cannot find Opera in any repository no how.   Mozilla, yes; but not Opera.  I have to disappear for a several hours but will resolve this one way or another later.

I am not by nature obnoxious; verbose, yes, but that is another matter.  I like to make myself clear.  Coming from DOS to Linux is like going from English to Mandarin Chinese.  I have no references and am flying by the seat of my pants.  Your patience is thus requested.  If is often the little things which are not at all obvious.

I am ancient; I didn't grow up with this stuff.  Cheers, Muzz aka SirCoistrel.

---

### Post by SirCoistrel on 2005-05-13
Don't ask me how, but Opera is now sitting in Synaptic under Installed (local or obsolete) as listed by Status.  That status was reached using one of the long commands suggested for Terminal.   Part of the mystery was a missing file starting with the letter "l".  It is not listed under Installed.

What are the chances that I have loaded a slightly corruped version of Ubuntu?

---

### Post by bored2k on 2005-05-13
[QUOTE=SirCoistrel]Don't ask me how, but Opera is now sitting in Synaptic under Installed (local or obsolete) as listed by Status.  That status was reached using one of the long commands suggested for Terminal.   Part of the mystery was a missing file starting with the letter "l".  It is not listed under Installed.

What are the chances that I have loaded a slightly corruped version of Ubuntu?[/QUOTE]
 I told you to dpkg -i opera right? well, after its installation, it gets managed by Synaptic. 
Your chances are 1 in a 100.

In a terminal window, type opera to run it.
YOu can make a shortcut for it, but thats a different thing.

---

### Post by SirCoistrel on 2005-05-13
If you want to get touchy, your last instructions were these:

sudo dpkg -i opera_8.0-20050415.5-shared-qt_en_sarge_i386.deb; sudo apt-get -f install

You're frustrated; want to try me at geophysics?

---

### Post by bored2k on 2005-05-13
[QUOTE=SirCoistrel]If you want to get touchy, your last instructions were these:

sudo dpkg -i opera_8.0-20050415.5-shared-qt_en_sarge_i386.deb; sudo apt-get -f install

You're frustrated; want to try me at geophysics?[/QUOTE]
 Just trying to help.

After you input those commands and execute them, what is the terminal window's response ? don't worry if its to big paste in inside quotes.

---

### Post by SirCoistrel on 2005-05-13
Okay, thanks.  It ran under the terminal command "Opera" but there are unresolved Java issues which I'll have to look into.  In essence it appears that Java was disabled.
"""

---

### Post by SirCoistrel on 2005-05-13
Again, big thanks.  No hard feelings.  IT TRULY IS LIKE LEARNING A FOREIGN LANGUAGE.
I am not certain as the to the status of Sun and Java with the Linux world.  But now I can test out Inkscape and see if it displays in Opera and Mozilla.  SVG is not well known, but will be. Mozilla are contemplating integrating it with XHTML.  Your efforts are much appreciated.  Apologies where necessary to all.  (That is what I call a "crash" course.)

---

### Post by bored2k on 2005-05-13
[QUOTE=SirCoistrel]Again, big thanks.  No hard feelings.  IT TRULY IS LIKE LEARNING A FOREIGN LANGUAGE.
I am not certain as the to the status of Sun and Java with the Linux world.  But now I can test out Inkscape and see if it displays in Opera and Mozilla.  SVG is not well known, but will be. Mozilla are contemplating integrating it with XHTML.  Your efforts are much appreciated.  Apologies where necessary to all.  (That is what I call a "crash" course.)[/QUOTE]
 I'm a KDE user. You are using GNOME. In KDE, Konqueror browser supports SVG wich is pretty nice. Regarding Linux and Java, it is very easy to install.

[http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)
Method 3 [my favorite]

---

### Post by bored2k on 2005-05-13
Tip: If you want 4/5 of your problems solved:

> Open a terminal session and enter:
```

wget http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh && sudo sh ubuntusetup.sh
```

Purpose: To automate installation of the following programs because I am lazy and hate selecting to install them manually after I format my computer (which is often) so this script saves me alot of time and I hope it helps you too.

build-essential - Compilers needed to build programs
beep-media-player - XMMS gtk2 clone. Compatible with XMMS plugins/skins
gstreamer0.8-mad - Add MP3 support for Rhythmbox
w32codecs - Windows codecs for playing various files
streamtuner - Online music streamer from shoutcast and a few others
xine-ui - The xine video player, user interface for playing dvd's and such
totem-xine - Have totem use xine so you can actually use it to play videos etc.
msttcorefonts - Windows True Type Fonts
acroread - Latest version of Adobe Acrobat Reader
acroread-plugin - Firefox Acobat Reader Plugin
libdvdcss2 - DVD Library
gnomebaker - The best gnome/gtk2 cd/dvd/cdrw burning software
gftp - Ftp Client
flashplayer-mozilla - Flash plugin for firefox
Java JRE 1.5 - Latest version of Java
Custom Firefox Forms - Make you firefox form widgets look decent
/etc/apt/sources.list - Add in universe, multiverse and misc repositories
Misc Windows Fonts - Misc fonts that are missing in the msttcorefonts package
You will be asked to select "Yes" or "No" on various things you will want to select yes on them.

And.. I'm an "advanced" french student. I can say Ubuntu is easier than learning a language, primarily because you got a community with over 20 thousand members willing to help.

---

### Post by SirCoistrel on 2005-05-13
[QUOTE=Malicine]the manual and repository installs have both worked for me.
I did manual download and terminal install, I noticed it in synaptic after.
However, also being a noob... 
Should opera have an icon somewhere now? I cannot seem to find the installed program anywhere ](*,) 

great thread btw, covering a number of areas.


cancel that, just noticed the 'run app~' button and typed "opera", works sweet.
Imported all my bookmarks,contacts,setup etc from my win partition. \\:D/[/QUOTE]
 You were right on the money.  I shall follow your trail.  It was a challenging thread.  I still have to figure out the file system.  Thanks for the comment.   Muzz aka SirCoistrel

---

### Post by bored2k on 2005-05-13
Tip: if you want to add opera to your menu list, follow this webpage
[http://www.realistanew.com/projects/smeg/](http://www.realistanew.com/projects/smeg/)

---

### Post by SirCoistrel on 2005-05-13
Hi Oh Bored One:  Your help, and that of others too (thanks Meg), have made this an auspicious start to Ubuntu.  This is my 3rd go at Linux and it is easy to see that this one is a keeper.  I have already convinced a friend equally disillusioned with alternatives to try out Ubuntu.  I unfortunately have much money tied up in valuable software elsewhere so it might take a year to make a complete switch, but switch indeed I am going to!!!!   I shall definitely try out all of your suggestions over the next few days, Once again, big-time thanks.  Muzz SC

---

### Post by bored2k on 2005-05-13
[QUOTE=SirCoistrel]Hi Oh Bored One:  Your help, and that of others too (thanks Meg), have made this an auspicious start to Ubuntu.  This is my 3rd go at Linux and it is easy to see that this one is a keeper.  I have already convinced a friend equally disillusioned with alternatives to try out Ubuntu.  I unfortunately have much money tied up in valuable software elsewhere so it might take a year to make a complete switch, but switch indeed I am going to!!!!   I shall definitely try out all of your suggestions over the next few days, Once again, big-time thanks.  Muzz SC[/QUOTE]
 No problem. Even if you dont have more problems, go to our Tips n Tricks section, there you will find interesting things you might have not thought of. Linux is a great didactic game! ;)

---

