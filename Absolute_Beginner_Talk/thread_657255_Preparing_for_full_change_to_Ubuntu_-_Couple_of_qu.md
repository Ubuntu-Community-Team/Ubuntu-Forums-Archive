---
title: "Preparing for full change to Ubuntu - Couple of questions"
date: 2008-01-03
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-01-03
Hi there. Thanks to the good advice found on this forum I am now *almost* ready to change over to Ubuntu from Windows. I have installed Virtualbox, which now contains Windows 2000 and those few applications that I simply cannot live without, and I am about ready to make the switch, however I have a few questions still.

Please forgive me if some of these seem foolish, Im going as fast as I can!

**1) Firewall and Virus checkers**
I have installed Firestarter, and have a *fair* idea of what I am doing with it, however, I only ever see the little arrow icon for it in the system panel *after* I have deliberately clicked on the icon in the menu to start it. Does this mean it is only running after I have implicitly started it, and if so, how do I get it to start when the desktop starts? (In other words how do I get it to behave like a Windows firewall, and simply be there all the time?)

As for virus scanners: I know that Ubuntu is more secure etc, etc, but I am naturally paranoid about virus infection and malware intrusion and I think thats a healthy attitude. So! Do I need this protection, and if so what programs would I need to install?

**2) Desktops**
This might seem strange, but I would really like an application to only ever start on one of my desktops, regardless of which desktop I might be on when I click its icon. Is there some way to force it to do so?

**3) Wine**
There are so many posts and articles available about this I am almost afraid to ask a question, but Iv simply not been able to find the answer to this!
I have installed Virtualbox because although I have Wine installed I have no idea how to go about installing a windows application for it! I mean, its there in the menu, and I seem to have a c: drive of some kind, but how do I install another program?

**4 Whats running and how do I stop it?**
In Windows I had the three fingered salute, where I could invoke the Task Manager and see what processes are running, how much memory and CPU they are taking up, and terminate them if need be. Is there anything similar for Ubuntu?

Edit: Oops! Forgot one!

**5 Backups**
How do I go about backing up my important data to a CD/DVD? Im an avid fan of this, since the OS can be replaced, but my data cannot!

Thanks for any help you might be able to give.

Max

---

### Post by ~LoKe on 2008-01-03
1.  Firestarter is just the graphical frontend for "IPTables", which is your firewall and is always running unless you told it not to.

3.  Right click on the .exe file and choose open with wine.  Or, from the command line, type:
```
wine /path/to/file.exe
``` and it should open and allow you to install.

4.  Gnome has gnome-system-monitor, I think it's located in System -> Administration -> System Monitor.  Or "top" from the command line.

---

### Post by aysiu on 2008-01-03
> **MaxVK said:**
> 
As for virus scanners: I know that Ubuntu is more secure etc, etc, but I am naturally paranoid about virus infection and malware intrusion and I think thats a healthy attitude. So! Do I need this protection, and if so what programs would I need to install? There's no reason to have a virus scanner unless you are running a mail server. Read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)


> **3) Wine**
There are so many posts and articles available about this I am almost afraid to ask a question, but Iv simply not been able to find the answer to this!
I have installed Virtualbox because although I have Wine installed I have no idea how to go about installing a windows application for it! I mean, its there in the menu, and I seem to have a c: drive of some kind, but how do I install another program? Read this:
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

> **4 Whats running and how do I stop it?**
In Windows I had the three fingered salute, where I could invoke the Task Manager and see what processes are running, how much memory and CPU they are taking up, and terminate them if need be. Is there anything similar for Ubuntu? Try Gnome System Monitor (Alt-F2 ```
gnome-system-monitor
```) You can also stop services by going to System > Administration > Services

> **5 Backups**
How do I go about backing up my important data to a CD/DVD? Im an avid fan of this, since the OS can be replaced, but my data cannot! Try a CD burning program like K3B or GnomeBaker.

---

### Post by seventhc on 2008-01-03
For your question on firestarter, it does start at start up, but the icon only shows when you click on it to check the logs or whatever. So if you don't click on it, you won't see the icon but it is running.

