---
title: "I think im ready to make the switch..."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by ninja senses on 2007-12-12
However I do have some questions and I was hoping you guys could answer for me:

1.  when I do switch, Im gonna have a dual boot xp/ubuntu, will I have to move all my files over to ubuntu  and what is the easiest way to do this?  Also should I make separate partitions?  

2.  Most program I use infrequently on windows but there are some key ones I still would like to use, are they availible for linux or do they have a similar counterpart?  they are:
-itunes, great cause when I throw parties, i can play music from my comp in my room to the one in the basement
-utorrent
-AIM
-photoshop
-nero

3.  I see there are different versions of ubuntu(kubuntu,xubuntu...) which is best for me?

4.  where can I get some cool themes?

5.  I am a computer science major and will be doing alot of programming in many different languages, which ones wont be supported?

6.  I have used unix before and know basic commands, will I be alright installing and everything?

7.  Should I look into anti-virus software?

8.  What about importing all my favorites and extensions on firefox?

thanks in advance, I have been messing around on the live cd recently but I havent had time to install it because of finals.  2 more tomorrow than its all the ubuntu I can handle for a good month!!  Thanks in advance guys....

---

### Post by Tux.Ice on 2007-12-12
hello

programing languages are basically able to be coded on linux (ubuntu) no matter what language i code using jscript,html,c,c#,python and perl

ubuntu is probably best for you its the most complete and suported

gnome-looks.org has some cool themes for linux

-itunes, great cause when I throw parties, i can play music from my comp in my room to the one in the basement
-utorrent
-AIM
-photoshop
-nero


to install stuff it is basically in terminal you type ```
sudo apt-get install programname
```

ubuntu viruses are rare but avg has a linux piece and firestarter is good for a firewall

favorites and extensions should be imported and youll figure out how to do that in the install. it will say like migrate from xp

you will need another partition

email me at [email]adam@techotec.com[/email] for more

tux.ice

---

### Post by spydon on 2007-12-12
1. you can access you XP files from ubuntu but you can't access you ubuntu files from XP.
2. itunes-  maybe rythmbox or amarok
utorrent - Azureus, there are very many torrent apps
AIM - pidgin, aMSN, kopete
photoshop - gimpshop, gimp
nero - K3b
3. Try out the live cd's
4. There are some nice themes implemented but you can get very many for compiz fusion too.
5. No idea, most languages is supported
6. The installation is VERY easy, you don't have to use any CUI when installing
7. no not really, maybe firewall. Currenty there are no viruses "in the wild" for linux.

---

### Post by Tux.Ice on 2007-12-12
-itunes, great cause when I throw parties, i can play music from my comp in my room to the one in the basement
-utorrent
-AIM
-photoshop
-nero

programs:

