---
title: "Java for Edgy - very basic"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by 2CV67 on 2007-01-04
Greetings community!

I am not trying to do anything advanced, development or gaming or...

Visiting some respectable (government!) websites with Firefox, I get notices saying I need to download a plugin & if I agree I get to an invite to download Java Runtime Environment, then "Not Available" & then "Manual Download", at which point I stop.

I have the default Firefox settings, which include "Enable Java" & "Enable Javascript" but not all the boxes in Advanced Javascript are ticked - see screenshot.

I looked in Synaptic & found & installed java-gcj-compat ("Java runtime environment using GIJ") & the associated packages (I love Synaptic...) which I assumed would do the job, but I still get the same reactions from my sites...

Of course I have looked through the last month's posts here on "Java" and found lots of confusing-to-a-noobie stuff about Automatix & Sun Java versions & Multiverse Repositories etc.

Before I try any of that & screw something up, could some kind soul please tell me if I should expect java-gcj-compat to be enough for normal use, and do I just need to check some detail somewhere?
If not, then what is java-gcj-compat there for?

If I really do need to use Sun Java, then I think I can get it through Synaptic with Multiverse enabled, can't I? (I am still trying to avoid Terminal where possible!).

Would I need to remove java-gcj-compat again before installing Sun?

Thanks very much guys.

---

### Post by oyvindaa on 2007-01-04
You'll need to enable the universe and multiverse repositories for this to work.

Installing the Java Runtime Environment, type in the terminal:

```
sudo apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts
```

Confirming the installation, type in the terminal:

```
java -version
```

If what you see isn't the Sun version, do this in the terminal:

```
sudo update-alternatives --config java
```

There you choose the Sun version, type its number and hit the enter button.

Next, open your browser and type ```
about:plugin
``` in the address bar.

If the java plugin comes up as installed, everything is ok :)

EDIT: this is for Dapper, but it might work just fine for Edgy as well (I hope).

---

### Post by MiCovran on 2007-01-04
Try this: [https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/web-browsing.html]("https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/web-browsing.html")

Maybe it would help if you posted the site that doesn't work.

---

### Post by 2CV67 on 2007-01-04
Thanks for those replies!

I skipped to the "Help" link first as I am still wary of Terminal Commands if I can get there by GUI. (That could be another long & interesting thread, but not here & now!)

There I saw the line on Java Plugin for Firefox & did just that after enabling Multiverse repositories.

...and now my problem site works just fine & I'm happy :D  thanks!
If interested, it was [here]("http://www.indices.insee.fr/bsweb/servlet/bsweb?action=BS_SERIE&ONGLET=1&BS_IDBANK=067517959&BS_IDARBO=05040909000000")

I would still be interested to know whether I should have expected the "Java runtime environment using GIJ" to handle this job...
...or does everybody end up having to install Sun's Java?

Thanks again!

---

