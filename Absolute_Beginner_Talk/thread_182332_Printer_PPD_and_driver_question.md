---
title: "Printer PPD and driver question"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by Ken Burgard on 2006-05-25
Installed ubunto 5.10 and am having trouble with printer setup.  HP 722c doesnt do anything but Gnome thinks it is printing a test page, so it seems.  Is a PPD a driver or do I need both?  Printer setup box "Location" space is blank so does it know where the printer is? (I don't really know where it is for that matter)  Sys does auto detect the printer fine.

---

### Post by khightower on 2006-05-25
How did you install the printer. I did a quick look under the printer setup and it seems the drivers are built-in (Drapper 6.06). You should be able to use this driver.

The location is the for Network Info and Desc.

---

### Post by Ken Burgard on 2006-05-25
Thank you for the reply,  I did install through the wizard like device and found my printer to specify.  Dialog box then asked ME for the PPD file location so I set about researching what a ppd file was and downloaded one from the linuxprinting website the told the dialog box it was there on my desktop.

---

### Post by linear on 2006-05-26
Hmm. Not sure, but I think cups normally wants the ppd file in a specific folder.
 
A look at the log file (in /var/log/cups, I think) might be enlightening.

---

### Post by steve.horsley on 2006-05-26
[QUOTE=Ken Burgard]Thank you for the reply,  I did install through the wizard like device and found my printer to specify.  Dialog box then asked ME for the PPD file location so I set about researching what a ppd file was and downloaded one from the linuxprinting website the told the dialog box it was there on my desktop.[/QUOTE]

See my response in this thread - may be your problem.
[http://www.ubuntuforums.org/showthread.php?p=1056500](http://www.ubuntuforums.org/showthread.php?p=1056500)

---

### Post by Ken Burgard on 2006-05-27
[QUOTE=steve.horsley]See my response in this thread - may be your problem.
[http://www.ubuntuforums.org/showthread.php?p=1056500](http://www.ubuntuforums.org/showthread.php?p=1056500)[/QUOTE]

I see, the driver was there already.  "Install Driver" is for when one wants to try a different driver than the one suggested.  I found the one I downloaded was the same as the suggested driver but printer still won't print

---

### Post by linear on 2006-05-27
You really need to take a look at /var/log/cups/error_log (after you attempt to print). Look for lines that start with "E".

---

### Post by Ken Burgard on 2006-05-30
[QUOTE=linear]You really need to take a look at /var/log/cups/error_log (after you attempt to print). Look for lines that start with "E".[/QUOTE]


Where do I enter this command?  When logged in TERMINAL at the $, this command results in "Access Denied".  What am I doing wrong?

---

### Post by linear on 2006-05-30
[quote=Ken Burgard]Where do I enter this command? When logged in TERMINAL at the $, this command results in "Access Denied". What am I doing wrong?[/quote]
That's not a command, it's a file. You should be able to open it in any text editor.
 
If there's nothing obvious, it might be helpful to enable a higher degree of logging (but this will make the log file much bigger).
 
If you decide to do this:
 
Edit the cups configuration file:
**sudo nano /etc/cups/cupsd.conf**
Find the line that reads **LogLevel info**. Change **info** to **debug** and save the file.
Restart cups:
**sudo /etc/init.d/cupsys restart**
Try to print, and then examine the log file again.

---

### Post by Ken Burgard on 2006-05-31
[QUOTE=linear]That's not a command, it's a file. You should be able to open it in any text editor.
 
If there's nothing obvious, it might be helpful to enable a higher degree of logging (but this will make the log file much bigger).
 
If you decide to do this:
 
Edit the cups configuration file:
**sudo nano /etc/cups/cupsd.conf**
Find the line that reads **LogLevel info**. Change **info** to **debug** and save the file.
Restart cups:
**sudo /etc/init.d/cupsys restart**
Try to print, and then examine the log file again.[/QUOTE]


Linear,

Thank you so much, you seem to posses the knowledge to help cure my ill.  However, I still do no understand how to use this knowledge you have graciously imparted to me.  I opened the "Text Editor" that is included with Ubuntu but do not see how to access the file  /var/log/cups/error_log.  I understand additional efforts may be required as shown in your last post but surely need to understand this first.  In this Text Editor, under "Open File", it appears I must go choose a file.  How would I simply enter the file name?

Sorry to be so uneducated but I'm trying.  This whole process with Linux is most intruiging, but, so far, I'm sooo stuck on monitor and printing issues that I cannot truly explore what all is possible.  What is possible simply is irrelevent if one cannot see IT on a monitor or print IT to paper.

What have I become!

---

### Post by Ken Burgard on 2006-06-03
[QUOTE=linear]That's not a command, it's a file. You should be able to open it in any text editor.
 
If there's nothing obvious, it might be helpful to enable a higher degree of logging (but this will make the log file much bigger).
 
If you decide to do this:
 
Edit the cups configuration file:
**sudo nano /etc/cups/cupsd.conf**
Find the line that reads **LogLevel info**. Change **info** to **debug** and save the file.
Restart cups:
**sudo /etc/init.d/cupsys restart**
Try to print, and then examine the log file again.[/QUOTE]


I found these error messaged playing in Terminal:

(gedit:7672): GnomePrint-WARNING **: Problem while creating filter from 'frgba':  filter 'frgba' is unknown

(gedit:7672): GnomePrintCupsPlugin-WARNING **: iconv does not support ppd charac ter encoding: ISOLatin1, trying CSISOLatin1

Does this help to underdand my problem?

---

### Post by linear on 2006-06-03
[quote=Ken Burgard]I found these error messaged playing in Terminal:

(gedit:7672): GnomePrint-WARNING **: Problem while creating filter from 'frgba':  filter 'frgba' is unknown

(gedit:7672): GnomePrintCupsPlugin-WARNING **: iconv does not support ppd charac ter encoding: ISOLatin1, trying CSISOLatin1

Does this help to underdand my problem?[/quote] Unfortunately, no. Were you trying to print from gedit (a/k/a Text Editor) at that point? A google search turns up a couple of references to that error message, but no explanation or fix.

To get to the error log:[LIST=1]
[*]Launch Text Editor (**Applications > Accessories > Text Editor**).
[*]**File > Open...**
[*]In the left pane of the dialog, double-click on **File System**.
[*]In the right pane, scroll down a little and double-click on **var**, then on **log**, then on **cups**.
[*]Double-click **error_log**.
[*]Now look through that for lines that start with "E".[/LIST]With luck, some obvious error will turn up.

---

### Post by Ken Burgard on 2006-06-04
[QUOTE=linear]Unfortunately, no. Were you trying to print from gedit (a/k/a Text Editor) at that point? A google search turns up a couple of references to that error message, but no explanation or fix.

To get to the error log:[LIST=1]
[*]Launch Text Editor (**Applications > Accessories > Text Editor**).
[*]**File > Open...**
[*]In the left pane of the dialog, double-click on **File System**.
[*]In the right pane, scroll down a little and double-click on **var**, then on **log**, then on **cups**.
[*]Double-click **error_log**.
[*]Now look through that for lines that start with "E".[/LIST]With luck, some obvious error will turn up.[/QUOTE]

Thank you for the directions.  Here are the two "E" lines from the log.  

E [04/Jun/2006:07:06:18 -0700] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory

E [04/Jun/2006:07:11:51 -0700] PID 7671 stopped with status 3!

---

### Post by linear on 2006-06-04
[quote=Ken Burgard]Thank you for the directions.  Here are the two "E" lines from the log.  

E [04/Jun/2006:07:06:18 -0700] LoadAllClasses: Unable to open /etc/cups/classes.conf - No such file or directory

E [04/Jun/2006:07:11:51 -0700] PID 7671 stopped with status 3![/quote] Ok, now we're getting somewhere. You can ignore the first error; it turns up in my error log as well but doesn't cause any problems. The second error is the one to focus on.

Set the loglevel to debug in cupsd.conf, and restart cups as detailed in an earlier post. With luck, the actual error will turn up in the series of debug messages (lines that start with "D").

(If you prefer using Text Editor over nano, start from a Terminal window and enter **gksudo gedit** - you need root privileges to edit the config file.)

BTW - are you running Breezy or Dapper?

---

### Post by Ken Burgard on 2006-06-08
[QUOTE=linear]Ok, now we're getting somewhere. You can ignore the first error; it turns up in my error log as well but doesn't cause any problems. The second error is the one to focus on.

Set the loglevel to debug in cupsd.conf, and restart cups as detailed in an earlier post. With luck, the actual error will turn up in the series of debug messages (lines that start with "D").

(If you prefer using Text Editor over nano, start from a Terminal window and enter **gksudo gedit** - you need root privileges to edit the config file.)

BTW - are you running Breezy or Dapper?[/QUOTE]

I am running Breezy.  Using debug, not debug 2, I got about 640 "D" lines.  Looking at them I don't know what may be relevent.  Perhaps having that many itself is relevent?  Seeking your advice before I post them all.  Sorry for the delayed answer, I lost internet connection which took me awhile to figure out.  Someone turned off the light switch that powers the DSL modem receptacle.  THAT IS funny!  I hadn't thought to look over and see if its light were all twinkly as usual.  Here are the first 8 "D" lines:

D [07/Jun/2006:20:08:02 -0700] AddLocation: added location '/'
D [07/Jun/2006:20:08:02 -0700] DenyIP: / deny 00000000/00000000
D [07/Jun/2006:20:08:02 -0700] AllowIP: / allow 7f000001/ffffffff
D [07/Jun/2006:20:08:02 -0700] AddLocation: added location '/jobs'
D [07/Jun/2006:20:08:02 -0700] AddLocation: added location '/admin'
D [07/Jun/2006:20:08:02 -0700] DenyIP: /admin deny 00000000/00000000
D [07/Jun/2006:20:08:02 -0700] AllowIP: /admin allow 7f000001/ffffffff
D [07/Jun/2006:20:08:03 -0700] LoadAllPrinters: Loading printer DeskJet-722C...

---

### Post by linear on 2006-06-08
Work backwards from the "PID 7671 stopped with status 3!" error message. I'm hoping there's a debug message from the thing that's actually failing.

---

