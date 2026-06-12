---
title: "Frostwire"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by blendmaster on 2006-11-03
Hello!

This is a problem that hasn't seemed to be solved yet on the Ubuntu forums.

When starting Frostwire, it says it's starting the connection, but it never does.

I have no router, and this wasn't a problem on Dapper (I upgraded through a clean install).

Does anyone have a solution to this?

Thank you!

---

### Post by PPAAUULL on 2006-11-03
you do have internet working on the computer right?

---

### Post by blendmaster on 2006-11-03
> you do have internet working on the computer right?

Yes.

---

### Post by PPAAUULL on 2006-11-03
Are you sure that you have configured frostwire correctly?

---

### Post by blendmaster on 2006-11-03
> Are you sure that you have configured frostwire correctly?


What is there to configure? It has all of the same settings that it had when I was on Dapper.

---

### Post by PrairieShaman on 2006-11-03
When I click on Frostwire it won't even load for me. ](*,)   . It wouldn't work on 6.06 and it does the same thing on 6.10. I click, and nothing happens as if it hadn't even been clicked. Not sure why.

---

### Post by IusedTObeSOMEONEelse on 2006-11-03
Sounds like a Java issue Do you have your Sun Java 5 and Java jre1.4 or 1.5 ?? Worth a try

---

### Post by blendmaster on 2006-11-03
> Sounds like a Java issue Do you have your Sun Java 5 and Java jre1.4 or 1.5 ?? Worth a try

Wait, is this directed to me or PrairieShaman?

Well, either way, I have both the latest versions of JRE and even JDK.

PrairieShaman, you should install [Automatix]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38"), it's great because it will directly install Automatix with everything needed to get it going.

Though, I installed it through Automatix, and I'm not able to get this working...

---

### Post by llamakc on 2006-11-03
Edgy has /bin/sh pointed to dash instead of bash and that's your problem (if JAVA is already installed). 

[http://ubuntuforums.org/showpost.php?p=1625895&postcount=6](http://ubuntuforums.org/showpost.php?p=1625895&postcount=6)

---

### Post by Midway on 2006-11-03
I haven't tried Frostwire since I upgraded to Edgy.  I just tried it and it does the same thing, just saying "starting connection".  Running it in terminal has this result:

Starting FrostWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_08]
Configuring environment...
Loading FrostWire:
log4j:WARN No appenders could be found for logger (com.limegroup.gnutella.gui.Initializer).
log4j:WARN Please initialize the log4j system properly.
/usr/share/themes/Human/gtk-2.0/gtkrc:70: Engine "ubuntulooks" is unsupported, ignoring
/usr/share/themes/Human/gtk-2.0/gtkrc:240: Priority specification is unsupported, ignoring

And it freezes at this point. :(

---

### Post by llamakc on 2006-11-03
It works for me on Edgy.

```
java -version
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

```

```

lrwxrwxrwx 1 root root 9 2006-10-16 20:29 /bin/sh -> /bin/dash

```

```


 head /usr/bin/frostwire
#!/bin/bash
#cd /usr/lib/frostwire
/usr/lib/frostwire/runFrost.sh

```

```

 head /usr/lib/frostwire/runFrost.sh
#!/bin/bash
#
# Runs FrostWire.  This script must be executed in your FristWire
# install directory. (/usr/lib/frostwire)
# Currently mantained by Gubatron
# Last update: May 23rd 2006

```

---

### Post by blendmaster on 2006-11-03
> Edgy has /bin/sh pointed to dash instead of bash and that's your problem (if JAVA is already installed).

[http://ubuntuforums.org/showpost.php...95&postcount=6](http://ubuntuforums.org/showpost.php...95&postcount=6)

I don't understand.

None of those lines are already in those files. Are they supposed to be added in?

---

### Post by llamakc on 2006-11-03
Yeah, I had to edit them to get it running. There are actually several threads on here about frostwire and the dash/bash issue.

This is just the way that I did it, leaving /bin/sh still linked to /bin/dash.

You can also just change the /bin/sh symlink to point to /bin/bash. Someone who has done that should come along.

---

### Post by blendmaster on 2006-11-03
Thank you Llmakc, but I found a weird solution.

This should be stickied or something because I know it's a common problem.

When I start Frostwire, it continually says starting coonection. Well, I right-clicked on the Frostwire connection (See attachment) and clicked restore.

Well, it reset Frostwire, and it now works with an excellent connection.

This is weird, and I don't know why you have to do it, but I'm very glad!

---

### Post by blendmaster on 2006-11-03
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

I forgot to put the attachment! ;)

---

### Post by jeff1968 on 2006-11-04
Hi

New to Ubuntu .......... I was able to get Frostwire working after much time, but 2 days ago it stopped working (after updating Ubuntu I think) .... "Starting Connection" but never connects, tried the above fix did not help... can some please tell me how to fix step by step 

Thanks

---

### Post by Linux&amp;Lizards on 2006-11-04
my computer "had" the same problem only i am using dapper.
i had to unplug and reinssert my internet cord.
sorry thats just my noobie solution but it worked for me!

---

### Post by Linux&amp;Lizards on 2006-11-04
Hi jeff are you using dapper or edgy? if you recieved free cds then you are probably using dapper.

---

### Post by Linux&amp;Lizards on 2006-11-04
OH NO! Now i im stuck starting a connection 2 this is horrible.
when i clicked restore it still said starting connection.
but just a minute ago i had one and now i dont hmmmmm....

---

### Post by jeff1968 on 2006-11-04
Hi

I downloaded Ubuntu from the internet and burned the ISO on a CD and booted from it ........... everything was working fine until 2 days ago ........any help would be appreciated

Thanks

---

### Post by Linux&amp;Lizards on 2006-11-04
> **jeff1968 said:**
> Hi

I downloaded Ubuntu from the internet and burned the ISO on a CD and booted from it ........... everything was working fine until 2 days ago ........any help would be appreciated

Thanks

jeff start your own thread and ill so we can discuss your problem without being banned for spamming

---

### Post by overdrank on 2007-02-19
Hey thanks It worked for me! I am really starting to like Ubuntu. :)

---