itunes you can use amorak or some other freebies
utorrent there is a bittorrent for linux i think
AIM= gaim (has the ability of signing on to msn as well as gmail,yahoo,aim etc at the same time)
photoshop - the gimp (comes with ubuntu), or inkscape another good one (i have both)
nero - k3b (install this by going apps > add/remove > click all supported up in top,right> then in search k3b>install

hope ive helped

---

### Post by LaRoza on 2007-12-12
>1.  when I do switch, Im gonna have a dual boot xp/ubuntu, will I have to move all my files over to ubuntu  and what is the easiest way to do this?  Also should I make separate partitions?  

The easiest way, is to leave them on Windows. Ubuntu will be able to read them there.

The best way, is to make a separate partition for them. Use NTFS (format from Windows) or FAT32. Use the GParted Live CD for painless partition and format editing.

>2.  Most program I use infrequently on windows but there are some key ones I still would like to use, are they availible for linux or do they have a similar counterpart?  they are:

-itunes, great cause when I throw parties, i can play music from my comp in my room to the one in the basement
-utorrent
-AIM
-photoshop
-nero

There are many Linux music players.
There are many Torrent clients, there is a poll somewhere on them, search the forum
Use Pidgin, it works with many protocols.
GIMP
There are many burning programs, Ubuntu has good ones by default, but some people prefer others. k3b is a favourite of many.

>3.  I see there are different versions of ubuntu(kubuntu,xubuntu...) which is best for me?

I would say, use Ubuntu 7.10. If you want the other desktop environments, you can install them later on Ubuntu.

>4.  where can I get some cool themes?

[http://www.gnome-look.org/](http://www.gnome-look.org/), just google what you want, usually you'll get a lot.

>5.  I am a computer science major and will be doing alot of programming in many different languages, which ones wont be supported?

Anything .NET, see the Development and Programming Subforum, under "Programming Talk" read the stickies.

>6.  I have used unix before and know basic commands, will I be alright installing and everything?

It is GUI all the way, on the Live disk. It is very easy.

>7.  Should I look into anti-virus software?

No.

---

### Post by spydon on 2007-12-12
> **Tux.Ice said:**
> -itunes, great cause when I throw parties, i can play music from my comp in my room to the one in the basement
-utorrent
-AIM
-photoshop
-nero

programs:

itunes you can use amorak or some other freebies
utorrent there is a bittorrent for linux i think
AIM= gaim (has the ability of signing on to msn as well as gmail,yahoo,aim etc at the same time)
photoshop - the gimp (comes with ubuntu), or inkscape another good one (i have both)
nero - k3b (install this by going apps > add/remove > click all supported up in top,right> then in search k3b>install

hope ive helped

Gaim is known as pidgin nowadays just so you know.

---

### Post by atomkarinca on 2007-12-12
> **ninja senses said:**
> 
1.  when I do switch, Im gonna have a dual boot xp/ubuntu, will I have to move all my files over to ubuntu  and what is the easiest way to do this?  Also should I make separate partitions?

Gutsy can read and write NTFS now, so you can make an NTFS partition for common usage

> 2.  Most program I use infrequently on windows but there are some key ones I still would like to use, are they availible for linux or do they have a similar counterpart?  they are:
-itunes, great cause when I throw parties, i can play music from my comp in my room to the one in the basement
-utorrent
-AIM
-photoshop
-neroI don't know for itunes but for utorrent I suggest ktorrent, AIM has a native linux client you can see [here]("http://www.aim.com/get_aim/linux/latest_linux.adp"), for photoshop you can try GIMP and for Nero you can use K3b or GnomeBaker. All of them are perfectly capable of their Windows alternatives.

> 3.  I see there are different versions of ubuntu(kubuntu,xubuntu...) which is best for me?Actually this depends on your taste. You can install one of them and later install different desktop environments (Gnome, KDE, Enlightenment, Xfce and so on). It's just a matter of inputting a few lines of code like KDE for example:

```
sudo apt-get install kubuntu-desktop
```> 4.  where can I get some cool themes?Depends on the desktop environment you choose.
[_gnome-look_]("http://www.gnome-look.org/")[URL="http://www.kde-look.org/"]
kde-look[/URL] [URL="http://www.xfce-look.org/"]
xfce-look[/URL] 

> 7.  Should I look into anti-virus software?That won't be necessary.

---

### Post by voteforpedro36 on 2007-12-12
> **ninja senses said:**
> 

2.  Most program I use infrequently on windows but there are some key ones I still would like to use, are they availible for linux or do they have a similar counterpart?  they are:
-itunes, great cause when I throw parties, i can play music from my comp in my room to the one in the basement
-utorrent
-AIM
-photoshop
-nero

3.  I see there are different versions of ubuntu(kubuntu,xubuntu...) which is best for me?

6.  I have used unix before and know basic commands, will I be alright installing and everything?


Those are the only 3 I'll address, because the other ones are taken care of for the most part.

Although none of those programs will run natively in Linux, some can be run in WINE, which allows Windows programs to be used in Linux. I know one of the Itunes can (not the latest version however), and Photoshop can, actually I think all but Nero can, and I believe it has a Linux version beta somewhere.

But I suggest looking for alternatives, first. 
Itunes: There can be a lot to replace it. Try Songbird, AmaroK, Exaile, Banshee, Beep, and XMMS (the last three aren't anything like Itunes, but...) I know 2 of those can handle Ipods, if you need it for that.
uTorrent has Deluge or Azeurus to replace it, but there are more.
GAIM is auto-installed if you choose Ubuntu, or Kopete if you pick Kubuntu.
GIMP or Inkscape, although I wouldn't really know.
Nero, well, the default (GNOME) Gnome-baker, or KDE's K3B.


Ubuntu is, IMO, the best. It offers the GNOME desktop evironment, as opposed to KDE, XFCE, or Fluxbox. If you want to change DE's, but not permanently or reinstall, you can install KDE or whatever you please overtop of default GNOME.

The installer won't need commands. It's not hard at all, for a dual boot it may be a little harder. You will have to (1) use GParted to resize the Windows partition (supposing you haven't already done something similair) to allocate space for Ubuntu. Then you select to install Ubuntu, and done. You can mount the Windows drive and play media, or whatever you need on the other partition.

Good luck, and remember: come back if you need help.

---

### Post by Majorix on 2007-12-12
1. I don't know what you mean with moving all your files. From where to where?

2. utorrent -> deluge or ktorrent
AIM -> pidgin
photoshop -> gaim
nero -> k3b

3. It is a matter of taste and the ram of your comp. Xubuntu is ideal for low-end machines. Ubuntu/Kubuntu is a matter of taste. And Ubuntu Studio is for the artist.

5. I am doing a major in computer science too and I have found myself much more comfortable under Linux.

6. You don't need command line to install.

7. No.

8. All your extensions will be available under Ubuntu.

---

### Post by dr.silly on 2007-12-12
few more things

1. no prob

2. itunes - i recomend songbird (songbirdnest.com)
utorrent - bittorent, azerus, frostwire, etc
AIM - pidgin (comes with ubuntu)
photoshop - gimp (almost as good, comes with ubuntu)
nero - exist but i haven't looked into em

3. probably ubuntu

4. you won't care once you get compiz running

5. all languages i've ever heard of are supported

6. should be

7. nope

8. should

hope it helps

---

### Post by Sims2789 on 2007-12-12
> **Tux.Ice said:**
> 

to install stuff it is basically in terminal you type ```
sudo apt-get install programname
```


No, you don't need the terminal to install things. Seriously, a misconception of desktop Linux being "hard to use" only exists because of the people in the community that tell everyone to use the command line (especially when they tell people who've used GUIs all their lives to use vi to edit config files) when using the GUI is 10 times easier for 99% of people. I don't mean to be hostile, but we need to remember that a main roadblock for Linux desktop adoption is cryptic instructions that can't be understood by most potential converts.

Anyway, to install something the normal way, either go to Applications -> Add/Remove and check a box for the program you want to install (it's even easier than "I Agree, next, next, next, install") or, occasionally, System -> Administration -> Synaptic Package Manager. They're the Ubuntu equivalent of the Start button.

If the program you want isn't there you have to download it, double-click it (it'll be a .deb file) and click next, next, next, install, like in a competing proprietary operating system.

---

### Post by ninja senses on 2007-12-12
> **LaRoza said:**
> >1.  when I do switch, Im gonna have a dual boot xp/ubuntu, will I have to move all my files over to ubuntu  and what is the easiest way to do this?  Also should I make separate partitions?  

The easiest way, is to leave them on Windows. Ubuntu will be able to read them there.

**The best way, is to make a separate partition for them. Use NTFS (format from Windows) or FAT32. Use the GParted Live CD for painless partition and format editing.**
.

could you explain why this would be better.  Also I think someone said I could acess my files from windows on linux but not vice versa.  SO say i download a song to linux, i wont be able to acess it on my windows machine?

---

### Post by spydon on 2007-12-12
> The best way, is to make a separate partition for them. Use NTFS (format from Windows) or FAT32. Use the GParted Live CD for painless partition and format editing.

Why should he use the GParted Live CD when the ubuntu live cd includes Gparted or doesn't gutsy have gparted? :P

---

### Post by Sims2789 on 2007-12-12
> **ninja senses said:**
> could you explain why this would be better.  Also I think someone said I could acess my files from windows on linux but not vice versa.  SO say i download a song to linux, i wont be able to acess it on my windows machine?

There're Windows drivers for some Linux file formats (ext2 and ext3). I don't know much about them, though. So, if you select ext3 as your hard drive format you can read your Linux partition from Windows if you install the ext3 Windows driver.

---

### Post by Sims2789 on 2007-12-12
> **spydon said:**
> Why should he use the GParted Live CD when the ubuntu live cd includes Gparted or doesn't gutsy have gparted? :P

It's better for partition handling than Ubuntu's. All you can do on Ubuntu's is specify how large you want your new partition to be, or you can wipe the old one and reformat it to a Linux format. In GParted you can resize partitions, move them, etc. and it's easier to use.

---

### Post by ninja senses on 2007-12-12
> **Sims2789 said:**
> It's better for partition handling than Ubuntu's. All you can do on Ubuntu's is specify how large you want your new partition to be, or you can wipe the old one and reformat it to a Linux format. In GParted you can resize partitions, move them, etc. and it's easier to use.

I have 2 hard drives(80 g and 180g)  I was gonna keep windows on my 80g and delete everything off my 180 and install ubuntu on that, than move the files I wanted from my usb to the ubuntu install whats the best way?  sound like gparted should do the job, what file system is best for use with ubuntu?  how can optimize this?

---

### Post by Sef on 2007-12-12
A) Ubuntu is recommended at first since most people on here use it, and your questions tend to get answered faster.   

B) The Ubuntu installer will do fine.  The Live CD even has an option that will partition automatically.

---

### Post by crjackson on 2007-12-12
> **ninja senses said:**
> However I do have some questions and I was hoping you guys could answer for me:

1.  when I do switch, Im gonna have a dual boot xp/ubuntu, will I have to move all my files over to ubuntu  and what is the easiest way to do this?  Also should I make separate partitions?  

2.  Most program I use infrequently on windows but there are some key ones I still would like to use, are they availible for linux or do they have a similar counterpart?  they are:
-itunes, great cause when I throw parties, i can play music from my comp in my room to the one in the basement
-utorrent
-AIM
-photoshop
-nero

3.  I see there are different versions of ubuntu(kubuntu,xubuntu...) which is best for me?

4.  where can I get some cool themes?

5.  I am a computer science major and will be doing alot of programming in many different languages, which ones wont be supported?

6.  I have used unix before and know basic commands, will I be alright installing and everything?

7.  Should I look into anti-virus software?

8.  What about importing all my favorites and extensions on firefox?

thanks in advance, I have been messing around on the live cd recently but I havent had time to install it because of finals.  2 more tomorrow than its all the ubuntu I can handle for a good month!!  Thanks in advance guys....

As you can see you have plenty of help here, so I'll throw my hat into the ring.

1) Let Ubuntu help you with setting up your partitions.  Don't try to start off with anything too elaborate.  Ubuntu does a good job on it's own.

2)
a. iTunes - can be replaced by many different players.  Try them all and keep what you like.
b. utorrent - Ubuntu comes equiped for torrents by default.  There are many fancier aplications available.  Try the all and keep what you like.
c. AIM - Pidgin is installed by default.  It's very nice. There are many others as well.  Try them out.
d. Photoshop - GIMP comes installed by default.  There are others.  You can even install some versions of photoshop using WINE.
e. Nero - I use Nero Linux 3 & K3b - There are many others.

