---
title: "Gaim--&gt;Pidgin; Pidgin fails!"
date: 2007-09-10
forum: Absolute Beginner Talk
---

### Post by flyingsolo on 2007-09-10
Tonight I downloaded & installed Pidgin which now shows in Applications menu but after clicking, it doesn't open.  Gaim, however still does work. (I followed instructions from here

[http://www.ubuntugeek.com/install-pidgin-instant-messanger-in-ubuntu.html]("http://www.ubuntugeek.com/install-pidgin-instant-messanger-in-ubuntu.html")

Any help would be appreciated.

---

### Post by misfitpierce on 2007-09-10
Try running pidgin in terminal and paste its output.

---

### Post by flyingsolo on 2007-09-10
Thanks (such a quick reply!).  My output is:

pidgin: error while loading shared libraries: libdbus-1.so.3: cannot open shared object file: No such file or directory

Not sure what this library is.  Maybe conflicting with Gaim?

---

### Post by diatribe on 2007-09-10
you probably need to install libdbus development headers.  you know there is a .deb for pidgin at getdeb.net right?  that should resolve any dependencies

---

### Post by isaacj87 on 2007-09-10
> **diatribe said:**
> you probably need to install libdbus development headers.  you know there is a .deb for pidgin at getdeb.net right?  that should resolve any dependencies

I too recommend the getdeb.net deb files. Quick and painless way of getting pidgin to work, even with gaim installed.

---

### Post by flyingsolo on 2007-09-10
The getdeb.net version specifies it is for Feisty 32 or 64 bit but I have Dapper on this old desktop.  Should that be a problem?

---

### Post by diatribe on 2007-09-10
I have installed feisty .debs on gutsy and had them work, dunno if they would work on dapper.

---

### Post by flyingsolo on 2007-09-10
When I download from getdeb.net and try to install Pidgin I get,

Error:  Dependency is not satisfiable: libatk 1.0-0

which sounds like a dead-end to me!

---

### Post by ryno519 on 2007-09-10
> **flyingsolo said:**
> When I download from getdeb.net and try to install Pidgin I get,

Error:  Dependency is not satisfiable: libatk 1.0-0

which sounds like a dead-end to me!

Do you have the universe and multiverse repositories enabled?

---

### Post by flyingsolo on 2007-09-10
> Do you have the universe and multiverse repositories enabled?

Yes, I believe so

---

### Post by Gremlinzzz on 2007-09-10
How i installed pidgin. first i used synaptic package manager to uninstall gaim and gaim data. cause they bump heads with pigdin.
then i installed using ubuntu guide.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.1.1_Instant_Messenger](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Pidgin_2.1.1_Instant_Messenger)

---

