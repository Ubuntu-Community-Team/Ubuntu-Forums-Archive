---
title: "Edubuntu LTSP Mac thin client"
date: 2006-07-27
forum: Apple PPC Users
---

### Post by jrobinson5 on 2006-07-27
Hi, this seemed like an obvious question, but I couldn't find the answer anywhere. Is it possible to use Apple computers as thin clients in Edubuntu? If so, is there anything special you should know?

---

### Post by navilon on 2006-07-28
It is, but it depends on the architecture of your processor. What type of mac do you have?

---

### Post by jrobinson5 on 2006-07-28
I don't have one already, I just wanted to know in case someone offers to donate one.

---

### Post by avtolle on 2006-07-28
I think if the potential donated Mac is a "new world" mac, it should work; if it is an "old world" mac, it may or may not, depending on the ability to use Boot-X, e.g. I know this may be too simplistic, so others with more knowledge please chime in; I may be faced with a similar issue in the future.

---

### Post by jrobinson5 on 2006-07-28
From what I gathered from Wikipedia, the "new world" firmware is used by PPC iMacs and later, while the "old world" is used by those before. Is this correct? So are you saying that thin clients can use different processor architechtures than their servers?

---

### Post by navilon on 2006-07-28
That is a very good question. I think that the arch must be the same as the server.

---

### Post by jrobinson5 on 2006-07-30
Yeah, OK. That's what I figured, but then I thought (excuse me for butchering the terminology) that you could run the PPC X server and it would communicate with the x86 software on the server. So, does this mean one would have to run the 32-bit version of Edubuntu on his/her 64-bit server if all the thin clients were 32? 

Also, I hope I'm not changing the subject to something completely unrelated, but eBay seems to be flooded with [these]("http://cgi.ebay.com/KeyTronic-ClienTerm-2001-Thin-Client-Terminal-NEW_W0QQitemZ300012274081QQihZ020QQcategoryZ11175QQrdZ1QQcmdZViewItem") cheap thin clients. Is there any way whatsoever to use these with Linux?

EDIT: [This]("http://www.ubuntuforums.org/showthread.php?t=113398") seems like it might be the answer to my last question.
Another edit: The ebay page I linked to seemed to indicate it used rj-11 networking, so nevermind on that one.

---

### Post by 3rdalbum on 2006-07-30
I thought that you'd be able to have a PPC thin client communicating with the x86 server, as it's just the X protocol; but I have heard that it *is* architecture-dependent for some reason.

---

### Post by dvenardos on 2007-10-15
> **3rdalbum said:**
> I thought that you'd be able to have a PPC thin client communicating with the x86 server, as it's just the X protocol; but I have heard that it *is* architecture-dependent for some reason.
The thin client can be a different architecture from the server, the server contains a mini-kernel for each architecture that is supported. Check out the Edubuntu Wiki.
I am looking for instructions on how to setup the macs, apparently you use yaboot.

---

