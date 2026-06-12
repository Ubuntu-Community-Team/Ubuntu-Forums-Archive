---
title: "Several Questions"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by Space Cowboy on 2007-03-16
Today I decided to clean up and organize my computers, I got to Ubuntu on my laptop, organized my files, and updated, but I realized theres several misc. errors and stuff I haven't gotten around to fixing, most of which are minor and have not caused me any trouble but still I would like to learn how to fix them. Any help with any one of my questions is really appreciated, and I must thank all of you again for being so pleasant and patient here.

[LIST]
[*] A while back I wanted to set up a server just for kicks, so I went and tried out a few IRCD's, Unreal, and a few others in the Synaptic Package Manager, one of which was RageIRCD, I never did anything with it so I uninstalled it eventually but now every time I install anything with Synaptic (or in terminal) everything installs fine but I get this error:```
E: rageircd: subprocess post-installation script returned error exit status 1
```
which doesn't affect my install, but its annoying, and I have no idea what it means...

Also I installed some other things like Apache, which I was going to read up on and learn to set up and use but I never did, and now its too late (I no longer have good enough internet to maintain a server) but all of these are still installed, is it safe to have these things installed? Should I remove them or just not worry about it? 
**

**
[*] Totem is seemingly useless. I have installed all of the g-streamer plugins and win32codecs but totem doesn't seem to play any media at all... I can play the same media just fine with VLC, XMMS, and other programs, but never Totem which is weird since its the default player...
**

**
[*] In the Places list there are two server addresses (Windows Shares) that I no longer use, how do I clear these from the list?
**

**
[*] I made it so Sound Juicer ripped a CD in mp3 format (to play on my ipod), the mp3's play fine in XMMS and Rythmbox, but I cant move them from their location, or add them to my ipod with gtkpod. When I try to copy them to any other folder (I have even tried copying them to the folder right above the one they're in) a pop-up says "Not enough parameters", I have also tried doing this in terminal manually and it simply says that the files are omitted. I can move around my FLAC and ogg music I rip all I want but not these mp3's... I would just go in and rip it again, possibly on a different machine/OS, but I borrowed the CD and it is no longer in my possession.
**

**
[*]Since I installed KDE, konquerer has been the default browser ONLY IN SOME SITUATIONS. I went under Preferred Applications, but konquerer is not set as the default browser (Swiftfox is). Whenever I click on a link from certain applications, like X-Chat, it opens the link with konquerer, and I would much rather it open with Swiftfox or Opera... It no big deal since I can just copy and paste the link, but still I forget about it every so often and it annoys me...
[/LIST]

Thanks in advance for any help. Also should I start posting in General Support? I mean I've been using Ubuntu for almost a year now, but these questions still sound like beginner questions to me....

---

### Post by chewearn on 2007-03-16
> **Space Cowboy said:**
> I cant change my screen resolution. My laptop screen is wide, and in Windows I have it set to 1280x800 and it looks nice, but in ubuntu I cant change it from 1024x768, and it looks sort of blurry since its stretched out. I go to screen resolution under Preferences but the only option is 1024x768. Is this a video controller/driver issue? I never fooled with any of my drivers since they all seemed to work fine right from a fresh install.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf
```Near the bottom of the file, you should see a list of resolutions; add 1280x800.  Example (with added resolution highlighted)

```
    SubSection "Display"
        Depth        24
        Modes        **"1280x800"** "1024x768" "800x600" "640x480"
    EndSubSection

```

Once you have made the changes, restart gdm:
```
sudo /etc/init.d/gdm restart
```

---

### Post by inCursorated on 2007-03-16
> I cant change my screen resolution. My laptop screen is wide, and in Windows I have it set to 1280x800 and it looks nice, but in ubuntu I cant change it from 1024x768, and it looks sort of blurry since its stretched out. I go to screen resolution under Preferences but the only option is 1024x768. Is this a video controller/driver issue? I never fooled with any of my drivers since they all seemed to work fine right from a fresh install.

the windows manager preferences are limited by the x server. try editing /etc/X11/xorg.conf and adding greater resolutions to the Modes option under Section "Screen". 

