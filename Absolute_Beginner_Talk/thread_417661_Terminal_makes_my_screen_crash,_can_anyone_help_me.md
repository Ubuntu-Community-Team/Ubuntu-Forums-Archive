---
title: "Terminal makes my screen crash, can anyone help me?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Oneironaut on 2007-04-21
Hello, my first post in the forums.

Well, my problem is that whenever I try to start terminal, my screen goes sort of blue with a lot of lines, and the OS goes to the log in screen, it's weird as my music keeps on playing the  whole time(i'm using Quark), but Firefox closes down, and the Quark tray icon also goes away.

Any help is appreciated, as this is my first day on ubuntu i'm trying to tweak several things, but without the terminal it's impossible.

I'm running Xubuntu on a laptop,

another thing, does anyone have any tutorials on optimizing Ubuntu, i'm running on 126 mb of ram and a 6 gb hard drive, so this is one of my main problems, thanks a lot.

---

### Post by braddcadd on 2007-04-21
Maybe someone (I'm not that smart) can help determine what happened if you post the error lines from /var/log/Xorg.0.log.  You can get to it without the terminal by going to System->Administration->System Log.

You barely meet the min requirements for the vanilla Ubuntu ( [https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/memory-disk-requirements.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/memory-disk-requirements.html) ).  But with old hardware you might want to consider Xubuntu ( [http://www.xubuntu.org/](http://www.xubuntu.org/) ).

---

### Post by Spectre5 on 2007-04-21
I am having this problem too....

When I start a terminal, my screen goes black...then returns to the login screen!  I don't know why but everything else is working fine!  This just started after upgrading to Feisty.

---

### Post by Oneironaut on 2007-04-22
I'm have also just installed Feisty..
anyone?, i'll try to post those code lines that braddcadd said by tomorrow

---

### Post by kid_a on 2007-04-22
I had the same problem, and i discovered that the problem is with the xfce4-terminal, i installed the gnome-terminal with synaptic and now it works fine, i suppose that i'll be using this terminal until this bug is repaired.

---

### Post by TheForkOfJustice on 2007-04-22
This is a well-known Xubuntu bug and has been reported in Launchpad (by myself no less ;)).

Quick fix (if still using Xubuntu):
```

sudo nano /etc/X11/xorg.conf
```

Find 'DefaultDepth' and change the value from 24 to 16.

Save, reboot.  Your golden :)

---

### Post by Oneironaut on 2007-04-22
> **TheForkOfJustice said:**
> This is a well-known Xubuntu bug and has been reported in Launchpad (by myself no less ;)).

Quick fix (if still using Xubuntu):
```

sudo nano /etc/X11/xorg.conf
```

Find 'DefaultDepth' and change the value from 24 to 16.

Save, reboot.  Your golden :)

I'm still using Xubuntu
thanks a lot, but I'm a total noob, can you tell me where do I put that code?, I thought all that code was input in the terminal, (which I'm unable to open).

regarding Kid_a's comment, I'm unable to use the gnome terminal as I'm running on 126 mb of ram.

---

### Post by Spectre5 on 2007-04-22
When you are at the login screen, choose session->failsafe terminal

Then type
sudo nano /etc/X11/xorg.conf

Then scroll down and change the default depth from  24 to 16

Then press ctrl+w, hit enter, press ctrl-x

Type exit and hit enter

Then restart the comp and login as normal....


This fixed the problem for me to, thanks a lot for the info!!  Wonder what changed from edgy to feisty as I did not have this problem with edgy....

-Scott

---

### Post by Oneironaut on 2007-04-22
that did IT'!!

thanks a lot

---

### Post by Minker17 on 2007-04-25
When I type that in, all I get is a white screen. No text at all to change the depth.

---

### Post by alfios on 2007-04-26
> **Minker17 said:**
> When I type that in, all I get is a white screen. No text at all to change the depth.

same here, its as if the file isn't there to edit

alfios

---

### Post by dbott67 on 2007-04-26
I would suspect that the path you're entering is not correct.

The path is case-sensitive.  Be sure that you capitalize the X in X11, but not in xorg.conf and don't forget the leading '/':
```
sudo nano /etc/X11/xorg.conf
```

You can use '[tab-completion]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/getting-started-guide/s1-managing-command-history.html")' to ensure that you don't make typos:
> 
Another time-saving tool is known as command completion. If you type         part of a file, command, or pathname and then press the         [Tab] key, **bash** will present         you with either the remaining portion of the file/path, or a beep (if         sound is enabled on your system). If         you get a beep, just press [Tab] again to obtain a list         of the files/paths that match what has been typed so far.       
For example, if you forget the command updatedb, but         remember a portion of the command, you can su to         root, then at the shell prompt, type up, press the         [Tab] key twice and you will see a list of possible         completions, including updatedb and         uptime. By typing the partial command         upd and pressing [Tab] again, your         command is completed for you.

---

### Post by ridgeland on 2007-05-13
Thank you TheForkOfJustice!
Changing default depth from 24 to 16 solved my problem too!
:)

---

### Post by Manganic on 2007-07-08
> **ridgeland said:**
> Thank you TheForkOfJustice!
Changing default depth from 24 to 16 solved my problem too!
:)

I had to knock it down to 8 to get it to work, but it seems to have fixed it at my end as well.

Perhaps someone could shed some light on exactly WHAT we all did with changing that parameter...?

---

### Post by neoguy2012 on 2007-07-08
> **Manganic said:**
> Perhaps someone could shed some light on exactly WHAT we all did with changing that parameter...?

