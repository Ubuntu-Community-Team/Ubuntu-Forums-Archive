---
title: "where to start?"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by DmitriK on 2006-06-24
This is my first time actually getting linux to work.  I've tried multiple distributions and no luck.  Well here I am.

Here's things I've done so far, installed the kubuntu with 'dmitrik' account, activated my MS BT mouse with info I've found on one of the threads and tried to update bluez-util file so I don't have to pair with the mouse every time I boot.  However, here comes the question.  Being such a beginner, I don't even know how to save the file.  Everytime I click save it says "...not pissible to write... check persmissions".  I read up about it and as I understand, I need to make myself a super user (sort of like the root account) or log in as root.  Before using root I need to activate it using 'sudo paswd root', which I did. The question is how can I convert my account that was created as default upon kubuntu install to root-type powers?  Basically I can't do anything with this account.  Is there a command I can type in the console to give me those powers temporarily or do I need to convert the account permanently?  I mean, I would really hate to re-login as root everytime I needed to save a file.  I must be doing something wrong.  In the beginner guide for accounts I read that 'sudo -s -H' logs me in as root, but I did that, clicked Save again and I get the same message.

Second question, i tried to play an MP3.  It's about 60 minutes but the file 'played' fro maybe 5 seconds and no sound.  It looked almost like it scans the file and doesn't actually play it.  If this of any help, the file is located on an NTFS partition which was mounted using Create New -> Link to device on the Desktop.  The sound does work tho, everytime I get that permission message after clicking Save, I hear the warning tone.

Thank you for all your help and understanding that I have no idea about linux what so ever.  Thank you.

---

### Post by CarpKing on 2006-06-24
[QUOTE=DmitriK]Everytime I click save it says "...not pissible to write... check persmissions"...

Second question, i tried to play an MP3.  It's about 60 minutes but the file 'played' fro maybe 5 seconds and no sound.  [/QUOTE]

First of all, welcome to the community!  I'm not sure if I can help you with the first problem, but where are you trying to save to?  Without using root or sudo, you should be able to save to your home folder.  

You can't play mp3's out of the box because the format is patented, and Ubuntu strives to avoid any "non-free" code.  You can, however, install what you need in order to play such restricted formats.  See [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by hajk on 2006-06-24
Hey, you made it to the forums, from there you can get to the Official Wiki (look at the top of the first forum page) for further hints on using Ubuntu.

A few comments though: it is not a good idea to run things directly as root user, in fact doing that has been disabled in Ubuntu as a matter of policy. It is possible to undo that, and there are forum messages that you can search for that explain how, but I don't recommend it. What you can do, however, is run isolated programmes with root priviledges by (1) prefixing commands in a terminal by sudo; or (2) use gksudo. Both will ask for your user password.   

Doing everything by clicking on a file name is a decidedly Windowsy thing to do. You might as well get used to the Unix/Linux way of editing files via the command line.
For example, changing the /etc/apt/sources.list: do this in a terminal with the command "sudo nano /etc/apt/sources.list", which will save the file once you're done with it. (Once you become more experienced with the Unix/Linux way, you might even try to use the "vi" (ViM) editor.)

---

### Post by DmitriK on 2006-06-24
Thanks for replies guys.  I got the MP3s to work, downloaded an XMMS player, seems to work just perfect now.

I am trying to save the file to /etc/default/.  I did get it to work by using "sudo kate" and in the program opening the file and saving it.  However just clicking on the file won't allow me to save it once it is opened.  Is there a shortcut for "sudo"-open of any file I click?  Like Shift+click opens the file in "sudo" mode? I would really be upset if I opened a file, edited it and can't save now because I forgot to open the program or the file using sudo.

It appears to me more and more that the console is the most used program in linux.  Does anyone know how to attach the console to the top of the screen and by pressing a button it'll slide down?  Sort of like quake 3 does.  I think i've seen that before.  Is it a function of the Konsole or I need to install a different package to replace my konsole program?

Last two questions.  What is a difference between shell and root shell?  Which terminal should I use?  Also every maybe 2 minutes I get a flash on the screen stating LCD panel off and than again LCD panel on, yet I didn't do anything.  Anyone has any idea what is going on?  My screen doesn't turn off or anything, just that message comes on and goes off.  It's more like a notification screen, there's nothing I can press and it only stays on the screen for a split second.

Thank you again for all your help.

---

### Post by muxecoid on 2006-06-24
I guess that you must ask person who persuaded you to use linux and he must help you. :)