3) Provided you are not limited by machine specs., it's a matter of preference.  Test them out 1st.

4) [GNOME-look.org]("http://gnome-look.org/")

5) I don't know.

6) Silly question - No you won't be alright, you will be delighted

7) None needed

8) Done during the install process when dual booting.

---

### Post by Sims2789 on 2007-12-12
> **ninja senses said:**
> I have 2 hard drives(80 g and 180g)  I was gonna keep windows on my 80g and delete everything off my 180 and install ubuntu on that, than move the files I wanted from my usb to the ubuntu install whats the best way?  sound like gparted should do the job, what file system is best for use with ubuntu?  how can optimize this?

Use ext3 for the Ubuntu hard drive, and don't touch the Windows one with GParted.

After the Ubuntu install, you could (in Ubuntu) copy and paste the files from the Windows drive to your Ubuntu drive, but you can't do it the other way around without an additional driver, and that driver only exists for ext2 and ext3.

---

### Post by Sims2789 on 2007-12-12
With iTunes, store-bought music won't work in Ubuntu unless you remove the digital restrictions management before switching over. So, in Windows, download myFairTunes-v7.0.2c-Setup.exe from [http://hymn-project.org/download.php]("http://hymn-project.org/download.php") and run it.

Also, in Ubuntu, you'll also need to go to Applications -> Add/Remove Programs and search for GStreamer and install all of the GStreamer plug-ins (there's about 5).

