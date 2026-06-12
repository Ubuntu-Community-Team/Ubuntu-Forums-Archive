---
title: "Simple Issues"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by Duwady on 2006-11-01
Hi all,

I am 20 years veteran of Wintel, who decided to jump to Linux bandwagon, and chose Ubuntu 6.06, and have been trying to install dual boot with XP, as there are still a lot of things on my Windows.

Despite my experience, I am COMPLETELY new to Linux, so sometimes even the most basic things looks very big.  

I have been playing with it for last one week, and getting the information from the Forums.  The Forums are excellent, and give a lot of info, which can be tried out.  I have not finished all the kinks I am having, but am enjoying trying it out.

And this is where I am lost...  

I understand (by playing around for last one week, and reading the forum a lot) that by using "Sudo" I can gain super user mode for that one particular command.  However, if I do want to log on as "root" how do I do it?  It had asked me for a password when I installed it, but does not accept it when I want to log on as "root".  I am trying to edit "menu.lst", as per the advice from people in this forum.  I can open it from GUI, but then I can not save it, as I gather it is read-only.  And if I try to go and change the properties, it tells me I am not the owner, so can not change it.

As I can open different files in GUI mode, but then I have problem when I use terminal.  is there any place where I can go and look for the basic commands and their syntax?  Also, the commands for navigating from one place to another?  

By the way, I still have not been able to access my Windows drives, my windows does not start, gives me HAL.DLL error message, though I have managed to get my WG111v2 USB wireless adapter working, I still have not been able to figure out WPA connection...  but hey, that is what I am trying to do, right? So I am really enjoying it at the moment, now if only I knew some basic stuffs.....  

Thanks a lot, guys...

Duwady

---

### Post by bulldog on 2006-11-01
Well to use the GUI methode use ```
gksudo nautilus
```
To use terminal ```
gksudo gedit /boot/grub/menu.lst
```

To mount windows partitions take a look here
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

For some info,
[http://www.unix-tutorials.com/tutorials.php?os=Ubuntu](http://www.unix-tutorials.com/tutorials.php?os=Ubuntu)

More interresting stuff,
[http://ubuntuforums.org/showthread.php?t=171507](http://ubuntuforums.org/showthread.php?t=171507)

---

### Post by Duwady on 2006-11-01
Thanks...

One more question please... 

What is the difference between sudo and gksudo?

Just trying to understand.

---

### Post by Chayak on 2006-11-01
Well the general advise even from a user point in any *nix os is not to work as root unless you have to.  If you want to edit your file you can.

```
sudo gedit /path-to-file 
```

That will open up gedit with root permissions to modify a config file and it's easier for someone new to linux than using vi/vim/nano to edit in the command line.

Edit: doh seems I was too slow on the draw ;)

---

### Post by aktiwers on 2006-11-01
About the thing being logged in as root all the time, that is not recomented.

But you can do a 
> sudo nautilusOr get automatix and then install the gnome scripts. This way you can just right-click on a folder and pick "scripts" and then pick "Root-nautilus-here". 

Or simply 
> sudo gedit /path/to/menu.lst

EDIT:
Wow you guys are fast!!

---

### Post by bulldog on 2006-11-01
> **Duwady said:**
> Thanks...

One more question please... 

What is the difference between sudo and gksudo?

Just trying to understand.

When you open a program with a GUI like gedit or nautilus,it's advised to use gksudo.
Otherwise you could getthings mixed up,there is a explanation site some where,I will see if I can find it.
You will see a warning but that's false alarm.

And for non graphical apps. you use sudo.
To become root for a longer periode you can use sudo -s

---

### Post by Duwady on 2006-11-01
Thanks a lot guys...  Used to doing everything in "Administrator" mode in Windows seems to have spoiled me...  But I do get your points.

And, heck...  You guys are fast...  

Thanks a bunch, I will be back... ;)

---

### Post by elcasey on 2006-11-02
Having managed to hose my permissions with the GUI (believe it or not) when I installed Ubuntu the first time about 10 days ago, I'll agree it's not a good idea to run as root.

