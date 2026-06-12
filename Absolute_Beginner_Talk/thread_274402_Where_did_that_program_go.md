---
title: "Where did that program go?"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by NoobieDoobie on 2006-10-09
Hi, I'm a noobie to Ubuntu and this forum. Instead of going straight to my problem, I would like to mention that installation was truly painless: no hassle internet connection and it recognized my Revolution 7.1 audio card, so I'm surfing and jamming. I must say I'm impressed with Ubuntu.

The problem is when I install programs sometimes it works and sometimes the program is nowhere to be found. For example, I installed Audacity with the Synaptic package manager and it appeared on the menu and works fine. However, when I installed MyPasswordSafe, nothing appeared on the menu and I can't even find the installation directory (probably cuz I'm a Noob, but why is it not on the menu?). The same thing happened with another password program. What gives?

---

### Post by Kateikyoushi on 2006-10-09
Seems those were not added to the menu.
You can do it manually.
To find which files did the application install right click on the package in synaptic then properties and select installed files.

---

### Post by timnoc1456 on 2006-10-09
Just logout and login again. You'll most problably find the prog/appl in the menu. If not try restart the system. This is provided you had installed the software through sypnaticmanager. Else go to: "/usr/bin " and locate the execuble file (same as in windows e;g C/program/*name_of application).

---

### Post by NoobieDoobie on 2006-10-09
Which file would I add to the menu? In Windows it is usually an .exe file, but Linux is VERY different.

---

### Post by CatKiller on 2006-10-09
> **timnoc1456 said:**
> Just logout and login again.

