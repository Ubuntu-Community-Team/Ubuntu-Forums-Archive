---
title: "Problems with Realplayer10gold.bin"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by tickmike on 2007-01-06
Hello All.
I have been trying  'Edgy Eft' for about one week and I'm very very imprested, I was introduced to the world of Linux when I built a 'Smoothwall Box' Firewall  (  [http://www.smoothwall.org](http://www.smoothwall.org)   )   and  think I am hooked on it now, good bye windows !.

I have installed the Firefox 2 and Opera browsers ok. (using copy and paste scripts off the guide).
I would like to install 'Realplayer 10 gold' , I have STF and read the Guide and tried a few ways to install without in any luck.

I have downloaded 'realplayer10gold.bin' in    home/michael/downloads/  

But I cannot install it.
Help please.

Michael

---

### Post by jvc26 on 2007-01-06
Have you:
Right clicked the file, properties, permissions, allow executing
Then closed permissions and tried double clicking on it?
Il

---

### Post by obsidion on 2007-01-06
> **tickmike said:**
> Hello All.
I have been trying  'Edgy Eft' for about one week and I'm very very imprested, I was introduced to the world of Linux when I built a 'Smoothwall Box' Firewall  (  [http://www.smoothwall.org](http://www.smoothwall.org)   )   and  think I am hooked on it now, good bye windows !.

I have installed the Firefox 2 and Opera browsers ok. (using copy and paste scripts off the guide).
I would like to install 'Realplayer 10 gold' , I have STF and read the Guide and tried a few ways to install without in any luck.

I have downloaded 'realplayer10gold.bin' in    home/michael/downloads/  

But I cannot install it.
Help please.

Michael


  Open a terminal

cd to your download direectory

chmod a+x Rea  hit tab to autocomplete hit enter.
This makes it an executable file

sudo ./Re hit tab hit enter

 Using sudo will allow you to install system wide rather just for your user and it will install the plugins for mozilla and firefox as well.  Note that my bin is called
RealPlayer10GOLD.bin
 The caps are important in linux

---

### Post by tickmike on 2007-01-07
Hi.Illuvator and obsidion, Thank you for your help and tips.

I have realpayer/ helix now installed, but on firefox it says "bad transport" on opera it is wanting a plug-in.
I have set up my proxy for helix ok.

Any ideas ?.

Michael.

---

### Post by obsidion on 2007-01-07
> **tickmike said:**
> Hi.Illuvator and obsidion, Thank you for your help and tips.

I have realpayer/ helix now installed, but on firefox it says "bad transport" on opera it is wanting a plug-in.
I have set up my proxy for helix ok.

Any ideas ?.

Michael.

  Have a look in /usr/lib/mozilla/plugins to make sure you only one set of rm plugins installed.
ie you should have only the two nphelix files there and not some mplayer or totem ones with rm in them.
  Also check that there are symlinks to those files in the /usr/lib/firefox/plugins directory. 
also what does about config with a : between the two rather than a space typed into firefox's address bar tell you.

---

### Post by tickmike on 2007-01-07
Hi .
Re...**.Have a look in /usr/lib/mozilla/plugins to make sure you only one set of rm plugins installed.**
In the lib folder I have two folders called "Firefox" and "Mozilla Firefox" in there 'plugins' folders they only have 'libunixprint[dot]so' in them !!! ?. 
Note.. just noticed the "Mozilla Firefox" is a short cut to the other folder.?

Re...**Also check that there are symlinks to those files in the /usr/lib/firefox/plugins directory**.
Not sure what you mean ?

Re...**also what does about config with a : between the two rather than a space typed into firefox's address bar tell you.**
Its only got these in for plugins (none for Helix or realplayer)
plugin.default_plugin_disabled =true
plugin.expose_full_path=false
plugin.override_internal_types=false

Michael.

---

### Post by obsidion on 2007-01-07
> **tickmike said:**
> Hi .
Re...**.Have a look in /usr/lib/mozilla/plugins to make sure you only one set of rm plugins installed.**
In the lib folder I have two folders called "Firefox" and "Mozilla Firefox" in there 'plugins' folders they only have 'libunixprint[dot]so' in them !!! ?. 
Note.. just noticed the "Mozilla Firefox" is a short cut to the other folder.?

