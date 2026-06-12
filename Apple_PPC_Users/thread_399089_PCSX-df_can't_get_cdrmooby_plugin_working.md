---
title: "PCSX-df can't get cdrmooby plugin working"
date: 2007-04-01
forum: Apple PPC Users
---

### Post by RedRedKrovy on 2007-04-01
Installed PCSX-df from the synaptic package manager, also installed the psemu plugins through synaptic.  Can't get PCSX to recognize the mooby cdr plugin but it will recognize everything else.  Is the plugin x86?  If so why is it in my package manager?  Does anyone else know of any other plugins, I really need one that will run a cd-rom not just an image or iso.

---

### Post by Azzco on 2007-04-21
I'm havin ght e exact same problem..  I don't think that there's other CDr plugins for linux. I took a breif look at NGemu and only found mooby. I even tried some older versions of it but it lead to no succes. I don't think that you should be hoping for one but just uninstall that package.. I haven't tried it myself but I'll shout if it's succesfull ;)

---

### Post by Virgofenix on 2007-07-23
Babump. Having the same issue.

---

### Post by ObsidianOps on 2007-08-11
Alright, I was having the same problem, but was able to get it working.

1) First step is to go open synaptic, and install the package *psemu-drive-cdrmooby*
2) Next, make a shortcut from the libcdrmooby file it installs to the plugins directory in your home/.pscx/  (In my case this was the following command)
```
~$ sudo ln -s /usr/lib/games/psemu/lib/libcdrmooby-2.8.so .pcsx/plugins/libcdrmooby-2.8.so
```

And it should now work for you. Hope that helps.

---

### Post by fuzzyworbles on 2008-05-19
cool. worked perfectly.

---

