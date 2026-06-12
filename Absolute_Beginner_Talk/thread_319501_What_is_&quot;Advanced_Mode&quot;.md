---
title: "What is &quot;Advanced Mode&quot;"
date: 2006-12-15
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2006-12-15
I have been attempting to install GnomeSword2  (bible program) into Ubuntu, edgy eft and receive the following
----------
Cannot install 'gnomesword'

This application conflicts with other installed software. To install 'gnomesword' the conflicting software must be removed before.

Switch to the advanced mode to resolve this conflict.
-------------

Where and How do I switch to the "Advanced mode" ?
Once switched to the advance mode, what do I look for and do?

Walk me through this slowly. . .

---

### Post by Iarwain ben-adar on 2006-12-15
Hiya chaplanger,
welcome :wink:

First of all,
i think that advanced mode means terminal fun.

So fire up your terminal,
and type in
```
sudo aptitude install gnomesword2
```

Normally it should work :D


Iarwain

---

### Post by mcduck on 2006-12-15
That means Synaptic Package Manager, it's in System/Administration/Synaptic Package Manager.

Open that, click 'reload' to update info about available applications, then 'search' to search for the app you want to install. When you've found it right-click and select 'Mark for Installation'. You can select as many at the same time as you want. When you are ready, click 'Apply' and Synaptic will install all those apps for you.

[How to install *ANYTHING* in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by chaplanger on 2006-12-15
Found the Synaptic Package Manager, but when I seek to install this way I get the following error
-----------
gnomesword:
 Depends: libsword5c2a (>=1.5.8-7) but it is not installable
----------
I have no clue what this means -- any translation of what I need to do next?

Thanks

---

### Post by jhochrein on 2006-12-28
I am having the exact issue.  Any resolution on this issue yet?

Thanks

---

