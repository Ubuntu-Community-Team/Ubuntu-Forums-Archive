---
title: "skype"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by Alain Mercier on 2007-08-27
i'm trying to install skype, it stop with that message : wrong architecture i386. means what?

---

### Post by Seisen on 2007-08-27
Are you trying to install it on a 64-bit computer?

---

### Post by WinterWeaver on 2007-08-27
you probably downloaded the wrong installer, for a different type of computer.

go here: [http://www.skype.com/intl/en/download/skype/linux/](http://www.skype.com/intl/en/download/skype/linux/)

and download the one for the distribution you are using. I assume you are using the latest version of Ubuntu? If so, download the Feisty Fawn installer.

If however you already have this installer, and you get the error, then I'm not too sure on why it's doing that. Someone else will need to give you assistance in that case, as I don't really have the adequate  knowledge.

You might have the 64 bit version of Ubuntu, which means that that installer probably dont like the architecture... (someone may have to correct me on this)

WW

---

### Post by wormser on 2007-08-27
How are you trying to install it?  The architecture refers to you processor type.  Do you have a 64 bit processor? 

Install it this way:  Applications> Accessories> Terminal

```
sudo apt-get install skype
```

---

### Post by mauris on 2007-08-28
I have exactly the same problem (AMD 64). 
Anybody could help? Not having skype causing me some troubles. I really need it at work. And without it I still have to switch often to windows.

---

### Post by aidanr on 2007-08-28
Tried the [static version]("http://www.skype.com/go/getskype-linux-static")?
Also you might want to [read this]("http://yro.slashdot.org/yro/07/08/26/1312256.shtml") first.

Edit:// The skype help section regarding 64bit points to this [thread]("http://forum.skype.com/index.php?showtopic=10125").

---

### Post by mauris on 2007-08-28
The static version didn't work for me. :(

---

### Post by Arwen on 2007-08-28
Hello!
I have installed the beta version,how can I uninstall it(sign in and reset buttons are not working) and try the static one?

---

### Post by quinnten83 on 2007-08-28
what is a shadow password, and does ubuntu use them by default?
if not, how do I shadow it?

---

