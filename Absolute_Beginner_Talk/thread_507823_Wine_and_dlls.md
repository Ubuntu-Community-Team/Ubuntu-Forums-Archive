---
title: "Wine and dlls"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Lucifiel on 2007-07-23
Okay, first: I'm trying to run UPP under Wine in Ubuntu. In Wolvix, UPP ran under Wine just fine(no crashes, totally stable!). 

But under Ubuntu, I keep getting the following messages even though I tried downgrading the Wine program to version 0.9.33. 
> 
err:ole:CoGetClassObject class {d45fd2fc-5c6e-11d1-9ec1-00c04fd7081f} not registered
err:ole:create_server class {d45fd2fc-5c6e-11d1-9ec1-00c04fd7081f} not registered
err:ole:CoGetClassObject no class object {d45fd2fc-5c6e-11d1-9ec1-00c04fd7081f} could be created for context 0x5

Now, I've figured out that I likely need the following dlls for Wine: OLE32, OLEAUT32 and MSCVRT 

However, what other dlls should I load and would it be safe to just retrieve them from my Windows installation folder to the wine "system32" folder?

---

### Post by MrFSL on 2007-07-23
Greetings.
I just asked the same (similar anyways) question not to long ago

[http://ubuntuforums.org/showthread.php?t=488630](http://ubuntuforums.org/showthread.php?t=488630)

In short the reply I got from the forum was a good one. I was directed to look up apps that I wanted to run in WINE on the wine website:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

You often get instructions concerning which dll's are required to make certain applications function well.

---

### Post by Lucifiel on 2007-07-23
> **MrFSL said:**
> Greetings.
I just asked the same (similar anyways) question not to long ago

[http://ubuntuforums.org/showthread.php?t=488630](http://ubuntuforums.org/showthread.php?t=488630)

In short the reply I got from the forum was a good one. I was directed to look up apps that I wanted to run in WINE on the wine website:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

You often get instructions concerning which dll's are required to make certain applications function well.

Thank you anyways but the application itself is not in the Wine database.

Edit: I'm now going to install the version of wine that Wolvix cub used. That might be a first step in getting UPP to run. :)

---

