---
title: "Seeking guidance after first Xubuntu install"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by garthoverman on 2006-11-29
Please bear with me as I supply some background. Cliff's notes at the bottom.

For my first foray into Linux and after some research I decided to use Xubuntu to resurrect my sister's old P3 machine for her. It was formerly a Win98 machine, but she basically stopped using it out of frustration with it's slowness and cumbersome operation. 

After some hang-ups trying to install from the LiveCD, I managed to succeed installing 6.06.1 from the alternate install CD. So far, the machine is connected to our gateway and able to browse. I upgraded Firefox to 2.0 and got OpenOffice installed. That's about it.

Should I install an anti-virus program? I understand that Linux is a much more secure OS, and if it simply isn't necessary, then great, but if one is recommended, which one should I install?

Her purposes with this machine are basically to use it for web-browsing and accomplishing work she takes home from her job (exclusively Office document work, using OpenOffice). To that extent, I think I have her covered. 

She's also used to accessing her email remotely using Internet Explorer as a webmail client, but Firefox was kinda buggy in accomplishing that for her. I'm thinking I could probably configure a POP account thru Thunderbird for her, but if there is a simple way to accomplish the webmail client, I'm sure she'd prefer that since it's what she's accustomed to.

Also, if it is possible she would like to use the machine to manage her digital pictures and even mp3 music. With regard to those, I'm not quite as confident in giving her support. She has an iPod Nano, and from what I've read it *should* work with Ubuntu, but I haven't tried it yet because I wanted to seek some feedback first. Personally, I've never owned nor used an iPod because I *HATE* the whole "partnership with iTunes" setup, so it makes me even more ignorant with regard to the capabilities and limitations inherent in the device.

I have a printer connected to my WinXP machine and shared on our network, and it would be nice if she could utilize the printer also from the Xubuntu machine. I have no idea how to accomplish that, either. I think I could setup a print server on her machine and connect the printer to her, allowing me to access the printer thru her, but again, I don't even know where to begin.

_Cliff's_:
1. New to Linux, installed Xubuntu for my sister
2. Is anti-virus a necessity, and if so, which?
3. Want to setup IE/Webmail client for her work emails, if possible
4. Want to learn about iPod & camera compatibility and usage in Xubuntu
5. Want to explore setting up a print server

Thanks in advance to anyone that can offer some direction for me.

-Garth

---

### Post by compmodder26 on 2006-11-29
> Is anti-virus a necessity, and if so, which?
I don't think it is needed, but ClamAV is pretty standard if you really want on.

> Want to setup IE/Webmail client for her work emails, if possible
Check out this page: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Internet_Explorer_.2B_Flash_9_.28IEs4Linux.29]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Internet_Explorer_.2B_Flash_9_.28IEs4Linux.29")

> Want to learn about iPod & camera compatibility and usage in Xubuntu
Can't help you here.  I've never used an ipod either.

> Want to explore setting up a print server
You should be able access your windows printer from xubuntu.

This little how-to should get you sorted out: [http://howto.gumph.org/content/use-smb-printer-in-xubuntu/]("http://howto.gumph.org/content/use-smb-printer-in-xubuntu/")

---

### Post by BoneKracker on 2006-11-29
> Is anti-virus a necessity, and if so, which?
Yes, if your machine serves files to Windows clients (e.g., an email server or web or ftp server that people load files up to and others will download).

If it's just a linux desktop machine, antivirus software is not a necessity -- yet; it may become so in the future.  There are viruses, worms, and rookits aimed at Linux machines, but only a very small number, and if properly configured, unix-like systems are inherently more well-protected (which is also why there aren't as many viruses).  If the machine has plenty of horsepower, it's a nice courtesy to run a virus-checker on your outbound email, because you could pass along a windows virus that's harmless to you and not know it.

A good antivirus application is clam; it's pretty widely used and a number of popular applications can tap into it to integrate its services as their virus-checking functionality.  Like most AV applications, it's built to run as a daemon (i.e. running all the time in the background).  However, what I like about it is that you don't have to run it as a daemon.  You can just scan a file with it when you want, and applications can call it to scan when needed without it having to run all time in the background, wasting your precious bodily fluids (for any lusers who didn't get that - see the movie, Dr. Strangelove).  

> Want to setup IE/Webmail client for her work emails
A webmail client is a web browser as far as I know.
If you are looking for an email client that can integrate with Microsoft Exchange/Outlook, I would suggest Evolution (since you're using xfce).  I'm not familiar with xubuntu - I would have expected them to package Evolution with it.

> Want to learn about iPod & camera compatibility and usage in Xubuntu
Somebody chime in here.
Search for iPod in the forums.  You might also find something in the Ubuntu Wiki.  iPod support in *nix applications is somewhat nacent.  Many media player applications can open and play what's on the iPod.  Others can put stuff there too.  Very few can synchronize with it.  Fewer still can do all this without reformatting the iPod rendering it incompatible with iTunes.  One thing you need to ask yourself is if you wish to continue to use the iPod with iTunes.  I haven't checked it out lately, but there is an application called Banshee that looked promising when I tried it about six months ago.  Amarok isn't bad either (if you don't mind installing a kde application on your system).