> I made it so Sound Juicer ripped a CD in mp3 format (to play on my ipod), the mp3's play fine in XMMS and Rythmbox, but I cant move them from their location, or add them to my ipod with gtkpod. When I try to copy them to any other folder (I have even tried copying them to the folder right above the one they're in) a pop-up says "Not enough parameters", I have also tried doing this in terminal manually and it simply says that the files are omitted. I can move around my FLAC and ogg music I rip all I want but not these mp3's... I would just go in and rip it again, possibly on a different machine/OS, but I borrowed the CD and it is no longer in my possession.

not sure what's going on here... try the force option to cp (-f). otherwise do it as root or with sudo. 

> 
Also I installed some other things like Apache, which I was going to read up on and learn to set up and use but I never did, and now its too late (I no longer have good enough internet to maintain a server) but all of these are still installed, is it safe to have these things installed? Should I remove them or just not worry about it?

so long as they're not running it doesn't matter. i've yet to set up an ubuntu server, so i'm not sure if it the services get set to auto start

---

### Post by Space Cowboy on 2007-03-16
Perfect. One down, thank you AstalaVista.

> **inCursorated said:**
> not sure what's going on here... try the force option to cp (-f). otherwise do it as root or with sudo. 
...
so long as they're not running it doesn't matter. i've yet to set up an ubuntu server, so i'm not sure if it the services get set to auto start
I tried root/sudo before, but doing -f yields the same error
```
john@john-laptop:~$ sudo cp -f /home/john/Music/Johann\ Sebastian\ Bach/ /media/data/music
cp: omitting directory `/home/john/Music/Johann Sebastian Bach/'

```

As for the services I don't know if they're up or not, I would assume they arent because you need to configure them, but its possible, would I need to listen for open ports or something? Sorry I am not good with networking, probably for the best I never set up a server. In any case I'm on either dialup or temporary wireless in coffee shops now so its not like anyone can do much harm...

---

### Post by inCursorated on 2007-03-16
> john@john-laptop:~$ sudo cp -f /home/john/Music/Johann\ Sebastian\ Bach/ /media/data/music
cp: omitting directory `/home/john/Music/Johann Sebastian Bach/'

thanks for the code... the problem here is that u haven't told cp to recursively copy. try cp -fR

> As for the services I don't know if they're up or not, I would assume they arent because you need to configure them, but its possible, would I need to listen for open ports or something? Sorry I am not good with networking, probably for the best I never set up a server. In any case I'm on either dialup or temporary wireless in coffee shops now so its not like anyone can do much harm...

u'd be surprised at the harm that could be done. but, u're prolly right and they're not running. u can check if the apache process is running with 'ps aux | grep httpd'. btw, u can check for listening ports with netstat -tnlp. if u have firewall rules in place (i hope so) and haven't modified it to allow access for the services then it doesn't matter.

---

### Post by Space Cowboy on 2007-03-17
> **inCursorated said:**
> thanks for the code... the problem here is that u haven't told cp to recursively copy. try cp -fR
...
u'd be surprised at the harm that could be done. but, u're prolly right and they're not running. u can check if the apache process is running with 'ps aux | grep httpd'. btw, u can check for listening ports with netstat -tnlp. if u have firewall rules in place (i hope so) and haven't modified it to allow access for the services then it doesn't matter.

Well the -fR successfully copied it to anywhere in my Home folder but not on any other disk, like my ipod itself or my data drive I share between windows and linux; it says "cp: cannot create regular file `FILE NAMES': Invalid argument". I can copy all my other music, like ogg's etc. though. Why do these files need the -fR, and why wont they copy to anywhere else...

Also I havent ever changed any of the firewall settings so I think I'm good. I did both of those commands though, and I don't completely understand what they mean but I don't see anything that looks suspicious...

---

### Post by azteech on 2007-03-18
There really is no problem having things installed, and running in the background. However, things you do not use do eat up resources. I would recommend halting and uninstalling services that you do not use. Just be careful of what you shut down and uninstall.

You can find a list of services you have installed by going to system > administration > services and entering your password when prompted to do so.
If is installed, and most probably set to run, it should have a mark in the check box. Remove the mark from the check box for items you do not want running. After you remove the check mark, reboot the computer, log in, and remove the software you wish to remove.

---