---

### Post by ninja senses on 2007-12-12
> **Sims2789 said:**
> Use ext3 for the Ubuntu hard drive, and don't touch the Windows one with GParted.

After the Ubuntu install, you could (in Ubuntu) copy and paste the files from the Windows drive to your Ubuntu drive, but you can't do it the other way around without an additional driver, and that driver only exists for ext2 and ext3.

EDIT:  so I can just install from my live cd, go through installation process and it will let me choose what folder I want to share between windows and linux?

---

### Post by ninja senses on 2007-12-12
> **ninja senses said:**
> EDIT:  so I can just install from my live cd, go through installation process and it will let me choose what folder I want to share between windows and linux?

up top...

---

### Post by dr.silly on 2007-12-12
if you use ext3 for your linux side and install a driver in windows, then your windows should see your entire linux, and linux by default will see your entire windows. The install lets you chose the size of your partitions (not sure if it lets you chose ext3??).

---

### Post by ninja senses on 2007-12-12
> **dr.silly said:**
> if you use ext3 for your linux side and install a driver in windows, then your windows should see your entire linux, and linux by default will see your entire windows. The install lets you chose the size of your partitions (not sure if it lets you chose ext3??).

so lets say I have all the files I want to transfer on a USB drive, after I install, can I just copy everything from that onto linux?

---

### Post by dr.silly on 2007-12-12
you won't need them on a usb you'll see them right from linux just like all the other files

---

### Post by ninja senses on 2007-12-12
so lets say I download an mp3 that I want to use on my windows machine, but I download to my mp3(shared) folder in ubunutu, will it show up on my windows install?

---

### Post by LaRoza on 2007-12-12
> **ninja senses said:**
> could you explain why this would be better.  Also I think someone said I could acess my files from windows on linux but not vice versa.  SO say i download a song to linux, i wont be able to acess it on my windows machine?

This would keep your data together, and in a place easily accessable by Windows or Linux. You would not have to worry about loosing or separating your files, and if you decide to get rid of Windows or Linux (or install another version), your data will be on another partition.

---

### Post by LaRoza on 2007-12-12
> **spydon said:**
> Why should he use the GParted Live CD when the ubuntu live cd includes Gparted or doesn't gutsy have gparted? :P

GParted is:

* Faster
* More flexible (it runs on more computers)
* A handy tool to have anyway
* It has never failed me

GParted will be GParted the world over, but having the lighter GParted Live CD (or floppy or usb) will be much handier and more reliable than runny a Ubuntu Live CD.

---

### Post by ninja senses on 2007-12-12
> **LaRoza said:**
> GParted is:

* Faster
* More flexible (it runs on more computers)
* A handy tool to have anyway
* It has never failed me

GParted will be GParted the world over, but having the lighter GParted Live CD (or floppy or usb) will be much handier and more reliable than runny a Ubuntu Live CD.

do I install GParted first then install ubuntu or ubuntu then GParted?

---

### Post by ninja senses on 2007-12-12
> **ninja senses said:**
> do I install GParted first then install ubuntu or ubuntu then GParted?

anyone know?

---

### Post by Tristicus on 2007-12-12
I just downloaded Geubuntu today, and I love it. The LiveCD desktop looked so clean and nice.

> **ninja senses said:**
> anyone know?

Well, you can use GParted before you install Ubuntu if you have a LIVECD, which works MUCH better, but if not, you install Ubuntu then use Gparted, but I would do the first because the 2nd could erase your XP if you aren't careful.

---