Also you can  sudo chmod file you want to edit and edit if from your primary login (not secure)

---

### Post by Z13 on 2006-06-24
Well, about your first question, DmtriK: just like others told you, you can save files in your home directory or if you want somewhere else, you have to use the sudo or root permission. BUT, you must understand that if you kept a windows/mac partition and you wanna modify/save files there... you just CAN'T. Ubuntu displays that partitions for read-only. Maybe this is the cause for Ubuntu not allowing you to save files.
Tell me if this was the problem.

---

### Post by steve.horsley on 2006-06-24
[QUOTE=DmitriK]Thanks for replies guys.  I got the MP3s to work, downloaded an XMMS player, seems to work just perfect now.

I am trying to save the file to /etc/default/.  I did get it to work by using "sudo kate" and in the program opening the file and saving it.  However just clicking on the file won't allow me to save it once it is opened.  Is there a shortcut for "sudo"-open of any file I click?  Like Shift+click opens the file in "sudo" mode? I would really be upset if I opened a file, edited it and can't save now because I forgot to open the program or the file using sudo.[/QUOTE]
You just get used to remembering to do it right.
> 

It appears to me more and more that the console is the most used program in linux.  Does anyone know how to attach the console to the top of the screen and by pressing a button it'll slide down?  Sort of like quake 3 does.  I think i've seen that before.  Is it a function of the Konsole or I need to install a different package to replace my konsole program?
In Gnome you can just drag the terminal icon from the menu to the taskbar. I don't know about KDE.
> 
Last two questions.  What is a difference between shell and root shell?  Which terminal should I use?  Also every maybe 2 minutes I get a flash on the screen stating LCD panel off and than again LCD panel on, yet I didn't do anything.  Anyone has any idea what is going on?  My screen doesn't turn off or anything, just that message comes on and goes off.  It's more like a notification screen, there's nothing I can press and it only stays on the screen for a split second.

Thank you again for all your help.
Root shell is one with root privilege. Use this only when working outside of your home directory.

---

### Post by DmitriK on 2006-06-24
Hi, 

Z13: the file I modified was in /etc/default/ directory.  It's not on the partition.
muxecoid: nobody really persuaded me into using linux.  I just decided to give it a try myself.  I've seen a couple of my acquaintances with linux systems, but that they are, acquaintances, I don't really talk to them on regular bases.

I use KDE, I don't actually even know the difference between the GNOME and KDE.  I read some articles about it but they are all giving me history and stuff or total sci-fi novel like here [http://www.illusionary.com/GNOMEvKDE.html]("http://www.illusionary.com/GNOMEvKDE.html")
which is quite amuzing to read, yet gives no useful info.

There's still a problem with LCD.  Anyone has any idea why it keeps on flashing me with "LCD on/off" message?  I have Asus z70 with ATI x700 if that helps.  

Last question, does KDE have "Device Manager" where I can see all the hardware devices and general info about my computer?  I can't even find out which video drivers I'm using since I don't know where to find it and so far unsuccessful with any help I could find online. 

Thanks.

---

### Post by Z13 on 2006-06-25
DmtriK,

For more information regarding linux systems just visit wikipedia. You see, the KDE is a MSWindows-like desktop environment and GNOME is a revolutionary environment which is specific to Linux (it is the default DE for both Debian Ubuntu and Red Hat Fedora). In my opinion, KDE makes you feel that you are still using a MS Windows system and that is probably the cause you expect linux to act like Windows. Please visit wikipedia's [KDE page]("http://en.wikipedia.org/wiki/KDE") and [GNOME page]("http://en.wikipedia.org/wiki/GNOME") and [Ubuntu Dapper guide page]("http://ubuntuguide.org/wiki/Ubuntu_dapper").

Don't understand why you do have to change a file in etc/default but if you want to do so it is quite simple: log in as root. Then leave the root account after you've done what you wanted to.

---

### Post by 3rdalbum on 2006-06-25
If you want to edit a file that requires root privileges:

```

sudo nano /etc/default/ (whatever the path is)

```

Press Control-O to save, and Control-X to exit.

---

### Post by DmitriK on 2006-06-26
Thanks guys, all seems to work now.

Z13: etc/default/... has the blue tooth config file.  I wanted to edit it so the bluetooth mouse i have would be connected autmatically (which works also by the way).  I do not want to reconnect my bluetooth mouse everytime I start kubuntu.

Thanks again.

---

