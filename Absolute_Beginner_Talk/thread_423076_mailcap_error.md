---
title: "mailcap error"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by swoskow on 2007-04-25
I have Ubuntu running in Edgy and upgraded to Fiesty.  I had a few problems pop up when I upgraded.  One is when I open VLC I get an error message that reads "Mailcap file/home/swoskow/.mailcap, line 1 incomplete entry".  It ignores it and plays but the sound does not shut down when I close the program.  I have to go to the system monitor  and stop process for wvlc.  I don't know if the two problems are related and I would like to fix both.  I have looked through the forums and it appears the wvlc problem may be a bug in VLC.  Any help fixing the mailcap error and/or the sound error is very appreciated.

Currrent Mailcap file 
-e 
# Java Web Start
application/x-java-jnlp-file; /usr/lib/java/bin/javaws %s

---

### Post by leibowitz on 2007-04-25
Is this the first line of your .mailcap file ?
> -e 

If yes, please delete that.

---

### Post by swoskow on 2007-04-25
yes

---

### Post by swoskow on 2007-04-25
That worked - thank you

---