### Post by spydon on 2007-12-13
> **Sims2789 said:**
> It's better for partition handling than Ubuntu's. All you can do on Ubuntu's is specify how large you want your new partition to be, or you can wipe the old one and reformat it to a Linux format. In GParted you can resize partitions, move them, etc. and it's easier to use.

I don't mean the installers default partition app, I mean the gparted app that is under System>administration or something like that.

---

### Post by lespaul_rentals on 2007-12-13
> **ninja senses said:**
> 1.  when I do switch, Im gonna have a dual boot xp/ubuntu, will I have to move all my files over to ubuntu  and what is the easiest way to do this?  Also should I make separate partitions?

You will need to resize your XP partition to allow room for Ubuntu.  The LiveCD installer will do this for you (back up your important data first just in case something goes wrong).  You will be able to view the XP files from Ubuntu but not the Ubuntu files from XP, unless you set up a shared fat32 partition, where you can dump shared documents so both operating systems can read them.

> 2.  Most program I use infrequently on windows but there are some key ones I still would like to use, are they availible for linux or do they have a similar counterpart?

> -itunes

Amarok would work for you.

> -utorrent

Ktorrent is a killer BitTorrent client.  I like it a lot.  Azureus is also available on Linux, and I've heard great things about Deluge.

> -AIM

Kopete is the best in my opinion.  It supports many different protocols.  You might also like Gaim.

> -photoshop

No comperable application yet (that is a point up to debate), but The GIMP is almost as powerful IMO.

> -nero

K3B, **amazing** CD/DVD burner.

> 3.  I see there are different versions of ubuntu(kubuntu,xubuntu...) which is best for me?

I would strongly recommend Kubuntu.  You can go with version 7.04 or 7.10 (whichever works better with your hardware), but I would definitely recommend Kubuntu.  It has the KDE desktop by default, which IMHO *slaughters* Gnome.  The default applications are far better.

> 4.  where can I get some cool themes?

[http://www.kde-look.org](http://www.kde-look.org)

That is, if you decide on Kubuntu.  If you're looking for skinnable, themable, configurable...KDE is your cup of tea.

> 5.  I am a computer science major and will be doing alot of programming in many different languages, which ones wont be supported?

The list is almost endless.  Certainly more friendly than Windows (for example, Python, Perl, and the like are naturally supported, there are others I'm sure).  I've worked with C, C++, Python, Perl, Ruby, and others, and have had no problems.  Visual Basic isn't supported, though, and C# might not be either, because it's Microsoft.

6.  I have used unix before and know basic commands, will I be alright installing and everything?

You'll be fine.  If you run into any trouble just ask here (you can even PM me and I'll get back to you).

7.  Should I look into anti-virus software?

Not neccesary at the current time.  You might like Avast for Linux, it's an on-demand virus scanner; you can scan when you want, which means it isn't running all the time hogging your resources.  Plus, it's command-line or GUI, so you can have a virus scan going in your terminal.  Pretty cool!

8.  What about importing all my favorites and extensions on firefox?

I'm not sure that's possible.  If you can export your favorites into some favorites file you might be able to.  Not sure though.  FX on Linux is not the greatest thing in the world, I will warn you now.  In *buntu 7.10 especially.  I haven't had many problems with it in *buntu 7.04, although I don't use it.  If you want a really good Linux browser try Opera.  ;)

> thanks in advance, I have been messing around on the live cd recently but I havent had time to install it because of finals.  2 more tomorrow than its all the ubuntu I can handle for a good month!!  Thanks in advance guys....

Hey man, just let me know if you need anything.  PM me or post a thread if you need some pointers!

---

### Post by stchman on 2007-12-13
> **ninja senses said:**
> However I do have some questions and I was hoping you guys could answer for me:

1.  when I do switch, Im gonna have a dual boot xp/ubuntu, will I have to move all my files over to ubuntu  and what is the easiest way to do this?  Also should I make separate partitions?  

2.  Most program I use infrequently on windows but there are some key ones I still would like to use, are they availible for linux or do they have a similar counterpart?  they are:
-itunes, great cause when I throw parties, i can play music from my comp in my room to the one in the basement
-utorrent
-AIM
-photoshop
-nero

3.  I see there are different versions of ubuntu(kubuntu,xubuntu...) which is best for me?

4.  where can I get some cool themes?

5.  I am a computer science major and will be doing alot of programming in many different languages, which ones wont be supported?

6.  I have used unix before and know basic commands, will I be alright installing and everything?

7.  Should I look into anti-virus software?

8.  What about importing all my favorites and extensions on firefox?

thanks in advance, I have been messing around on the live cd recently but I havent had time to install it because of finals.  2 more tomorrow than its all the ubuntu I can handle for a good month!!  Thanks in advance guys....

You are in luck, Ubuntu should be just the ticket for you.

1.  Ubuntu can read/write to NTFS partitions so that is no problem.

2.  There are Linux equivalents for all the programs you run.
      - Use XMMS, or VLC for media playing.  Amarok or GTKPod for your iPod
      - Use Ktorrent to download torrents off the net
      - Gaim or Pidgin will handle your IM protocols
      - The GIMP is a good equivalent to Photoshop, but the menus are quite a bit different
      - K3B is an excellent CD/DVD burning program

