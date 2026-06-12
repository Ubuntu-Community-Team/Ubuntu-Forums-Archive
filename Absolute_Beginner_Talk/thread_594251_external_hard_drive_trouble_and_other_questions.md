---
title: "external hard drive trouble and other questions"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by mangurt on 2007-10-27
Greeting all,
Well, last night I did the dive and got rid of windows xp (the system was incredibly bloated).  Anywho, I installed ubuntu 7.10 without any trouble.  I am noticing something that seems to be odd.  I have a 320g external hard drive that has all of my data backed up onto it (music, movies, games, ect).  when I start ubuntu, the hard drive is mounted on the desktop, and I have no trouble looking at the content, but if I don't go to the drive right away, or wait for some time, I get an error stating that there is an error reading information on the drive.  If I reboot, I have no problem.

Secondly, I am having some basic problems trying to install stuff via terminal.  I am sure it's something basic, but I am so out of touch with command line stuff that I feel like I just started using a computer for the first time.  The things I am trying to load are flash player and java.  I know java can be "evil" but I was thinking about running azureus as my torrent program (I can't stand the stand alone bittorrent program).  Any clues or links to send me in the right direction?

As for the operating system, so far, so good.  I like how clean the program feels (hate to say it, but it really reminds me of my old mac ibook I got when I was in college [that ran OS X.01]) which I really enjoyed.  I am sure that once I get use to running stuff via command line, that I will wish I could use linux at work (which is impossible, I already asked).

Thanks again!

---

### Post by DezSP on 2007-10-27
First problem, I have no clue. :s

Second, the command you want is apt-get install, but it needs to be run as root. So something like "sudo apt-get install <package name>". I've no idea what the package names for JRE and Flash are though, but the package azureus likely depends on them, so you can just install that directly (though I prefer ktorrent myself (some people swear by deluge)). Synaptic provides a GUI for package installation and can be found in System -> Administration. You've also got the command-line GUI-ish program aptitude (both must be run as root).

And you could always sneak a LiveCD into work... ;)

---

### Post by carloslosgrande on 2007-10-27
[FONT="Comic Sans MS"]You can also look in Applications>Add/remove its a very useful gui where I loaded java and flash from.[/FONT]

---

### Post by mangurt on 2007-10-27
Sweet!  The add/remove application was great!  I just need to install macromedia flash player (for some reason I can not select it)  Oh well...not that much I need via flash anyway...

Thanks for the help!

---

