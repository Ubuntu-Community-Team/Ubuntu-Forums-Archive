---
title: "Terminating a command"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Parasitesss on 2007-04-02
Upon pressing **Cntrl + C** which is, I believe, to terminate a command;

was everything downloaded by the now terminated command undone?

I was & still am having a problem with getting my hpdeskjet 5150 to connect with my comp, so I followed instructions which said to post the code below into my terminal:


[PHP]sudo apt-get install build-essential python2.4-dev python2.4-qt3 libcupsys2-dev libsnmp9-dev libjpeg62-dev lsb libtool automake1.9 libusb-dev[/PHP]

I suddenly got I feeling that I should have done the quick install instead of the manual one and quickly pressed **Cntrl + C** in hopes to terminate what ever the code above installed.

Do I have to retrace everything that was downloaded by that command and delete all or did the **Cntrl + C** do it all for me?

---

### Post by Bachstelze on 2007-04-02
Could you explain what "the quick install" is ?

---

### Post by Parasitesss on 2007-04-02
oh hey, thanks btw for the solutions to my other questions :]
[B]
[http://hplip.sourceforge.net/install/index.html](http://hplip.sourceforge.net/install/index.html)[/B]

There are "There are two different ways to install HPLIP."
I followed the one labeled "Manual install" at the bottom.

---

### Post by Bachstelze on 2007-04-02
Hm, it seems to be just a shell script which apt-get's the packages. You can just go on with it :)

---

### Post by Parasitesss on 2007-04-02
cool, but would it hurt to go use the quick way instead, as opposed to the manual install?

The manual install seems to long to go on but if its better that way then I'll go ahead with it.

---

### Post by Bachstelze on 2007-04-02
You can use the automatic script if you want. If some of the packages it wants to install were already installed, it will just skip them.

---

### Post by Parasitesss on 2007-04-02
thankyou soo much

---

