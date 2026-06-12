---
title: "[SOLVED] Error on adding extention to OO.org"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by al.adab on 2008-04-08
hello everyone,

I'm adding the Creative Common extension to Open Office.org (2.4) and I get the following message (after clicking Tools>Extension Manager>ccooo.oxt): 

*Extension manager: could create Java implementation loader*

Any idea, anyone? Thanks.

---

### Post by erginemr on 2008-04-08
Try this workaround (i.e. disabling and enabling Java):
[http://www.oooforum.org/forum/viewtopic.phtml?t=42403](http://www.oooforum.org/forum/viewtopic.phtml?t=42403)

Otherwise, with regard to this post:
[http://extensions.services.openoffice.org/project/ooo2gd#comment-123](http://extensions.services.openoffice.org/project/ooo2gd#comment-123)

You normally have an open-source java implementation installed in Ubuntu by default, whereas the extension you are trying to implement might be requiring for the Java version developed by Sun:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

The following command from the terminal:
```
java -version
```
will reveal which Java version you have installed in your system.

---

### Post by al.adab on 2008-04-08
thanks. This is the Java version I have: 

$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

Please notice that I've just re-installed ubuntu gutsy. In my previous installation, I had OO.org 2.3 with the Creative Commons extension (installed without any problem) which I updated to 2.4 (the extension appeared automatically in the new version). I also had the same JRE 1.6.

After re-installing gutsy, I didn't install the CC extension on OO.org 2.3. I first updated it to 2.4 and THEN tried to install the CC extension. 

I've just had a look at the links you sent, but couldn't find a solution (probably I just couldn't understand what I should do). Can you help? Thanks.

---

### Post by erginemr on 2008-04-08
No problem, buddy.

You appear to have Sun's Java v.1.6, so that is not the source of the problem.

The final post in that link says:
> Apparently you go into Options and uncheck Java/"Use a Java runtime environment."
Close Impress and try to enable the extension again. Received the same error.
Return the check to the "Use a Java runtime environment" box.
This time it'll work.

So, I thought maybe if you go into OpenOffice Menu -> Tools -> Options -> Java and uncheck "Use a Java Runtime Environment", and reinstall the CC extension, and finally check "Use a Java runtime environment" again, then you will be able to use the CC plugin. I am not sure if it will work though, as it looked like a flimsy technique to me.

---

### Post by al.adab on 2008-04-08
it is rather flimsy...besides, it didn't work :)
This looks like a mystery, doesn't it. Any idea?

---

### Post by erginemr on 2008-04-08
I have no means to try OpenOffice 2.4 (I guess you have updated it manually), but I could successfully install the CC extension in v2.3 by following:
[http://ubuntuforums.org/showthread.php?t=733836](http://ubuntuforums.org/showthread.php?t=733836)

So, probably the new OOo 2.4 is incompatible with the CC extension. The version I have downloaded is 0.6.1? Are you also running the same version of CC? Otherwise, you can try updating the extension via the "Updates..." button.

---

### Post by al.adab on 2008-04-08
I feel a bit stupid to be honest...the little circle next to Sun Microsystems was not ticked...it works now. Thanks for your patience!

---

### Post by al.adab on 2008-04-08
Here's what it's got to look like:

---

### Post by erginemr on 2008-04-08
No problem.

Take care. :D

---

