---
title: "[SOLVED] i want a application which will...."
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by rahul_bhise on 2007-07-12
my internet broadband provider does not charge for the first 1 GB upload+download (per month)  data usage(besides a monthly subscription rent). 
though there is a web page where i can go and login to know my current data usage.
i need such a software which wood keep a track of this on my own computer. and show a graph on my desktop while data transfer.
in windows xp i used netmeter downloaded it from [http://www.metal-machine.de/readerror/](http://www.metal-machine.de/readerror/)
(so that you could see what i really want)

---

### Post by wolfen69 on 2007-07-12
System-->Administration-->System Monitor-->Network History

---

### Post by jordanmthomas on 2007-07-12
check out slurm as well.

---

### Post by rahul_bhise on 2007-07-12
but in network history does it show data for the whole month

---

### Post by jordanmthomas on 2007-07-12
if you've had your network up all month it does.  :)
You could probably write a script pretty easily that gets the amount transferred when you shutdown your network and that keeps a running total though...something basically like this:
```

get the usage
read total monthly usage from a file (say ~/bandwidth)
add the usage this session to it
save it back into the file.

```

EDIT:  you could also look into using curl to get the bandwidth from your ISP and then use awk / sed to tell you the number it finds.
EDIT2: my computer has only been up for 2 hours and I've already used 660 MB.  ;)

---

### Post by rahul_bhise on 2007-07-12
OK ...so to do this i have to start learning c  c++  java

---

### Post by LaRoza on 2007-07-12
> **rahul_bhise said:**
> OK ...so to do this i have to start learning c  c++  java

The word "script" was used; none of the above languages are scripting languages.

---

### Post by jordanmthomas on 2007-07-12
> The word "script" was used; none of the above languages are scripting languages.
..though it could easily be done in these languages as well.

---

### Post by rahul_bhise on 2007-07-12
sorry for my nuisance.
but i am ready to do what ever it takes to be in ubuntu like i was in windows XP

---

### Post by Fornax-101 on 2007-07-12
you could use [vnstat]("http://humdi.net/vnstat/"), its in the repo's

---

### Post by rahul_bhise on 2007-07-12
thanks fornax-101 i downloaded vnsat and installed it and red my report of the month.
this was easy then author package
so now i am back to solve some author problems

---

### Post by jordanmthomas on 2007-07-13
Very nice find, Fornax-101.  I'll probably use that because I love to keep tabs on little things like that.

---

### Post by ramjet_1953 on 2007-07-13
KTrafficManager works for me.

It has a nice GUI and has a reports section for daily and monthly stats.

It works fine on both KDE and GNOME.

You can get at deb package from here:

[http://wiki.suselinuxsupport.de/wikka.php?wakka=KTrafficAnalyzer](http://wiki.suselinuxsupport.de/wikka.php?wakka=KTrafficAnalyzer)

Just scroll down to the downloads section and the Ubuntu deb package is the first on the list.

It is listed as a 6.10 package but it works fine with Feisty.

Regards,
Roger :cool:

---

### Post by rahul_bhise on 2007-07-13
ramjet_1953
this was THE ONE i wanted 
many thanks man
i just downloaded it and running it
thanks once again

---

