---
title: "download/upload monitor"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by kane77 on 2007-02-20
I just heard I have some monthly quotas, but I cant find an application that would monitor my upload/downoload...
I know there are stats for session, but I need the sum in current month etc.. plus nice graphs would be cool too (but it's not needed)... something like DUmeter for windows... is there anything like that?

---

### Post by kerry_s on 2007-02-20
Doesn't the nm-applet do that? (right clck panel> add applet)

---

### Post by kane77 on 2007-02-20
> **kerry_s said:**
> Doesn't the nm-applet do that? (right clck panel> add applet)

not quite, it only shows the data from one session and writing it down every time I turn off the computer would be tedious work...
I need something that would log the data and sum them up... (plus show weekly monthly totals etc...)

---

### Post by kane77 on 2007-02-21
bump

---

### Post by kane77 on 2007-02-22
okay I searched the net through and through and I found zenoss which seems to do what I want, but its a bit too complex for me :D (in terms of functions it has.. I dont need all that)
all that I want is simple bandwidth/data transfer statistics...

---

### Post by Ben Sprinkle on 2007-02-22
Is this for apache or something?

---

### Post by kane77 on 2007-02-22
no. just something like du meter that would show totaly downloaded/uploaded data.
the output should look something like this:
```

day                DL      UL      both ways
10.2.2007      10MB  15MB       25MB

```
etc...

---

### Post by Ben Sprinkle on 2007-02-22
Double click your network icon on the taskbar, it shows that. :)

---

### Post by kane77 on 2007-02-22
but I need logging + monthly totals...

---

### Post by Ben Sprinkle on 2007-02-23
Why is this? Are you running some sort of upload server?
Sorry but I have never used any software that does what you need. =(

---

### Post by opticyclic on 2007-04-21
Netmeter is a freeware Windows application that looks very similar to DU meter
[http://www.softpedia.com/get/Network-Tools/Bandwidth-Tools/NetMeter.shtml](http://www.softpedia.com/get/Network-Tools/Bandwidth-Tools/NetMeter.shtml)

It also works perfectly under Wine
[http://appdb.winehq.org/appview.php?iVersionId=5626](http://appdb.winehq.org/appview.php?iVersionId=5626)

---

### Post by guysmiley25 on 2007-05-12
I believe that your after an application similar to what I'm after, and I have had no luck so far myself. [Here]("http://ubuntuforums.org/showthread.php?t=440977") is my thread.

What your after, I would expect to be a feature of the application I am after. I see no reason why what we want is unavailable.

I used to use a distribution called [ClarkConnect]("http://www.clarkconnect.com/"). By using it's web interface, you could do what we are both after. Maybe Clark Connect is a solution for you.

However ClarkConnect lacked many other features, and this is why I changed to Ubuntu. I suspect that the web interface is just a front-end for what is already available, and hence why I see no reason why this can not be done.

Can anyone help us out?


**Edit:** [This]("http://www.linux.com/article.pl?sid=05/12/15/177232") sounds interesting a might be a start to a solution for you. However looks quite complex for the task you require.

---

### Post by opticyclic on 2007-05-12
I have subsequently found Knemo
So if you are using Kubuntu then this is perfect.
It integrates into the Control Centre and automatically starts on login.
It is in the repos too

See here for more info
[http://www.kde-apps.org/content/show.php?content=12956](http://www.kde-apps.org/content/show.php?content=12956)

---

### Post by unnes on 2007-06-27
Hmm, Knemo sounds and looks like a perfect DUMeter replacement. However, when I open up Kcontrol and try to turn it on, nothing seems to happen. Knemo should open up in the tray, right?

---

### Post by Papi-KB7VGW on 2007-06-27
GKrellM does what you want.  On the chart for eth1 is a button that brings up daily, weekly and Monthly totals.

---

### Post by opticyclic on 2007-06-28
> **unnes said:**
> Hmm, Knemo sounds and looks like a perfect DUMeter replacement. However, when I open up Kcontrol and try to turn it on, nothing seems to happen. Knemo should open up in the tray, right?
It should start in the tray. Have you restarted your session?

---

### Post by kane77 on 2007-11-30
> **opticyclic said:**
> It should start in the tray. Have you restarted your session?

okay finaly I found a program called vnstats, that does exactly what I need... (and is in the repositories...)

---

