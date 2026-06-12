---
title: "A few misc. beginner questions"
date: 2005-05-14
forum: Absolute Beginner Talk
---

### Post by davidmigl on 2005-05-14
Hello all,

I recently installed Ubuntu and am liking it alot.  I have got the major components working for the most part, and am just trying to "iron out the wrinkles" and make my Ubuntu machine capable of anything Windows could do.  Here are my questions:

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
1. I tried to install Firefox 1.0.4 so I could access some plugins.  However, when I go to the folder that I installed it in, I am left utterly confused by a list of files.  How do I launch Firefox 1.0.4, make it the default browser, etc.

2. Whenever I try to play an .mp3 file in Totem Movie Player, I get an error saying that “there were no decoders found to handle the stream in file [file name],” and that I might need to install the corresponding plugins.  How do I solve this?

3. This has to be something that is just slipping my mind.  Is there any way to turn off the visualization in Totem Movie Player?  My 233 mhz (secondary, of course) machine just cannot handle the load.

4. Is there a way to play .wma files? If so, how?

5. Whenever I try to open a .doc file from a Windows XP machine on a network, I get an error message: Error loading document [file name].  [file name] does not exist.”  However, when I copy the file onto the Ubuntu desktop, I can read it just fine.  What is happening and how do I get Ubuntu to play nice with Windows?

6. I know that very few viruses are written for Linux because of its low market share.  However, do I still need to run antivirus/firewall/antispyware/etc, or can I surf the web without fear of getting infected with what is provided out of the box?
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Thank you all for helping an Ubuntu newbie.   :grin:

---

### Post by monchichi on 2005-05-14
1. The cleanest solution would be to wait until the official Ubuntu package is updated, and install that. 

