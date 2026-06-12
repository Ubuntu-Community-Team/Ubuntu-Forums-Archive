---
title: "problem installing java runtime..."
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by mstrchfmjolnirty on 2008-04-10
I have been trying to install the java runtime for a few hours now and I started by going to Add/Remove Programs and found the Sun Java 5.0 runtime I click it and go into installing it but it pops up an error that says: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
i went into terminal and copied dpkg --configure -a into it and it got an error that said: 

dpkg:  requested operation requires superuser privalage....

not sure what to do here at all

---

### Post by wolfen69 on 2008-04-10
```
sudo dpkg --configure -a 
```make sure to put sudo in there.

---

### Post by mstrchfmjolnirty on 2008-04-10
sweet action...i got that bt now...what do i do with that?, sorry about my incompetence im fairly new to linux

---

### Post by stchman on 2008-04-10
> **mstrchfmjolnirty said:**
> I have been trying to install the java runtime for a few hours now and I started by going to Add/Remove Programs and found the Sun Java 5.0 runtime I click it and go into installing it but it pops up an error that says: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.
i went into terminal and copied dpkg --configure -a into it and it got an error that said: 

dpkg:  requested operation requires superuser privalage....

not sure what to do here at all

To install Java follow this step:

```
sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin
```

If you want Java 1.6 substitute 6 for 5 in the above statement.

---

### Post by mstrchfmjolnirty on 2008-04-10
alright i tried this way now, and it came up with the same error message but in the terminal....it also may be reasonable to note that i attempted to install the limewire package earlier and as it was on the "installing java runtime environment" step it completely froze at about 50%....so idk if theres files left over causing this or what...

---

### Post by MasterCylinder on 2008-04-20
Hey, I am having similar problems installing Java, I followed the code 

[QOUTE]sudo apt-get -y install sun-java5-bin sun-java5-fonts sun-java5-jdk sun-java5-jre sun-java5-plugin[/QOUTE]

and after that finishes I get this weird message thing in the console 

"Configuring sun-java6-bin" at the bottom of the thing, looks like something from DOS. It has a  <Ok>  at the bottom... but I cant push it or do anything along those lines... help?

Here is a screenshot of the window that it displays

---

### Post by tangibleorange on 2008-04-20
that thing you are getting in the terminal is perfectly normal. it's simply a license Sun requires you to accept in order to use the JRE. Just scroll down to the bottom (down arrow key) and press enter when you are highlighted over "OK".

---

### Post by bdailey on 2008-04-20
Like DOS you can use your arrow keys and the enter key to navigate the menus you get. Try pressing the right arrow key to get from the scroll to the ok. Hope this helps.

---

