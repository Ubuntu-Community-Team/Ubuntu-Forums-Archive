---
title: "make a program start on ubuntu startup"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by hockeyfighter09 on 2007-11-22
how do i make the checkgmail program start up when ubuntu starts up?

---

### Post by jordanmthomas on 2007-11-22
system --> preferences --> sessions
go to the "startup programs" tab and add checkgmail

---

### Post by hockeyfighter09 on 2007-11-22
what command do i type in to make it work?  It doesnt seem to show up on the list when i click on the current session tab.

---

### Post by fastTalker on 2007-11-22
you should have added the "checkgmail" command to list in the "Startup Programs" tab.  You will have to log out and log in for it to run the command automatically.   The "Current Session" tab shows all the processes that are running currently.

---

### Post by hockeyfighter09 on 2007-11-22
im trying to do that, but I dont know what to type in the command section when I am trying to add it to the list. Where it asks you to write the Name, Command, and Comment. What do i type into the command section?

---

### Post by fastTalker on 2007-11-22
checkgmail

---

### Post by rahimveron on 2007-11-22
In The Name Section enter "Check GMail" or anything you desire
Command section enter ```
checkgmail
```
Comment, anything you want, like "Checks Gmail for new mails"

---

### Post by hockeyfighter09 on 2007-11-22
thanks for the reply, this is what i was looking for. :guitar:

---

### Post by shuttleworthwannabe on 2007-11-22
this is such a basic question: How does one know what the application names are (as they appear in synaptic), unless one has a list to choose from? A simple spelling error, let alone case-senstive names, will not run the app. also some apps need a % sign infront; I have seen this in the properties.

Sorry to ramble, but would be great if there was a place to check the names, spelling, case-sensitivity, etc; I know there is synaptic and all, but, a system that would automagically recognize as you type and then select the one that one wishes.

Anyway, to answer your Q: type [COLOR="Red"]checkgmail[/COLOR] in the command section

---

### Post by MrFSL on 2007-11-22
It would appear that the command to start checkgmail is:

```
checkgmail
```

---

### Post by rahimveron on 2007-11-22
> **shuttleworthwannabe said:**
> this is such a basic question: How does one know what the application names are (as they appear in synaptic), unless one has a list to choose from? A simple spelling error, let alone case-senstive names, will not run the app. also some apps need a % sign infront; I have seen this in the properties.

Sorry to ramble, but would be great if there was a place to check the names, spelling, case-sensitivity, etc; I know there is synaptic and all, but, a system that would automagically recognize as you type and then select the one that one wishes.

Anyway, to answer your Q: type [COLOR="Red"]checkgmail[/COLOR] in the command section

Yes i agree with you . But in most cases its quite straightforward like amarok, exaile or firefox,etc.

---

### Post by rahimveron on 2007-11-22
> **hockeyfighter09 said:**
> thanks for the reply, this is what i was looking for. :guitar:

UF is very freindly :)

---

