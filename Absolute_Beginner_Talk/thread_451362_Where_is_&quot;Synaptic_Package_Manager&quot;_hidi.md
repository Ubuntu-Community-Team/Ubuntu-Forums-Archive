---
title: "Where is &quot;Synaptic Package Manager&quot; hiding my downloads???????????"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by stuck on 2007-05-22
After an almighty struggle and random swearing and smashing things ive finally got Ubuntu to access the web.

I've down loaded things with "synaptic package manager" but where the hell is it hiding them. I cant find the files or folder.

Ive got the same problem with Applications>>Add/remove, where the hell does this hide them.

I want things to show up in applications or somewhere when i download and install them, is it possible to do it.

I want it more like Vista. Point and click and it works. Is it possible to do this with Ubuntu

Still havnt been able to get madwifi-ng installed but that another problem.

---

### Post by taurus on 2007-05-22
If you tell which programs/apps you installed with synaptic, then perhaps somebody can tell you where they are, only if you calm down.

---

### Post by argie on 2007-05-22
What you install should show up in the menus with a nice icon. Some packages don't have a menu item (like codecs, or data packages). 
If you want to see what files your package contains, highlight the package in Synaptic and click Properties on the top toolbar. Then switch to the "Installed Files" tab. That will show you what the package contains and where it puts the files in it. Your program will most likely be the one with 'bin' in the path. 
For example: For the 3ddesktop package, the programs are /usr/bin/3ddesk and /usr/bin/3ddeskd

Synaptic and apt (in general) puts downloaded packages in a cache. The cache is in:
/var/cache/apt/archives

Perhaps you would like to tell us what program you are having trouble with?

---

### Post by ikonia on 2007-05-22
Hello, 

the package manager downloads the packages and puts them in the appropriate place on your file system.

Some do not have launcher configurations for the gnome menu.

There are multiple types of packages that can be downloaded.

1.) an X based application with a gnome launcher.
Gimp is an example of this - the package manager will download and install everything in the correct place and update the gnome menu to include the gimp icon for launching.

2.) an X based application without a gnome launcher
xterm is an example of this, this s an X11 based application that insn't intergrated within gnome, the package manager will install this for you in the correct place (for example /usr/X11/bin) but requires you to configure the launcher.

3.) a none X based application.
"ps" is an example of this. the package manager will download and install the ps binary into the appropriate location ( /bin) but because this application has to be executed from a terminal there is no point having a launcher icon as it will not execute.

4.) a server or daemon
Mysqld is an example of this, the mysql client is launched from a terminal however the daemon or server process is not "launched" or invoked at all by the user. the package manager will download and install the daemon for you (mysqld in /usr/bin) and create an init script (/etc/init.d) for the operating system to stop and start mysqld as appropriate. The user will never see this run.

---

### Post by ubuntonista on 2007-05-22
One a command line, use $dpkg -L <package-name> to get a list of files installed by the package. In synaptic, select the installed package, right click and view the details to know where things were put.

Now, if, say, you installed a package of fonts, of course there wont be any menu entries or any place where you will see the fonts, but they are installed nevertheless.

On windows, if you install a driver, or, say new fonts, these don't show up in the menus either. So there!

---

### Post by stuck on 2007-05-22
applications>>>>add/remove.

Downloaded ATI binary X.org driver.


downloaded about 7 different/random things(programs not fonts or scripts) with "synaptec...." didnt really take much notice of what they were. Thought they might show up in the menus. I guess they not important as i was just trying it out to see how to work it.

Yes your right, sorry I need to calm down. Only been online for last 12 hours trying to connect to the net, booting between Vista and Ubuntu(even re-installed it) every 10 mins or so takes it out of you. (The mouse is now dead, had a little 13yr style temper tantrum on it :evil:)


Ive read loads of the HOW TO's but there is so much to take in.


Thanks for any help.

---

### Post by argie on 2007-05-22
Just hang in there. I don't think the ATI driver gives you any menu entries, it just tells your computer how to interact with the graphics card properly.

---

### Post by stuck on 2007-05-22
Thank you.

---

### Post by shavenlunatic on 2007-05-22
> **stuck said:**
> downloaded about 7 different/random things(programs not fonts or scripts) with "synaptec...." didnt really take much notice of what they were. Thought they might show up in the menus.

erm, well if they have  GUI end they are most likely in your menu system somewhere, but if you didn't know what apps you had in there to start with and you don't know what you added, how can you know that they aren't there??


/me sighs
#-o

---

### Post by psmar on 2007-05-22
for future reference should you be running feisty, up in _systems preferences, main menu_ any program that has a gnome launcher config file can be added or hidden on your applications menu

---

### Post by irish_flu on 2007-05-22
I might be able to clarify a couple of things, most of which have been said by other folks.

- When you use Synaptic (or add/remove programs) it not only downloads the application, it installs it when you hit "apply".  With Vista, you download and then install.  With Synaptic Package Manage, there's one less step  :)

- if the thing you install is a driver (or some other non-interface type of thing, like a codec to play DVD) you don't see a menu entry.  There may be some configuration you need to do for your video card driver, use google and these forums to see what setup your ATI driver might require.

-if the thing you install is a command-line-only application, you won't see a menu item for that either.

-If you want to make sure things are working right as far as program download/installation goes, pick something that you know darn well has a GUI (like a game or something).

Good luck my friend, hang in there!

---

### Post by fjf on 2007-05-22
Yes, this is where linux and windoze aren't the same.  I sometimes just type in a terminal the name of the program I just installed, and in the few seconds that it takes to initiate (or not) I silently pray to the Linux God for it to work...  ;)

---

### Post by stuck on 2007-05-22
Thank you all for the constuctive advice, and not flaming me.

My little tantrums over now, I think I spent too long (sudo)bashing my head against the wall.

Guess my 15 years or so of "hand holding" by MS made me forget my DOS days.

Now I've managed to kill something else, so time for a new thread.


MOD: can close this thread as resolved.

---