Re...**Also check that there are symlinks to those files in the /usr/lib/firefox/plugins directory**.
Not sure what you mean ?

Re...**also what does about config with a : between the two rather than a space typed into firefox's address bar tell you.**
Its only got these in for plugins (none for Helix or realplayer)
plugin.default_plugin_disabled =true
plugin.expose_full_path=false
plugin.override_internal_types=false

Michael.

  Ok we need to symlink them from the realplayer directory to the /usr/lib/firefox/directory then.

Where did you install realplayer ?

Did you use the been method or did you use another method ?


Are there any files in /usr/lib/mozilla/plugins  if so what ?

---

### Post by tickmike on 2007-01-07
> **obsidion said:**
> Ok we need to symlink them from the realplayer directory to the /usr/lib/firefox/directory then.

Where did you install realplayer ?

Did you use the been method or did you use another method ?


Are there any files in /usr/lib/mozilla/plugins  if so what ?


Re...**Where did you install realplayer ? **
 I just did what you said in your first post to me.

Re....**Did you use the been method or did you use another method ?**   
Pass ?   I first downloaded the realplayer  for linux ( as my first post) then did what 'Illuvator' told me to do, then followed what you told me.

Re...**Are there any files in /usr/lib/mozilla/plugins  if so what.. **  
Yes one . ....libunixprint.so

I'm on one of my windows machines now and will try some more later,
do you think I should uninstall and reinstall again ?

 "**symlink**" does this mean system link ?

Michael

---

### Post by obsidion on 2007-01-08
>>Where did you install realplayer ? ]
> I just did what you said in your first post to me.

  Ok then the files should be in /usr/lib/mozilla/plugins
with symlinks in /usr/lib/firefox/plugins

>Re...**Are there any files in /usr/lib/mozilla/plugins  if so what.. **  
>Yes one . ....libunixprint.so

Ok they haven't installed where they should
Now you have to find where realplayer installed, you could try running it from the menu and telling it to configure the mozilla plugins first though.


>I'm on one of my windows machines now and will try some more later,
>do you think I should uninstall and reinstall again ?

 No that is a windows fix.
Once you know where you installed realplayer and can give me the directory I can give you how to symlink the files to firefoxes plugins directory. Mine is in /usr/local/Real for instance.


>symlink does this mean system link ?

No it means symbolic link, it is a link from a file in one directory so another directory knows how to run it. 
You could probably find a better description than my poor attempt if you do a google for it though :)

---

### Post by tickmike on 2007-01-08
Hi. First thing I only have 'Helix Player 1.0.6.778 (experimental) on my system from RealNetworks is this ok  ?,it was downloaded from the realplayer site for Linux.

On the Helix Player >tools>plugins there is a lot in there .

Did a search for RealPlayer folder, The only place it was in my downloads folder.
So I cut/copied it to a 'temp' folder out of the way ( to be deleted later if not required).

Then I went though this again.
**you said**...
Open a terminal

cd to your download directory

chmod a+x Rea hit tab to autocomplete hit enter.
This makes it an executable file

sudo ./Re hit tab hit enter

and I followed more closely what it said in the terminal window.
when it got to where do you want the 'symlink' to piont to ?. =    /usr/lib/firefox/plugins directory
It configured it and said it was ok.

ok now we have an entry in Applications>sound&video>RealPlayer10..  But try to open it says..error..could not launch menu item..details failed to execute child process "realplay" (no such file or directory).

My real folder is in /usr/local/real            should this real folder be called realplayer ? or realplay  ? or not..

**You said.**...Have a look in /usr/lib/mozilla/plugins to make sure you only one set of rm plugins installed.
libunixprintplug.so    ,    nphekix.so (shortcut arrow on it)   ,    nphelix.xpt  (shortcut arrow on it)

**You said** .......Also check that there are symlinks to those files in the /usr/lib/firefox/plugins directory.
Yes its the same ones as above. =   
libunixprintplug.so    ,    nphekix.so (shortcut arrow on it)   ,    nphelix.xpt  (shortcut arrow on it)