Now that I see the "Gnome-UI" warning is nothing to worry about, I have to ask:

Why did the Ubuntu install process never ask me to set up a root account and root password? I know having to sudo all the time is equivalent to using "su root" but in the other times I've used Red Hat, Debian and Mandrake (never could get used to them, alas, but this was all 5-7 years ago) I had a separate root account, then my main user account.

Just curious since I see that "sudo" and "gksudo" will essentially do the same thing. But if I intend to do a series of things, maybe some GUI and some CLI, why can't I do an "su root"? It tells me my password is wrong.

:???:

---

### Post by devilsadvocate1987 on 2006-11-02
Ubuntu somes with the root account disabled. Its deemed a dangerous thing to have, and considering the fact that ubuntu is trying to be as user friendly as possible to new users, especiall those used to the admin account on windows, its a good idea not to give them root. Typing sudo each time ensures that you know that you're doing something that could do some damage if not done nicely. 

The su account can be enabled if you like, but I would recommend against it.

---

### Post by CatKiller on 2006-11-02
> **elcasey said:**
> Why did the Ubuntu install process never ask me to set up a root account and root password?

Because then you'd use it. Thinking it was an "Administrator" account that you could use all the time.

> why can't I do an "su root"? It tells me my password is wrong.

Tell me, what's the password of the root account? **That's** why it tells you the password is wrong.

If you're desperate to run as root for a little while, use **sudo -s** or **sudo -i**.

EDIT: > I know having to sudo all the time is equivalent to using "su root"  No it isn't. "su root" is "switch user root" - it logs you in as root. "Sudo" is "switch user, do" - it runs a command as root. Not the same idea at all.

---

### Post by ramjet_1953 on 2006-11-02
If you really want to have a root account, do this:

In a console, type :

"sudo password root"

Using the instructions listed, make a root password.

Viola! You now have an accessible root account.

Please make sure that you use this account only when necessary, though, as you can completely hose your system, if you are not careful.

A root account is necessary to have if you have a HP printer and want to use the extra facilities that HPLIB offers.

Roger 8)

---

### Post by elcasey on 2006-11-02
> **CatKiller said:**
> Because then you'd use it. Thinking it was an "Administrator" account that you could use all the time.
Not me. I've screwed up enough with my regular account, much less root. This isn't the first time I've run Linux, but this is the first time I've installed a distro that didn't frustrate so badly that I removed it within a month. :P



> Tell me, what's the password of the root account? **That's** why it tells you the password is wrong.
For some unknown reason I thought it might be set to some default, not realizing what an incredibly glaring security hole that'd be. :-# 

> If you're desperate to run as root for a little while, use **sudo -s** or **sudo -i**.
And what do those individual switches do? I'd just "man sudo" but I'm installing a load of updates right now (I'm writing this on my Mac).

> No it isn't. "su root" is "switch user root" - it logs you in as root. "Sudo" is "switch user, do" - it runs a command as root. Not the same idea at all.
What I meant by that was that I could "su root" and then run a series of commands, or I could type "sudo" before each command I run, not that they did the same thing. It was poorly worded on my part. The only reason I wanted to run as root was because I tend to add loads of images, icons, themes, etc. and when I'm moving 15-20 .tar.gz's into /usr/share/pixmaps/icons from ~/Desktop it can get pretty unwieldy typing "sudo" before each gunzip or mv, know what I mean? 

And Ramjet, thanks so much! I'll do it shortly, make the password extremely difficult and put it my safe deposit box at the bank. :mrgreen:

---

### Post by houstonbofh on 2006-11-03
There are several better ways to do this that turning on the root account.  (And some good reasons not to)  'sudo -s' and 'sudo -i' have already been mentioned.  You can also spawn a rooted process.  One example was already mentioned, 'sudo nautilus&' or 'gksudo nautilus' but if you just want a root term, try 'sudo xterm&' and you have it.  (The & spawns the process and allows you to continue to use the same cli window)  And remember that anything launched from a rooted process is also rooted.  So a file edited by double clicking in the rooted file manager (nautilus) will belong to root.

---

### Post by CatKiller on 2006-11-03
> **elcasey said:**
> And what do those individual switches do?

```
       -i  The -i (_simulate initial login_) option runs the shell specified in
           the passwd(5) entry of the user that the command is being run as.

```

```
       -s  The -s (_shell_) option runs the shell specified by the _SHELL_ envi&#8208;
           ronment variable if it is set or the shell as specified in
           passwd(5).

```

---

### Post by elcasey on 2006-11-03
Thanks for the replies, houston, CatKiller.

Since the "sudo -s/-i" and other options are available maybe I'll leave root well enough alone. But here's a better question - am I keeping my system *more* secure by leaving the root password "blank" (for lack of a better term), even though I, or an intruder, could perform the same functions with the password of my current account using "sudo"?

Just curious...I've got the basics of the graphical portions of the OS down fairly well, so I'm going to jump more into the shell now and get familiar with it.

Thanks again! :)

