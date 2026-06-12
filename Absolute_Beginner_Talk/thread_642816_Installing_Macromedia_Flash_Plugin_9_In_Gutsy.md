---
title: "Installing Macromedia Flash Plugin 9 In Gutsy"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by shuttleworthwannabe on 2007-12-17
When I read a couple of threads here about flash not installing even after going through the Add/Remove... or even clikcing on a Firefox pluging required alert message, NOTE: Add/Remove... confirms that Macromedia Flash plugin is installed; but flash does not work (even after rebooting). The problem seems to lie in the fact that the file **libflashplayer.so** in the tarball or the deb installer/or RPM installer, does not get to the destination folder of the respective browsers; I have confirmed this on my clean install of Gutsy.

I googled a bit and came a cross [this]("http://ubuntu-tutorials.com/2006/10/19/how-to-install-flash-player-9-for-linux/") solution. All credit to the owner of the site.


Briefly, the steps are:

1. Download Installer for Linux from [Adobe]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") into your home folder
2. Unpack the archive
3. Change into the unpacked folder: cd install_flash_player_9_linux
4. For Firefox: sudo cp libflashplayer.so /usr/lib/firefox/plugins/
5. For Opera: sudo cp libflashplayer.so /usr/lib/opera/plugins/
6. Done

Re-start the browsers.

Hope it helps,

S:popcorn:

---

### Post by Sef on 2007-12-17
The problem has been fixed if you download Flash from the repository.   For Opera, you need 9.50 beta.

---

### Post by shuttleworthwannabe on 2007-12-17
Yes, Sef. I tried that and it did not work for me. That's what made me go this route.

Thanks,
S

---

### Post by RawMustard on 2007-12-17
> **Sef said:**
> The problem has been fixed if you download Flash from the repository.   For Opera, you need 9.50 beta.

Not for me it hasn't, the damn thing doesn't work.  Damn as in it's a damned piece of crap software that we unfortunately need :(

---

### Post by shuttleworthwannabe on 2007-12-17
> Not for me it hasn't, the damn thing doesn't work.
I thought Sef's suggestion was correct,, unitl I did a clean install of Gutsy. went to Add/Remove..., installed the Macromedia Flash plugin, rebooted, and it DID NOT WORK.

Sorry Sef, it seems I am not alone,
S

---

### Post by shuttleworthwannabe on 2007-12-20
Erratic behavior I have noticed recently; Opera or even Firefox does not recognize that flash is installed even though the file libflashplayer.so is in the plugins folder.

I had to do this again: For Opera: sudo cp libflashplayer.so /usr/lib/opera/plugins/

and relaunch the browser to make it work.

Annoying, but at least I figured out a work around.
S

---

### Post by divali on 2007-12-20
Can anyone tell me where libflashplayer.so resides?

---

### Post by Presto123 on 2007-12-20
I have never had this issue when I download from the Adobe site and follow their directions. My Gutsy still kickin out the movies.

---

### Post by BCtom on 2007-12-20
I just installed Flash on a friend's machine who faced that same problem until I reread an article in Linux Magazine, January 2007 issue, called "Plug in your Browser." The author says that Flash is part of three problems that Linux Firefox posses: 1. Binary Distribution; 2. Architectural Problems; 3. Legal Problems. I got Flash working in a matter of minutes, but I used the manual method.

There are two ways of doing this, installing Flash Player on your browser, either local, as mentioned above, or system wide--in the root. But in Ubuntu, because of these three issues, you pretty much need to do a manual install as using Synaptic or the Flash installer won't do the job.

So I got the latest Flash Player: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Then I unpacked the .tgz file, and got a folder which has the libflashplayer.so file in it.

Without doing anything to the libflashplayer.so file, I made a directory called "plugins" in the /.mozilla/ directory, so I  now have /home/user_name/.mozilla/plugins and put the libflashplayer.so file in there.

I restarted Firefox, and had Flash working. Firefox will find it!

To get it to work system wide, put the libflashpalyer.so in /opt/firefox/plugins, chmod the file to 755. 

It's confusing, and time consuming to install Flash like this, but I can see the issues that are faced with Open Source--you gotta bend the rules a little bit to get what you want. In Widow$, there is an agreement that you are supposed to accept with Flash, so you really don't see that in Linux, so you sort of need to place the player/file in your browser, as opposed to having a self extracting installer do that for you.

---

### Post by BCtom on 2007-12-20
I found this today. This seems to be the most comprehensive set instructions for installing Flash that I have seen so far. The Author explains the bug and he has a two step process for installing FlashPlayer using the terminal.

[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

But I still think that shuttelworthwannabe's solution is the simplest. It's quick and dirty, and gets the job done. :)

---

### Post by shuttleworthwannabe on 2007-12-21
even quicker is someone suggested putting the libflashplayer.so in the profile folder
.opera/plugins 