The ones with these shortcut arrows on (as in window os ) are they the symlinks ?.

Now just looked in /usr/local/real/mozila   two files =  nphelix.so and nphelix.xpt


Now just looked in /usr/local/real/plugins    there is lots in there. 

I do appreciate your help.
Michael.:)

---

### Post by obsidion on 2007-01-08
Did you do this as described on the heliplayer page.

# Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x hxplay-1.0.8.806-linux-2.2-libc6-gcc32-i586.bin" command from a terminal window.
# Execute the .bin file by typing hxplay-1.0.8.806-linux-2.2-libc6-gcc32-i586.bin. It will provide you with several prompts and will walk you through the installation.
# Confirm that the installer has copied the nphelix.so and nphelix.xpt files to your mozilla plugins directory. If you installed as root, this should be under /usr/lib/mozilla/plugins. If you installed as a user, they will be under ~/.mozilla/plugins.
# If your distribution uses a different folder for mozilla plugins, or if the install failed to copy the plugins, you may have to copy the plugin manually. After copying the files to the Mozilla plugins directory restart mozilla, and look at "about:plugins" in mozilla to check that they are being loaded. It should look like this:

Helix DNA Plugin
File name: nphelix.so
Helix DNA Plugin (for Mozilla)
MIME Type 	Description 	Suffixes
	Enabled
audio/x-pn-realaudio-plugin 	RealPlayer Plugin Metafile 	rpm 	Yes

---

### Post by obsidion on 2007-01-08
Re reading your original post
> I have downloaded 'realplayer10gold.bin' in home/michael/downloads/ 

Now you are saying

> Hi. First thing I only have 'Helix Player 1.0.6.778 (experimental) on my system from RealNetworks is this >ok ?,it was downloaded from the realplayer site for Linux.

  You keep moving the goalposts making it difficult to help or advise you. I was giving advice on the basis that you were installing realplayer instead you now tell us you only have helix player and rather an old one as well. I downloaded helixplayer myself and it installed fine as per the instructions on the website and installed the plugins to the correct place to make them system wide. I have no idea why yours won't install properly either it is because of the older version or you are just not following instructions properly.

---

