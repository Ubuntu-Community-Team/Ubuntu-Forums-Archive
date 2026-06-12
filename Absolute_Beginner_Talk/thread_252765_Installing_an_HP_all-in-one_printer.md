---
title: "Installing an HP all-in-one printer"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by Shenandoah on 2006-09-07
I'm running Kubuntu in persistent mode on a 2gb usb flashdrive and am trying to set up a printer.  I have an HP 1209 all-in-one printer/scanner connected via USB.  

I go under k-Menu>System Settings>printers and select administrator mode.  The other drop down box has CUPS selected.  I then click on add printer.  I see the printer and I select the appropriate drive but then get this message in a pop up window:

[I]Unable to load the requested driver:
Unable to create the Foomatic driver [HP-PSC_1210,hpijs]. Either that driver does not exist, or you don't have the required permissions to perform that operation.[/I]

What am I not doing right?  Thanks.


Shenandoah

---

### Post by whizbaby on 2006-09-07
Two thoughts suddenly come to my mind:
(1)did you do **sudo adduser cupsys shadow**?(otherwise cups is not allowed to verify passwords)
(2)do you have the package *hpoj* installed (in addition to the *hpijs*)?
(3)is the .ppd (located in */usr/share/ppd/hpijs/HP/HP-PSC_1210-hpijs.ppd* really there? If not, download it and put it where it belongs.
(My wife's got an PSC1210 and it prints and scans fine! For scanning install *xsane*)

---

### Post by Shenandoah on 2006-09-07
whizbaby,

Thanks for the info.  I checked and the .ppd file is there.  I'm trying to install the printer under the KMenu>systems settings>printer.  I'm not sure how use the command line you listed below.  Is there another way to add a printer outside of the Kmenu>system settings option?  Thanks.

Shenandoah

---

### Post by whizbaby on 2006-09-07
Yes, it is. When you have typed what I suggested to add password-verification ability to CUPS open your favourite browser and type (after turning on the printer of course):
localhost:631    
in the adress-bar.(nothing else except RETURN-key)
The cups web-interface will pop up, and under *administration* you will simply have to add your printer (which will be automatically detected since it's .ppd is there)
And now? Spitting words on paper?

---

### Post by Shenandoah on 2006-09-07
I'm not sure I got any farther.  The following message came up in a green screen:
[B][I]
413 Request Entity Too Large

HTTP/1.1 413 Request Entity Too Large Date: Thu, 07 Sep 2006 17:06:05 GMT Server: CUPS/1.2 Content-Language: en_US Upgrade: TLS/1.0,HTTP/1.1 Connection: close Content-Type: text/html; charset=utf-8 Content-Length: 370
413 Request Entity Too Large[/I][/B]

I tried again and this one came up

[B][I]413 Request Entity Too Large

HTTP/1.1 413 Request Entity Too Large Date: Thu, 07 Sep 2006 17:06:45 GMT Server: CUPS/1.2[/I][/B]

Shenandoah

---

### Post by whizbaby on 2006-09-07
You leave me ... breathless.
Seems to be a KDE/kubuntu issue, didn't know about that:
[http://www.kdedevelopers.org/node/2117/](http://www.kdedevelopers.org/node/2117/)
(it's not exactly your problem, but what you experience could be a symptom of it)
Only to be sure, you added yourself to the group *lpadmin* and you restarted *cupsys*, right? (if not, do **sudo adduser *your_username_here* lpadmin** and **/etc/init.d/cupsys restart**  maybe everything is right ...)

---

### Post by Shenandoah on 2006-09-07
whizbaby,

Thanks for your suggestions.  I'll keep looking.

Shenandoah

---

### Post by whizbaby on 2006-09-07
Only for clarifying:
after adding you to *lpadmin* and adding *cupsys* to *shadow* you have to restart cups with **/etc/init.d/cupsys restart**(or complete reboot), otherwise none of the changes will take place. (perhaps you knew this already...)

---

### Post by Shenandoah on 2006-09-07
I ran the command line to restart cups and got this message:

[B][I]ubuntu@ubuntu:~$ /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd                                start-stop-daemon: warning: failed to kill 6717: Operation not permitted
cupsd: Child exited on signal 15![/I][/B]

I then tried the cups web interface and still got the same messages about request entity too large.

Could the problem be in that I'm running Kubuntu in persistent mode?  I'm new to Kubuntu so I'm not real familiar with how everything works yet.

Shenandoah

---

### Post by whizbaby on 2006-09-07
try
**sudo /etc/init.d/cupsys restart**

---