> Want to explore setting up a print server
Somebody chime in here too...
I think there is a howto on the wiki.  This is a subject to research thoroughly before you start dabbling.

---

### Post by garthoverman on 2006-11-29
Hey thanks a bunch for your guys' input. 8) 

I managed to get IEs4Linux installed with Wine, so when she gets back here after work we'll make sure it will work as her webmail client.

I'm going to save the printer project for the weekend probably.

---

### Post by scc4fun on 2006-11-29
> **garthoverman said:**
> 
4. Want to learn about iPod & camera compatibility and usage in Xubuntu
-Garth

I have a printer connected to my WinXP machine and shared on our network, and it would be nice if she could utilize the printer also from the Xubuntu machine.

I have heard AmaRoK works great for iPod synchronization. It might be a little heavy though as it uses KDE or the KDELibs (see [here]("http://amarok.kde.org/wiki/FAQ#Can_I_use_Amarok_without_KDE.3F")). It is also recommended that you have a recent (3.3.5 or higher qtlibs installed (see [here]("http://amarok.kde.org/wiki/FAQ#Drag_and_Drop_doesn.27t_work_at_all_.28e.g._in_playlists.29")).

Also, as long as it is not a Lexmark printer it will usually work fine from (X)Ubuntu.

---

### Post by Rodneyck on 2006-11-29
From what I have read, other music players that sync with the ipod include...*drum roll*...

Banshee, Listen, Rythmbox Music Player, gtkpod and lastly a device for downloading internet audio programs called iPodder.

---

### Post by garthoverman on 2006-11-29
> **scc4fun said:**
> Also, as long as it is not a Lexmark printer it will usually work fine from (X)Ubuntu.
D'OH! ](*,) It *is* a Lexmark printer. In fact, it's one of those all-in-one print/copy/scan/fax jobbies. Am I screwed?

---

### Post by garthoverman on 2006-11-29
> **Rodneyck said:**
> From what I have read, other music players that sync with the ipod include...*drum roll*...

Banshee, Listen, Rythmbox Music Player, gtkpod and lastly a device for downloading internet audio programs called iPodder.
Thanks, I will investigate those recommendations.

If you'll excuse a small rant, however, I absolutely LOATHE the synchronization aspect of iPods. I just want it to interface with my comp like a plain ol' drive where I can copy/paste/delete files as I require. I have a small 512MB mp3 player that I use exclusively for the gym, and I love it for the simple fact that I can plug it in, drag n' drop my mp3s and be on my way.

Maybe there's some convenient aspect about the synchronization that I'm missing, but it's probably the one thing that keeps me from getting an iPod.

Okay, rant over. Thanks for your help.

---

### Post by igknighted on 2006-11-29
> **garthoverman said:**
> D'OH! ](*,) It *is* a Lexmark printer. In fact, it's one of those all-in-one print/copy/scan/fax jobbies. Am I screwed?

If you are running it as a shared printer from a windows machine you /might/ have a fighting chance, but I had one of those and swapped it out for an HP cause I could not for the life of me get it to work directly from Ubuntu.

---

### Post by igknighted on 2006-11-29
> **garthoverman said:**
> Thanks, I will investigate those recommendations.

If you'll excuse a small rant, however, I absolutely LOATHE the synchronization aspect of iPods. I just want it to interface with my comp like a plain ol' drive where I can copy/paste/delete files as I require. I have a small 512MB mp3 player that I use exclusively for the gym, and I love it for the simple fact that I can plug it in, drag n' drop my mp3s and be on my way.

Maybe there's some convenient aspect about the synchronization that I'm missing, but it's probably the one thing that keeps me from getting an iPod.

Okay, rant over. Thanks for your help.

You *can* reformat an iPod to a more linux friendly file system, and I believe you can then drag and drop, but you lose some special functionality (none of which is available in the nano anyways I don't believe).  You may want to look into this, but some proprietary music formats may no longer work (ie iTunes music).

---

### Post by BoneKracker on 2006-11-29
Don't listen to _him_ -- he use's Suse Linux! the distro:
[LIST]
[*]that takes a _month_ to get their security patches out
[*]that chose a default file system invented by murder suspect
[*]that bent over for Microsoft
[/LIST]

Just kidding   :-P
Actually Suse is a great distro (one of my top 5 preferences).

If that's all you're trying to do with your iPod, you might simply try Rhythmbox first - that's default music player in Ubuntu.  Being gtk-based, it should fit nicely in with xfce.  

The ability to mount, open, transfer files to/from the iPod is handled in Ubuntu (if I recall) by udev, dbus, hal, and ivman. (Stuff that makes it automount when plugged in and just show up on your desktop.)  So if xubuntu is set up like that, these behaviors are more or less independent of the music player you choose.

What you need to do though is take your sister's iPod and put Linux on that!  She can be the first kid on the block with a  Penguin in her pocket.

---

