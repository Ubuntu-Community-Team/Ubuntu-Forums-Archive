---
title: "[SOLVED] Brother MFC-240c"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by bigsleep on 2007-06-27
I would like to have my Feisty x64 run my all in one Brother MFC-240c and I do not have the slightest idea on how to do this. I would greatly appreciate HELP from anyone that is out there.

---

### Post by Seisen on 2007-06-27
This might help

[http://ubuntuforums.org/showthread.php?t=423461]("http://ubuntuforums.org/showthread.php?t=423461")

---

### Post by bigsleep on 2007-06-27
Read your solution and I do not have the first clue as to where to key in your codes or how to activate them.

---

### Post by bodhi.zazen on 2007-06-27
???

---

### Post by starcraft.man on 2007-06-27
> **bigsleep said:**
> Read your solution and I do not have the first clue as to where to key in your codes or how to activate them.

Why on earth are you making a new thread because your having trouble with an answer given in response to another... simply respond to the one you already began please. We have enough threads going on here just trying to keep up without having redundant ones.....

Not to mention if you don't want to post and want to speak directly to a member we have PMs.

Edit: [Original thread in question.]("http://ubuntuforums.org/showthread.php?t=486346")

Edit2: Hey there Bodhi, good to see you around :D.

---

### Post by Seisen on 2007-06-27
I'll private message Bigsleep and help them out.

---

### Post by bodhi.zazen on 2007-06-27
> **starcraft.man said:**
> Edit2: Hey there Bodhi, good to see you around :D.

Starcraft.man ;)

Threads merged :twisted:

> **Seisen said:**
> I'll private message Bigsleep and help them out.

OK , but it is nice to see answers on the forums as well ...

To help others with similar problems ...

---

### Post by Seisen on 2007-06-27
I going to make a nice little howto on how to install the printer and post it for everybody and I will pm BigSleep when I done with it. I am going to bed now otherwise I would put it together right now.

---

### Post by Seisen on 2007-06-28
**[SIZE="6"]How To install your Brother MFC-240C in Feisty X64[/SIZE]**

The first step in installing your MFC-240C in Feisty 64-bit  is to download the LPR driver and the cupswrapper driver. The LPR driver can be downloaded here. 
[http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html")
and the cupswrapper driver can be downloaded here.
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html")
Make sure when you download the drivers that you download the drivers for Debian and not Redhat. 

After you have downloaded the drivers you need to install them. Make sure that you install the LPR driver first before you install the cupswrapper driver. To install the LPR driver put this in the terminal. For anybody who doesn't know to open the terminal it can be found by going to Applications>Accessories>Terminal.

```
sudo dpkg -i --force-architecture mfc240clpr-1.0.0-9.i386.deb
```  and to install the cupswrapper

```
sudo dpkg -i --force-architecture mfc240ccupswrapper-1.0.0-9.i386.deb
```

After both of those install successfully open up firefox or whatever other browser you use and put this in. 
[http://localhost:631]("http://localhost:631")

If for some reason you get a error saying page not found than you need to start cups by putting this in the terminal
```
sudo /etc/init.d/cupsys start
```

Click on “Manage Printers” and confirm that the device name is listed there. If the device name is NOT listed there, click on "Add Printer" and install the driver following the on-screen instructions.

If you cannot print you need to install this file.
```
sudo apt-get install lib32stdc++6
```

I am going to post this also in the tutorials and tips section so if you have any problems with it feel free to reply over their and we will try to help you the problem.


[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install6.html")

---

### Post by bigsleep on 2007-07-12
Have recently been having a problem down-loading from the Web. Have MFC-240C and Feisty Fawn 7.04.  Did not experience this problem when first connected.  Error message reads: printer name: postscript/default......any solutions out there? bigsleep

---

### Post by Al3xK3aton on 2007-07-12
You're going to have to make sure your printer is set up correctly. What name is your printer shared under?

---

### Post by ReaderRat on 2007-07-12
Pardon me, but are you having a problem downloading something from the web, or are you having printer problems?

---

### Post by bigsleep on 2007-07-13
What ever happened to KISS? I love my FF 7.04, but I believe in some cases it is OVER-FUNCTIONED.
Is Dale Puckett still out there?

---

### Post by bigsleep on 2007-07-14
All requests for help/solutions have been solved. Thank you.
All problems solved.

---

### Post by davidjmayo on 2007-07-14
> **bigsleep said:**
> All requests for help/solutions have been solved. Thank you.
All problems solved.

Here's a better way. OK you don't this when you first start out

Near  the top of the  page you see search. Click on it and from the list click "find all your threads"

go into **each** thread once and repeat this procedure
you see another option called **thread tools**
click this and from the list click "thread solved"

that's all you need to do

just mark them one by one as solved.

---