Or, later, when you're feeling more confident about these things,```
sudo killall gnome-panel
```

---

### Post by timnoc1456 on 2006-10-09
Hello Catkiller,

The first reason being and Ubuntu might be help! in whatever capacity, did you play the Experience ubuntu.ogg file on your desktop?

I believe I need not  be confident, to help others in need. It's thier progative to take or not... ( only in a lighter mood) ..hiss

---

### Post by CatKiller on 2006-10-09
I'm afraid I didn't. And I'm sorry, I didn't mean to offend - I meant that when the **original poster** was feeling more confident he could run that command.

It requires knowing how to find the terminal, knowing how to use sudo, and not being panicked by the fact that the command has "kill" in it, so it's not really something that a beginner would instinctively reach for.

But it does have the advantage of refreshing the menus without having to save and close other applications, so it's a lot quicker.

Again, apologies if I caused you any offense. And you don't need to be some Linux veteran of many years to help someone here - I've not been using it for very long and I like to think that I've managed to help some people. I'm sure you have too, and will continue to do so. In this case, your suggestion was a very good one, and tailored well to the requirements of the original poster at this time.

---

### Post by NoobieDoobie on 2006-10-09
> **Kateikyoushi said:**
> Seems those were not added to the menu.
You can do it manually.

It is not listed under "Add/Remove Applications." How can I do it manually?

> To find which files did the application install right click on the package in synaptic then properties and select installed files.

I found LOTS of installed files but no way to know which file to put on the menu, or how to get it on the menu.

---

### Post by CatKiller on 2006-10-09
> **NoobieDoobie said:**
> I found LOTS of installed files but no way to know which file to put on the menu, or how to get it on the menu.

Of the installed files, those that are in directories called bin - /bin or /usr/bin, usually - are the commands used to run the program. They usually have the same name as the program you installed. If typing the name of them in a Terminal window opens the program that you want; success!

> It is not listed under "Add/Remove Applications." How can I do it manually?

Right-click on the Applications menu and select "Edit Menus". This will open a program called Alacarte. Go to the menu entry for the menu you'd like to add your application to and then select File -> New Entry. Put whatever name and comment you'd like in their respective boxes, and in the Command box type the command that you discovered above. Select an icon if you wish. Click on OK and you're done.

---

### Post by NoobieDoobie on 2006-10-09
With Nautilus I found GNUCash in /usr/bin but it is not on the menu either. I can launch gnucash from nautilus, but I can see no way to get it on the menu. This is getting frustrating.

---

### Post by CatKiller on 2006-10-09
> **NoobieDoobie said:**
> With Nautilus I found GNUCash in /usr/bin but it is not on the menu either. I can launch gnucash from nautilus, but I can see no way to get it on the menu. This is getting frustrating.

That is what Alacarte is for.

---

### Post by NoobieDoobie on 2006-10-09
> **CatKiller said:**
> 
Right-click on the Applications menu and select "Edit Menus". This will open a program called Alacarte. Go to the menu entry for the menu you'd like to add your application to and then select File -> New Entry. Put whatever name and comment you'd like in their respective boxes, and in the Command box type the command that you discovered above. Select an icon if you wish. Click on OK and you're done.

Ahhh. Thanks. I can't find MyPasswordSafe, but I right-clicked gnucash and selected "open" and it worked. Would the path be /usr/bin/gnucash

Why doesn't the OS list these programs on the menu automatically?

---

### Post by podunk on 2006-10-09
An easy thing to do is create a launcher. Resize Nautilus so you can still use it but get to the desktop. Right click the desktop and chose “Create Launcher”

click and drag the file you want to run from Nautilus over to the launcher and drop it in the 
Command
space.  Give it a name, any comments that you want, click OK. You can leave this on your desktop or drag it to the work bar at the top of your screen where it is easy to get to.

Another thought!

If you get the program automatix from here:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

One of the things you can install is “Debian Menu” and that will keep up with all the programs you install.

---

### Post by CatKiller on 2006-10-09
> **NoobieDoobie said:**
> Ahhh. Thanks. I can't find MyPasswordSafe, but I right-clicked gnucash and selected "open" and it worked. Would the path be /usr/bin/gnucash

For programs that are sensible - which is most, if not all, of the supported ones you may find in the repositories - you don't need to specify the path to the executable (although you may, if you have more than one version installed, for example), you need only specify the name. If you find that that doesn't work for a particular program, then you should specify the full path.

Oh, and apparently the command to run MyPasswordSafe is simply MyPasswordSafe. It's in /usr/bin.

> Why doesn't the OS list these programs on the menu automatically?

It depends entirely on the application. If the developers haven't included a .desktop file, or if it is malformed in some way, then it won't appear on the menu.

---

### Post by szf on 2006-10-09
> **NoobieDoobie said:**
> Ahhh. Thanks. I can't find MyPasswordSafe... Why doesn't the OS list these programs on the menu automatically?

First, props to you in selecting the Linux-based port Mr. Schneier's excellent program. I believe that you may have run afoul in that MyPasswordSafe is not in the official Ubuntu repositories AFIACT.  You'll want to check that it did install correctly using [FONT="Courier New"]
locate[/FONT] (don't overlook [FONT="Courier New"]updatedb[/FONT] first if the install is very recent) and then use alacarte to point to the binary.

Alternately, there's Revelation for Gnome...

---

### Post by Andavane on 2008-02-12
> **NoobieDoobie said:**
> Ahhh. Thanks. I can't find MyPasswordSafe, but I right-clicked gnucash and selected "open" and it worked. Would the path be /usr/bin/gnucash

Why doesn't the OS list these programs on the menu automatically?

I am also struggling to get "[COLOR="Red"]MyPasswordSafe[/COLOR]" onto the applications menu. I have right-clicked on "Applications", then "+ New item". Under Name I have typed in "[COLOR="Red"]MyPasswordSafe[/COLOR]" and in command I have browsed to usr\binMyPasswordSafe.
Should I click there and open? I must admit I am a bit fearful, in case it messes things up!

I was in  Ubuntu Feisty last year, and left due to hardware problems. Now I have returned and installed gutsy.

Regards
John

---

### Post by Andavane on 2008-02-12
.

---

### Post by Andavane on 2008-02-22
> **timnoc1456 said:**
> Just logout and login again. You'll most problably find the prog/appl in the menu. If not try restart the system. This is provided you had installed the software through sypnaticmanager. Else go to: "/usr/bin " and locate the execuble file (same as in windows e;g C/program/*name_of application).
In my case I have installed
imagemagick
but have been totally unable to locate where it is.
I have read the posts in this thread as best I am able.

Being unable to find an installed program seems to be becoming a regular thing.

Right-clicking on imagemagick properties and going to "Installed files" shows a very long list of files.

Regards

John

---

### Post by Andavane on 2008-03-23
> **CatKiller said:**
> I'm afraid I didn't. And I'm sorry, I didn't mean to offend - I meant that when the **original poster** was feeling more confident he could run that command.
and
> **CatKiller said:**
> Or, later, when you're feeling more confident about these things,```
sudo killall gnome-panel
```
Hi I followed this command and now my entire panel 
Help... I ran that command and now I can't get my panel back.
What do I do now.
John

---

### Post by Darganot on 2008-03-23
It's not as frustrating as you think, just different.  What you need to do is type the name of the program to run it.  There wasn't an icon added to the menu so you have to do it manually.  You can also open a terminal and just type the name of the program you want in (it's CASE SENSITIVE):

> GNUCash

The hardest thing is figuring out what it's named.  Since you already know how to get to /usr/bin/ you can do this.  All your programs should be listed here.  These are the 'binaries' for your programs.  Running them runs the program, SIMILAR to a windows .exe - but the whole program is usually somewhere else on your tree, like /usr/share/ or somewhere like that.

Once you know the name, you can make a shortcut on the desktop if you prefer by right clicking and selecting add launcher.  Put the name of your program in the command line and add the rest yourself.  Now you have an icon to run the program.

---

### Post by Andavane on 2008-03-23
> **Darganot said:**
> It's not as frustrating as you think, just different.  What you need to do is type the name of the program to run it.  There wasn't an icon added to the menu so you have to do it manually.  You can also open a terminal and just type the name of the program you want in (it's CASE SENSITIVE):

The hardest thing is figuring out what it's named.  Since you already know how to get to /usr/bin/ you can do this.  All your programs should be listed here.  These are the 'binaries' for your programs.  Running them runs the program, SIMILAR to a windows .exe - but the whole program is usually somewhere else on your tree, like /usr/share/ or somewhere like that.

Once you know the name, you can make a shortcut on the desktop if you prefer by right clicking and selecting add launcher.  Put the name of your program in the command line and add the rest yourself.  Now you have an icon to run the program.
Thank you very much: the trouble was though, I couldn't get to the terminal because there was no panel, I couldn't shut down, navigate anywhere... nothing. Pressing F2+alt did nothing. Eventually  I held down button in a wild random panic and got a black screen thing asking for my user name and then password. When I did that it asked me again, and so on. IN the end I just held down the on button until it killed everything.
It seems to have booted up normally, with panels restored.
I guess I had better create a desktop launcher to a terminal so I can at least shut the system down gracefully should the need arise. Will try to work that out next.
Kind regards
John

---

### Post by Darganot on 2008-03-23
ctrl+alt+backspace restarts gnome (returns you to login screen)

ctrl+alt+del restarts when at a terminal (after hitting ctrl+alt+F2)

There are ways to change ctrl+alt+del to do whatever you want it to (bring up the system monitor or restart the system), just search around the forums.

---

### Post by Darganot on 2008-03-23
from a terminal you can also type

> sudo reboot

or

> shutdown -r now

to restart your computer

---

### Post by Andavane on 2008-03-25
> **CatKiller said:**
> That is what Alacarte is for.
I didn't know what or where Alacarte was, but found it last night.
For any newbie who was equally mystified, you:

Right-click on the desktop and selected "Launcher"
(If you want it in the panel (top or bottom) you Right-click on the panel, select add to panel then 'custom application launcher' if the item you want isn't in the displayed menus);
Then you select 'browse'/ file system/usr/bin*

click on the item you want.

Remember to put the name of your choice in the 'name' panel pr it won't work!

* 'browse'/ file system/usr/games

if the item you want is in there.

---

