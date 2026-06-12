---
title: "Installing JRE in 7.04"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Aturner on 2007-05-13
I have been trying with no success to install java 6.o on my system. I tried the package installer, seemed to work fine, but when I opened up firefox, no dice! Any Ideas from anyone??
Thanks, Adrian.

---

### Post by taurus on 2007-05-13
Fire up synaptic and search for sun-java6-bin.  Otherwise, here is something you can look at.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Aturner on 2007-05-13
> **taurus said:**
> Fire up synaptic and search for sun-java6-bin.  Otherwise, here is something you can look at.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Did that, the package installer insists that 6.0 is installed, but firefox won't buy it!!

---

### Post by taurus on 2007-05-13
Okay, you are talking about the java plugins.  I assume you did close and open firefox again after you installed java?

Did you also remember to install sun-java6-plugin?

---

### Post by Aturner on 2007-05-13
> **taurus said:**
> Okay, you are talking about the java plugins.  I assume you did close and open firefox again after you installed java?

Did you also remember to install sun-java6-plugin?

Yes sir, did that. Maybe I'll try Opera <G>

---

### Post by mikewhatever on 2007-05-13
I used the following from ubuntuguide.org
> sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts

---

### Post by FastZ on 2007-05-15
> **taurus said:**
> Okay, you are talking about the java plugins.  I assume you did close and open firefox again after you installed java?

Did you also remember to install sun-java6-plugin?

I had initially just installed the JRE packages and then tried to access a webpage that had a Java applet on it and FF still said I had to install Java.  That's when I read further down this thread here and saw your post about the java6-plugin package.  I closed FF and installed that package through synaptic and then reopened FF and went to the page I was trying to access earlier and whadaya know?  It's working fine!  Thanks.

---

### Post by Aturner on 2007-05-15
I tried all the above, then checked the version of java installed and received:
Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0. Please click the button below to get the recommended Java for your computer.

---

### Post by gewitty on 2007-05-17
I'm getting the same error message - "Oops! You don't have the recommended Java installed.
Your Java version is 1.6.0. Please click the button below to get the recommended Java for your computer."

If I download the recommended update - jre-6u1-linux-i586.bin and then try to install it with Archive Manager, I get an error message saying that the file type is not supported.

Anybody got any ideas on how to fix this? I use LogMeIn a lot to support remote machines and without Java, this just doesn't work.

---

### Post by esoterica on 2007-05-17
The fix is don't use Java 6 yet, fall back to an older stable version and you'll be fine.

As far as Java 6 in Firefox, not sure about the Linux version of Firefox, but about a month and a half ago Java 6 would run on Firefox in Windows, then Firefox did an auto update and reported back that version of Java (6) would not work with Firefox. In Windows I've yet to see an update yet that would allow Java 6 to run in Firefox even though it did (sort of) before that last Firefox update a month and a half ago or so.

I've had so many problems with Java 6 in both Windows and Linux now that I have already resorted back to the older versions to lower the problems with Java, the JRE at least, the compiler seems to work ok for the Java 6 SDK, it's the JRE that's causing everyone so much grief though.

It's not directly obvious that JRE 6 is the cause of numerous problems unless you actually write Java code and fire the JRE on and off often enough to notice that this is when other problems with other things on your system start turning up.

In Linux I've dropped back to Java version 1.4.2-02 and it seems so far stable and working (at least as stable and working as Java can be, I hate java by the way so that doesn't help). In Windows Vista Business with Aero I've so far only stepped back to version 5 and it's holding together better than what I had happening with Java 6 on that system.

---

### Post by gewitty on 2007-05-17
That did the trick alright. I used Synaptic to uninstall Java 6 and then re-installed Java 5. Restarted Firefox and everything worked.

Thanks for the tip.

---