---

### Post by Duwady on 2006-11-03
I have also come to the same conclusion, to leave it alone at the moment.

But while on the subject, while using Wintel, we are used to GUI functions a lot.  Though I am equally comfortable using terminal, and using sudo commands, is there a way to have the same for GUI functions?  

Still learning, and hope to master it...  some day.

---

### Post by CatKiller on 2006-11-03
If you don't change the password for the root account, it's a randomly-generated string that no one knows. That's pretty secure.

As you say, it doesn't really matter that much, since anyone that can guess your password and get access to the machine can do the same thing anyway. So you should probably stop those two things happening :)

Although having the root account disabled means that a hypothetical intruder may have to guess your user name as well as your password.

---

### Post by CatKiller on 2006-11-03
> **Duwady said:**
> But while on the subject, while using Wintel, we are used to GUI functions a lot.  Though I am equally comfortable using terminal, and using sudo commands, is there a way to have the same for GUI functions?

If you mean "is it possible to run graphical applications with superuser privileges?", then yes. That's exactly what happens when you run Synaptic, for example, or the network settings thing.

If you mean "is it possible to use the Windows approach and log in as root all the time?", then yes, it's possible. But don't do it, because it's stupid.

---

### Post by elcasey on 2006-11-03
I took it as meaning "is there a way to open apps via GUI that does the same function as running a 'gksudo nautilus' or the like in terminal." And that's a good question. Would you set it to "run in terminal," then use the string "gksudo *appname*"?

And good point on having to guess the user account name. I'm definitely leaving root alone now since, with the switches, there's really no need to run as root now.

Thanks again, you guys are so great on these forums! 8)

---

### Post by CatKiller on 2006-11-03
> **elcasey said:**
> I took it as meaning "is there a way to open apps via GUI that does the same function as running a 'gksudo nautilus' or the like in terminal." And that's a good question. Would you set it to "run in terminal," then use the string "gksudo *appname*"?

You don't need to set it to run in the terminal. You'd just have your launcher or menu item set to either "gksudo <*graphicalapp*>" or "gksu <*graphicalapp*>". That's why I suggested you look at the Synaptic launcher.

---

### Post by Duwady on 2006-11-03
> **CatKiller said:**
> You don't need to set it to run in the terminal. You'd just have your launcher or menu item set to either "gksudo <*graphicalapp*>" or "gksu <*graphicalapp*>". That's why I suggested you look at the Synaptic launcher.

Yes, I did mean run the application with temporary sudo priviliges.  

Maybe one example will make myself clear...  I went (under GUI, by double cliking) to /etc and tried to edit menu.lst because of the problems I had with booting with WinXP.  But I could not save the changes because I did not have the rights, obviously.

