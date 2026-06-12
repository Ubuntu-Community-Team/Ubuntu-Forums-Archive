---
title: "Problems starting web browsers"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by Crossbow on 2007-01-16
I was using Firefox with no problem for a few weeks, but suddenly it shut down. (I was changing the fonts in my "preferences" when it happened and I don't see how anything I did there could have caused it.)

Now when I try to launch it, it clocks for a few minutes, then stops. When I tried launching Swiftfox, it did nothing at all. I'm using Opera now, which is fine, but I'm annoyed that I can't figure out what happened.  Suggestions?

---

### Post by 23meg on 2007-01-16
Do you get any error messages when you launch it from a terminal?

---

### Post by Crossbow on 2007-01-17
Well... I don't know how to launch it from a terminal. :oops: What do I type in?

---

### Post by taurus on 2007-01-17
Applications -> Accessories -> Terminal
```
firefox
```

---

### Post by Crossbow on 2007-01-17
Oh, is that all? I knew it would be something really simple that I didn't know. Same thing for swiftfox?

I'm at work, but I'll truy it as soon as I get home. Thanks.

---

### Post by taurus on 2007-01-17
> **Crossbow said:**
> Oh, is that all? I knew it would be something really simple that I didn't know. Same thing for swiftfox?

Yip.

---

### Post by Crossbow on 2007-01-17
Alrighty. I tried swiftfox, then firefox. Here are the errors: 

For swiftfox: 
**bash: swiftfox: command not found**

Dunno what I need to do for that. Is it telling me I don't actually have Swiftfox? I installed swiftfox from Automatix, and it is showing up in my "Accessories," so at least some part of it is in there. Also installed the plug-ins that were available in Automatix. 

For Firefox: 
**Floating point exception**

Huh? :confused:

---

### Post by taurus on 2007-01-17
```
whereis swiftfox
```

---

### Post by Crossbow on 2007-01-17
Well, before I got your message I decided to unistall Swiftfox with Automatix and try downloading it off the internet. Then when I tried running it I got this error: 

**/opt/swiftfox/run-mozilla.sh: line 131: 10691 Floating point exception"$prog" ${1+"$@"}**

What is this floating point of which they speak?

---

### Post by taurus on 2007-01-17
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)

---

### Post by Crossbow on 2007-01-17
Looked like it was working, then... 

> Downloading Swiftfox from the Swiftfox site

--22:15:13--  [http://getswiftfox.com/builds/releases/swiftfox-2.0.0.1-pentium3.tar.bz2](http://getswiftfox.com/builds/releases/swiftfox-2.0.0.1-pentium3.tar.bz2)
           => `swiftfox-2.0.0.1-pentium3.tar.bz2'
Resolving getswiftfox.com... 208.113.142.250
Connecting to getswiftfox.com|208.113.142.250|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
22:15:14 ERROR 404: Not Found.

Previous command did not complete successfully. Exiting.


---

### Post by Crossbow on 2007-01-18
Please help!

These are the error messages I'm currently getting: 

>  anna@Rivendell:~$ firefox
Floating point exception
anna@Rivendell:~$ swiftfox
/opt/swiftfox/run-mozilla.sh: line 131:  6141 Floating point exception"$prog" ${1+"$@"}
anna@Rivendell:~$

I Googled "floating poing exception," and there were a few hits but they were all waaaaay over my head. All articles were addressed to programmers or mathematicians. 

Am I just permantly stuck with only Opera now? Not that I mind Opera, but it bothers me that it's my only option.

---

### Post by mahiyar on 2007-01-18
This is all I found to help u [http://www.linuxquestions.org/questions/showthread.php?t=513294](http://www.linuxquestions.org/questions/showthread.php?t=513294)

---

### Post by arnieboy on 2007-01-18
FYI: swiftfox not working is because of firefox core dumping.

---

### Post by Crossbow on 2007-01-18
> **arnieboy said:**
> FYI: swiftfox not working is because of firefox core dumping.

Not sure what that means, but I'll take your sord for it. 

Anyway, I tried the renaming thign and got he error message tha tFirefox was already running and I had to close it or reboot, I couldn't see anything that indicated it was running, so I tried rebooting (again) to no avail.

---

### Post by MkfIbK7a on 2007-01-18
i dont think you needed to uninstall swiftfox in automatix...

---

### Post by arnieboy on 2007-01-19
> **Crossbow said:**
> Not sure what that means, but I'll take your sord for it. 

Anyway, I tried the renaming thign and got he error message tha tFirefox was already running and I had to close it or reboot, I couldn't see anything that indicated it was running, so I tried rebooting (again) to no avail.

Check and see if your home config folder is borked or not.
```
mv -f ~/.mozilla ~/.mozilla_backup
```
copy and paste the above command (to make sure you dont make typos)
now start firefox (leave swiftfox alone for the time being)

---

### Post by MightyFrog on 2007-06-04
Arise, thread of olde!

I took the advice of the previous post. Firefox got to the point of asking whether I wanted to import bookmarks from Opera or another program, but crashed after that. The terminal output was again 

Floating point exception (core dumped)

What should I do next? Reinstall Firefox?

---

