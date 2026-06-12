---
title: "Software index broken"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by CLUGENHEIM on 2007-11-19
I had tried to install Java runtime from the Add/Remove.. app, but it screwed up during the install. Ever since I get this when I try updating anything:
[IMG]http://i34.photobucket.com/albums/d122/fudge123/Screenshot-update-manager.png[/IMG]

So I tried both of those things.

Running Syanptic got me this: 
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."
So I tried doing that in Terminal. (is that where I am supposed to do it?) And I get this:
"dpkg: requested operation requires superuser privilege"

So I decided to try the other way.

And again, I got this:
"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

... help?

---

### Post by taurus on 2007-11-19
Close Add/Remove, synaptic, or whatever else you have open.  Then, open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by Paul820 on 2007-11-19
Did you run the command **sudo dpkg --configure -a** from the terminal?

---

### Post by CLUGENHEIM on 2007-11-19
I had left out the "sudo" part. >.<

Thanks,

---