Now I understand that I can launch the application with gksudo.  But (please don't laugh, I am still learning...  :)) what does gk mean in gksudo?  Do I have to start the terminal, type 'gksudo nautilus'  and then work on the GUI application?

Thanks.

---

### Post by Duwady on 2006-11-03
> **CatKiller said:**
> You don't need to set it to run in the terminal. You'd just have your launcher or menu item set to either "gksudo <*graphicalapp*>" or "gksu <*graphicalapp*>". That's why I suggested you look at the Synaptic launcher.

CatKiller, I definitely would like to know what I am supposed to look for in the Synaptic launcher, and what I need to do to set the menu item  as you have described to get what I want to do.

Thanks.

---

### Post by CatKiller on 2006-11-03
> **Duwady said:**
> Now I understand that I can launch the application with gksudo.  But (please don't laugh, I am still learning...  :)) what does gk mean in gksudo?  Do I have to start the terminal, type 'gksudo nautilus'  and then work on the GUI application?

I don't know what the "gk" stands for, but gksudo is [subtly different]("http://www.psychocats.net/ubuntu/graphicalsudo") to normal sudo. You should use **gksudo** for graphical applications and **sudo** for command-line ones.

What happens when you type **gksudo nautilus** is that you run Nautilus as root. Similarly, when you type **gksudo gedit** you run GEdit as root. It's the same for any application. Stick a gksudo/gksu/sudo in front of it, and you'll run it as root.

The reason I pointed you towards the Synaptic and Network Manager launchers was so that you can see they're just normal launchers, the same as any other. It's just that the command they run starts with gksu. For the most part the way I've found out how to do stuff, both under Ubuntu and Windows, is to see how people have done something similar previously.

There aren't many user applications that you'd want to run as root though. Nautilus is the most commonly used, and some people **do** use launchers for that. Personally, I prefer to just press **Alt-F2** and then type in the command. I find it much quicker, and I don't clutter up either my desktop or menu with spare items :)

EDIT: To have a look at the Synaptic launcher, right-click on the menu and select "Edit Menus", then navigate to the System/Administration/Synaptic entry, right-click and selcet Properties.

EDIT 2: To make a new launcher, you can either right-click on the desktop - or select New Entry in Alacarte if you want it in the menu - and fill in the Name and Command boxes. Everything else is optional, I believe.

---

### Post by Duwady on 2006-11-03
> **CatKiller said:**
> I don't know what the "gk" stands for, but gksudo is [subtly different]("http://www.psychocats.net/ubuntu/graphicalsudo") to normal sudo. You should use **gksudo** for graphical applications and **sudo** for command-line ones.

What happens when you type **gksudo nautilus** is that you run Nautilus as root. Similarly, when you type **gksudo gedit** you run GEdit as root. It's the same for any application. Stick a gksudo/gksu/sudo in front of it, and you'll run it as root.

The reason I pointed you towards the Synaptic and Network Manager launchers was so that you can see they're just normal launchers, the same as any other. It's just that the command they run starts with gksu. For the most part the way I've found out how to do stuff, both under Ubuntu and Windows, is to see how people have done something similar previously.

There aren't many user applications that you'd want to run as root though. Nautilus is the most commonly used, and some people **do** use launchers for that. Personally, I prefer to just press **Alt-F2** and then type in the command. I find it much quicker, and I don't clutter up either my desktop or menu with spare items :)

EDIT: To have a look at the Synaptic launcher, right-click on the menu and select "Edit Menus", then navigate to the System/Administration/Synaptic entry, right-click and selcet Properties.

EDIT 2: To make a new launcher, you can either right-click on the desktop - or select New Entry in Alacarte if you want it in the menu - and fill in the Name and Command boxes. Everything else is optional, I believe.

CatKiller, you are the man!!!  Your response along with the edits was what I was actually looking for...  Now the whole thing makes a lot of sense...  Thanks a lot.

All you Linux guys, watch out, here I come....  Slowly, but surely... :-D

---

### Post by CatKiller on 2006-11-03
> **Duwady said:**
> CatKiller, you are the man!!!  Your response along with the edits was what I was actually looking for...  Now the whole thing makes a lot of sense...  Thanks a lot.

All you Linux guys, watch out, here I come....  Slowly, but surely... :-D

Two edits, and there's still typos *sigh*

Glad it's clicked. I **will** be expecting you to explain stuff to me in the future.

---

