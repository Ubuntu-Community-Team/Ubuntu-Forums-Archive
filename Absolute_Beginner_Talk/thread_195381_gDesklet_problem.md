---
title: "gDesklet problem"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by JGKC9AYC on 2006-06-12
I leave my machine on pretty much 24/7.  It seems that after a few hours, gDesklets disappears & I have blank, gray squares on my screen & no gDesklet icon on the top menu bar.
Is this a bug?  Has anyone else experienced this?  Is there a fix/solution for it?
Thanks in advance.

---

### Post by taurus on 2006-06-12
Are you running Dapper or Breezy?  What version of gdesklets do you have and how did you install it?  I don't have any problem with my version, 0.35.3 (from repo), running under Dapper...

---

### Post by JGKC9AYC on 2006-06-12
Sorry...I guess I should've stated that in my post.
I'm running Dapper...K7 kernel.  It's the same version as yours...0.35.3.
I installed it through the Add/Remove programs, if i'm not mistaken.

---

### Post by taurus on 2006-06-12
What kind of desklets do you run anyway?  I have IWeather, analog clock, and FBS HD space (four of them) (plus gdeskcal & gkrellm)...

---

### Post by JGKC9AYC on 2006-06-12
I'm using the starter bar with my most frequently used apps.  Which reminds me of another problem I was having with it...when I clicked my Opera starter, as soon as Opera would load, it'd disappear.  All the other starters worked fine.
I'm unsure which weather i'm using...actually i'm using 2...one is the 10 day forecast & the other is the current conditons.  I tried the FTB(?) one, but it seemed like Tokyo was the only option.

---

### Post by taurus on 2006-06-12
When you installed gdesklets with apt-get, did you happen to install gdesklets-data as well using apt-get?

---

### Post by JGKC9AYC on 2006-06-12
[QUOTE=taurus]When you installed gdesklets with apt-get, did you happen to install gdesklets-data as well using apt-get?[/QUOTE]

I think I just went under "Applications" to "Add/Remove"...I don't remember doing an apt-get.
Should I uninstall through "Add/Remove" & go a different route?  If so, what's your recommendation?
Thanks.

---

### Post by taurus on 2006-06-12
I always install stuff from repos using apt-get from a terminal, Applications -> Accessories -> Terminal...
```

sudo apt-get install gdesklets gdesklets-data

```

---

### Post by JGKC9AYC on 2006-06-12
[QUOTE=taurus]I always install stuff from repos using apt-get from a terminal, Applications -> Accessories -> Terminal...
```

sudo apt-get install gdesklets gdesklets-data

```[/QUOTE]

I just tried to remove it from "Add/Remove" programs & it wouldn't let me...something about other programs dependent on it or something.
If I went your route, would it just install over it?
Thanks.

---

### Post by taurus on 2006-06-12
Make sure it is not running before you try to remove it!!!  I assume you can use apt-get to remove it as
```

sudo apt-get remove gdesklets

```

---

### Post by JGKC9AYC on 2006-06-12
[QUOTE=taurus]Make sure it is not running before you try to remove it!!!  I assume you can use apt-get to remove it as
```

sudo apt-get remove gdesklets

```[/QUOTE]

Well, i'm not sure if it's running now or not...like I said, the icon's gone from the top toolbar & there's gray squares on my screen where the starter bar, etc were.  If I go to "Applications", then "Accessories", I get a blank gDesklet shell.  When I close it out, I get this message:

[I]The window "gDesklets Shell" is not responding.

Forcing this application to quit will cause you to lose any unsaved changes.[/I]

Is there like a "kill" command to stop a program that's running?  I'm new to this & haven't learned the commands yet.

---

### Post by taurus on 2006-06-12
You can kill your gdesklets with a kill command.  Run this command from a terminal to see what's process ID (first column) for python since gdesklets calls up python.  Then kill it with
```

ps -A
sudo kill -9 1234 (assuming that 1234 is the process ID for python from above!)

```

---

### Post by JGKC9AYC on 2006-06-12
Well, I uninstalled gDesklets & gDesklets-data, reinstalled both, & am having the same problem w/the Opera starter...as soon as Opera loads, it disappears.
Should I try again?  It seemed that even though I removed gDesklets, it remembered my settings...is that normal?

---