you will have to create a folder in the .opera folder (hidden folder in home)

---

### Post by einfeldt on 2007-12-22
hi,

I just wanted to report the Shuttleworthwannabe's original tips work like a charm.  Follow them to the exact letter, and you will have no problems.

Do NOT attempt to use Synaptic to install the flash installer!!!  Here is what I did to successfully install Flash 9 under Gutsy 32 bit:

1.  I first went to Synaptic, and installed libflash-plugin.  I then tested a Flash site.  No joy.
2.  I tried to install the flashplugin-nonfree using Synaptic.  I then tested a Flash site.  No joy.  I received an error message in Synaptic that looked like this:

Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 90277 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--18:06:44--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.247.170.70
Connecting to fpdownload.macromedia.com|72.247.170.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   70.56 KB/s
   50K .......... .......... .......... .......... ..........  3%  155.26 KB/s
  100K .......... .......... .......... .......... ..........  5%  151.14 KB/s

<snip for brevity>

 2850K .......... .......... .......... .......... .......... 97%  114.63 KB/s
 2900K .......... .......... .......... .......... .......... 99%  113.67 KB/s
 2950K .......... ....                                       100%  120.51 KB/s

18:07:06 (139.09 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

3.  I then uninstalled flashplugin-nonfree using Synaptic.

4.  I then came to this forum and followed Shuttleworthwannabee's instructions to the letter.  

5.  Happiness ensued.  

I am not sure if it is necessary to first install libflash-plugin.  I am going to install Flash on another similar Gutsy box.  I will let you know the outcome here.

---
Christian Einfeldt,
Producer, The Digital Tipping Point

---

### Post by Leo the Lion on 2007-12-22
> **shuttleworthwannabe said:**
> When I read a couple of threads here about flash not installing even after going through the Add/Remove... or even clikcing on a Firefox pluging required alert message, NOTE: Add/Remove... confirms that Macromedia Flash plugin is installed; but flash does not work (even after rebooting). The problem seems to lie in the fact that the file **libflashplayer.so** in the tarball or the deb installer/or RPM installer, does not get to the destination folder of the respective browsers; I have confirmed this on my clean install of Gutsy.

I googled a bit and came a cross [this]("http://ubuntu-tutorials.com/2006/10/19/how-to-install-flash-player-9-for-linux/") solution. All credit to the owner of the site.


Briefly, the steps are:

1. Download Installer for Linux from [Adobe]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash") into your home folder
2. Unpack the archive
3. Change into the unpacked folder: cd install_flash_player_9_linux
4. For Firefox: sudo cp libflashplayer.so /usr/lib/firefox/plugins/
5. For Opera: sudo cp libflashplayer.so /usr/lib/opera/plugins/
6. Done

Re-start the browsers.

Hope it helps,

S:popcorn:

I'm very new to Ubuntu and I've been trying to follow your instructions but I have a question:
I've unpacked the flash player in Home and it created a folder called "install_flash_player_9_linux". In your instructions you say to "Change into the unpacked folder: cd instal_flash_player_9_linux". What does this mean? Better yet, could you give me a step by step of how to do this?

Thanks a bunch for your help.

---

### Post by einfeldt on 2007-12-22
Hi Leo the Lion,

You wanted to know how to do this command:

cd instal_flash_player_9_linux

First, let me point out that there is a typo in the command that you have written above.  That might be why you are having problems.  You left out the second "L" in install_flash.. 

I am in the process of tying up a few other instructions, but first please check your spelling and re-run that command.

Also, please let me ask, do you know how to open a shell terminal?  You can do so by going to Applications > Accessories > Terminal.  You will find the "Applications" menu in the very upper right hand corner of your screen.  Please let me know if that helps, or if you need more help.

---

### Post by einfeldt on 2007-12-22
Hi Leo The Lion,

You wanted to know how to run the following command:

cd install_flash_player_9_linux

It's a little intimidating at first, but if you go slowly and methodically, it will work out for you.  First, you might need to tell us what version of Ubuntu you are using, because there are lots of varieties.  I am assuming that you are using Gutsy Ubuntu (version 7.10). If you don't know what this means, please feel free to ask.  If you are using Gutsy, here is how how you do it:

Go to Applications > Accessories > Terminal. You will find the "Applications" menu in the very upper right hand corner of your screen.  When you click on Terminal, you will get a window that looks like the old DOS system (but it's much more powerful than DOS).  You will see something that looks like

LeoTheLion@LeosComputer:~$

That is what we call a "shell prompt."  It is asking you to tell it what to do.  There you can just paste in the command

cd install_flash_player_9_linux

then hit enter.

If that is not enough detail, please feel free to ask more questions.

---
Christian Einfeldt,
Producer, The Digital Tipping Point

---

### Post by einfeldt on 2007-12-22
hi, 

someone suggested a different solution for installing Flash 9 on Gutsy.  This solution did NOT work, so I wanted to post it here for the benefit of all.  Again, it seems as if the solution offered at the top of this post by Shuttleworthwannabe works just fine.  But don't try this, because at least as of 22 December 2007, it does not work:

$ sudo aptitude install flashplugin-nonfree

Here is what happened when I tried it:

cje@sb:~$ sudo aptitude install flashplugin-nonfree
[sudo] password for cje:
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done            
The following NEW packages will be installed:
  flashplugin-nonfree
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 18.1kB of archives. After unpacking 160kB will be used.
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse flashplugin-nonfree 9.0.48.0.2+really0ubuntu12 [18.1kB]
Fetched 18.1kB in 1s (10.9kB/s)           
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 97260 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--19:10:19--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.170.70
Connecting to fpdownload.macromedia.com|72.246.170.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%  157.09 KB/s
   50K .......... .......... .......... .......... ..........  3%  156.24 KB/s
  100K .......... .......... .......... .......... ..........  5%  152.72 KB/s
  150K .......... .......... .......... .......... ..........  6%  158.21 KB/s
 
<snipped for brevity>

 2800K .......... .......... .......... .......... .......... 96%  155.38 KB/s
 2850K .......... .......... .......... .......... .......... 97%  151.19 KB/s
 2900K .......... .......... .......... .......... .......... 99%  154.57 KB/s
 2950K .......... ....                                       100%  161.88 KB/s

19:10:40 (139.36 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

Reading package lists... Done            
Building dependency tree      
Reading state information... Done
Reading extended state information     
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done            
cje@sb:~$

---

### Post by einfeldt on 2007-12-22
Hi Leo The Lion,

It just occurred to me that you might not realize what directory you are in when you open your shell terminal.  So, let me start over.  Go to Applications > Accessories > Terminal. You will find the "Applications" menu in the very upper right hand corner of your screen. When you click on Terminal, you will get a window that looks like the old DOS system (but it's much more powerful than DOS). You will see something that looks like

LeoTheLion@LeosComputer:~$

That is what we call a "shell prompt." It is asking you to tell it what to do.  

Now here is the part that I didn't tell you before.  At the $ sign, you will see a blinking cursor.  At that point, please type

$ pwd

Your who line should look like this:

LeoTheLion@LeosComputer:~$ pwd

Then hit enter.  You should then see something like this:

LeoTheLion@LeosComputer:~$ pwd
/home/LeoTheLion
LeoTheLion@LeosComputer:~$

The command "pwd" means that you are asking the computer to Print the Working Directory.  The "Working Directory" is the folder that you are working in.  So in the above example, it means that you are in LeoTheLion's home directory. 

Whenever you see something like this:

LeoTheLion@LeosComputer:~$

It means that Linux has finished doing what you asked it to do, and it is waiting for you to do something else.  When you type "pwd" you are telling it to tell you what directory (folder) you are in.  If you are a new user, you probably find that the Adobe file has downloaded into the Desktop folder, meaning that you should be able to see it on your desktop.  So to go to the Desktop directory, you should please type this:

LeoTheLion@LeosComputer:~$ cd Desktop

and hit enter.  Then you should see something like this:
 
LeoTheLion@LeosComputer:~Desktop$ 

On my computer, I know  I am in my Desktop directory, when I see this:

cje@sb:~/Desktop$

Do you see the pattern?

That means that you have just changed directories (cd) into the Desktop directory.  To confirm that you have downloaded the Adobe file into that directory, please type this:

LeoTheLion@LeosComputer:~Desktop$  cd install_flash_player_9_linux

Now if you type pwd, you should see this, (as it appears on my computer):

cje@sb:~/Desktop/install_flash_player_9_linux$ 

Now you are in the correct place to type the next command to install Adobe, assuming that you have unpacked the Adobe software.  If you need help unpacking the Adobe software, please just ask here.

---
Christian Einfeldt,
Producer, The Digital Tipping Point

---

### Post by GCCC on 2007-12-22
I just tried shuttleworthwannabe's method, and couldn't get it to work.

I have Firefox 2.0.0.11 running on a 64 bit system, which I just updated using ubuntuzilla.  This fixed a problem I was having where Firefox would hang and turn black whenever I went to a Flash-enabled site.  The problem started when I upgraded from Feisty to Gutsy.

I had used a similar method as shuttleworthwannabe's to get Flash to work in Feisty the last time, but now, the flash player seems to not load.  Firefox notices the plugin is there, because it doesn't prompt me to download the plugin, but it also won't show anything.

Any thoughts?

---

### Post by boo-koo2 on 2007-12-23
Thanks  shuttleworthwannabe 

Your method at the beginning (first post of this thread) worked for me.  

I had to do it for mozilla and iceweasel

---

### Post by CCNA_student on 2007-12-23
GCCC, I thought that there was no version of Adobe Flash Player for the 64bit version of Linux, but maybe that changed very recently. And if anyone is still have trouble getting Adobe Flash Player installed, I put detailed instructions on my Linux User's Group blog. 

         Sin Cere,

         CCNA

---

### Post by boo-koo2 on 2007-12-23
I think some people may be confused here.  When you go to adobe website just download the tar ball but DO NOT follow the instructions on the adobe website.

Instead simply right click on the downloaded file named: install_flash_player_9_linux.gz

then choose "Extract here"

this will create a folder that has the file we need inside.  Now just navigate to that directory using "Konsole"

Now go into package manager Adept or Synaptic and uninstall the "flashplugin-nonfree" so you dont have any conflicts.

and then follow the instructions given in the first thread.  Simple.  If you use firefox then change the word "mozilla" to "firefox" and if you use swiftweasel then change "mozilla" to "iceweasel"

---

### Post by metalf8801 on 2007-12-23
> **BCtom said:**
> I just installed Flash on a friend's machine who faced that same problem until I reread an article in Linux Magazine, January 2007 issue, called "Plug in your Browser." The author says that Flash is part of three problems that Linux Firefox posses: 1. Binary Distribution; 2. Architectural Problems; 3. Legal Problems. I got Flash working in a matter of minutes, but I used the manual method.

There are two ways of doing this, installing Flash Player on your browser, either local, as mentioned above, or system wide--in the root. But in Ubuntu, because of these three issues, you pretty much need to do a manual install as using Synaptic or the Flash installer won't do the job.

So I got the latest Flash Player: [http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Then I unpacked the .tgz file, and got a folder which has the libflashplayer.so file in it.

Without doing anything to the libflashplayer.so file, I made a directory called "plugins" in the /.mozilla/ directory, so I  now have /home/user_name/.mozilla/plugins and put the libflashplayer.so file in there.

I restarted Firefox, and had Flash working. Firefox will find it!

To get it to work system wide, put the libflashpalyer.so in /opt/firefox/plugins, chmod the file to 755. 

It's confusing, and time consuming to install Flash like this, but I can see the issues that are faced with Open Source--you gotta bend the rules a little bit to get what you want. In Widow$, there is an agreement that you are supposed to accept with Flash, so you really don't see that in Linux, so you sort of need to place the player/file in your browser, as opposed to having a self extracting installer do that for you.

Thanks that worked great

---

### Post by Leo the Lion on 2007-12-23
Einfeldt,
WOW, what a great help that was. You truly bring out the meaning of Ubuntu! 
Thanks a bunch for the step by step instructions. They did the trick and I learned a few basic commands.

---

### Post by einfeldt on 2007-12-23
> **Leo the Lion said:**
> Einfeldt,
WOW, what a great help that was. You truly bring out the meaning of Ubuntu! 

My pleasure!  Lots and lots of people have helped me.  So it was a pleasure to pass it along!

> 
Thanks a bunch for the step by step instructions. They did the trick and I learned a few basic commands.

Yeah, that's cool.  The command line can be scary, but it is also really powerful and really useful once you get the hang of it.  And kudos to you, too, for sticking in there and figuring it out and not tossing in the towel.  

LeoTheLIon, if you are not a member of any LUG mailing lists, you might want to consider joining one.  I am sure that Ubuntu here has several good mailing lists.  I happen to belong to the international WFTL-LUG mailing list, which you can find here:

[http://www.marcelgagne.com/wftl-lug.html](http://www.marcelgagne.com/wftl-lug.html)

The feature that I appreciate about that list is that it is for multiple Linux distros, whereas the Ubuntu email lists will probably expect you to stay on topic with Ubuntu, which is fine for that purpose.  I am not saying anything bad at all about the Ubuntu emailing lists, since I obviously use Gutsy and this forum has been really helpful for me in using Gutsy.  But if you find that you have issues that are not strictly Ubuntu issues, then you might want to consider joining a similar list that addresses more broad Free Open Source Software issues.  Of course, you can keep using this forum and you can also join the Ubuntu lists.  The power of Ubuntu is that it has a really awesome community.

see ya

---
Christian Einfeldt
Producer, The Digital Tipping Point

---

### Post by casper911ca on 2008-01-24
thanks a bunch "shuttleworthwannabe" this worked great!

---

### Post by svQuick on 2008-01-25
Just like hooked on fonics, it works for me!!!!

---

### Post by Nuggs on 2008-01-25
Just thought I'd mention that I had a similar problem with the flash plugin a week ago, and I fixed it by removing the plugin using Synaptic Package manager, and downloading the plugin from the adobe website.  I installed it following the instructions on the website, and it worked for me...  

FYI, I'm using Firefox in Gutsy...

---

