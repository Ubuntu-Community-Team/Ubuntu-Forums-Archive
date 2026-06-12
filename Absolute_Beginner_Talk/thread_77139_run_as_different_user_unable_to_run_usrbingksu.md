---
title: "run as different user: unable to run /usr/bin/gksu"
date: 2005-10-16
forum: Absolute Beginner Talk
---

### Post by red_Marvin on 2005-10-16
I have recently upgrased from hoary to breezy.
Sometimes when i'm logged in another person want's to f.x. check his/her mail,
with hoary that was easy to do with "run as different user", however now it seems
to get an error:
"Unable to run /usr/bin/gksu: The file or folder does not exist" (translated)
I tried to *re*install the following packages through synaptic (to eliminate any installation problems.)
[LIST]
[*]gksu
[*]libgksu1.2-0
[*]libgksuui1.0-0
[/LIST]
But that didn't solve anything. Also when I checked /usr/bin I found the following programs:
[LIST]
[*]gksu
[*]gksudo (which is arrow-marked, whatever that means)
[*]gksuexec
[/LIST]

When i run gksudo I get the error
> # gksudo -u username evolution
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(evolution:13092): Gtk-WARNING **: cannot open display:


and it makes no difference wether or not I put quotes around user and/or evolution or not...

---

### Post by irifan on 2005-10-16
Hi,

i can´ t help you with gksudo, but you might try $sudo instead. when using the commandline, you can also change the user with $su username. Use $exit to return to your regular user.

---

### Post by mfobrien on 2005-10-28
Hi, I am getting the same error when trying to use the "Run as different user" option from the Applications menu.  The error says "unable to run /usr/bin/gksu no such file or directory", but it is clearly there. It worked fine before upgrading from Hoary to Breezy.  Is this a known issue?  Thanks.

Mark

---

### Post by Tiede on 2005-11-28
Hi everyone. I am having a slightly different problem with the "run as different user" option. When I click on it, it does open and let me put the program I want to use, but when I press on ok, the system appears to be working for about half a second, and then nothing; the application does not come up, nor do I get an error message.
Is anyone else esperiencing this problem?

---

### Post by Mustard on 2005-11-28
I just tried it on my copy of breezy and when I did it, it brought up a dialog telling me that I needed to set a password for the default keyring, as it didnt currently have one.  I then entered a password and repeated the command and it worked for me, so I haven't been able to recreated the problem unfortunately.

---

### Post by ssam on 2005-11-28
[QUOTE=red_Marvin]I have recently upgrased from hoary to breezy.
Sometimes when i'm logged in another person want's to f.x. check his/her mail,
with hoary that was easy to do with "run as different user", however now it seems
to get an error:
"Unable to run /usr/bin/gksu: The file or folder does not exist" (translated)
I tried to *re*install the following packages through synaptic (to eliminate any installation problems.)
[LIST]
[*]gksu
[*]libgksu1.2-0
[*]libgksuui1.0-0
[/LIST]
But that didn't solve anything. Also when I checked /usr/bin I found the following programs:
[LIST]
[*]gksu
[*]gksudo (which is arrow-marked, whatever that means)
[*]gksuexec
[/LIST]

When i run gksudo I get the error


and it makes no difference wether or not I put quotes around user and/or evolution or not...[/QUOTE]

from that error it looks like X is refusing the connection from evolution.

try running
```
xhost +
```
first.

this allows anyone to connect to your x server.

if this work then you will need to read

```
man xhost
```
and work out a secure way of doing (only allowing local connections)

---

### Post by zaphod_es on 2005-11-29
Try using gksuexec. In my Kubuntu 5.10 there is an entry for it in "Kmenu/System/Run as different user"

This brings up a username and program name fields. This works on most programs but not, for instance kate (I use gedit). It can also bring up Konqueror from where you can  open kate. Yes I know that it is a really bad idea to run Konqueror as root.

---

### Post by porter on 2005-12-18
i've got the same problem trying to run firefox and nautilus as another user. anyone find a solution?

---

### Post by porter on 2005-12-31
anyone?

---

### Post by Omnios on 2005-12-31
Think you have to go into groups and give that user sudo rights. Not shure though as I was just checking out permitions and not trying any changes.

 Look what your sudo bin/bash thingy is and try setting the user as the same?

---

### Post by porter on 2006-01-03
??? no change, i added the admin rights but no change, still getting the same error.

---