For antivirus, some say it is good to use just for when you trade files with windows users, since it may not harm your machine, but possibly could theirs. This is all opinion.
I don't use wine, so no info on that.

To see whats running, you can click on System>Administration>System monitor. from there you can see whats running and end tasks.

---

### Post by laidback on 2008-01-03
For 4) have a look at:-

System>Administration>Sytem Monitor

Also useful to identify an app that needs to be killed (not often; but useful)

---

### Post by hyper_ch on 2008-01-03
> **MaxVK said:**
> 
**1) Firewall and Virus checkers**
I have installed Firestarter, and have a *fair* idea of what I am doing with it, however, I only ever see the little arrow icon for it in the system panel *after* I have deliberately clicked on the icon in the menu to start it. Does this mean it is only running after I have implicitly started it, and if so, how do I get it to start when the desktop starts? (In other words how do I get it to behave like a Windows firewall, and simply be there all the time?)

Firestarter is not a firewall. Firestarter is just a tool to configure iptables. Iptables is the actual firewall and it runs from boot. Although you can use also firestarter to check how the firewall performs but no need to keep it running.

> **MaxVK said:**
> 
As for virus scanners: I know that Ubuntu is more secure etc, etc, but I am naturally paranoid about virus infection and malware intrusion and I think thats a healthy attitude. So! Do I need this protection, and if so what programs would I need to install?

You don't need any. A virus can attack through a leak. So ones there is a virus, the software producer could (a) patch the system and make the virus ineffecitve, or (b) do nothing.
Linux is being patched for the 40 viruses there are around (which can affect Linux... compared to 60'000+ viruses for windoze). Basic rules: Only get software from trusted sources, like the repositories and you should be fine... there's a whole lot more on that issue but basically forget about AV software, there's no need for it.


> **MaxVK said:**
> 
**2) Desktops**
This might seem strange, but I would really like an application to only ever start on one of my desktops, regardless of which desktop I might be on when I click its icon. Is there some way to force it to do so?

Are you running KDE? I think only in KDE all programs appear on all desktops. You can, however, change this behaviour... but the way on how to do it depends on what Desktop you run ;)


> **MaxVK said:**
> 
**3) Wine**
There are so many posts and articles available about this I am almost afraid to ask a question, but Iv simply not been able to find the answer to this!
I have installed Virtualbox because although I have Wine installed I have no idea how to go about installing a windows application for it! I mean, its there in the menu, and I seem to have a c: drive of some kind, but how do I install another program?

Wine tries to translate windows procedures into linux format. Once installed (and configured --> run "winecfg" in the terminal) you would then run wine this way:
```

wine /media/cd-rom/setup.exe

```
or for an installed program (depending on the installation path):
```

wine ~/.wine/drive_c/programs/PROGRAM/file.exe

```

> **MaxVK said:**
> 
**4 Whats running and how do I stop it?**
In Windows I had the three fingered salute, where I could invoke the Task Manager and see what processes are running, how much memory and CPU they are taking up, and terminate them if need be. Is there anything similar for Ubuntu?

There are plenty of ways in Linux. I prefer to do that through the temrinal with an additional application called htop. There's also a terminal program called "top" but the htop is, IMHO, nicer:
```

sudo apt-get install htop

```
and run it by:
```

htop

```
You see on the bottom a couple of F-Keys to perform things and you can select processes with the mouse or by using up/down arrow keys.

[QUOTE=MaxVK;4065453]
**5 Backups**
How do I go about backing up my important data to a CD/DVD? Im an avid fan of this, since the OS can be replaced, but my data cannot!
[/code]
Well, install some burning software (I like K3B the best) and copy your stuff on it... basically you only need to backup your the /home folder. Other folders might also be good like /etc or /var/www or /var/lib/mysql

---

### Post by carrett on 2008-01-03
> **aysiu said:**
> 
Try a CD burning program like K3B or GnomeBaker.


Or for CD/DVD backups, nautilus has a pretty slick interface, just type this into your address bar in a nautilus window:

```
burn:///
```

---