3.  If you have a more modern machine use Ubuntu as most of the resources/tutorials talk about Gnome.  If you prefer KDE then use Kubuntu.  Xubuntu is for older machines as it has a more lightweight GUI called XFCE.

4.  Themes can be had at [www.gnome-look.org](www.gnome-look.org)

5.  You are in heaven as there are a plethora of compilers free to Ubuntu, C, C++, C#, Java, Pascal, Python, ADA, PERL, FORTRAN and development tools.

6.  Yes, the CLI syntax is pretty similar.  You will have a learning curve though.

7.  Viruses and Spyware are pretty much a non-factor in Ubuntu or Linux in general.

8.  Just save your bookmark.htm file and go get your extensions again.

My website in my sig has a lot of tutorials.  Glad to have you on board.

---

### Post by zoe-scutterbug on 2007-12-13
regards 8

most firefox extensions work in linux

including a variety of bookmark/favourite sync extensions..I forgotten which one I use but its very useful when upgrading to new hardware etc etc

rush rush bye

zoe

---

### Post by ninja senses on 2007-12-13
Im at the last install screen, i decided to have one hard drive used for just windows and another for just ubuntu, I selected option 2 and picked the drive im going to install ubuntu to.  This will erase that drive but wont delete my windows one, correct?  heres the screen im at:

 Language: English
 Keyboard layout: U.S. English
 Name: sense
 Login name: sense
 Location: America/New_York
 Migration Assistant:
 Microsoft Windows XP Home Edition (/dev/hda1):
 ninjasense: Mozilla Firefox, Internet Explorer, Wallpaper, User Picture, My
Documents, My Music, My Pictures


If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.

The partition tables of the following devices are changed:
 SCSI2 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #1 of SCSI2 (0,0,0) (sda) as ext3
 partition #5 of SCSI2 (0,0,0) (sda) as swap

---

### Post by ninja senses on 2007-12-13
im just gonna wait for an answer before i hit my install button hah

---

### Post by evil316 on 2007-12-13
You can access all your windows files from Ubuntu with Samba.  As far as dual booting goes I think the easiest and safest way to do it is using two seperate hard drives.

rythm box is far better than itunes.  My 13 year old daughter switched from XP to Ubuntu and loves rythm box.  She always had issues with itunes.  

There is bitorrent for Linux.

Comes with Pidgin which does instant messaging for all IA platforms.  There are tons of other apps for it too.

Gimp is as good or better than photoshop, also there is google picasa or something like that which is good too.

Tons of burning software, way too numerous to mention.

I prefer Ubuntu, Kubuntu seems to have a more windows like GUI but it will only take about 5 minutes to get up to speed with Ubuntu.  Before long you'll want to configure your desktop to look how you want it to look, not how you have been used to with Windows anyway.

Google for themese, there are tons out there.

Don't know about programming but I doubt there are many if any that aren't supported, mainstream ones anyway.

Linux has come a long way in terms of GUI and ease of use.  If you can isntall Windows and use it you can install Ubuntu and use it.

Clam antivirus for Linux.  There are not that many viruses for Linux as there are for Windows so it is less of a concern but you should always protect yourself regardless.

Just export your favorites to a file and then import that file from the firefox browser in Ubuntu.

---

### Post by evil316 on 2007-12-13
What are the two HD's listed as?  Have you been at the partition screen yet?

---

### Post by ninja senses on 2007-12-13
> **evil316 said:**
> What are the two HD's listed as?  Have you been at the partition screen yet?

it says guided - use entire disc:

ide1 master (hda) - 80 GB (my windows one)
scsi2(0,0,0,)(sda) - 200 GB (the one I want linux on)

I chose the second one

---

### Post by ninja senses on 2007-12-13
*click*

its installing :D

now I need to transfer my files off my usb to my linux partition, whats the best way?

---

### Post by evil316 on 2007-12-13
OK, so in your earlier post it says Ubuntu is going on sda.  Shows hda as where it is importing windows from.  This would be correct.  Continue without fear.

---

### Post by lespaul_rentals on 2007-12-13
> **ninja senses said:**
> *click*

its installing :D

now I need to transfer my files off my usb to my linux partition, whats the best way?

Is this a thumb drive or a hard drive you speak of?  How is it formatted?

---

### Post by evil316 on 2007-12-13
just plug in the usb, it will recognize it and you can drag and drop just like in windows.

---

### Post by ninja senses on 2007-12-13
> **lespaul_rentals said:**
> Is this a thumb drive or a hard drive you speak of?  How is it formatted?

hard drive, almost done installing :D

---

### Post by bren on 2007-12-13
regarding no. 8 in the original post I can recommend installing FOXMARKS

this is a firefox extension which saves/synchronises your bookmarks on an external server...... you can acess from either xp or ubuntu with the same bookmarks

bren

---

### Post by evil316 on 2007-12-13
He's using dual boot on the same machine.

---

### Post by evil316 on 2007-12-13
The usb device you want to transfer files from...is it a usb hard drive or a thumb drive?

---

### Post by lespaul_rentals on 2007-12-13
> **evil316 said:**
> just plug in the usb, it will recognize it and you can drag and drop just like in windows.

