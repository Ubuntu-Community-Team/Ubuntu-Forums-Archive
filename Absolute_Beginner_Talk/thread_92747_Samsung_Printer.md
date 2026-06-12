---
title: "Samsung Printer"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by deNoobius on 2005-11-20
**THIS ISSUE IS SOLVED**.  SEE TOWARD END OF THREAD--EDITS TO CUPSD.CONF FILE.


The issue now is printing.  The printer (Samsung CLP 510N) simply will not install in Ubuntu via a direct USB connection, or a network connection via CUPs.  The Samsung-provided software does not work on Ubuntu, although it works fine in Windows.  My latest attempt (you can read my others elsewhere) was to use some Windows software Samsung provided to set an IP address for the printer.  The only effect that had, other than adding a little icon (in Windows, I mean) for the printer, was to crash my entire home network and Internet connection.  I tried to set up a printer and use CUPS anyway, but of course it didn't work (I have the network back).

Is there any other technique I may have overlooked?  Thanks,

---

### Post by timczer on 2005-11-20
Have you tried the samsun web site.  They have linux software for download for many of their printers.  On my first linux install I had to use the software off their web site to get my printer working.

---

### Post by aysiu on 2005-11-20
[Here](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=US&CttFileID=264040&CDCttType=DR&ModelType=C&ModelName=CLP-510N/XAA&VPath=DR%2f200503%2f20050322102424156_lpp-1.1.4-19-i386.tar.gz[/url) is the Linux driver from the Samsung website. Download it to your Desktop and extract the file (double-click and click on "Extract"). Then click on setup.sh.

Apart from that I don't know. There's a Readme file in that .tar.gz. You can read that. You may have to run setup.sh as sudo ```
sudo setup.sh
```. Play around a bit.

---

### Post by deNoobius on 2005-11-20
Yes, I managed to install the Linux drivers that Samsung provided for printers in this family.  I tried the drivers for the 510, the 500, and the 550 (CLP series), as well as the driver for a xerox printer that is supposed to be compatible.  It wasn't easy, because they are made to be installed by the root user only, but I managed.  I also followed the advice on a web site devoted to Linux printing to extract two particular files and set up an alias and write a particular config file.  Nothing doing.  These drivers are not advertised to work in Ubuntu and as far as I can tell, they do not.  The printer does not recognize postscript or other common printing protocols, which may be why I was able to get a color laser at a rock-bottom price! Little did I know.

Network printing over CUPS also failed, and, believe me, I've tried everything, although did manage to (temporarily) crash my entire home network. All I can do now is reboot in Windows when I want to print, and what I really wanted to do was make this computer a 99% Linux box.  It's an old machine, just sitting in a corner and serving the printer, and having to get back there for all the Windows security patches, virus updates, etc., is just annoying and I was hoping to get something stable going where I could leave it alone for weeks at a time.  

The only other thing that occurs to me, but I don't know much, would be using the Windows drivers in some kind of emulation mode, which I'd be willing to do if I thought it might work.  Any advice on going that route?  Has anyone ever had any success running any sorts of proprietary Windows drivers that way?

---

### Post by maxper on 2005-11-30
[QUOTE=aysiu][Here](http://org.downloadcenter.samsung.com/downloadfile/ContentsFile.aspx?CDSite=US&CttFileID=264040&CDCttType=DR&ModelType=C&ModelName=CLP-510N/XAA&VPath=DR%2f200503%2f20050322102424156_lpp-1.1.4-19-i386.tar.gz[/url) is the Linux driver from the Samsung website. Download it to your Desktop and extract the file (double-click and click on "Extract"). Then click on setup.sh.

Apart from that I don't know. There's a Readme file in that .tar.gz. You can read that. You may have to run setup.sh as sudo ```
sudo setup.sh
```. Play around a bit.[/QUOTE]

i followed your advice but it did not work (my printer is CLP-500) extracting the archive results in the image directory (i put it on my desktop) and double clicking on setup.sh nothing happens... maybe i made somthin wrong?:confused:

---

### Post by crispingatiesa on 2005-11-30
[QUOTE=maxper]i followed your advice but it did not work (my printer is CLP-500) extracting the archive results in the image directory (i put it on my desktop) and double clicking on setup.sh nothing happens... maybe i made somthin wrong?:confused:[/QUOTE]


The command is actually: sudo sh <applicationname> in your case: sudo sh setup.sh

good luck

---

### Post by deNoobius on 2005-11-30
Well, I got the setup software installed.  However, when I try to add the printer, it asks for the adminstrator login and password.  No matter what I do--login as me, login as root--I get a "could not authenticate" message and can go no further.  So, I still can't print.

The printer is the Samsung CLP-510N.

---

### Post by briguy on 2005-12-01
There are a few refs here, doesn't look good overall: [http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-CLP-500]("http://www.linuxprinting.org/show_printer.cgi?recnum=Samsung-CLP-500")
:???:

---

### Post by deNoobius on 2005-12-01
No, nothing seems to work.  Now I'm following the instructions for printing via a WinXP printer by adding a Unix printer share on the XP computer, but that doesn't work either--which is odd, because I can print from that computer.  It would be a work-around, but acceptable, but it doesn't work.

 The really funny thing is, if I send a test page from Ubuntu, and leave it in the queue, and reboot into windows, the printer will sometimes print it then.  It seems the print jobs are going to the printer, but it just refuses to print if Ubuntu is involved.

---

### Post by sean on 2005-12-03
cd  /etc/cups
sudo cp cupsd.conf cupsd.conf.orig

vi cupsd.conf

You'll want to edit the <Location> section at end of file as follows:

Insert #
#AuthType Basic
#AuthClass System

Add this text
AuthType None
AuthClass Anonymous
AuthGroupName lp

Save and exit your editor of choice.

sudo /etc/init.d/cupsys restart

linux-config
...add printer

Done.



[QUOTE=deNoobius]No, nothing seems to work.  Now I'm following the instructions for printing via a WinXP printer by adding a Unix printer share on the XP computer, but that doesn't work either--which is odd, because I can print from that computer.  It would be a work-around, but acceptable, but it doesn't work.

 The really funny thing is, if I send a test page from Ubuntu, and leave it in the queue, and reboot into windows, the printer will sometimes print it then.  It seems the print jobs are going to the printer, but it just refuses to print if Ubuntu is involved.[/QUOTE]

---

### Post by deNoobius on 2005-12-04
Sean, thanks!  Those edits to the cupsd.conf did get me past the login issue with the printer setup and did get it printing.

---

### Post by sean on 2005-12-04
Glad I could help.

Sean

[QUOTE=deNoobius]Sean, thanks!  Those edits to the cupsd.conf did get me past the login issue with the printer setup and did get it printing.[/QUOTE]

---

### Post by mxsteini on 2006-01-11
After playing around for some hour, I figured out the following procedure.
Well so, simple.
download the newest driver from samsung (link above):
extract the file
sudo image/setup.sh
click what you want.
After that samsung asks you to start linux-config - do that.
Click to add printer
And than: _Give your own userid and password_ (Hey, I don't know why. An amazing cups-thing) :p 
Than select clp510 as you like and finish.

Yeah, that's all
Bye Michael

---

### Post by deNoobius on 2006-01-11
[QUOTE=mxsteini]After playing around for some hour, I figured out the following procedure.
Well so, simple.
download the newest driver from samsung (link above):
extract the file
sudo image/setup.sh
click what you want.
After that samsung asks you to start linux-config - do that.
Click to add printer
And than: _Give your own userid and password_ (Hey, I don't know why. An amazing cups-thing) :p 
Than select clp510 as you like and finish.

Yeah, that's all
Bye Michael[/QUOTE]

Michael, this is a blast from the past!  Thanks.  Right now, I have my printer working based on the other solution, so I'm not tempted to mess with it, but I'll save this in case I need to reinstall.

When I tried this before, neither my regular user and password nor a root user and password worked, but, on the other hand, I was VERY new to Linux then and I might have made some other mistake that caused that problem.

---

### Post by Copter on 2006-01-12
[QUOTE=sean]cd  /etc/cups
sudo cp cupsd.conf cupsd.conf.orig

vi cupsd.conf

You'll want to edit the <Location> section at end of file as follows:

Insert #
#AuthType Basic
#AuthClass System

Add this text
AuthType None
AuthClass Anonymous
AuthGroupName lp

Save and exit your editor of choice.

sudo /etc/init.d/cupsys restart

linux-config
...add printer

Done.[/QUOTE]

i had the same problem with xerox phaser 3122. your trick worked here also !! thanks a lot !

copter :]

---

### Post by n0fx on 2006-04-17
[QUOTE=sean]cd  /etc/cups
sudo cp cupsd.conf cupsd.conf.orig

vi cupsd.conf

You'll want to edit the <Location> section at end of file as follows:

Insert #
#AuthType Basic
#AuthClass System

Add this text
AuthType None
AuthClass Anonymous
AuthGroupName lp

Save and exit your editor of choice.

sudo /etc/init.d/cupsys restart

linux-config
...add printer

Done.[/QUOTE]

Sean,

I tried doing this with my phaser 6100DN, which is exactly the same as the Samsung CPD-500 printer but when I run linux-config as an ordinary user, I don't get the option to add the printer.  When I run sudo linux-config to add the printer, it asks for authentication and it doesn't seem to work. Is there something I'm missing here? I copy and pasted the exact changes to the /etc/cups/cupsd.conf file.

EDIT: Nevermind, I figured this out but I used a different way to get this printer working.

---

### Post by mxsteini on 2006-06-29
Hi there,
hope I can give a little help for that printer.
I wrote an artikel at:
[http://www.linuxprinting.org/forums.cgi?group=linuxprinting.samsung.general;article=1416](http://www.linuxprinting.org/forums.cgi?group=linuxprinting.samsung.general;article=1416)
where you can find my patches ppd-file and my printers.conf.
All you need is to copy the samsung-filter-files on the right postition.

But beware: 
The printer only make 600dpi
only colorprinting
sometimes black rectangles instead of graphics

Michael

---

### Post by Tulip on 2006-06-30
deNoobius - I wonder if you might be able to post your cupsd.conf file please? Im really struggling with this and I think I have stuffed up the editing of the file.  

I was able to install the software using sudo sh setup.sh. I was having trouble with authentication but I was not sure where to add the changes and my attempt didn't work. The linux-config command then didnt seem to do anything, and if I now try to run sudo sh setup.sh at the end of the install process, terminal reports  LPP_Init() failed! Waiting 2 seconds...

I'd really appreciate some help with this please, Im out of my depth!

---

### Post by drtvasudevan on 2006-06-30
what is the real problem with system> admin >printers and add printer anyway?
there is no need for any authentication etc.
what model?

tv

---

### Post by Tulip on 2006-07-01
This was my original post, but I didnt get much of a response unfortunately.

[http://www.ubuntuforums.org/showthread.php?t=203739](http://www.ubuntuforums.org/showthread.php?t=203739)

I found this post and it addresses a similar problem but with a different printer - mines a Samsung 6060. I was able to progress to actually getting the installation page to display, but Ive edited my cups file and screwed it up.

---

### Post by drtvasudevan on 2006-07-01
system> admin >printers and add printer 
remove any printer that you have installed by remove printer dialogue.
then do a fresh installation.
while in the second part of dialogue it will suggest a driver once you have given the model.
note it.
go to linux printing org and search for the driver.
get a ppd made and install that from add printer wizard.

tv

---

### Post by Tulip on 2006-07-02
The add printer function in Ubuntu does not automatically detect the Samsung 6060 and does not recommend a driver. The 6060 is not listed at linuxprinting.org. Samsung DOES provide a driver installation package from their website that includes a driver for this printer. The driver installation package appears to be an all-in-one for all of their printers, and it appears to be the same package being discussed in this thread. The problems being described and answered in this thread are the same as what I have experienced, albeit with a different model printer. I believe I could have installed the printer if I had correctly edited my cups file, but I found the instructions a little vague, made a guess, and guessed wrong. Now when I run the driver installation package I get the error message mentioned above.

---

### Post by drtvasudevan on 2006-07-03
ok
this seems to be a discontinued printer.
am downloading the driver and will hv a look and post later.

tv

---

### Post by drtvasudevan on 2006-07-03
since ther are no other solutions try this method.
it is somewhat similar to what i did for mine.

you have the ppd files for the printer downloaded.
open the add printer dialogue from system>admin>printing
the connected printer should be detected (it worries me that you say it is not. make sure the power for the printer is on and check the connection.)
select some samsung printer like 6040 in stead 6060 which is not listed.
ther may be a suggestion or not aboiut driver.
but click on install ppd and point to the ppd that has been downloaded.
it takes some time for the installed printer to show on the list.
exit wizard.

then open a doc and click print.
various options are shown.
click on the printer that you installed.
if that does not work select a generic ps printer option from the print dialogue.
if that too does not work, i am sorry, i am out of ideas.
best of luck

tv

---

### Post by Tulip on 2006-07-05
No luck unfortunately. Im going to try reinstalling ubuntu to get this installer working again, and have another go at editing this cups file.

---

