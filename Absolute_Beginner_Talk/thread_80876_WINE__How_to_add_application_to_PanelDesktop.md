---
title: "WINE : How to add application to Panel/Desktop"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by flub on 2005-10-23
Hi all,

Fairly new to all this but getting there slowly.

I have installed a program via WINE and this works fine. However, I would like to run this program by clicking on an ICON in my PANEL.

How would I go about added a WINE application to either the GNOME PANEL or to the Desktop ?

Any help would be much appreciated.

Cheers

---

### Post by GrootBrak on 2005-10-23
Sorry can't help you with your question, but maybe you can help me in installing programs in wine? I've never managed to get any program running or installed with wine.

---

### Post by flub on 2005-10-23
What programs are you trying to run ?
What error messages are you getting ?

Let me know a little more about what you are trying to do and I'll see if I can help you.

I've had some success in getting programs working, which has helped me move nearly 100% over to Linux.

---

### Post by JakeSpeare on 2005-10-23
hi.  me too1 :)

I want to install WordPerfect to use in ubuntu, but have no clue where to start.  Is there a how-to somewhere?  I looked for one, but so far no luck.

---

### Post by flub on 2005-10-23
I would suggest [http://www.winehq.com](http://www.winehq.com) 

There is a good FAQ and User Guide available along with an Application database which list what has been tested etc.

---

### Post by JakeSpeare on 2005-10-23
thanks!

BTW, that is a scary avater you have!  My kids are running away screaming!

---

### Post by Snakey on 2005-10-23
Use the applications menu editor to add a starter with the command to start your program (wine app.exe)

---

### Post by flub on 2005-10-24
Thanks shakey...

I tried that but no joy...

The following command works when run from the Terminal.

sudo wine "/home/andy/.wine/drive_c/Program Files/myTVinfo DigiGuide TV Guide/client.exe"

However when I add it as new entry in the menu and use the same command nothing seems to happen when I then go a select this new entry from the menu.

Any thoughts.

---

### Post by flub on 2005-10-25
Is there a LOG file or something that I can view to see why the same command in Terminal does not run from the Menu ?

---

### Post by GrootBrak on 2005-10-25
[QUOTE=flub]What programs are you trying to run ?
What error messages are you getting ?

Let me know a little more about what you are trying to do and I'll see if I can help you.

I've had some success in getting programs working, which has helped me move nearly 100% over to Linux.[/QUOTE]

My top two would be Age of Empires and Coraldraw. I have both installed on my windows partition, neither works. Its suggested to install the programs to wine. Great idea, but I have the CD, but clicking install on the CD does nothing.

---

### Post by Jengu on 2005-10-25
You want to create a new menu item (not sure how to do this in gnome, I use kubuntu). It'll ask you what command the menu item should correspond to, and you'll put "wine path/to/my/application/whatever.exe"

As for installing word perfect -- why? Unless there is a feature in it you specifically need, try openoffice and spare yourself the trouble.

Wine is still alpha software. Lots of stuff doesn't work. Although what it can do is pretty amazing considering it's a small band of hackers reverse engineering a multibillion dollar corporation's work.

---

### Post by jwalch on 2005-10-25
I suspected that Linux does not like the MS syntax for naming folders, ie "Program Files" for ex., with the space. So I put my MS appöication directly under "drive_c" and could launch the wine <application> from the panel.

---

### Post by webbie180 on 2005-10-26
How to remove wine completely including all configurations in the home directory?  Have to reinstall wine as I messed up something.

---

### Post by JakeSpeare on 2005-10-26
> As for installing word perfect -- why? 

Because I know it intimately.  I have been using it since 1986 and I love it.  Word sucks.  I tried openoffice and it appears to want to emulate word.  I can't stand it when a wordprocessor starts doing stuff for you.  Drives me insane.  I want control over my application.

:)

---

### Post by KLineD on 2005-10-31
[QUOTE=flub]Thanks shakey...

I tried that but no joy...

The following command works when run from the Terminal.

sudo wine "/home/andy/.wine/drive_c/Program Files/myTVinfo DigiGuide TV Guide/client.exe"

However when I add it as new entry in the menu and use the same command nothing seems to happen when I then go a select this new entry from the menu.

Any thoughts.[/QUOTE]

The problem is the space between Program Files, in linux you would have to do it like 'Program\ Files' so the string would be:

sudo wine "/home/andy/.wine/drive_c/Program\ Files/myTVinfo\ DigiGuide\ TV\ Guide/client.exe"

there you go :D

---

### Post by flub on 2005-11-06
Thank you VERY much :)

---

### Post by majikstreet on 2005-11-06
to anybody: if you have to sudo and you aren't in a terminal, you can use "gnome-sudo program" replacing program with the program..

just thought I may be able to help :)

---