Not neccesarily, you've obviously never dealt with corrupted NTFS permission tables.

ninja, when you are done installing and boot up into your new Ubuntu, you will need to run the following codes:

```
sudo apt-get update
```

```
sudo apt-get install ntfs-3g usbmount
```

If it says these are already installed, that's okay.  When these are done plug in your hard drive and you should see an autorun box come up.  If so you should be golden.  ;)

EDIT: Run these in the Terminal.

---

### Post by stchman on 2007-12-13
> **evil316 said:**
> You can access all your windows files from Ubuntu with Samba.  As far as dual booting goes I think the easiest and safest way to do it is using two seperate hard drives.

rythm box is far better than itunes.  My 13 year old daughter switched from XP to Ubuntu and loves rythm box.  She always had issues with itunes.  

There is bitorrent for Linux.

Comes with Pidgin which does instant messaging for all IA platforms.  There are tons of other apps for it too.

Gimp is as good or better than photoshop, also there is google picasa or something like that which is good too.

Tons of burning software, way too numerous to mention.

I prefer Ubuntu, Kubuntu seems to have a more windows like GUI but it will only take about 5 minutes to get up to speed with Ubuntu.  Before long you'll want to configure your desktop to look how you want it to look, not how you have been used to with Windows anyway.

Google for themese, there are tons out there.

Don't know about programming but I doubt there are many if any that aren't supported, mainstream ones anyway.

Linux has come a long way in terms of GUI and ease of use.  If you can isntall Windows and use it you can install Ubuntu and use it.

Clam antivirus for Linux.  There are not that many viruses for Linux as there are for Windows so it is less of a concern but you should always protect yourself regardless.

Just export your favorites to a file and then import that file from the firefox browser in Ubuntu.

Samba is used to access Windows shares over a network.  I believe he is talking about accessing his NTFS partitions in that case he will need to mount them in fstab.  He can install ntfs-config that will give him a GUI to mount NTFS partitions.

---

### Post by evil316 on 2007-12-13
> **lespaul_rentals said:**
> Not neccesarily, you've obviously never dealt with corrupted NTFS permission tables.

ninja, when you are done installing and boot up into your new Ubuntu, you will need to run the following codes:

```
sudo apt-get update
```

```
sudo apt-get install ntfs-3g usbmount
```

If it says these are already installed, that's okay.  When these are done plug in your hard drive and you should see an autorun box come up.  If so you should be golden.  ;)

EDIT: Run these in the Terminal.


I had assumed he was talking about a simple thumb drive.

---

### Post by evil316 on 2007-12-13
> **stchman said:**
> Samba is used to access Windows shares over a network.  I believe he is talking about accessing his NTFS partitions in that case he will need to mount them in fstab.  He can install ntfs-config that will give him a GUI to mount NTFS partitions.

Right, sorry.

---

### Post by ninja senses on 2007-12-13
im trying to sort out a problem with my monitor first, i knew about it before I installed and was going to update the xorg file but I can't back it up?

