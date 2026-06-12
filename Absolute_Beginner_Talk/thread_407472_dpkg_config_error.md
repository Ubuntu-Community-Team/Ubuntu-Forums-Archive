---
title: "dpkg config error"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by plainjane on 2007-04-12
When I try to install packages I am getting errors telling me that  they can't continue because dpkg may be broken.  So I ran sudo dpkg --configure -a  and got:


jane@POS:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/available' near line 12769:
 invalid package name (may not be empty string)

I have no idea what this means or what to do!!!  Any ideas?
               Thanks!
P.S.  Apparently I am also getting errors that preconfile dpkg is broken when I try to do updates through adept?!?!
P.S.S.  This is in Feisty,  dont' know if that makes a difference.

---

### Post by mohjlir on 2007-04-12
Doesn't sound great. Try 

#: dpkg-reconfigure dpkg

---

### Post by plainjane on 2007-04-12
That gave me the same error.  Bummer!  So does this mean a reinstall?  
                                                                 Thanks.

---

### Post by Malakia on 2007-04-12
try typing this in the command line and see if it helps.

```
dselect update
```

---

### Post by eljalill on 2007-04-12
Not sure whether this is an option for you, and is certainly not very elegant, but why don't you just see, what the package name is, it is complaining about is?

Just do ```
gedit /var/lib/dpkg/available 
```
and use the pict down to scroll to the line (takes a while but...). You might be able to just correct the file. At least for me this file is quite readable. Not sure at all whether this will work though, and even less sure, whether this would be more than a temporary solution.

---

### Post by plainjane on 2007-04-12
Thanks for the help, but nothing worked.

     The  gedit wouldn't work because it says that gedit isn't installed and won't let me install.

    The dselect  wouldn't work, just told me that there were errors and couldn't continue.

Any other ideas, or should I just go ahead and reinstall?
     Thanks again!

---

### Post by plainjane on 2007-04-12
I did a reinstall, and the same thing happened when I installed an upgrade for open office.  When I did another install, I unmarked the upgrade for openoffice, and no problems so far.  Hope it keeps working!  Guess I just won't upgrade open office for now.
     Thanks for all your help!

---

