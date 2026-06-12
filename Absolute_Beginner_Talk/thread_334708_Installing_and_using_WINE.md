---
title: "Installing and using WINE"
date: 2007-01-09
forum: Absolute Beginner Talk
---

### Post by konungursvia on 2007-01-09
It may sound like a silly question, but I installed WINE using aptitude and it seemed to go through a normal looking install, but I notice no difference to my Dapper environment, no ability to browse my ntfs drive, no "launch wine" or such in my start menu trees, no ability to change session to wine at the graphical login. Am I missing something?

---

### Post by meng on 2007-01-09
You launch it from the command line:
wine <name of executable>

wine runs in your session, it is not a separate environment like GNOME/KDE.

---

### Post by konungursvia on 2007-01-09
> **meng said:**
> You launch it from the command line:
wine <name of executable>

wine runs in your session, it is not a separate environment like GNOME/KDE.

So I so something like:

wine c:\windows\program files\ws_ftp\ws_ftp.exe ?

Which executables are available in other words?

---

### Post by gosh on 2007-01-09
First run winecfg to configure your drives etc.
When you install a windows app like:

wine install_application_name.exe

it will be installed in /home/username/.wine/drive_c/Program Files/application_name/application_name.exe

To run it:

wine /home/username/.wine/drive_c/Program Files/application_name/application_name.exe

---

### Post by konungursvia on 2007-01-09
> **gosh said:**
> First run winecfg to configure your drives etc.
When you install a windows app like:

wine install_application_name.exe

it will be installed in /home/username/.wine/drive_c/Program Files/application_name/application_name.exe

To run it:

wine /home/username/.wine/drive_c/Program Files/application_name/application_name.exe

Wow, thanks very much, guys! This is the best online community.

---

### Post by meng on 2007-01-09
> **konungursvia said:**
> wine c:\windows\program files\ws_ftp\ws_ftp.exe ?
This is Linux, there is no c:\ anymore. I wouldn't advise you to execute files off your Windows partitions. Furthermore, I wouldn't advise you to use a Windows ftp client when you could use a Linux ftp client. Also, wine is not a perfect substitute for Windows!

So, perhaps you should back up a couple of steps and let us know what you want to use wine for.

---

### Post by bodhi.zazen on 2007-01-09
You can also look at this:

[How to wine](http://doc.gwos.org/index.php/HowToWine)

---

### Post by konungursvia on 2007-01-09
> **meng said:**
> This is Linux, there is no c:\ anymore. I wouldn't advise you to execute files off your Windows partitions. Furthermore, I wouldn't advise you to use a Windows ftp client when you could use a Linux ftp client. Also, wine is not a perfect substitute for Windows!

So, perhaps you should back up a couple of steps and let us know what you want to use wine for.

Thanks. Actually I only typed in ws_ftp as an example. I in fact no longer use it as my server requires secure connections and I use this other ftp with a strange name I forget what it is now. I just want to have wine to use World of Warcraft, CivIV and stuff like that, as well as my ftp client.

---

### Post by meng on 2007-01-09
Getting WoW to run on wine is a little tricky, but others have managed it, you should search the forums for a howto on that subject.
According to the application database for wine ([www.winehq.com](www.winehq.com), look for AppDB), Civ IV doesn't play nice with wine. I'm fairly sure Cedega has it running, but you have to pay for Cedega.
If you want to play several Windows games, then I advise you keep a Windows machine or at least a Windows partition on a dual-boot system.
You sure we can't convince you to use a Linux ftp client? You're generally better off running native Linux applications than Windows ones, unless there's no native equivalent.

---

### Post by konungursvia on 2007-01-09
> **meng said:**
> 
If you want to play several Windows games, then I advise you keep a Windows machine or at least a Windows partition on a dual-boot system.
You sure we can't convince you to use a Linux ftp client? You're generally better off running native Linux applications than Windows ones, unless there's no native equivalent.

Thanks for the gaming advice and info, I'll keep a Windoze partition dual bootable. I tried the Firefox extension ftp from Synaptic, but couldn't get it to connect to my ftp server at the University of Toronto. Is there a good client with the latest security from a safe repository?

---

### Post by sn0m on 2007-01-09
Hi, i'm trying to configur it using sudo winecfg, it opens  in a window, which is green and the wine windows inside. I checked for drives and didn't have one, so added them using autodetect. Anyway, when it comes to validate it, the windows is to small to show apply changes. I can drag it down but not up to show the clickabale option at the bottom of the window.
Any help how to overcome this.
thanks

---

### Post by konungursvia on 2007-01-09
Well I ran winecfg, but it seems there are no installed win programs. Does this mean I can't run things from the ntfs partition? Many thanks for all the great help.

---

### Post by MindRiot on 2007-01-11
If you _did not_ install the program with WINE,

You _cannot_ run the program with WINE.

In other words;

To _run_ the program with WINE,

You must _install_ the program with WINE

---

### Post by bernardfrancois on 2007-01-13
Not necessarily, I do have some programs running under wine which I didn't install using wine.

---

### Post by Drillbit on 2007-02-04
can someone please help me?

I've just install a progam at paul@paul-desktop:~$ wine /home/paul/Desktop/Setup.exe
using WIne.

Where did it install to? I have read many, many HOWTO's over the last few days but can't seem to figure this one out.

Thanking you in advance.

---

### Post by Drillbit on 2007-02-04
Sorry to ask again but I'm about to leave work and I need this software at home.

Can anyone help me?

---

### Post by bodhi.zazen on 2007-02-04
See the link I gave above for a detailed overview of wine.

Top answer your question, you installed to the "fake c drive" in your home directory.

It is hidden, ie it starts with a .

.wine

To see it: Open nautilus (Places -> home)

view -> Show hidden files

Or in a terminal:

ls -a ~ 

( ~ is shorthand for /home/user_name )

Your program is likely in **~/.wine/c/Program Files** or a sub directory

---

### Post by closetpirate on 2007-02-05
KftpGrabber might be something you would be interested in.

---

### Post by tjtansey on 2007-02-11
Quick question, how do you uninstall applications that are running with wine?

---

### Post by uboat on 2007-02-11
There is always codeweavers cross over office whic I use to run msoffice2k3, I lnow the xover office supports WoW. How ever you might run into some bumps with Civi IV due to the fact that no onw has tested it with Cross over Office.

another graet linux user community is linuxquestions.org which is most say is a great resource for linux users of all skill levels.

[lq ubuntu forum  ]("http://www.linuxquestions.org/questions/forumdisplay.php?f=63")

---

