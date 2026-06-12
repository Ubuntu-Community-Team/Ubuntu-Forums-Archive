---
title: "tryin to install realplayer"
date: 2007-04-15
forum: Alabama Team - US
---

### Post by crimsontide on 2007-04-15
I am trying to install realplayer via synaptic but i keep gettin this error..... [ATTACH]29776[/ATTACH]
Uninstall helix?

---

### Post by strabo40 on 2007-04-15
I just installed Real Player this morning with no problem. The way I did it was go to Applications - Add/Remove and when the applet started I searched for Real Player. I then installed it from there. I think Helix is the company/person that ported Real Player to Ubuntu.

---

### Post by crane on 2007-04-15
Sorry I missed your IM earlier RollTide. I was off playing with the kids. 
I just did a search in synapic and the add remove thing and could not find Real Player at all. I was going to install it and see what happened. I do not have the helix player installed though. Did you add repos or change anything?

---

### Post by crimsontide on 2007-04-16
Hey np crane. Could'nt find it in add/remove either. Don't think it will be added until the final release of fiesty. But anyway I unistalled helix from symnaptic and then installed realplayer with no problem. Guess you have to have one or the other. Anyways thanx for the help guys.

---

### Post by strabo40 on 2007-04-16
Sorry..didn't realize you guys were using Feisty version. I am on Edgy....

---

### Post by MerlinsLair on 2007-04-16
Heh, not much sense in me having a go at it then...I'm still running Dapper! LOL :)

---

### Post by crane on 2007-04-16
Cool, glad you got it worked out.
 I love trying to help out. If someone is having a problem I will try to duplicate it on my machine so I can help find a solution. I reckless that way.LOL
Actually, I just have everything partitioned and mounted so if I totally screw up I can reinstall with very little issues.

I've been running Feisty for about a month now. 3 more days until official release!

---

### Post by tomcat1965 on 2007-04-20
RealPlayer is not in Fiesty repo's yet. Install from site: [http://uk.real.com/player/](http://uk.real.com/player/) make the file executable (chmod a+x) then ./  it will now ask you to choose a path(where you want to install it) opt is good. Simple.:)

---

### Post by Saptagirish on 2007-06-18
tried the way described. I am having Fiesty Fawn. Keep getting this message "chmod: cannot access `realplayer10GOLD.bin': No such file or directory
How do I go about this problem.
Bye

---

### Post by crane on 2007-06-18
> **Saptagirish said:**
> tried the way described. I am having Fiesty Fawn. Keep getting this message "chmod: cannot access `realplayer10GOLD.bin': No such file or directory
How do I go about this problem.
Bye

In a terminal window cd to the directory where you downloaded it. The typ ls to list contents of the directory. Then make sure you have spelled everything correct. This is a mistake I make constently. I decided to try and see if I would have the same problem, so I will post what I did.
```
jason@Jason:~$ cd Desktop
jason@Jason:~/Desktop$ ls
crankygeeks.068.i.mp4  LinuxActionShowEP051.mp3  logo.gif
dl.tv.174.i.mp4        logo1.gif                 RealPlayer10GOLD.bin
jason@Jason:~/Desktop$ chmod a+x RealPlayer10GOLD.bin
jason@Jason:~/Desktop$ 
jason@Jason:~/Desktop$ /home/jason/Desktop/RealPlayer10GOLD.bin

Welcome to the RealPlayer (10.0.8.805) Setup for UNIX
Setup will help you get RealPlayer running on your computer.
Press [Enter] to continue...
[COLOR="Red"]*hit enter*[/COLOR]

Enter the complete path to the directory where you want
RealPlayer to be installed.  You must specify the full
pathname of the directory and have write privileges to
the chosen directory.
Directory:  [/home/jason/Desktop/RealPlayer]: [COLOR="Blue"]/opt/RealPlayer[/COLOR] [COLOR="Red"]*hit enter*[/COLOR]

You have selected the following RealPlayer configuration:

Destination:            /opt/RealPlayer

Enter [F]inish to begin copying files, or [P]revious to go
back to the previous prompts: [F]:[COLOR="Red"] *hit enter*[/COLOR]

Copying RealPlayer files...configure system-wide symbolic links? [Y/n]: .[COLOR="Blue"].y.[/COLOR] [COLOR=Red] *hit y then enter*[/COLOR]
enter the prefix for symbolic links [/usr]: ... [COLOR="Red"] *hit enter*[/COLOR]
Setting up realplay symlinks in /usr...
configuring icons...
configuring document icons...
configuring pixmaps...
configuring locale...
.configuring desktop...
configuring applications...
configuring GNOME mime types...
Configuring realplay script...

RealPlayer installation is complete.
Cleaning up installation files...
Done.








```

---

### Post by Harry789 on 2007-09-17
this works great but I have really bad sound, and not smooth playback. what can I do?

---

### Post by crane on 2007-09-18
So is the sound issue just in real player?

---

### Post by Harry789 on 2007-09-25
yes this is just in real player I have sound issues

---

### Post by crane on 2007-09-25
I am not very familiar with real player myself. Is it just the sound or is the entire playback poor quality? Maybe someone else running Real Player can step in and help out.

---

### Post by kk4et on 2007-10-26
when I get to the point where I need to put the directory, I dont know what to put there, I used the above illustration /opt/RealPlayer and it says access denied,  I cant get any farther than this, dont know the exact path to enter

when I type in the directory and hit enter  this is what I get
 error creating directory /opt/RealPlayer  (permission denied), exiting...
Cleaning up instillation files...
Done.  

 And when I try to run RealPlayer it comes up says missing  a couple of plugins,  because it isnt installed correctly.

---

### Post by crane on 2007-10-26
> **kk4et said:**
> when I get to the point where I need to put the directory, I dont know what to put there, I used the above illustration /opt/RealPlayer and it says access denied,  I cant get any farther than this, dont know the exact path to enter

when I type in the directory and hit enter  this is what I get
 error creating directory /opt/RealPlayer  (permission denied), exiting...
Cleaning up instillation files...
Done.  

 And when I try to run RealPlayer it comes up says missing  a couple of plugins,  because it isnt installed correctly.

Are you running the command as sudo?
That's the only thing I can think of that would keep it from creating the directory.

---

