---
title: "Wine Install"
date: 2006-01-14
forum: Absolute Beginner Talk
---

### Post by mike63730 on 2006-01-14
I Installed Wine But Still Cant Find It When I Got To A File And Try To Open With Its Not In The List

---

### Post by Arktis on 2006-01-14
You should really be using from the terminal anyways.  If something goes wrong, you've got a better chance of finding out what it is by reading the terminal output.

But if you really want to open double-clicked exe's with wine, add it yourself.  Right-click the file > "Open with Other Application..." > "Use Custom Command".

---

### Post by mike63730 on 2006-01-14
I Dont Think I Got It Installed Right I Am New With Linux And Lost I Am Thinking About Going Back To Microsoft!! I Hate The Thought Of That

---

### Post by Arktis on 2006-01-14
Yeah well, you should take some time to learn first.  It's a steeper curve than you might have anticipated, especially for a win-user.  But if you want to go back to windows, nobody is going to stop you.  You should at least dual-boot for a while.  This let's you learn linux while still being able to jump back into windows if the need should arise.

---

### Post by mike63730 on 2006-01-14
ya i want to learn cause i hate the other one and as far as wine i cant figure weather its installed or  not i need advice on how to proper way of installing it

---

### Post by hyg53 on 2006-01-14
What do you want to do with wine?
Usually, people first reaction is that they try to install their windows favourite applications on linux (this why my reation too).

If you tell us what you need, we may find a linux program that suits what you need.

Don't forget that only few applications work properly with wine

---

### Post by BigOldCar on 2006-01-14
Greetings:

I also have a question about Wine, so I put it here rather than start a new thread.