I could be wrong (chances are I am), but I think the DefaultDepth attribute defines the default [color depth]("http://en.wikipedia.org/wiki/Color_depth").  The desktop manager probably crashed when attempting to run a program at a higher color depth.  Of course, this is pure speculation.  :confused:

---

### Post by Manganic on 2007-07-08
> **neoguy2012 said:**
> I could be wrong (chances are I am), but I think the DefaultDepth attribute defines the default [color depth]("http://en.wikipedia.org/wiki/Color_depth").  The desktop manager probably crashed when attempting to run a program at a higher color depth.  Of course, this is pure speculation.  :confused:

Yeah, it's the colour depth.  I switched to 8, and realized my colours were all "horrible" now.  I think I'll have to look for another solution; perhaps simply log out and use the FailSafe terminal because switching back and forth from 8-bit is annoying.

---

### Post by Pointswest on 2008-01-26
After  using the command  "sudo nano /etc/Xll/xorg.conf"  I can see a directory for config, but where is this file to change default depth?  my screen shows several files but not one called default depth.  Where are you supposed to make these changes? 
Thanks for any help

Pointswest

---

### Post by ridgeland on 2008-01-26
Hi Pointswest

Sorry no one has answered yet.
I'm using Ubuntu rather than Xubuntu but the xorg.conf file is still the same stuff.  Here is a part of my xorg.conf file:

```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation GeForce 7300 LE"
    Monitor        "FPD1810"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection
```

Notice that in this section is a line for the default depth.  Also note that the default resolution here is 1280x1024.  If I edit the file to put 800x600 first that that will become the default resolution.

Hope that helps.  Post back if you don't follow or if your xorg.conf file does not have a "Screen" section.  I've seen that happen, but I don't know how to fix it.

---

### Post by Pointswest on 2008-01-27
Ridgeland

Thanks for following up on this.  I will list the files in my Xll/xorg.conf file.  After executing the command and using control r and  control t, i see a list of  files, one called config, below are the contents of this file.

** (parent dir)           autostart     (dir)             Thunar        (dir)
xfce4       (dir)

Opening these files dont show anything for Screen.  Hope this gives a clue to this problem.

---

### Post by ridgeland on 2008-01-27
Huh?
xorg.conf is a file not a directory. 
There are no files in the file.
Which flavor of Xubuntu are you using?
I'll install that on my old PC so I can better see what you are seeing.
The file is /etc/X11/xorg.conf
It's in the /etc/X11 directory.
I'm not sure but isn't there an editor called mousepad or am I thinking of DSL or something?

---

### Post by Pointswest on 2008-01-28
I found my mistake, when looking for the file, I was using the minimized window and didn't see the whole file.  I found the default depth line and changed it from 24 to 16 and this solved my problem with the terminal screen timing out to the log-in screen.  Thanks for the help solving this problem.

Pointswest

---

### Post by cd-r80 on 2008-02-17
Hi ! I cannot says that this is a fix. My card does 24bit & 1024x768. Why I need to turn it to 16bits. I don't want to use less colors .  I saw something about removing  agpart or more videoram from bios. Anyone?

---

### Post by Midwest-Linux on 2008-04-08
I know this is a old thread, but this might help others. I have a old Gateway computer with a max limit of 256 MB RAM. I had Freespire 2.0 in it, and while it worked good. It was slow and Freepire 2.0 needed a bit more RAM to work as it should. So I decided to install Xubuntu 7.04 with the alternate installer CD. Everything went well, but after installing VLC, I could not get the player to "associate" with websites that had streaming audio...there was no plug in. 

I went to the terminal and wanted to add the plug-in, after going to the terminal I ended up instead with the desktop log in. I saw the cure and how by changing the default depth from 24 to 16 would help, somehow I messed up and xorg didn't work properly. I wiped the install and reinstalled.

 This time I didn't even bother changing the default depth. Again I instead went to the terminal and got the desktop login again, this time I clicked the "session", and then "clicked failsafe terminal" did the log in and went to the terminal and did the code that I wanted which was.

sudo apt-get install vlc vlc-plugin-* mozilla-plugin-vlc

Then went through the prompts and did the install and then exited. Clicked on one of the streams and I still was not able to associate when I click the stream. While I solved the terminal problem very easily. I cannot bring up VLC instantly when I click on a stream....and thats my current problem...

 Instead it still brings up that 

"You have chosen to open 32k.pls which is a pls file from [http://www.wtprn.com](http://www.wtprn.com)  What should firefox do with this file? " 

On the website I tried all three options, which are

Most media players
Real player
Windows media

Then I have a choice between browse and save to disc. I looked through the browse to see if I can locate VLC. I can't find it (through browse)  under desktop, user or file system. what am I missing? I thought I installed the browser plug-in. The G-Streamers are installed. I can bring up VLC and manually add in the file and it will play.

 But through that browse (when that window pops up after clicking on the link to the stream) I cannot locate VLC, though I can locate VLC under Applications>Multimedia...I cannot locate VLC through that browser that pops up when I click on of the streaming  links....


I thought a plug in makes it that when one clicks on a streaming link it brings up the appropriate player. What am I missing or what did I miss? Did I install the wrong plug in? Wrong player? 

 This particular problem is not caused by the Flash plug in, I was able to watch a video archive from a NY TV station with no problem. But it wasn't with the VLC, but with the built in flash player. I am talking about streaming audio where you click on a link and your installed player is supposed to play automatically...

I got those commands for the vlc from [http://ubuntuguide.org/wiki/Ubuntu:Feisty#MPlayer_plug-in_.28Installs_MPlayer_media_player_as_well.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#MPlayer_plug-in_.28Installs_MPlayer_media_player_as_well.29)


Thanks for any help you can provide.

---

