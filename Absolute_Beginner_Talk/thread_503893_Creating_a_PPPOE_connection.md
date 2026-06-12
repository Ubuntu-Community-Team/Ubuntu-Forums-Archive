---
title: "Creating a PPPOE connection"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Snitz on 2007-07-18
When I first used Ubuntu (2 years ago) I got help here on how to create a PPPOE broadband connection and I still remember.

I got into my Ubuntu 2 mins ago and typed in the terminal the following:

> sudo pppoeconf

And it work, I was able to detect my network card and set a username and password for my connection. However, now with my connection I need to set a Service Name which is **Mnets\PRB** and I don't know how to do it with Ubuntu. Can anyone help me with that please?

---

### Post by Snitz on 2007-07-18
And another question, isn't there an interface to setup a broadband connection instead of launching it in the terminal?

---

### Post by DM was on fire! on 2007-07-18
Try System > Administration > Networking. :D What you need might be somewhere in there.

---

### Post by Snitz on 2007-07-18
> **DM was on fire! said:**
> Try System > Administration > Networking. :D What you need might be somewhere in there.
I tried that and it wasn't there. It's there on Fedora but not in Ubuntu :D

---

### Post by upal2286 on 2007-07-18
Though i'm also a beginner in ubuntu, i can help u to solve ur 2nd prob
just right click -> Create Launcher -> in the commend space write "sudo pon dsl-provider" (for connecting) click ok or u can choose an icon for it.
Using the same process by writing "sudo poff"  u can disconnect,
By the way in both case u have to select App in terminal option.

---

### Post by Wim Sturkenboom on 2007-07-18
You can leave the 'sudo' out; it's not required for either *pon* nor *poff*; makes life a bit easier ;)

---

### Post by Snitz on 2007-07-18
I still need to know how to enter a Service Name like I do on windows. It's important otherwise, I'll stay without internet at home!

---

### Post by Snitz on 2007-07-18
Anyone please :(

---

### Post by Wim Sturkenboom on 2007-07-19
From [http://publib.boulder.ibm.com/infocenter/wsphelp/index.jsp?topic=/com.ibm.wesm.doc/wesmpla-broadbandservicesusingpppoe.htm](http://publib.boulder.ibm.com/infocenter/wsphelp/index.jsp?topic=/com.ibm.wesm.doc/wesmpla-broadbandservicesusingpppoe.htm)

> 
Most PPPoE clients allow the subscriber to create a connection profile with this information.The PPPoE service name may be entered separately or entered as part of the username. In the latter case, it is the portion of the username that follows the @ (for example. if john@IBM is entered as a username, IBM is the PPPoE service name).

Found it googling for [pppoe service name](http://www.google.co.za/search?hl=en&q=pppoe+service+name&btnG=Google+Search&meta=) (third link), so I suppose that you could have found it as well.

---

### Post by Snitz on 2007-07-19
I will give it a try right now. BRB.

---

### Post by Snitz on 2007-07-19
That didn't work. I launched the pppoeconf via Terminal and I entered **mak70@Mnets\PRB** as my username. Mnets\PRB as my service name. And when I launched the connection using **sudo pon**, I got this error:
> /usr/sbin/pppd: In file /etc/ppp/peers/provider: unrecognized option '/dev/modem'

---

### Post by Snitz on 2007-07-19
Maybe the FriendlyPPPoE software can help me with my problem, where can I download it from? I'm on windows now.

---

### Post by Wim Sturkenboom on 2007-07-20
If it's pppoe, use *sudo pon dsl-provider*. And as said, I never use sudo for it.

---

### Post by az on 2007-07-20
> **Snitz said:**
> That didn't work. I launched the pppoeconf via Terminal and I entered **mak70@Mnets\PRB** as my username. Mnets\PRB as my service name. And when I launched the connection using **sudo pon**, I got this error:

That message means that you have the wrong device.  It has nothing to do with username/password stuff.

---

