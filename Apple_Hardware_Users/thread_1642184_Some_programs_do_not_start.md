---
title: "Some programs do not start"
date: 2010-12-10
forum: Apple Hardware Users
---

### Post by fleeze on 2010-12-10
Hi,

I am using ubuntu 10.10 on a 12 inch PowerBook G4.  Everything runs well except for a strange issue: some programs do not start.  For example, System->Administration->Users and Groups.  When I select it from the menu, I see that it does try to start up, but after a few seconds nothing happens.

The other program that does not start for me is Applications->Internet->Empathy Internet Messaging.

Most other programs starts up fine.

Can anyone help me with this?

Many thanks!

---

### Post by sikander3786 on 2010-12-10
Welcome to the forums :-)

Go to Terminal (Applications > Accessories) and try starting your programs from the command line.

```
users-admin
```

```
empathy
```

You might see some error messages. Post them here ;-)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

### Post by fleeze on 2010-12-10
Ah.... ok, it looks like a pretty silly error:

```

GLib-GIO-ERROR **: Settings schema 'org.gnome.system-tools.users' is not installed

aborting...
Aborted


```

For some reason, the menu option is there but the program is not installed!?

So I suppose all I need to do is install it?  (duh)

Thanks a lot for your help........

---

### Post by sikander3786 on 2010-12-10
I see, it might be a bug on PPC Ubuntu.

[http://ubuntuforums.org/showthread.php?t=1616980](http://ubuntuforums.org/showthread.php?t=1616980)

---

### Post by Ksiazkowicz on 2010-12-10
Ubuntu 10.10 PowerPC bug. After updating from Lucid, ALSA stopped working properly (headphone detection), and this error, or "Illegal instruction" (but I think, it's because of mess, that I've made, trying to get ALSA work).

Install Ubuntu 10.04 - there everything is working fine.

---

### Post by fleeze on 2010-12-10
After searching around a bit more, I found this bug report:

[https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/672873](https://bugs.launchpad.net/ubuntu/+source/glib2.0/+bug/672873)

Which contains a fix to the problem.  I've verified that it resolves this issue completely.

Thanks so much for both of your inputs!!
:p

---

### Post by sikander3786 on 2010-12-11
Glad to know that you found the fix :-)

You can mark this thread Solved using **[COLOR="Red"]Thread Tools[/COLOR]** near the top of this page so it may be beneficial to some other PPC users as well.

Happy Ubuntu-ing!

---