2. I'd recommend using Beep-Media-Player or Rhythmbox to play MP3s... much better programs for music. If you want to stick with Totem, try installing totem-xine in place of totem-gstreamer:```
sudo apt-get install totem-xine
```
3. In Totem, if you go to Edit->Preferences, then click on the "Display" tab, uncheck the option to "show visual effects."

4. You need to install the w32codecs. Refer to [http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs) Bookmark this guide, it will answer many of your questions!

5. I'm not sure about this one. It may have to do with the file permissions on the WIndows side.

6. Don't worry about it. You may want to run Amavis or Clamav to help protect other Windows machines on your network, but in Linux it's anything but necessary. A firewall is always a good idea. Try Firestarter, it's a great, easy to use gui for iptables.```
sudo apt-get install firestarter
```
Happy Hacking!

---

### Post by az on 2005-05-14
Xmms is a great mp3 player.  It does not chew up a lot of cpu.

Viruses are sparse on linux/unix probably because of the way things are made, and not because of market share.  There are a staggering number of linux and unix machines serving the internet.  Unix and linux have a greater market share of the internet server market.

There are fewer opportunities for viruses to run than on a windows based machine.

---

### Post by Moobert on 2005-05-14
in answer to your first question if you are in a hurry to get firefox 1.0.4, you can take a look at the backports at: [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

or install the package from [www.getfirefox.com](www.getfirefox.com) to your home space and then del this when ubuntu updates. Do this by:

untaring the package to /home/<user> 

and running the 'firefox-installer'

cd ~/firefox-installer
sh firefox-installer

Then follow the gui installing to

/home/<user>/firefox-installer

then run firefox by

cd ~/firefox-installer
sh firefox

[QUOTE=davidmigl]
6. I know that very few viruses are written for Linux because of its low market share.
[/QUOTE]

Not true linux has a high market share in server systems, also it has been around as long as windows. So plenty of targets and time to write the viruses. First explains why we escape the virus/malware issue:

[http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/](http://www.theregister.co.uk/2003/10/06/linux_vs_windows_viruses/)

Basicly:

linux is a true multiuser system, thus prevents programs run by the user effecting the operating system. As to edit the os settings you need to be root user, which reqires the user to input a password. You aslo have proper control over your files, thus to get that e-mail virus

'read e-mai, save out file, become root, give executable permissions, run file'

Also linux is very different computer to computer thus a hack that works on one ystem wont work on another and again hackers have to get past the above system.

Being on a debian based system also means you get security updates at an 'sudo apt-get upgrade' and being from the open source model software is tested and fixed by 1000s of people.

not to mention the iptables, which are a firewall sytem at the bae system level wich uses very little ram/cpu.

On the issues of of mailware i'd say that 99% of my software comes from the ubuntu apt system in which i could if a wanted to see the source code and wot its doing to my pc and if i dont alot of people already have...

anyway welcome to linux, you can now regard viruses/malware was Windows bugs :)

---

### Post by davidmigl on 2005-05-14
Thanks for all the help.  When I try to install the w32 codecs by the following code,
```
sudo apt-get install w32codecs
```
, the terminal returns the following message: "E: couldn't find package w32codecs"

What am I missing?

EDIT:  I just saw the above post right after I posted this one.  Sorry for my assumption, I get the point that it is not caused by market share.  No more explanation necessary (your explanations do seem to make more sense).

---

### Post by Moobert on 2005-05-14
[QUOTE=davidmigl]Thanks for all the help.  When I try to install the w32 codecs by the following code,
```
sudo apt-get install w32codecs
```
, the terminal returns the following message: "E: couldn't find package w32codecs"

What am I missing?

[/QUOTE]

you need to get more apt-get sources, do it by following:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then refresh your apt list:
sudo apt-get update

[QUOTE=davidmigl]
EDIT:  I just saw the above post right after I posted this one.  Sorry for my assumption, I get the point that it is not caused by market share.  No more explanation necessary (your explanations do seem to make more sense).
[/QUOTE]

yeah, no need for the sorry... i probably went on abit :) Its just a comman theory... by people applying windows way of doing things to linux. When in fact they couldn't be more different.

---

### Post by bruizer on 2005-05-14
You also asked about changing your default applications. Go to System - Preferences - Preferred Applications to change the dault browser, email client or terminal.

Also, many of the basics for us newbies have been assembled on this site:
[http://ubuntuguide.org/](http://ubuntuguide.org/)

---

### Post by davidmigl on 2005-05-14
[QUOTE=Moobert]you need to get more apt-get sources, do it by following:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then refresh your apt list:
sudo apt-get update



yeah, no need for the sorry... i probably went on abit :) Its just a comman theory... by people applying windows way of doing things to linux. When in fact they couldn't be more different.[/QUOTE]
 [quote=Moobert]you need to get more apt-get sources, do it by following:
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then refresh your apt list:
sudo apt-get update[/quote]

I have added the extra repositories, but still get the same error message.  Is there any way to download it manually and install it by hand, through Synaptic Package Manager or something else?

---

### Post by poofyhairguy on 2005-05-15
[QUOTE=davidmigl]I have added the extra repositories, but still get the same error message.  Is there any way to download it manually and install it by hand, through Synaptic Package Manager or something else?[/QUOTE]


What you need to add is the backport repo:

[http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by atezun on 2005-05-15
[QUOTE=davidmigl]Hello all,
5. Whenever I try to open a .doc file from a Windows XP machine on a network, I get an error message: Error loading document [file name].  [file name] does not exist.”  However, when I copy the file onto the Ubuntu desktop, I can read it just fine.  What is happening and how do I get Ubuntu to play nice with Windows?[/QUOTE]

Well if you have an NTFS filesystem in WinXP which you most likely do, (pardon me if you do not) I beleive OpenOffice attempts to write a few things back to the partition mostly metadata and since Ubuntu can't write to NTFS it fails, I could be wrong though. I have the same problems with Archives i downloaded in Win2000, if you have a copy of partition magic, what i usually recommend is making a small FAT file partition to swap files between windows and linux (mines 10 Gigs but it can be much smaller) that way you can work with files between the two operating systems. However if you do decide to do this make sure you know EXACTLY what you're doing before you attempt this as you may already know playing with partitions can get rather messy.

---

### Post by Moobert on 2005-05-15
[QUOTE=davidmigl]I have added the extra repositories, but still get the same error message.  Is there any way to download it manually and install it by hand, through Synaptic Package Manager or something else?[/QUOTE]

apt-cache search -n w32codecs

returns ?

you can do it though by 

```