### Post by PeterJS on 2008-01-03
> **MaxVK said:**
> Hi there. Thanks to the good advice found on this forum I am now *almost* ready to change over to Ubuntu from Windows. I have installed Virtualbox, which now contains Windows 2000 and those few applications that I simply cannot live without, and I am about ready to make the switch, however I have a few questions still.

Please forgive me if some of these seem foolish, Im going as fast as I can!

**1) Firewall and Virus checkers**
I have installed Firestarter, and have a *fair* idea of what I am doing with it, however, I only ever see the little arrow icon for it in the system panel *after* I have deliberately clicked on the icon in the menu to start it. Does this mean it is only running after I have implicitly started it, and if so, how do I get it to start when the desktop starts? (In other words how do I get it to behave like a Windows firewall, and simply be there all the time?)

As for virus scanners: I know that Ubuntu is more secure etc, etc, but I am naturally paranoid about virus infection and malware intrusion and I think thats a healthy attitude. So! Do I need this protection, and if so what programs would I need to install?


This is a common point of confusion, firestarter isn't a firewall, it's a firewall monitoring and configuration tool, the firewall itself, iptables, is automatically started at boot before the network interfaces.

As for AV the maxim of an ounce of prevention is better than a pound of cure is the model to follow. The ubuntu security guide:
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)


> 
**2) Desktops**
This might seem strange, but I would really like an application to only ever start on one of my desktops, regardless of which desktop I might be on when I click its icon. Is there some way to force it to do so?

I've heard mention of a program called wmctl that seems todo stuff like that, but can't find an ubuntu package for it, or any documentation, I've seen it's used in scripts, but the use is cryptic if you don't know exactly what it's doing.

> 
**3) Wine**
There are so many posts and articles available about this I am almost afraid to ask a question, but Iv simply not been able to find the answer to this!
I have installed Virtualbox because although I have Wine installed I have no idea how to go about installing a windows application for it! I mean, its there in the menu, and I seem to have a c: drive of some kind, but how do I install another program?

To install stuff in wine you can just double click on the installer, it will work (good) or not (bad), because wine is kinda hit or miss like that. If you've got virtual box installed and working go with that, google around for virtual box seemless integration, I've seen some pretty impressive hacks done to merge virtualbox in to the desktop.

> 
**4 Whats running and how do I stop it?**
In Windows I had the three fingered salute, where I could invoke the Task Manager and see what processes are running, how much memory and CPU they are taking up, and terminate them if need be. Is there anything similar for Ubuntu?


Linux also has a three finger salute, it's different keys and works slightly differently. Ctrl+ Alt+Backspace kills the X session and all running apps, not exactly like the windows version but it'll get you out of lockups

As for monitoring if you go to System > Administration > System Monitor, the gnome system monitor will open up and it behaves a lot like the windows task manager, I don't believe their is a default key combo to open it up, but I haven't looked very hard.

> 
Edit: Oops! Forgot one!

**5 Backups**
How do I go about backing up my important data to a CD/DVD? Im an avid fan of this, since the OS can be replaced, but my data cannot!

Thanks for any help you might be able to give.

Max

Under Places there is a CD/DVD Creator, you can use that to just burn files an manage it your self. If you look around at backup tools, like partimage and rsync, they will create backups for you that you can then burn to disk.

---

### Post by MaxVK on 2008-01-03
Wow! You guys are quick off the mark!

Thanks to all who have replied. I'm working through each of the things mentioned, and in reply to hyper_ch I am running Gnome, since that is what was installed when I installed Ubuntu. I thought you needed to install KUbuntu to be using KDE.

Again, thanks to everyone who has contributed.

Max

---

### Post by aysiu on 2008-01-03
> **MaxVK said:**
> I thought you needed to install KUbuntu to be using KDE. You need to install KDE to use KDE. Kubuntu is just one implementation of KDE (it is the *kubuntu-desktop* metapackage--other KDE metapackages are *kdebase*, *kde-core*, and *kde*).

But you do not need to install KDE to install and use KDE applications. You can use Konqueror or AmaroK in Gnome, for example.

---

### Post by MaxVK on 2008-01-03
Right. Well. A little time to digest things!

