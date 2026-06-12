---
title: "Installing?"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by durdensbuddy on 2008-01-15
This REALLY showcases my lack of preparedness, so in advance I apologize.  

I am trying to install flash player, I am currently in terminal, have gotten to desktop directory, listed the files the flash tar and flash unpacked files show up, but i can't seem to get it to actually install.  What command do I need?

---

### Post by dstew on 2008-01-15
Are you trying to compile and install from source, or install a Debian package? If installing from source, you need to have the package build-essential installed. If installing a Debian package, the command is dpkg -i <package-name>. Or, you just double-click on the package file.

In Ubuntu, you usually do not need to do this. You can almost always install using Synaptic other graphical installer. If you are trying to install the Adobe flash plugin, in Synaptic you need to have the **multiverse** repository enabled in settings. The package name is **flashplugin-nonfree**.

---

### Post by durdensbuddy on 2008-01-15
Thanks for the help, but I'm still stumbling around on HOW to get to multiverse/universe.

I found the wiki HOWTO article, but I don't know the address for the repository, or am hugely missing something.  

Might give up on this, just cause I hate having to annoy people.  

Oh, and yeah I suppose the plug-in of flash would be best, but I had initially been trying to install the full flash player and follow Abobe's instructions. 

So I now have 2 concerns.  1. Activating the universe/multiverse repositories, and 2. installing anything using the terminal.  (My concept is that terminal is the command line, kinda the DOS in Windows.  Is that right?)

---

### Post by carverj on 2008-01-15
> Thanks for the help, but I'm still stumbling around on HOW to get to multiverse/universe

Open Synaptic in System > Administration
Open Settings > repo's and ensure that multiverse is enabled

> Might give up on this, just cause I hate having to annoy people. 

Not annoying... learning which is the purpose of forums!!
We all have to start somewhere right?
I was lucky enough to have a neighbour to show me how to use linux.... without him I probably wouldn't have come across this forum or to learn linux.

> Oh, and yeah I suppose the plug-in of flash would be best, but I had initially been trying to install the full flash player and follow Abobe's instructions.

If you want to install from Adobe direct, I suggest a little research into how to install software manually (such as the link in my signature below)

> 
installing anything using the terminal. (My concept is that terminal is the command line, kinda the DOS in Windows. Is that right?)

Same again, a bit of research and a lot of practice required.
I recommend to begin with you follow the community link at [www.ubuntu.com](www.ubuntu.com) to install everything
and then finish with a lengthy visit to [www.ubuntuguide.org](www.ubuntuguide.org)

---

### Post by sowelie on 2008-01-15
It sounds like you downloaded and un-tared the installer.  Just go into the installer folder, it was called install_flash_player_9_linux in my case, and run the installer via the terminal.

```
./flashplayer-installer
```

It'll ask a few questions, just accept the defaults and you should be good to go.

---

### Post by durdensbuddy on 2008-01-16
I have attempted to follow the walkthroughs listed above, but I still can't get flash on to my system.  

I'm including some screencaps because I THINK i have the universe/multiverse enabled (and if so did the whole time) And the flashplugin-nonfree install, but still can't access flash games or youtube

[IMG]home/shannon/Desktop/Repositories.png[/IMG]  and [IMG]http:///home/shannon/Desktop/flash.png[/IMG]

I even thought maybe i had to go into the add/remove programs menu, but couldn't find flash there.  Why am i so stuck on something this *seemingly* easy?

---

### Post by sowelie on 2008-01-16
I am not sure why you are having such a hard time.  Are you using a 64-bit version of ubuntu?  Also, did you try just click "install missing plugins" this generally works believe it or not.  The other thing to try would be automatix.  It does a pretty good job of installing the flash plugin.  But honestly, the easiest way I've found is to just download and run the installer, if the "install missing plugins" doesn't work.

---

### Post by durdensbuddy on 2008-01-16
i am on a 64 bit system actually.  Does that change things up?

Where would I find the install missing plug ins button?  Automatix?  Losing me quickly.  I had tried to install the flash using terminal, as opening the folder and doing it the "windows" way didn't work for me.  but i didn't know the command, i thought it was apt-get or get-apt install (then file name) but that came up as incorrect or invalid.  forget.

---

