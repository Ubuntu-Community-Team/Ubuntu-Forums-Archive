---
title: "automatix"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by spur on 2007-07-16
I receive this error when I try to update apt from command line for automatic install.
'E: Type '“deb' is not known on line 44 in source list /etc/apt/sources.list'
Does any one know why?  I don't think this is actually an automatix problem but an apt one.

---

### Post by vbmds on 2007-07-16
I'd suggest opening up your sources.list and check the automatix repository path.

---

### Post by Outrunner on 2007-07-16
Post the output of ```
cat /etc/apt/sources.list
```cat /etc/apt/sources.list

---

### Post by expatCM on 2007-07-16
At the command line you may want to enter the following 

```
sudo pico /etc/apt/sources.list
```

and then have a look at line #44 and see if there is an obvious problem ....  right now you do not know what is on that line ....

---

### Post by spur on 2007-07-16
I've spotted the problem  there is a " before the word deb on the second last line that I think needs removing. 
I will have to sudo to do that but I'm hopeless with the command line . How do I get to edit the file?

---

### Post by spur on 2007-07-16
I managed to work out how to open gedit as sudo and then opened sources.list in gedit and edited and updated apt with 'sudo apt-get update' all went well. Now I can complete my installation of automatix.
Thanks to all for your prompt replies.

---

### Post by expatCM on 2007-07-16
At the command line - 

sudo pico /etc/apt/sources.list

(this will open sources.list in pico)

scroll down and edit your problem.

Press Control O to write out (save).

Close pico.

enter 

sudo apt-get update.

at the command line

Done

---

