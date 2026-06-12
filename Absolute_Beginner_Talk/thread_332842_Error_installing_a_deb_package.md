---
title: "Error installing a deb package"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by mistypotato on 2007-01-06
Hello,
I could really use your help.

I am trying to install a "deb" package but I am running into a brick wall and don't know what to do next.

It DOES say "all dependencies satisfied" which I think is good?

When I double click on the deb package, it statrs working and then I get...

(Reading database ... 93685 files and directories currently installed.)

Unpacking m2300w (from m2300w_0.51-2_i386.deb) ...
[COLOR="Red"]
dpkg: error processing m2300w_0.51-2_i386.deb (--install):
trying to overwrite `/usr/share/foomatic/db/source/driver/m2300w.xml', which is also in package foomatic-db
dpkg-deb: subprocess paste killed by signal (Broken pipe)[/COLOR]


Errors were encountered while processing:
m2300w_0.51-2_i386.deb
e)
Edit/Delete Message

Any suggestions?

Thanks

---

### Post by taurus on 2007-01-06
Applications -> Accessories -> Terminal
```
cd ~/Desktop
sudo dpkg -i m2300w_0.51-2_i386.deb
```

---

### Post by mistypotato on 2007-01-06
Thanks Taurus but that just gives me the same error?

MP

---

### Post by dannystaple on 2007-01-06
Taurus - would it be a good plan to recommend he use a "force" command line override for that if he is already sudoing?

---

### Post by mistypotato on 2007-01-06
Taurus,

Is the command you posted any different than double clicking on the DEB package?

Thanks

---

### Post by Bachstelze on 2007-01-06
The message is pretty self-explanatory. The package you're trying to install tries to overwrite a file which belongs to an already-installed package. You can either remove foomatic-db or try to find a more Ubuntu-friendly version of the one you're trying ot install.

---

### Post by mistypotato on 2007-01-06
ohhh...

So maybe if I remove foomatic db?

I'll try that.  Odd thing is that the pre-requisite for this package IS having foomatic installed but maybe foomatic-db is an unnecessary something or another?

I-dunno.

Thanks for your help!

---

### Post by mistypotato on 2007-01-07
Resolution....

I deleted the foomatic-db package and it's dependencies (I think, I'm terribly new to all this stuff)...and it then installed fine.


Thanks HTL...that was the key.

Sometimes to a noob the "obvious" is hardest to see.

---