wget ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20050412-0.0_i386.deb

sudo  dpkg -i w32codecs_20050412-0.0_i386.deb

```

but its easier into apt-get in the long run

---

### Post by dweeb on 2005-05-15
Howdy! 

 I am brand new to the ubuntu/linux world, and am overjoyed to find such a helpful community here.  I think that I will struggle on my own to solve some issues that I am having, then crawl back here to confess that I am truly an idiot.

Do chicks dig guys that manipulate their ubuntu?

dweeb

---

### Post by TravisNewman on 2005-05-15
My fiancee digs me ;) Kassetra, one of the mods, is a "chick" as you call them (;)).

EDIT: It occurs to me that the previous comment may sound like Kassetra IS my fiancee. That's not the case at all.

---

### Post by monchichi on 2005-05-15
davidmigl--

Are you using **AMD64** Ubuntu? If you are, the w32codecs are not available and will not work, because they are closed-source 32-bit codecs (hence the w and the 32). Just a thought.

---

### Post by dweeb on 2005-05-15
"Chicks" is not a good choice of words, in review!  

dweeb

---

### Post by davidmigl on 2005-05-15
@ atezun: Yes, I am using NTFS on the XP machine.  Reading files from the network is more of a conveniece than necessity, so I guess I can just skip over this.

@ monchichi: No, I'm using the 32-bit version (on a 233 MHz machine :grin:)

I need to try Moobert's suggestion before continuing.  I'll get back with you later.

---

### Post by davidmigl on 2005-05-17
[QUOTE=Moobert]apt-cache search -n w32codecs

returns ?

you can do it though by 

```

wget ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/w32codecs_20050412-0.0_i386.deb

sudo  dpkg -i w32codecs_20050412-0.0_i386.deb

```

but its easier into apt-get in the long run[/QUOTE]
 
"apt-cache search -n w32codecs" returns nothing.  I tried downloading the package and installing it manually.  Everything goes fine, but in the end, I am still unable to play the files.
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Looking at the big picture, this is what answers I have gotten:

1. Ubuntu will update this.  In the meantime, I could just edit the version in the about:config page.

2. Still unresolved.

3. Solved

4. Still unresolved

5. Not possible with NTFS file system

6. Don't worry about it.

So, pretty much the only thing left is how to play multimedia files.  I have tried using XMMS, but it hangs as soon as I hit the play button.  Could this be because of a slow machine?

---

### Post by bored2k on 2005-05-17
[QUOTE=panickedthumb]My fiancee digs me ;) Kassetra, one of the mods, is a "chick" as you call them (;)).

EDIT: It occurs to me that the previous comment may sound like Kassetra IS my fiancee. That's not the case at all.[/QUOTE]

:-O I did not know this ! :-P

---

### Post by davidmigl on 2005-05-17
Update: I installed alot of software after reading this thread: [http://www.ubuntuforums.org/showthread.php?t=22646&highlight=automatic+script](http://www.ubuntuforums.org/showthread.php?t=22646&highlight=automatic+script)

It was a script that automatically installed a bunch of programs that made ubuntu more ocnvenient.  Now I can play .mp3's and .wma's.   Thanks everyone!

---

### Post by Usha on 2005-05-19
Um, I installed clamav through synaptic, and it doesn't appear in the applications, and tried typing clamav in run application, but nothing.  How do I get it work or maybe  I didn't install all of the components?

---

### Post by bored2k on 2005-05-19
[QUOTE=Usha]Um, I installed clamav through synaptic, and it doesn't appear in the applications, and tried typing clamav in run application, but nothing.  How do I get it work or maybe  I didn't install all of the components?[/QUOTE]
 [http://ubuntuguide.org/#antivirusserver](http://ubuntuguide.org/#antivirusserver) might help you.

---

