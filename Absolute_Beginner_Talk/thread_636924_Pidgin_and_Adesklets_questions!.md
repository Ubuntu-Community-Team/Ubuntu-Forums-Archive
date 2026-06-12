---
title: "Pidgin and Adesklets questions!"
date: 2007-12-10
forum: Absolute Beginner Talk
---

### Post by Dark Star on 2007-12-10
I compiled my Pidgin to 3.31 I donno what was that everything was fine but I uninstalled the older pdgin from Synaptic cause after compiling it was not upgraded :| Now whenever I try to open MSN accounts I get this error. . SSL suppport is needed please install SSL Support also 1 for Gmail TSL is not installed .. I guess  I did worng I updated again from apt but same error. How can I overcome this :| 

Also I installed Adesklets but I cannot find any thing of launching it ? ALT+F2 also fail even it did not starts via Terminal.. Even conky did not work....:mad:

Regard.. Please help me

---

### Post by Dark Star on 2007-12-10
Bump :|

---

### Post by SOULRiDER on 2007-12-10
Wheny ou compiled from source the older one didnt get replaced because you didnt build a Debian Package.
I think there are some packages for Pidgin in getdeb.net check it out.

---

### Post by Dark Star on 2007-12-11
> **SOULRiDER said:**
> Wheny ou compiled from source the older one didnt get replaced because you didnt build a Debian Package.
I think there are some packages for Pidgin in getdeb.net check it out.
I did d/l the getdeb very but same error :| No help from otehr guys :? and what abt adesklets :(

---

### Post by Dark Star on 2007-12-12
Bump c'mon guys its really irritating  cannot connect MSN and GMAIL :? Please help me :)

---

### Post by shae on 2007-12-12
To try to fix pidgin: 

Do you still have the folder from which you compiled pidgin.  If you do:
```
cd /path/to/pidgin/source/folder
sudo make uninstall
```
If you do not, then go to the next step.

Then
```
sudo apt-get purge pidgin
```
Add any other packages related to pidgin to the previous command.

If you skipped the first step because you lack that folder anymore, you now need to search your system for any remaining parts of pidgin and remember in the future if you want to compile from source to use checkinstall.

The finally install the deb file from getdeb.

---

### Post by itsjustarumour on 2007-12-12
I'd try uninstalling Pidgin again and reinstalling from the Gutsy repos to see if that works.  When you uninstall Pidgin, also make sure that you have deleted /Home/(username)/.purple as this is where all your Pidgin settings are kept. Don't worry, this will be recreated when you install Pidgin again.

---