cannot create regular file `/etc/X11/xorg.conf.backup': Permission denied
 command : cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

---

### Post by evil316 on 2007-12-13
use sudo before your command then enter your password.  SuperUser Do...I don't know if that's what it stands for but that's what it does.  Runs the command as a super user.  like this:

sudo touch cp /etc/X11/xorg.conf /etx/X11/xorg.conf.backup

---

### Post by ninja senses on 2007-12-13
> **evil316 said:**
> use sudo before your command then enter your password.  SuperUser Do...I don't know if that's what it stands for but that's what it does.  Runs the command as a super user.  like this:

sudo touch cp /etc/X11/xorg.conf /etx/X11/xorg.conf.backup

i have about 2 inches of just black on left side of my screen, i thought I would be able to resolve it with this:  [http://www.theatons.com/blog/2007/08/24/how-to-setup-dell-e228wfp-on-ubuntu-704/](http://www.theatons.com/blog/2007/08/24/how-to-setup-dell-e228wfp-on-ubuntu-704/) but its not working...hmm?

---

### Post by evil316 on 2007-12-13
No answer off the top of my head other than making sure you auto adjust your monitor.  What video card driver are you using?  Is there a restricted driver available?

---

### Post by Achetar on 2007-12-13
> **ninja senses said:**
> However I do have some questions and I was hoping you guys could answer for me:

1.  when I do switch, Im gonna have a dual boot xp/ubuntu, will I have to move all my files over to ubuntu  and what is the easiest way to do this?  Also should I make separate partitions?  

2.  Most program I use infrequently on windows but there are some key ones I still would like to use, are they availible for linux or do they have a similar counterpart?  they are:
-itunes, great cause when I throw parties, i can play music from my comp in my room to the one in the basement
-utorrent
-AIM
-photoshop
-nero

3.  I see there are different versions of ubuntu(kubuntu,xubuntu...) which is best for me?

4.  where can I get some cool themes?

5.  I am a computer science major and will be doing alot of programming in many different languages, which ones wont be supported?

6.  I have used unix before and know basic commands, will I be alright installing and everything?

7.  Should I look into anti-virus software?

8.  What about importing all my favorites and extensions on firefox?

thanks in advance, I have been messing around on the live cd recently but I havent had time to install it because of finals.  2 more tomorrow than its all the ubuntu I can handle for a good month!!  Thanks in advance guys....

1. You won't have to move all of your files from Windows to Ubuntu, just search for ntfs in synaptic and you will find stuff to let you edit windows files in Ubuntu. See [here ]("http://www.fs-driver.org/")for editing Ubuntu files in Windows.

2.Programs:
iTunes - Rhythmbox is AMAZING!!! So much better than iTunes!
uTorrent - There may be a Linux port, or use [frostwire]("http://www.frostwire.com") or download bittorrent from synaptic

3. Different Versions:
Ubuntu: Easiest Upgrade inbetween different versions, mid-range computer requirements. Uses [GNOME]("http://www.gnome.org")
Kubuntu: Major difference is that it uses [KDE]("http://www.kde.org") rather than GNOME. Other than that, not much difference. Higher computer requirements than Ubuntu.
Xubuntu: Uses [Xfce4]("http://www.xfce.org") rather than GNOME. Fastest, easiest to skin. Downside is that when you upgrade versions, it installs GNOME, which breaks Xfce4, and requires you to use recovery mode to remove GNOME. My Personal favorite BTW.

4. [www.gnome-look.org]("http://www.gnome-look.org"), [Compiz-Fusion]("http://www.compiz-fusion.org")

5. All languages (not sure about C#) are supported, just not their .NET counterparts.

6. Oh definately, when I installed Ubuntu last year (switched to Xubuntu after a hard crash because it was the latest LiveCD I had, planned on installing ubuntu-desktop, but liked Xfce4 better) I knew no Linux commands besides ls and rm and it went so smoothly, much better than XP or Vista ever has.

7. I have none, but I am not connected the the 'net much. I don't know anything about that, besides the fact that there are not many malicious viruses/trojans/worms out for Linux/Unix computers.

8. *sigh*, that will most likely be the hardest part of setting up your computer, except for graphics cards possibly. I don't know how to do that. Extensions can be downloaded from [addons.mozilla.org]("http://addons.mozilla.org/") quite easily.

---

### Post by the Didey on 2007-12-13
EDIT: I think i answered question from 3 pages ago.....man you guys type fast,
the last question is both.

you can use gparted from the Live CD and then you can get it in applications---->add/remove programs and use it from the install.


I changed my partitions after the install and during....so both work fine.

2 thoughts that I have not seen mentioned....

firefox was really slow (for some)....swiftfox is will be faster and uses your .mozilla (or .firefox) folder so it will keep most of you new settings and works with most of the plugins/themes/etc. As far as moving settings from windows to ubuntu....dunno.

Also, I don't know if this is a good idea or not....but I know the NTFS support is pretty new to ubuntu, and I have a decent amount of space.....

So i made a FAT partition for music that would be accessible from both sides with no worries. That said, I have had no problems accessing/reading/writing to my NTFS partitions whatsoever.

---

### Post by ninja senses on 2007-12-13
> **evil316 said:**
> No answer off the top of my head other than making sure you auto adjust your monitor.  What video card driver are you using?  Is there a restricted driver available?

not sure where can i find out my video card driver?

EDIT:  I also cant import my firefox settings/bookmarks/extensions???

---

### Post by ninja senses on 2007-12-13
> **ninja senses said:**
> not sure where can i find out my video card driver?

EDIT:  I also cant import my firefox settings/bookmarks/extensions???

if I make changes to xorg.conf to they take effect immediatly without needing to reset?  It sucks cause I can't do anything cause I cant see my whole screen

---

### Post by evil316 on 2007-12-13
To restart X it's control - alt -backspace

did you export the bookmarks in windows to a file?  Can you access the file?

---

### Post by ninja senses on 2007-12-13
hey guys,

I pretty much got everything sorted out:

My monitor I hit auto adjust to get it to fit right, but i have to hit it everytime I load ubuntu.  at least I can see the whole screen.

I couldnt import my extensions and such on firefox but I did get my bookmarks by hitting import bookmarks, then read from file, and chose the .html file I had from windows.

Well im basically set-up, thanks for all your help guys!!!

now for cutomization:twisted:

---

### Post by evil316 on 2007-12-13
No problem, always happy to help.  Please search the forums and google with problems you have as most have already been addressed and the answers are pretty easy to find with a litlte bit of searching.

---

### Post by lespaul_rentals on 2007-12-14
> **ninja senses said:**
> hey guys,

I pretty much got everything sorted out:

My monitor I hit auto adjust to get it to fit right, but i have to hit it everytime I load ubuntu.  at least I can see the whole screen.

I couldnt import my extensions and such on firefox but I did get my bookmarks by hitting import bookmarks, then read from file, and chose the .html file I had from windows.

Well im basically set-up, thanks for all your help guys!!!

now for cutomization:twisted:

Did you go with Gnome (Ubuntu) or KDE (Kubuntu)?  Try:

[http://gnome-look.org](http://gnome-look.org)
[http://kde-look.org](http://kde-look.org)

Have fun!  :)

---