### Post by sowelie on 2008-01-16
Haha, it sure does. If you have the 64-bit version of ubuntu installed.  This is because adobe has not released a 64-bit flash player.  You'll have to install 32-bit firefox to use flash if this is the case.  Although, I seem to remember it working a little better on gutsy.  I also ran into this earlier...there may be an issue with the flash player in the repos: [http://ubuntuforums.org/showthread.php?t=636397]("http://ubuntuforums.org/showthread.php?t=636397").

---

### Post by eolson on 2008-01-16
failsafe ....

if you've alread untarred it,  find the file called libflashplayer.so

open a terminal and copy that file to

/home/yourusername/.mozilla/plugins/libflashplayer.so

---

### Post by sowelie on 2008-01-16
Right...that's all the "installer" really does, haha.

---

### Post by lswest on 2008-01-16
well, last bit of info, to run the flashplayer installer you have to run ```
sh [name of flash install script]
``` and yea, 64bit does matter

---

### Post by durdensbuddy on 2008-01-16
So eolson, if i'm understanding you correctly what I want to do is

Open a terminal, and type cp libflashplayer.so .home/shannon/.mozilla/plugins/libflashplayer.so  hit enter and then be off?  

To bring eveyone up to speed.  I have installed 32 bit firefox, began to follow a walkthrough on how to add flash, but say that gutsy can't do that so quit.  Attempted to install missing plugins through fox, once was told that flash is already installed, and then 2 more times that installation failed -> manual install.  Attempted that and here I am again.  

At this point since I have played with some command line stuff in terminal

 sudo apt-get install ia32-libs lib32asound2 lib32ncurses5 ia32-libs-sdl ia32-libs-gtk gsfonts gsfonts-x11 linux32

would it be best for me to scrap everything and reinstall?  I have a 32 bit version of gutsy here, but wanted to try out 64 as I only had 32 for windows.

Also a HUGE thanks for nto publicly ridiculing me for total ineptness.  :)  I owe you guys a beer if you're ever in the Toronto area.

---

### Post by eolson on 2008-01-16
that's pretty much it,   just copy the .so file into the plugins directory and your done.

---

### Post by durdensbuddy on 2008-01-16
So I tried that.  here's what happened 

shannon@shannon-desktop:~$ cp libflashplayer.so .home/shannon/.mozilla/plugins/libflashplayer.so
cp: cannot stat `libflashplayer.so': No such file or directory
shannon@shannon-desktop:~$ 

the tar and untarred versions of the flash download are located on desktop, should i change directories?

---

### Post by eolson on 2008-01-16
If it's on the desktop

cp /home/yourusername/libflashplayer.so /home/yourusername/.mozilla/plugins/libflashplayer.so

---

### Post by eolson on 2008-01-16
Ooooops!

cp /home/yourusername/Desktop/   etc ......

---

### Post by Michl on 2008-01-16
An excellent source of info on this and other ubuntu issues is:

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

I go back to it all the time.

M

---

### Post by timbounceback on 2008-01-16
Much easier to do something like this:
```
wget http://fr.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb && sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb && rm flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb
```
Just paste into a terminal, and you're done. You can (if it works) remove the folders you previously downloaded.

---

### Post by sowelie on 2008-01-16
I was running 64 bit ubuntu for a while but I found it hard to find 64 bit deb's and repositories.  I ended up going to 32 bit, I've found it's much easier.  And to be honest, on my AMD 64 3500+ I don't notice a difference at all.

---

### Post by carverj on 2008-01-16
I also had to go through all the 64-bit installation ehelp. Follow this link:
[https://help.ubuntu.com/community/RestrictedFormats/Flash#amd64andppc](https://help.ubuntu.com/community/RestrictedFormats/Flash#amd64andppc)

---

### Post by durdensbuddy on 2008-01-17
> **sowelie said:**
> I was running 64 bit ubuntu for a while but I found it hard to find 64 bit deb's and repositories.  I ended up going to 32 bit, I've found it's much easier.  And to be honest, on my AMD 64 3500+ I don't notice a difference at all.

Tried googling this but the steps were a little above my head.  How did you make the switch?  Did you have to uninstall the 64 bit version, then install 32, or can you just install the 32 bit livecd?

thanks.

---

### Post by durdensbuddy on 2008-01-17
SOLUTION!!!!    64 bit users can be directed to the following thread in the future.  One final thank you to all for helping.     

[http://ubuntuforums.org/showthread.php?t=476924](http://ubuntuforums.org/showthread.php?t=476924)

---