### Post by tickmike on 2007-01-08
From the download page at  [http://www.real.com/linux/](http://www.real.com/linux/)    it says

 "What's Helix and why does it matter?
RealPlayer 10 for Linux is based on the open source Helix player"

So it installed the Helix player with RealPlayer. I have not installed them separately. The Helix player will open up the realplayer will not.

At the moment I'm installing Ubuntu 6.1 (Edgy Eft) on another spare computer because I want to compare the file folders as they were before I installed Firefox2 .

Michael.

---

### Post by obsidion on 2007-01-08
Ok the short cut arrows are symlinks, but why are you using a file manager the instructions were how to use a terminal.

  From a terminal type realplay and see there are any errors, I'm not at all sure what you have installed atm, one post it is realplayer then it is helix player, they are two different things albiet that perform a similar function.

---

### Post by obsidion on 2007-01-08
First you say you have downloaded realplayer gold then you say you only have helix player experimental on your system and now you apparently downloaded them both in the one package and installed them both.
 So what have you installed, where did you get the file and what was the name of the bin you did install ?
1.06 helix player is old. I can't see a download for helix player on the real.com homepage though I do see one here.
[https://player.helixcommunity.org/2005/downloads/](https://player.helixcommunity.org/2005/downloads/)

 You are going around in circles and making it increasingly difficult to figure out what you have done, installing ubuntu on another computer and comparing them may give you some ideas.

---

### Post by tickmike on 2007-01-09
Hello
Update ---- second computer with Edgy Eft.
New install went ok on second computer, installed RealPlayer ok, tested it on BBC news web site-video, It tried to work, It played a video, But no sound, and green flicker on the picture.( At least I got some-thing ! )

In Firefox browser it said I had the plugins you told me about.

Then tonight I have installed the latest Firefox2 browser ok, and video still works as above. 

-------------------------------------------------------------------------------------------------------------------
Now first computer.

what has happened realplayer also firefox has installed Multi lots of files and folders all over the place .Opp's

Eg.Did a search on computer 2 for "Firefox" it came up with 48 files.

Did a search on computer 1 for "Firefox" it came up with  86 files.

Did a search on computer 2 for "RealPlay" it came up with 7 files.

Did a search on computer 1 for "RealPlay" it came up with 83 files.

Shall I reinstall ( is that the easiest way ) or can they be deleted and make a fresh start and install them again in the correct place this time.

Well I'm on a steep leaning curve.
I have had no formal computer training. 
Michael.

---

### Post by obsidion on 2007-01-09
[QUOTE=tickmike;1991037]Hello

> Shall I reinstall ( is that the easiest way ) or can they be deleted and make a fresh start and install them again > in the correct place this time.

> Well I'm on a steep leaning curve.
> I have had no formal computer training. 

 It smooths out believe me :)

Ok what does sudo dpkg -l |grep firefox 
and                  sudo dpkg -l |grep realplay 


Tell you, it would seem like you have multipule installs of firefox and realplayer.


  I'm guessing that you have a local install of realplayer and a systemwide install and the firefox plugins are a little confused about it :)

  If you installed them via the bin method then you can sudo rm -rf therealfolder.
This will delete it and all its files, be very careful with this though and make sure you know which folder you are removing and type correctly. If you installed them via synaptic or another package manager then you can sudo apt-get remove theprogram.

  I am not sure of what you have done on your computer, so I'm shooting in the dark about how to fix it.
The problems you are having with realmedia is just something I have never experianced the several times I have installed realplayer on mine and other people's computers I have done exactly what I explained to you and I have never had a problem. You either have a very weird computer/net connection or you somehow did not follow the instructions I gave you and the real website outlined as well. Typos can make a big difference in linux, it is case sensitive so a capital in the wrong place or a one instead of a small L can make a huge difference as to the function performed for instance.

  Reinstalling is a windows solution, it is better to find out what you did wrong and fix it otherwise you just won't know and could perform the same mistake again.

---

### Post by tickmike on 2007-01-12
Update ..I have not forgot about this post.
I have lost all admin functions, see....   [http://www.ubuntuforums.org/showthread.php?t=335749](http://www.ubuntuforums.org/showthread.php?t=335749)

So until I get them back I cannot do any further functions with this post.

---

### Post by tickmike on 2007-01-14
Hello .
I'm back again after sorting out my other problem.

I did this...
michael@vectra:~$ sudo dpkg -l |grep firefox
Password:
ii  firefox                                1.5.dfsg+1.5.0.9-0ubuntu0.6.06    lightweight web browser based on Mozilla
ii  firefox-gnome-support                  1.5.dfsg+1.5.0.9-0ubuntu0.6.06    Support for Gnome in Mozilla Firefox
ii  firefox-themes-ubuntu                  0.4.5    Firefox themes matching the Ubuntu desktop l
ii  libnspr-dev                            1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06 Netscape Portable Runtime library - developm
ii  libnspr4                               1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06 Netscape Portable Runtime Library
ii  libnss-dev                             1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06 Network Security Service Libraries - develop
ii  libnss3                                1.firefox1.5.dfsg+1.5.0.9-0ubuntu0.6.06 Network Security Service Libraries - runtime
ii  mozilla-firefox-locale-en-gb           1.5.0.1ubuntu6-2    Mozilla Firefox English language/region pack
michael@vectra:~$ sudo dpkg -l |grep realplay
michael@vectra:~$

as you can see the realplayer was blank .. even when I have all the files installed. 
you said ..**.If you installed them via the bin method**   What is that ?.

Sould I try deleting the realplayer files and start again ?.

Edit .. I have just thought that at my first time I tried to install Realplayer the computer froze and I had to switch of the computer and reboot ..Maybe that corrupted the files.?


Michael

---

### Post by tickmike on 2007-01-16
update.

Well I tried ..sudo apt-get remove  realplayer    it said could not find the files.
 
synaptic package manager will not let me mark realplayer and its not in add/remove programs  ](*,)

---

