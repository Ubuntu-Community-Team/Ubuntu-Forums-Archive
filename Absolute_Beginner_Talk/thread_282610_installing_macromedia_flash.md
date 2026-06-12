---
title: "installing macromedia flash"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by Sarah13 on 2006-10-23
Can anyone help me? I admit it, I've only used linux for all of 2 hrs now, so I'm not too familiar with how it works.

So here's the situation. I'm trying to install a flash player so that I can watch all the flash videos on the net; I'm a real big multimedia person.

I went to the Adobe Flash Player download center, and I downloaded the linux version of Macromedia flash player. I now have a file called install_flash_player_7_linux.tar.gz. A little while ago I tried to extract it to the tmp folder and then install it from there, but that didn't work. What do I need to do?

The site says to " Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s)."

Do they mean run the line "./flashplayer-installer" in terminal?

Anyone know what I should do? Any help would be appreciated.

---

### Post by Dr. Nick on 2006-10-23
you must be in the directory its extracted to to install it that way.

---

### Post by Dr. Nick on 2006-10-23
Oh, and flash player 7 is a older version, You can install 9 pretty easy using post 7 here
[http://ubuntuforums.org/showthread.php?t=282198&highlight=flash+9](http://ubuntuforums.org/showthread.php?t=282198&highlight=flash+9)

may be a bit different on the directory names though, post  what browser you use if you need some help

---

### Post by Dr. Nick on 2006-10-23
\\:D/Oh an Welcome to the forums

If you are using firefox (or maybe konqueror if your on KDE) you may also be able to go to a site that uses flash and click the green paperclip, that works sometimes

To see if firefox sees the plugin installed type 

```
about:plugins
``` into the address bar

---

### Post by Sarah13 on 2006-10-23
Alright, so I browsed a bit and got entered this code into the terminal rather than going thru firefox.

This is what it showed. What's next?

penguin@penguin:~$ wget [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz)
--22:41:59--  [http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz](http://download.macromedia.com/pub/labs/flashplayer9_update/FP9_plugin_beta_101806.tar.gz)
           => `FP9_plugin_beta_101806.tar.gz'
Resolving download.macromedia.com... 72.246.115.191
Connecting to download.macromedia.com|72.246.115.191|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,609,188 (2.5M) [application/x-gzip]

100%[====================================>] 2,609,188     17.17K/s    ETA 00:00

22:44:32 (16.62 KB/s) - `FP9_plugin_beta_101806.tar.gz' saved [2609188/2609188]

penguin@penguin:~$ tar xvzf FP9_plugin_beta_101806.tar.gz
flash-player-plugin-9.0.21.55/
flash-player-plugin-9.0.21.55/libflashplayer.so
flash-player-plugin-9.0.21.55/readme.txt
penguin@penguin:~$ sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/flashplugin-nonfree/
Password:
**(Here I entered what I thought was my password)**Sorry, try again.
Password:
sudo: 1 incorrect password attempt

---

### Post by Sarah13 on 2006-10-23
> **Dr. Nick said:**
> \\:D/Oh an Welcome to the forums

If you are using firefox (or maybe konqueror if your on KDE) you may also be able to go to a site that uses flash and click the green paperclip, that works sometimes

To see if firefox sees the plugin installed type 

```
about:plugins
``` into the address bar

Yeah, I was hoping it would be that easy, and I tried that first, but it fails to install.

---

### Post by Synikk on 2006-10-23
> **Sarah13 said:**
> Can anyone help me? I admit it, I've only used linux for all of 2 hrs now, so I'm not too familiar with how it works.

So here's the situation. I'm trying to install a flash player so that I can watch all the flash videos on the net; I'm a real big multimedia person.

I went to the Adobe Flash Player download center, and I downloaded the linux version of Macromedia flash player. I now have a file called install_flash_player_7_linux.tar.gz. A little while ago I tried to extract it to the tmp folder and then install it from there, but that didn't work. What do I need to do?

The site says to " Navigate to this directory and from the command line type ./flashplayer-installer to run the installer (Note: this can only be run from the command line). The installer will instruct you to shut down your browser(s)."

Do they mean run the line "./flashplayer-installer" in terminal?

Anyone know what I should do? Any help would be appreciated.

Okay, here's the deal:

1. Flash 7 is old. You need Flash 9 to watch Flash videos with Ubuntu.

2. Download this file into your home directory: [flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb")

4. Close Firefox.

5. Open Terminal and copy and paste this line into it:
```
sudo dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
```

6. 2 installation screens should come up, one after another. Choose "Yes" for both of them.

After that, Flash 9 for Firefox should be installed. Go to Youtube or whatever site you like that uses Flash to make sure it worked. These instructions worked for me without any problem :) 

I hope this helps.

---

### Post by Perfect Storm on 2006-10-23
Just a note; Flash 9 beta is still full of bugs.

---

### Post by Sarah13 on 2006-10-23
> **Synikk said:**
> Okay, here's the deal:

1. Flash 7 is old. You need Flash 9 to watch Flash videos with Ubuntu.

2. Download this file into your home directory: [flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb]("http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb")

4. Close Firefox.

5. Open Terminal and copy and paste this line into it:
```
sudo dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
```

6. 2 installation screens should come up, one after another. Choose "Yes" for both of them.

After that, Flash 9 for Firefox should be installed. Go to Youtube or whatever site you like that uses Flash to make sure it worked. These instructions worked for me without any problem :) 

I hope this helps.

I did as you suggested, and this is the error I got.

penguin@penguin:~$ sudo dpkg -i flashplugin-nonfree_9.0.21.55vlubuntu0_i386.deb
dpkg: error processing flashplugin-nonfree_9.0.21.55vlubuntu0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 flashplugin-nonfree_9.0.21.55vlubuntu0_i386.deb
penguin@penguin:~$


I assume this means it's not seeing the file? I put it into the home folder.

---

### Post by Perfect Storm on 2006-10-23
Make sure you do the command where the package is.

You can;
cd <distination>


also check if it have the same name etc.

---

### Post by Sarah13 on 2006-10-23
Also, this is now affecting Synaptic Package monitor. When I try to open Synaptic up, I receive this error:

E: The package flashplugin-nonfree needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.


But if I try to reinstall the file, it will end up freezing up.

---

### Post by Sarah13 on 2006-10-23
> **Artificial Intelligence said:**
> Make sure you do the command where the package is.

You can;
cd <distination>


also check if it have the same name etc.

I checked to make sure they had the same name, but (my complete ignorance is showing here, lol) how do you type the command where the package is? Do you mean like what in windows would be a C:\ ?

---

### Post by Synikk on 2006-10-23
Did you put the installation deb into your home directory (in your case, "penguin")?

If not, put it there and run the installation command again.

---

### Post by aysiu on 2006-10-23
This should help you out:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

---

### Post by Sarah13 on 2006-10-23
> **aysiu said:**
> This should help you out:
[http://www.psychocats.net/ubuntu/flashubuntu](http://www.psychocats.net/ubuntu/flashubuntu)

Thanks! I can see the videos now, but they won't play. They load, but if I hit the play button it just sits there.

Any advice?

And Synikk, it is in my home directory.

---

### Post by Synikk on 2006-10-23
> **Sarah13 said:**
> Thanks! I can see the videos now, but they won't play. They load, but if I hit the play button it just sits there.

Any advice?

And Synikk, it is in my home directory.

It seems you typed in the command wrong:

> I did as you suggested, and this is the error I got.

penguin@penguin:~$ sudo dpkg -i flashplugin-nonfree_9.0.21.55vlubuntu0_i386.deb
dpkg: error processing flashplugin-nonfree_9.0.21.55vlubuntu0_i386.deb (--install):
cannot access archive: No such file or directory
Errors were encountered while processing:
flashplugin-nonfree_9.0.21.55vlubuntu0_i386.deb
penguin@penguin:~$

You typed the package name as being ```
flashplugin-nonfree_9.0.21.55vlubuntu0_i386.deb
``` instead of ```
flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
```

Notice the "-3" you missed before "v1ubuntu0_i386.deb"?

Make sure you type it in correctly, or simply copy and paste the command.

It's simply a typo, I've done that sort of thing before too :oops:

---

### Post by Sarah13 on 2006-10-23
> **Synikk said:**
> It seems you typed in the command wrong:



You typed the package name as being ```
flashplugin-nonfree_9.0.21.55vlubuntu0_i386.deb
``` instead of ```
flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
```

Notice the "-3" you missed before "v1ubuntu0_i386.deb"?

Make sure you type it in correctly, or simply copy and paste the command.

It's simply a typo, I've done that sort of thing before too :oops:

Oops. :oops: I didn't even see that I had entered it wrong. Thank you; you just saved me a lot of time. I'll try entering it the correct way after my software updates finish installing and post about the progress. I am hopeful that this will fix it. Maybe that was the package that EasyUbuntu wanted me to fix before it could install. Hopefully. :D

---

### Post by Sarah13 on 2006-10-23
Well, I fixed by typo and entered it into Terminal, and this is what I received.

penguin@penguin:~$ sudo dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
(Reading database ... 72640 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.21.55-3v1ubuntu0 (using flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.21.55-3v1ubuntu0) ...
Checking and removing obsolete files in users' home...


Does that mean it loaded fully? If I go to a site with embedded video, say YouTube, it will load the video, but when I hit play it will play a hundreth of a second or so, then pause for 5+ seconds, play another hundreth, etc. Within a few pauses, it stops completely. And there's no sound. So I'm assuming that there is still something wrong with the flash.

---

### Post by Synikk on 2006-10-23
> **Sarah13 said:**
> Well, I fixed by typo and entered it into Terminal, and this is what I received.

penguin@penguin:~$ sudo dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
(Reading database ... 72640 files and directories currently installed.)
Preparing to replace flashplugin-nonfree 9.0.21.55-3v1ubuntu0 (using flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb) ...
Unpacking replacement flashplugin-nonfree ...
Setting up flashplugin-nonfree (9.0.21.55-3v1ubuntu0) ...
Checking and removing obsolete files in users' home...


Does that mean it loaded fully? If I go to a site with embedded video, say YouTube, it will load the video, but when I hit play it will play a hundreth of a second or so, then pause for 5+ seconds, play another hundreth, etc. Within a few pauses, it stops completely. And there's no sound. So I'm assuming that there is still something wrong with the flash.

It should have brought up a blue screen inside of Terminal asking you to accept a license agreement (since the plugin is technically non-free). Something's wrong here :-k 

You installed Flash 7, right? There's probably a conflict, and you'll need to uninstall Flash 7 so Flash 9 will be used instead.

Worst case scenario, you uninstall both 7 and 9 and do a reinstall of 9.

I installed the Flash 9 plugin on a clean install of Ubuntu 6.06, so I didn't have Flash 7 installed previously, and it worked perfectly. Tested it on Youtube and all videos played flawlessly.

I'm a bit of a noob too, so if you end up having problems even after uninstalling/reinstalling the plugin, try asking in the #ubuntu IRC channel. Plenty of knowledgeable people hang out there.

---

### Post by Dr. Nick on 2006-10-24
Would you try using the epiphany browser for a minute?

I installed flash 7 and 9 at once, I think it always uses 9 though. But after this my flash playback in firefox has been goofed up, works perfect in epiphany though. 

If you want to try epiphany you may have to install the epiphany-browser package.

For some reason epiphany always seems better with all the plugins then FF

---

### Post by Sarah13 on 2006-10-24
> **Dr. Nick said:**
> Would you try using the epiphany browser for a minute?

I installed flash 7 and 9 at once, I think it always uses 9 though. But after this my flash playback in firefox has been goofed up, works perfect in epiphany though. 

If you want to try epiphany you may have to install the epiphany-browser package.

For some reason epiphany always seems better with all the plugins then FF

I installed epiphany, and the flash is still really choppy, with no sound (but I need to install a driver for my Soundblaster card, so that's unrelated). For me, unfortunately it handles the flash about the same as Firefox.

What else can I try? I'm ready to do just about anything to get the flash to work on this computer.

---

### Post by Dr. Nick on 2006-10-24
hmm, Which version of flash do you believe to have installed now, and how did you do it? I havent seen problems like this before, Mine has either worked or hasnt, their was no inbetweens.

And what soundblaster card is it? I had to set one up manually on another computer if you needed any help with it.

---

### Post by Sarah13 on 2006-10-24
> **Dr. Nick said:**
> hmm, Which version of flash do you believe to have installed now, and how did you do it? I havent seen problems like this before, Mine has either worked or hasnt, their was no inbetweens.

And what soundblaster card is it? I had to set one up manually on another computer if you needed any help with it.

I have Macromedia Flash 9, or the flash-player-plugin-9.0.21.55. I really don't know what the heck is going on with it; I have tried nearly every fix imaginable. I originally tried to just install it from Firefox (going to a page that needed Flash), but that didn't work, so I ended up downloading/installing it from the Macromedia site thru terminal. I might have messed it up (I don't think I did, but given that I'm a newbie, anything is possible).

It is weird that it only works half-way, I would think it would be an all or nothing thing, like it was in the beginning.
 
It's getting to the point where I'm wondering how long it would take me to reload Ubuntu. 

There were a couple mistakes made in installation, like giving the majority of the disk drive to /root rather than /home. It's not a big deal, and I know how to work around it using superuser, but its just an annoyance. I wouldn't rebother building the OS again just for that, but that coupled with the fact that my flash isn't working, and I'm going to be putting in a new sound card... I've been considering whether I just want to start over with a blank slate now that I have a vague idea of what I'm doing. :D  I have some programs installed, but I used Automatix2, so I could easily get those again.

Thanks for the offer of help. My dad and I figured out that the problem with my sound card was that Linux isn't recognizing it (its just an 8 bit sound card built into the motherboard). We have Soundblaster live which is a seperate chip in a computer we aren't using, so he's going to gut it and give me the memory and the Soundblaster card.

---

### Post by Dr. Nick on 2006-10-25
May just be easier to reload if you are going to redo the partition setups, Depending on the computer it shouldnt take long. I reloaded a few times aswell before i got the hang of it. 

One hint about the soundcard, If you can; disable the onboard one in the bios or via a jumper on the motherboard. I dropped a SB Live into a computer and it didnt work off the bat since ubuntu recgonized the non-working onboard one.


Once you install the sb card you can use "lsmod" to make sure the emul.. something module is loaded, also if it doesnt appear to work then check all the volume levels. mine "worked" but was muted.

---

### Post by Sarah13 on 2006-10-25
> **Dr. Nick said:**
> May just be easier to reload if you are going to redo the partition setups, Depending on the computer it shouldnt take long. I reloaded a few times aswell before i got the hang of it. 

One hint about the soundcard, If you can; disable the onboard one in the bios or via a jumper on the motherboard. I dropped a SB Live into a computer and it didnt work off the bat since ubuntu recgonized the non-working onboard one.


Once you install the sb card you can use "lsmod" to make sure the emul.. something module is loaded, also if it doesnt appear to work then check all the volume levels. mine "worked" but was muted.


Thanks for the advice! I think I actually will end up reloading it; we had to do it once before because we loaded Ubuntu, but then it wouldn't connect to the hard drive (we found out an old cable had broken, so not Ubuntu's fault) so we reloaded it. At this point in time, like you said, since I'm repartitioning it, it would probably be the easiest. My dad said we could do it through kernels, but all things considered, the cd is a bit easier.:D

---

### Post by Sarah13 on 2006-11-04
My flash works now!!! I decided to update Firefox to Firefox 2.0, and now I can play flash videos! No skipping or stopping.

Now I just need to get my SOUND working so I can actually hear the videos. :D

---

### Post by Sef on 2006-11-04
> You need Flash 9 to watch Flash videos with Ubuntu.

Depends on the site.  I was able to watch Youtube with Flash 7.

---

### Post by dinkdrmr on 2006-11-04
is there a way to do this on an AMD64 install?

---

### Post by Dr. Nick on 2006-11-05
> **dinkdrmr said:**
> is there a way to do this on an AMD64 install?

may have to go to the amd 64 forums here, last I knew flash wasnt native in 64bit, but could be accomplused by installing 32bit firefox, Last I knew that hadnt changed. They will be of better help though.

---

