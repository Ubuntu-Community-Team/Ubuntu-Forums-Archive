---
title: "Setting up Kazekahase as preferred browser"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Jugney on 2008-04-06
I recently switched to Kazekahase as my web browser and I'm likin it a lot. I went to Preferred Applications, selected "Custom" for web browser and entered the following command:

```
kazekahase %s
```

I don't know that the %s does, but it was how all the other browsers were set to open (am assuming it says to open whatever URL was clicked and triggered the browser to open). However, it still doesn't work - it launches fine when I manually open it, but when I click on a link in another app that should open a web page, nothing happens.

Help?

---

### Post by myusername on 2008-04-06
the program should be in /usr/bin just look for the program and it should be set up like this under the command:
/usr/bin/Kazekahase and it should work...if not use a lowercase K

---

### Post by Jugney on 2008-04-07
Thanks for the reply, but I tried this too and it didn't work.

I don't think the path to the file is the issue. I can type in "kazekahase" in a terminal and ubuntu will open up a kazekahase browser. I think it's something to do with the operator "%s" but I don't know how to get it to work.

---

### Post by myusername on 2008-04-07
did you install it through synaptic? try that and it should be one of the options

---

### Post by Jugney on 2008-04-07
I installed it through the Add/Remove feature but it doesn't show up on the list.

---

### Post by myusername on 2008-04-07
uninstall it and install it through synaptic and try...honestly if doing the /usr/bin/appname thing didnt work then i am absolutly clueless

---