Ubuntu is up and running (nice 'n' easy) minus sound (which I'll fight with later).  However, my internet access is through Netzero (till I move and get DSL), which means that a little Windows program has to run for me to get onto the Internet.  Which means I need to have Wine working to access the Internet.  However, all the instructions I've seen basically direct the computer to go download some stuff from somewhere to complete the Wine install.

In other words: I need Wine to get onto the Internet.  But I need to be on the Internet to install Wine.

Is there an offline way to go about this?

Please be as exacting as possible.  I am able to access the Internet through another PC, which can also burn CDs.  But entering the debs.[http://blah](http://blah) blah blah address into the web browser only yields an error message.

All help appreciated!

S.W.

---

### Post by hyg53 on 2006-01-14
BigOldCar, I think you should have made a new thread for your problem.
Offline installation has nothing to do with mike's problem...

---

### Post by mike63730 on 2006-01-14
im wanting to install turbo lister for ebay if possible and play game called delta force black hawk down ? they are both windows programs  
and while im thinking the following link is the method i used to install wine 
[http://www.winehq.org/site/download-debhttp://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-debhttp://www.winehq.org/site/download-deb)

---

### Post by BigOldCar on 2006-01-14
[QUOTE=hyg53]BigOldCar, I think you should have made a new thread for your problem.
Offline installation has nothing to do with mike's problem...[/QUOTE]

Hmmm... perhaps you're right.  But it is a Wine Installation issue.  Well, if nothing arises here I'll repost as a new thread.

S.W.

---

### Post by BigOldCar on 2006-01-14
[QUOTE=mike63730]the following link is the method i used to install wine 
[http://www.winehq.org/site/download-debhttp://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-debhttp://www.winehq.org/site/download-deb)[/QUOTE]

Perhaps you mis-typed.  Clicking that link yields only:

[FONT="Fixedsys"]404 not found 

Sorry, that document was not found. Please check your URL and try again. 

If you followed a link from a WineHQ.org page and reached this page in error, please report it to the WineHQ.org Bugzilla. [/FONT]

S.W.

---

### Post by mike63730 on 2006-01-14
this is it here were i got the other one i dont know 
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

---

### Post by hyg53 on 2006-01-14
Use this instead
[https://wiki.ubuntu.com/Wine?highlight=%28wine%29](https://wiki.ubuntu.com/Wine?highlight=%28wine%29)
I have used an other how to, with the 0.9 beta version of wine, but it's in french sorry. [http://forum.ubuntu-fr.org/viewtopic.php?id=18625](http://forum.ubuntu-fr.org/viewtopic.php?id=18625)
Maybe is there on here too, that beta version is really great.

to play games, people usually use cedega, a fork of wine
[https://wiki.ubuntu.com/Cedega?highlight=%28cedega%29](https://wiki.ubuntu.com/Cedega?highlight=%28cedega%29)

The wiki [https://wiki.ubuntu.com/](https://wiki.ubuntu.com/) provides a lot of usefull information to everybody.

Turbo lister seems to be quite hard to install, look for it on the forum, but I don't think it'll ever work

---

### Post by ed_d on 2006-01-14
Big Old Car, Netzero does have the .deb installer of juno/netzero dialer. Just get that, dpkg -i the file and you should be good. 

mike63730, just apt-get install wine, then run winecfg. when you want to install you program, just "wine <path to install>.exe and it should install, then re-run the winecfg, add the start up .exe to the list and choose the os version of windows to run it on. should be all you need.

---

### Post by BigOldCar on 2006-01-14
"dpkg -i the file"???

Could you break that down a little further for me?  I don't understand the jargon just yet (working on day three in Linux-land).

I've got the file on a disk.  Disk is in the machine.  I see it in the window manager.  But I can't make it do anything.

"Add application" doesn't see it; "expand" doesn't do it.  I got an "archive type not supported" error.

Thank you for your direction so far...

S.W.

---

### Post by hyg53 on 2006-01-14
you have to open a terminal (applications->accessories), then, you type
sudo dpkg -i name_of-the_package.deb
to install it

---

### Post by ed_d on 2006-01-14
ok, so you have the file, and its something like file.deb, right?

then just sudo dpkg -i file.deb

I use the word file as I do not know what the file name is off hand. Also, copy it to your home directory first. then in a termalnal, cd /home/yourname/
then do the dpkg -i command

---

### Post by BigOldCar on 2006-01-14
Okay, gang, so I became root user; switched to /media/cdrom0 and ran that command.  It asked for the password, prepared and then unpackaged the file.

Now what?  I can't find the application!  Did it install correctly or did I do something wrong?  Was I supposed to copy it to somewhere on the hard drive first?  If so, I should have been under swear@ubuntu rather than /cdrom0, right?  If that's correct, how does one copy the file from the disk to the hard drive?  And is there a preferred location?  Messing around on the desktop I got an icon that says it's netzero.deb, but it's got a lock icon superimposed over the top of it.

Look, I know this is all super-basic stuff here, and I'm real sorry about that, but it's all new to me.  I'm very used to a Windows environment... I guess I now know how little old ladies feel when they have to venture online for the first time to switch Medicare plans!

Thanks all for the help so far.

ALSO... care to recommend a good place for newbies to start reading up on how to get along in Linux?

S.W.

---

### Post by Arktis on 2006-01-15
If you installed it correctly, you just need to know the right command to run to start it up.  Check the documentation, or open up synaptic package manager (system > administration > synaptec package manager) and locate the section "Installed local or obsolete" and you should see the netzero package you installed.  Right-click it, select properties, and click the Installed Files tab.  Look for something listed in /bin/, /usr/bin/, or /usr/share/bin/, and that's going to be the command you need to run to start the app.  For example, it if a file is listed as something like /usr/bin/netzerodialer, then the command you need to run is netzerodialer.  Once you know the command, you can create yourself an applications menu shortcut with smeg (right click applications menu > "edit menus").

As far as newbie help, see [http://www.psychocats.net/linux/installingsoftware.php](http://www.psychocats.net/linux/installingsoftware.php) for info on installing things.  See System > Help > Ubuntu 5.10 Starter Guide for common newbie Q's and A's.

---

### Post by BigOldCar on 2006-01-16
Thank you, Arktis, and everyone else, for your excellent and precise instructions.  Alas, however, I am not able to get the damn thing going.  Activating "runclient.sh" gives the message "DM set to off," followed by a blinking cursor, then half a minute later it's back to the command line.  I don't know why... maybe java isn't installed with Ubuntu?  This is too much trouble and clearly isn't gonna work.  Thanks anyway, all.

S.W.

---

### Post by claypole on 2006-08-22
I would recommend you install Automatix first, as this has the latest Wine, Java etc and would save you a lot of time and hassle.  Also, install the Ubuntu forums Firefox extension which creates a menu on Firefox with direct links to How To's, 3rd Party projects (such as Automatix) and of course Searches (Go to <Tools><Extensions> <Get more extensions> and search for Ubuntu).

Ubuntu is a breath of fresh air after subjugating yourself to Windows for so long.  I don't hate Microsoft, I hate Windows, it should be so much better in the 21st Century.  Unfortunately Ubuntu's strengths can also be its weakness at times; stick with it and you will be rewarded.  Having another PC with Windows, dual boot or VMWare for now is no bad thing until you are comfortable.

---

