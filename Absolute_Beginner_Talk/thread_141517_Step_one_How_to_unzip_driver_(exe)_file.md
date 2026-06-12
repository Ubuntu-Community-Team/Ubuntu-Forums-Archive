---
title: "Step one: How to unzip driver (exe) file?"
date: 2006-03-08
forum: Absolute Beginner Talk
---

### Post by Papa-san on 2006-03-08
I have the downloaded file. Once they are on the desktop, what do I do to unzip it?

---

### Post by rattking on 2006-03-08
I think drivers are usually in cab format.. if so
cabextract will do it
if it really is a self extracting zip then unzip would do it

---

### Post by Klaidas on 2006-03-08
What are you installing?

---

### Post by Papa-san on 2006-03-08
need to extract the .inf files so ndiswrapper can be used to activate my wireless card

I have downloaded it, but file-roller cannot open this type of file.

---

### Post by trorion on 2006-03-08
Hi Papa!

Good plan to get a new thread going.  Sorry I thought file-roller would unzip it.
you could try typing "unzip" in a terminal window.  If that doesn't work maybe try "sudo apt-get install unzip" then typing "unzip" in a terminal window?

Can anyone confirm this (I know the files he has are a self extracting zip file).  File is r94826.exe downloaded from Dell.  He is working his way through the Broadcom HOWTO ([http://www.ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+broadcom](http://www.ubuntuforums.org/showthread.php?t=25683&highlight=HOWTO+broadcom))

Just for teaching purposes:
When you type something in a terminal window the computer tries to execute it.  In this case I wanted to try executing the program "unzip"
```
unzip
```
If that didn't work I wanted to try to find and install that program.  You have to do that as the "SuperUser" which is commonly called "root" or "/"
```
sudo apt-get install unzip
```
-sudo = run the following as root / superuser /
-apt-get = the program you want to run (called apt-get)
-install = a command that you want passed to the program "apt-get" which says 'hey, apt-get I want you to install this program'
-unzip = the program you are telling apt-get to install.

---

### Post by Papa-san on 2006-03-08
[QUOTE=trorion]Hi Papa!

Good plan to get a new thread going.  Sorry I thought file-roller would unzip it.[/QUOTE]

Either way I do it I get:

Error
File type not supported

Hey!
No prob... You have been trying pretty hard!

Thanks, and I have the other post ready for when I do get this done!

---

### Post by kaamos on 2006-03-08
Probably an overkill solution, but you could use wine to run it:
```
sudo apt-get install wine
wine thefile.exe
```

I think wine is a single package so you could get it from packages.ubuntu.com and transfer (usbstick?) to your ubuntu machine if that does not have any internet.. Again this is really a way too complex solution, and I hope someone has better ideas.

---

### Post by Papa-san on 2006-03-08
[QUOTE=kaamos]Probably an overkill solution, but you could use wine to run it:
```
sudo apt-get install wine
wine thefile.exe
```

I think wine is a single package so you could get it from packages.ubuntu.com and transfer (usbstick?) to your ubuntu machine if that does not have any internet.. Again this is really a way too complex solution, and I hope someone has better ideas.[/QUOTE]
 I actually think it a capital idea, but in two attempts to install wine, there have been fatal errors... This system has  connectivity via cat 5 so I can do it with my ubuntu system...

~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 67 not upgraded.
Need to get 12.5MB of archives.
After unpacking 48.6MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Get:1 [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.9-winehq-1 [12.5MB]
Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.9-winehq-1
  Error reading from server. Remote end closed connection
Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.9-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.9-winehq-1_i386.deb)  Error reading from server. Remote end closed connection

---

### Post by trorion on 2006-03-08
did "unzip" work?

---

### Post by Papa-san on 2006-03-08
[QUOTE=trorion]did "unzip" work?[/QUOTE]
Unzip unable to find file(s) should I be typing in more than the filename? Maybe the 'directory' ?

---

### Post by kaamos on 2006-03-08
[QUOTE=Papa-san]
Err [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ wine 0.9.9-winehq-1
  Error reading from server. Remote end closed connection
Failed to fetch [http://wine.sourceforge.net/apt/binary/wine_0.9.9-winehq-1_i386.deb](http://wine.sourceforge.net/apt/binary/wine_0.9.9-winehq-1_i386.deb)  Error reading from server. Remote end closed connection[/QUOTE]

Bad timing apparently. Wine 0.9.9 just got released a few days ago and their servers are getting so many connections that they can't handle it.. Here is an easy solution for you: paste the url for the .exe here and I'll unzip it and upload to a server.

---

### Post by meborc on 2006-03-08
[QUOTE=kaamos]Bad timing apparently. Wine 0.9.9 just got released a few days ago and their servers are getting so many connections that they can't handle it.. Here is an easy solution for you: paste the url for the .exe here and I'll unzip it and upload to a server.[/QUOTE]

i was just about to suggest that :-D good call! ... hey papa, good to see that you are still at it... i guess 2-3 months from now you will be looking back with a smile... good luck :p

---

### Post by trorion on 2006-03-08
[QUOTE=Papa-san]Unzip unable to find file(s) should I be typing in more than the filename? Maybe the 'directory' ?[/QUOTE]

Do you want me to just send the file to you on e-mail?  or paste it to a message here that you can then do ```
gedit
``` copy/paste to that and then you can save it to desktop?

For the person doing the upload to server:
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R94826&formatcnt=1&fileid=122974](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R94826&formatcnt=1&fileid=122974)

I'm not sure if it's bcmwl5.inf OR bcmwl5a.inf
Wait: it's bcmwl5.inf

---

### Post by kaamos on 2006-03-08
[QUOTE=trorion]I'm not sure if it's bcmwl5.inf OR bcmwl5a.inf
Wait: it's bcmwl5.inf[/QUOTE]

bcmwl5.inf & sys here -> [http://tinyurl.com/q892r](http://tinyurl.com/q892r)

---

### Post by rattking on 2006-03-08
[QUOTE=Papa-san]Unzip unable to find file(s) should I be typing in more than the filename? Maybe the 'directory' ?[/QUOTE]

the file name is what you want
unzip R94826.EXE
or whatever the file name is

---

### Post by mlind on 2006-03-08
btw. did you try using cabextract?

---

### Post by Papa-san on 2006-03-08
Hi peeps...
sorry, I had to get away for a bit... I kinda have a workable setup now, so I can handle a little more time at it. (We also had to teach a class in our youth group tonight)

I did try the cabextract with no luck. 
The url where I got the driver is:
[http://ftp.us.dell.com/network/R94826.EXE](http://ftp.us.dell.com/network/R94826.EXE)
(and, by the way, I tend not to quit, I REFUSE to go back to windows... I'll stop using a computer first)

---

