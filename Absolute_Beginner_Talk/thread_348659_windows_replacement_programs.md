---
title: "windows replacement programs"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by TheNemeses on 2007-01-29
k, im using ubuntu 6.10, and im swtiching from windows and i was wondering what are some alternatives and good ones for windows programs such as... AIM, Norton Anti Virus, Limewire, MS Office, and other window apps you might think of.

---

### Post by opossumjack on 2007-01-29
Here are some programs:

AIM ---> you could use GAIM. It works with almost every communication protocol

Norton ---> You don't really need an antivirus on linux...but if you want look for avast for linux or aegis

Limewire ---> you could use aMule (it's similar to eMule)

Office ---> Well, there is OpenOffice (that should come with the basic installation of ubuntu) that it's even better than office




Hope you'll find what you need

OpossumJack

---

### Post by TheNemeses on 2007-01-29
i know this might be a pain, but if possible could you and anyone in the future please post links.

---

### Post by Tux Aubrey on 2007-01-29
Here's a link to a [UK review of OpenOffice]("http://http://www.itreviews.co.uk/software/s355b.htm").  It comes as part of the Ubuntu default installation and provides all the common "office" apps.  There is a free version for Windows. I actually use Abiword myself for most purposes as I find it quicker and less cluttered with functions I don't use.

There are literally thousands of linux programs compatible with Ubuntu - and most of them are downloadable and installable with Synaptic (under the System>Administration menu).

Some examples:

The Gimp - graphics and photo manipulation - equates with a slightly cut-down version of Adobe photoshop.  It comes with Ubuntu but there is a Windows version too.

Inkscape is a vector illustration program - don't remember what I used in Windows, but inkscape is very good.  You would need to get this one through Synaptic.

There are so many music players I couldn't begin to list them all.  I like Rythmbox, Listen! and Banshee, but also use Beep and XMMS.  There is a Realplayer for Linux too.

Mplayer is (I think) the built-in video viewer (it also plays music files just fine).

I use Azureus to get torrents - it is also available for Windows.

Its probably best to ask a specific question about a particular app that you are interested in.

---

### Post by RomeReactor on 2007-01-29
1.- For AIM, use GAIM, comes with Ubuntu's base install (Applications-->Internet-->Gaim)

2.- Antivirus: You don't need it in Linux yet, save for vaccinating files for transfer to windows machines. Aegis is in Synaptic (aegis-virus-scanner), as is ClamAv (clamav); Avast is a download from its [web page]("http://files.avast.com/files/linux/avast4workstation_1.0.7-2_i386.deb").

3.- For LimeWire, try [FrostWire]("http://www.frostwire.com/download.php?file=http://www.frostwire.com/frostwire/4.13.1/frostwire-4.13.1.5-1.i586.deb"), or try aMule as suggested; look for it in Synaptic (amule)

4.- Open Office comes with Ubuntu's default install (Applications-->Office-->OpenOffice.org Word Processor, etc.)

To install from the command line:

```
sudo apt-get install aegis-virus-scanner
```

```
sudo apt-get install clamav
```

```
sudo apt-get install amule
```

To install downloaded .DEB's, just double-click on them.

Edit; Tux Aubrey beat me to posting some of it #-o :mrgreen:

Look for Mplayer on Synaptic, or install it from the command line:

```
sudo apt-get install mplayer w32codecs
```

---

### Post by bapoumba on 2007-01-29
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/index.html")
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows]("https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows")
[http://doc.gwos.org/index.php/AppHelper]("http://doc.gwos.org/index.php/AppHelper")
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software]("http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software")

---

### Post by MC_Jonn on 2007-01-29
Lime wire is available for Ubuntu, i installed it and it works perfectly fine. You just need to have anything alteast near to the latest version of Java eg: Java 5 update 10 or 9. I picked up the following instructions from ubuntu guide website, its what i followed:

Enter the following in Terminal, when you are prompted to install Dash, select “NO.”

   ```
sudo dpkg-reconfigure dash
```