Firstly, thanks for the advice on security issues. I knew that Firestarter was a front end to the iptables settings, but I was unsure about its status. Cleared up now. As for virus and malware problems, I'm still reading up on it.

I now have wmctrl installed, and I found a website ([http://sweb.cz/tripie/utils/wmctrl/]("http://sweb.cz/tripie/utils/wmctrl/")) that shows how to use it, although so far Im not entirely sure how I will integrate that into the startup icon of a program.

I rather like the K3B interface for my backup needs so Ill be using that in the future.

Now then, one last question if I may, born out of the Wine question (Sorted, thanks very much!) and the firewall question:

Is it possible to deny a specific application access to the network/internet, and if so, how? I can see nowhere in Firestarter to do this, and so far in all my reading I have seen nothing that suggests that its possible, but surely you must be able to block access to certain programs?

Very many thanks to all who have contributed; you are sure making this transition from Windows a lot less painful that I thought it would be!

---

### Post by PeterJS on 2008-01-03
For wmctl, that's the best documentation I've seen, I think for the launcher something like
```

*appname* & wmctrl -r *"Window Title"* -t *desktopnumber*

```I can't find which package wmctl is in, I'm starting to think there isn't one, I'll see what I can do about building a deb with checkinstall. I'm sure after I play around with it more I can give a better answer.

Edit:
The name of the program is wmctrl (with an r) and is in the ubuntu repositories, it kinda works with compiz but not really, back to poking things.

Edit2:
However it works beautify with metacity. Now I'm going to see about getting a launcher that works.

---

### Post by MaxVK on 2008-01-03
Hi Peter, I found a few links on the wmctrl page and one was to a program (Also in Synaptic) called Devils Pie, which uses wmctrl to identify windows by name as they open, and if it finds a match, performing various tasks on them, including forcing them onto a particular desktop.

[Devils Pie Main Site]("http://www.burtonini.com/blog/computers/devilspie")

Devils Pie Turorials: (Not had the chance to read through these properly yet, although the last one seems to be a little old.

[http://foosel.org/linux/devilspie](http://foosel.org/linux/devilspie)
[http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)
[http://xlife.zuavra.net/index.php/48/#ig-7](http://xlife.zuavra.net/index.php/48/#ig-7)

You quoted some code in your post, mentioning that it was for the 'Launcher'. Any chance of an explanation on that? Where would the code go (Iv found the launcher creation thing on the desktop, but Iv yet to try and work out how to use it properly).

I did find a program, billed as a Firewall, that claimed it could block programs by name, but as with all other applications that I find, I search for them in Synaptic, and if I don't find them I leave them alone. This one wasn't in Synaptic so I carried on surfing and I have now managed to lose the link! and my poor old memory cant recall the name of the program!

---

### Post by Paqman on 2008-01-03
For backups, there's a good package called sbackup. It can make one-off or incremental backups of important system and/or data files. You can specify what to back and where. Automated. Handy!

---

### Post by PeterJS on 2008-01-03
Devil's pie looks like it's based on pre-configured rules and doesn't do so well for doing stuff on the fly. And for some reason the launcher doesn't want to execute complex commands. The best I've been able to come up with is creating a small shell script that launches the program given to it and then runs wmctrl on that.
Devilspie clone (dpc.sh):
```

#!/bin/bash
$1 &
sleep 1
wmctrl -r "$2" -t $3

```And then in the launcher for the command portion:
```

/home/user/dpc.sh *appname* "*windowtitle*" *desktop_number*

```For example to open konqueror on desktop 0 the command would be:
```

/home/user/dpc.sh konqueror "Conq" 0

```

Not the best solution, doesn't work under compiz, it's pretty hackish, but it gets the job done.

---

### Post by MaxVK on 2008-01-03
Shell Script. Aha. Yes. Well.

Im very new to this, so while I understand roughly *what* a Shell Script is, the actual creation and execution of them is still a bit of a dark art.

Am I right in assuming that you create that script in a text editor, save it as dpc.sh in your home folder, and then call it from a launcher created on the desktop? If so, what are the first three lines for and would it then be permissible to have a 'Scripts' folder in your home folder, where you could store all your scripts? (Changing the location in the launcher of course)

---

### Post by vambo on 2008-01-03
> **MaxVK said:**
> Shell Script. Aha. Yes. Well.

Im very new to this, so while I understand roughly *what* a Shell Script is, the actual creation and execution of them is still a bit of a dark art.

Am I right in assuming that you create that script in a text editor, save it as dpc.sh in your home folder, and then call it from a launcher created on the desktop? If so, what are the first three lines for and would it then be permissible to have a 'Scripts' folder in your home folder, where you could store all your scripts? (Changing the location in the launcher of course)

You might want to have a look at and download this: [http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

The first couple or so chapters are a very good intro to bash and bash scripts.

---

### Post by eolson on 2008-01-03
Something I found out about firestarter.   I like to play around alot.   I set some iptable rules with firestarter.  Then I uninstalled it using add/remove.  The next day I re-installed it and the rules were still there.  Suspect once you set the rules iptables remembers them no matter what you do to firestarter.

---

### Post by PeterJS on 2008-01-03
> **PeterJS said:**
> 
```

#!/bin/bash
$1 &
sleep 1
wmctrl -r "$2" -t $3

```
 
The first line tells the shell that this isn't just a text file but a series of command to be executed by the program given (in this case the shell itself). The second line tells the script to run the first thing it was give as a program, the & tells it to start the command in the background and keep running the script in the foreground. The sleep command tells the script to pause for one second to give the window time to open up. The last line runs wmctrl telling it to move the window.

Yeah having a scripts folder isn't a bad idea, I've got one, I'm just lazy about putting things in it, I'll remember every once in a blue moon and go on a cleaning spree. It's also not a bad idea to edit your ~/.bashrc to add your scripts folder to your $PATH so you can execute them from anywhere without using the full path. For example you could add:
```

export PATH=$HOME/scripts/:$PATH

```to the bottom of the bashrc.

After saving the script but before running it you have to tell the system that it's allowed to execute the script with:
```

chmod +x *scriptname*

```The +x means add execute privilages. Going back to the AV thing this is one of the reasons that linux viruses are rare, you have to explicitly give them execute permissions before they can run, so even if something nasty does get on your system they then have to trick you in to giving it executable privileges.

---

### Post by MaxVK on 2008-01-03
Things are beginning to fall into place with the Shells Scripting (Thanks for that link vambo), and I have created that script, given it the correct privileges and created the launcher.

However, although the program Im calling opens just fine, it opens on the same desktop that Im working on, and its not moved to the specified one. Unfortunately its rather late here now, and Im too tired to try and work out whats going on.

Many thanks for all your help.

---

### Post by ByteJuggler on 2008-01-03
> **MaxVK said:**
> Am I right in assuming that you create that script in a text editor, save it as dpc.sh in your home folder, and then call it from a launcher created on the desktop? If so, what are the first three lines for and would it then be permissible to have a 'Scripts' folder in your home folder, where you could store all your scripts? (Changing the location in the launcher of course)

Yep more or less. Some comments:
1) Linux don't rely solely on file extentions to identify file types.  Instead it uses "magic numbers", that is the first 2 bytes of a file is deemed to indicate the file type.  The characters #! correspond to the magic number for "script" and the convention is that the path to th interpreter for executing the script shall follow the "#!" magic marker.  Furthermore, executable files are marked in the filesystem, so you can mark a script as non-executable if required.  So, in your case you can name your script whatever you like (without having to worry about extensions), and simply mark it as executable, after which it will run when launched, wether from a terminal prompt or a launcher.
2.) It's quite common to have your own scripts (or more generically "bin" for "binaries") folder where your own program binaries and scripts may live. If you create a "bin" folder in your home folder, then the system will automatically add that folder to your search PATH environment variable, so that any commands/programs/scripts you place in it will automatically be found when run from a command prompt.

---

### Post by hyper_ch on 2008-01-04
I think this is a good page for starting shell scripting:

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by MaxVK on 2008-01-04
Thanks for all the help everyone. Im now going through the links and reading up on things. No doubt Ill be back asking questions soon enough! ;)

---

