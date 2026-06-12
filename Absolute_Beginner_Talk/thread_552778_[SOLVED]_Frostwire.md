---
title: "[SOLVED] Frostwire"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by ExSuSEusr on 2007-09-16
Frostwire was working great.  Then out-of-the-blue it stopped.  Wont even load.  I click on the launcher and nothing.... no error messages... no glitches... nothing.... just silence.

Anyone familiar with this issue?

---

### Post by kevin11951 on 2007-09-16
not sure what is wrong, but just to let you know, limewire (the original one) has ubuntu .debs... try limewire...

---

### Post by sumguy231 on 2007-09-16
Try running it from the terminal to get extra error output.

---

### Post by ExSuSEusr on 2007-09-16
Ok fixed the issue:

Maybe someone else can find some use of this "How To" if they run into a similar situation...

I ran Frostwire in terminal and found that i was missing the latest JRE's (1.5.x) or newer.  Which was odd, because Frostwire was working just fine for a while...

Anyway.  To fix the problem was simple...

Get the latest JRE from Java.com:  

[Linux (self-extracting file)]("http://javadl.sun.com/webapps/download/AutoDL?BundleId=11284")

I download all files into a folder in my /home directory... 

Go to the file and right click on it -> Permissions -> Check the executable box -> Close

Click on it and select "Run in Terminal" - this will unpack the contents and you'll have a new folder in your /home directory called **jre1.6.0_02**

Open a terminal and type:

> gksudo nautilus

Simply cut and paste the folder to the /usr/java folder.

This worked and I got Frostwire back.

I just wish I knew what caused it to stop working in the first place....

If was working before, that should mean the right JRE was installed - then it wasn't?  How does that happen without root permissions?

---

### Post by Maestro23 on 2007-09-16
Good deal.  Can you mark this SOLVED.

---

### Post by ExSuSEusr on 2007-09-16
I can do that, but for an FYI...

What causes folders to mysteriously go *poof* in protected directories? 

Makes me nervous when this happens... being a recovering Windows user and all - that's something you see a virus doing.  Not saying I have a virus, but you know... curious.

---

### Post by Maestro23 on 2007-09-16
> **ExSuSEusr said:**
> I can do that, but for an FYI...

What causes folders to mysteriously go *poof* in protected directories? 

Makes me nervous when this happens... being a recovering Windows user and all - that's something you see a virus doing.  Not saying I have a virus, but you know... curious.

What folders are missing?

---

### Post by ExSuSEusr on 2007-09-17
Frostwire was working great for a couple of days... no problems at all.

Then out of the blue it stopped working... wouldn't even load.

I fixed the problem by installing the JRE's.  If was working before wouldn't that mean the JRE's were installed in the /usr/java directory?  They weren't there when I cut and pasted the new folder into /usr/java.

To me it seems obvious that some way, some how - the original JRE folder was deleted/removed from the /usr/java directory... 

Unless I'm missing something.

With the /usr/java directory being protected - and I know I didn't remove or delete the JRE folder - how did it get removed? 

See what I mean?

---

### Post by FuturePilot on 2007-09-17
Because when you install Java through the repositories it doesn't install it to /usr/java. As I do not have that directory. It's installed to /usr/lib/jvm/

---