Now download LimeWire(Linux RPM) from site [http://www.limewire.com/english/content/downloadfree2.shtml](http://www.limewire.com/english/content/downloadfree2.shtml)

To convert the package to a Ubuntu *.deb file you must have alien installed:

  ```
sudo apt-get install alien
```

Then type the following into Terminal to convert the package from the *.rpm to a *.deb file:

   ```
sudo alien -d LimeWireLinux.rpm
```

Once it has been converted, double-click the new *.deb file to install LimeWire and that’s it, you’re done. 

That should be all.

---

### Post by glabouni on 2007-01-29
as a replacement for AIM you can use [kopete ]("http://kopete.kde.org/")(KDE), [gajim ]("http://www.gajim.org/")(gnome), [psi ]("http://psi.affinix.com/")(both) or [gaim]("http://gaim.sourceforge.net/")

norton anti virus is one piece of bloated non working software. 
using linux, chances are you'll never encounter a virus. To protect yourself nonetheless, you can use a firewall, have a try at [firestarter]("http://www.fs-security.com/")

as a replacement for limewire, you can use limewire:
> LimeWire will also run on several on Unix and Linux varieties if you have the Java Runtime Environment installed, although the installer may not work correctly. 
[http://www.limewire.com/english/content/faq.shtml#com5]("http://www.limewire.com/english/content/faq.shtml#com5")

for your office needs you should use [openoffice]("http://www.openoffice.org/")

if you didn't find something that suits you in those links bapoumba posted, check [The table of equivalents / replacements / analogs of Windows software in Linux.]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html")

---

### Post by mrdeeno on 2007-01-29
I installed Frostwire (using Automatix2).  It's virtually a clone of limewire...if it wasn't for the different color scheme (purplish blue rather than green) and the splash screen at startup, I would swear i was using limewire.

As for antivirus, I use AVG free on my Windows partition, but nothing on Linux.

For Office I use OpenOffice and it takes a little getting used to, but no more than going from Windows to Linux.

AIM/MSNM/Yahoo IM programs, I use gaim.

---

### Post by TheNemeses on 2007-01-29
kk cool, thanks everyone i have gotten some ideas and are trying some things but one thing still bothers me, i sent my favorites folder from windows onto linux, but how do i convert them or get linux to recognize them in firefox, or import them, even better.

---

### Post by jvc26 on 2007-01-29
In firefox: Bookmarks -> Organise Bookmarks -> File -> Import -> From File and then select the file.
Il

---

### Post by Matusel3 on 2007-01-29
[https://addons.mozilla.org/firefox/2410/](https://addons.mozilla.org/firefox/2410/) will allow you to synchronize your bookmarks.  It's an add-on to Firefox.  I've heard good things about it, you might want to check it out.

---

### Post by TheNemeses on 2007-01-29
hmm it doesnt seem to work. i xferd all ym windows favs from internet explorer, do i have to convert them? when i try to import it doesnt do anything.

---

### Post by Corfy on 2007-01-29
> **TheNemeses said:**
> hmm it doesnt seem to work. i xferd all ym windows favs from internet explorer, do i have to convert them? when i try to import it doesnt do anything.

By "it doesn't do anything", do you mean it won't let you choose the file to import from, or do you mean that you choose the file, but it doesn't import the favorites into Firefox?

I recently put together a CD full of free software for Windows and gave it out as Christmas presents. Most of the programs were open-source programs that are available for Windows and Linux (as you might guess, there was an ulterior motive behind me handing this out). This was my own derivative of the OpenCD.

But in describing the various programs, I compared them to their commercial equivalents, and since you asked about windows replacement programs, it seemed appropriate here (or a simplistic version, anyway):

**AbiWord** - Microsoft Word
**Audacity** - ACID Music Studio
**Blender** - Poser 6
**Firefox** - Internet Explorer, Netscape Navigator
**Gaim** - AOL Instant Messenger, Yahoo Instant Messenger, MSN Instant messenger
**GIMP** - Adobe Photoshop, Adobe Photoshop Elements
**Inkscape** - Adobe Illustrator, Corel Draw
**LinCity** - SimCity
**Nvu** - Microsoft Frontpage, Adobe GoLive
**OpenOffice.org** - Microsoft Office, Corel WordPerfect Office
**Scribus** - Adobe InDesign, Adobe PageMaker, Quark XPress
**SuperTux** - Super Mario Bros.
**Thunderbird** - Microsoft Outlook Express
**VLC Player** - Quicktime, Windows Media Player

I realize that this isn't a comprehensive list, but it is a nice listing of the software that I have on my CD that are available for Windows, available through Ubuntu's repositories, and also have commercial equivalents. Of course, there are some that are more equivalent than others.

There are some other programs, like Celestia, that I have on my CD and are available for both but I don't know what commercial program to compare them to. And a few others that aren't available as such, but very similar derivatives are available.

But I compared this software with the cost of the commercial equivalents and determined that my CD could theoretically save someone over $3,000 per computer. That is a huge savings. And if they get used to using all of these programs, what do they need Windows for? ;) :twisted:

---

### Post by TheNemeses on 2007-01-29
like the i could click the file. blahblah.url and hit open, and it would open, but the file would like never show up. i htink i have to convert it from IE to Firefox??

---

### Post by Corfy on 2007-01-30
Oh, I see what you have done now.

Um... good question (made tougher since there doesn't appear to be an export feature in IE... gotta love MS).

Firefox in Windows can import directly from Internet Explorer. I'm sure there is a way to import your Favorites into Firefox in Ubuntu, I'm just not sure how to do it off the top of my head.

Last night I didn't understand the problem because I wasn't in Windows. Now I can't work on the problem because I'm not in Ubuntu. But let me play around with it this evening and see what I can come up with (unless someone else beats me to it). There has to be an easy way.

If you still have Windows installed, then there is a fairly easy way. Install Firefox on your Windows computer, have it import the bookmarks from Internet Explorer (in Windows, Firefox offers the option to import bookmarks "From File" or "From Microsoft Internet Explorer", but Firefox in Ubuntu didn't have that second option, presumably because Internet Explorer isn't installed in Ubuntu). Then turn around and export the bookmarks from Firefox and move that file to Linux.

But if you don't have Windows anymore, then you obviously can't do that.

---

### Post by TheNemeses on 2007-01-30
yeah i really dont want to interfer with my windows drive, so yea, im researching now but not finding much, let me know if anyone finds out.

---

### Post by Corfy on 2007-01-30
I don't see any way to directly import those files. The problem exists because IE uses separate shortcuts (Windows shortcuts, I might add) to store the separate bookmarks, whereas Firefox uses an HTML file to store the bookmarks, which means they aren't compatible with each other. And without IE installed on Linux, Firefox has no direct import tool.

I still think your best bet is to install Firefox on your Windows computer and use that to import your IE bookmarks. You don't even have to set Firefox up as the default browser, although if you ask me, Firefox is ten-times safer to use than IE. Personally, Firefox has been my default browser in Windows since version 0.8, long before I started testing Linux.

Now, if you don't have many bookmarks, you can open each one up in a text editor (I used Kate, but I'm in Kubuntu rather than Ubuntu) and copy the addresses and paste them into the Firefox address bar, but if you have a lot of bookmarks, that would take forever.

---

### Post by AmandaKerik on 2007-02-01
> **TheNemeses said:**
> i know this might be a pain, but if possible could you and anyone in the future please post links.

We don't really need to post links because Ubuntu variants (ubuntu, kubuntu, etc) have built in programs that look for the program you want, and all the little files and subprograms it needs as well.

Click on Applications > Add / Remove... (it's on the bottom)
Put the program you want in the search box - if it doesn't come up, click on advanced.
In advanced you need to click on the [search] button.

I actually prefer this way of doing things - it installs the programs for you. No command line needed most of the time! It's great!

---

### Post by housam on 2007-02-01
> **TheNemeses said:**
> yeah i really dont want to interfer with my windows drive, so yea, im researching now but not finding much, let me know if anyone finds out.

You can check [this list]("http://ubuntuforums.org/showthread.php?t=293798")

---

### Post by SunnyRabbiera on 2007-02-01
Remember:
Open source apps will not fully "replace" your favorite MS software.
OS software is an ALTERNATIVE to MS software, the common mistake I find annying is that people come to linux and open source apps as a replacement to thier MS software.
Truth is OS software and MS software are totally different, sure OS software can fill in the blanks but it will NOT be a full fill in for your favorite MS software.
The best advice i can give anyone is that try everything, if program a doesnt work try program b, or worst comes to worst keep your windows boot.

---

### Post by easyease on 2007-02-01
theres nothing windows can do that ubuntu cant.......

---

### Post by Jnex26 on 2007-02-01
> **easyease said:**
> theres nothing windows can do that ubuntu cant.......

Can Ubuntu BSOD ? That seems to be the main feature of windows.

---

### Post by TheNemeses on 2007-02-01
ubuntu cant crash like windows. gg no re.

---

### Post by tagginannie on 2007-02-01
> **Jnex26 said:**
> Can Ubuntu BSOD ? That seems to be the main feature of windows.


Wise a$$ :P

Suzy:KS

---

### Post by Corfy on 2007-02-01
> **Jnex26 said:**
> Can Ubuntu BSOD ? That seems to be the main feature of windows.

Yes, it can. That is one of the screensavers, showing crashes from various systems through the years.

---

### Post by housam on 2007-02-02
Here is another [great list .]("http://www.linuxrsp.ru/win-lin-soft/table-eng.html") :guitar:

---

### Post by TheNemeses on 2007-02-02
> **Corfy said:**
> Yes, it can. That is one of the screensavers, showing crashes from various systems through the years.

Where can i find this screensaver?

---

### Post by Corfy on 2007-02-02
> **TheNemeses said:**
> Where can i find this screensaver?

[http://ubuntuforums.org/showthread.php?t=189447&highlight=BSOD+screensaver](http://ubuntuforums.org/showthread.php?t=189447&highlight=BSOD+screensaver)

According to that, it is in the Gnome interface if you have xscreensaver-data-extra installed. But I'm in KDE, and I don't see it. I know I used to have it (although I haven't used it in a long time).

---

### Post by jrj2john on 2007-02-03
To Import: choose:  1.  Bookmarks 
                                 2. Organize Bookmarks
                                 3. File
                                 4. Import

---

### Post by Corfy on 2007-02-03
> **jrj2john said:**
> To Import: choose:  1.  Bookmarks 
                                 2. Organize Bookmarks
                                 3. File
                                 4. Import

Except that doesn't work with IE favorites. The import only seems to recognize HTML files, not Windows URL files, which is what IE uses to save favorites.

---

### Post by Pom2122 on 2007-02-03
Go into IE. Choose File, Import and Export. Choose Export Favorites. It will export your favorites as an html file which can be imported perfectly into Firefox/Iceweasel.
:)

---

### Post by Big_Croc7 on 2007-06-19
Hi, does anyone know of a good dtp program that I could use as a replacement for Adobe Indesign?  That's one thing that I seem to need a windows box for, but it would be great if I could find something that will run at work and home.  Would be nice if it supported the same file formats, but that's not essential.  Something like OOo draw doesn't quite have the features I'd like.

---

### Post by Corfy on 2007-06-19
> **Big_Croc7 said:**
> Hi, does anyone know of a good dtp program that I could use as a replacement for Adobe Indesign?  That's one thing that I seem to need a windows box for, but it would be great if I could find something that will run at work and home.  Would be nice if it supported the same file formats, but that's not essential.  Something like OOo draw doesn't quite have the features I'd like.

I use Scribus, which can be found in the repositories. Their website is [http://www.scribus.net](http://www.scribus.net). Unfortunately, it can't open InDesign files (or Quark XPress files), and it takes some getting used to, but it is a fairly nice program.

---

### Post by Big_Croc7 on 2007-06-20
Thanks for the quick reply! It looks good from the website, I'll give a spin and see how I find it. Cheers!

---

### Post by Corfy on 2007-06-20
I'm hardly an expert at Scribus, but I do use it to produce a bi-monthly newsletter for my homeowner's association. And with my newspaper background, I made it look like a small newspaper. I'm still learning all of the quirks on it, and I think InDesign and Quark would be a lot easier at times, but I'm not about to pay $700 for either of those programs for a free, bi-monthly newsletter. And like a lot of other open-source programs I have tried, the more I use it, the more I like it.

---

### Post by Jammy4041 on 2007-11-21
Is there an open source replacement to Ejay or Acid Xpress?

---

### Post by Corfy on 2007-11-21
> **Jammy4041 said:**
> Is there an open source replacement to Ejay or Acid Xpress?

I'm not familiar with those programs. However, Acid Express I think is a music editing program. If that is the case, you might want to look at Audacity. If I am wrong about what that program is, I apologize.

---

### Post by Jammy4041 on 2007-11-21
Thanks for the post. Audacity is good, but I used Ejay once on somebody's computer an liked it. It is very similar. I would have to check and see about Audacity.

Would there be any free loops which I can use on Audacity?
James

---

### Post by Jammy4041 on 2007-11-21
I have checked Audacity and installed it. Hopefully I cans scrounge for some loops.

---

### Post by toddlohenry on 2008-03-18
I'm a recent convert to Ubuntu and am looking for a replacement program for Asutype, a windows app that allows you to replace short strings of text with longer strings, ie. type nasa and space and nasa is replaced with National Aeronautics and Space Administration automatically. It's on the web at [http://asutype.com/](http://asutype.com/). I don't care about replacing the spelling features -- I don't use them...

---

### Post by hyper_ch on 2008-03-18
> **TheNemeses said:**
> i know this might be a pain, but if possible could you and anyone in the future please post links.

I know this might be a pain, but if possible could you try and search for the according programs that the friendly helpers here post as replacement on the net and find more information about them yourself?

---

### Post by Corfy on 2008-03-18
> **toddlohenry said:**
> I'm a recent convert to Ubuntu and am looking for a replacement program for Asutype, a windows app that allows you to replace short strings of text with longer strings, ie. type nasa and space and nasa is replaced with National Aeronautics and Space Administration automatically. It's on the web at [http://asutype.com/](http://asutype.com/). I don't care about replacing the spelling features -- I don't use them...

I don't know about a separate program, but I know several word processors already have that ability, or something similar to it.

OpenOffice.org Writer, for instance, has "AutoText" (found under the "Edit" menu, or by hitting Ctrl-F3). You can set it up so that you can type in NASA and then hit the "F3" key,and it will replace NASA with National Aeronautics and Space Administration. Yes, that requires hitting an extra key, but on the other hand, there are times when  you would actually want it to say "NASA" rather than spelling it out all the time.

If you really want automatic changes, you should be able to set up "AutoCorrect" (found in the "Tools" menu) to do that. I don't know how long of strings AutoCorrect can hold. I know AutoText can hold very long items, and it can even hold formatting.

---

