---
title: "Applications&gt;System Tools&gt;Add Remove Programs..."
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by Error_Msg on 2005-06-23
Starts but doesn't display anything, just that hypnotizing little circle going round and round forever.
How can I fix this?
Also, with some Flash stuff from the web, I don't get any sound unless I do a killall esd. How can I kill esd for good? Are there any undesirable consequences from doing this?
TIA
E_M

---

### Post by andlinux21 on 2005-06-23
don't really know how you kill it for good i am sure you would have to check the startup config files for that. It should do any harm if you edit it out but someone with a bit more knowledge would have to let you know

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=Error_Msg] How can I kill esd for good? Are there any undesirable consequences from doing this?
TIA
E_M[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=10537&highlight=esd](http://www.ubuntuforums.org/showthread.php?t=10537&highlight=esd)

there is how. I don't know what it will do, and I don't know if its reversable...but there is how.

---

### Post by Error_Msg on 2005-06-23
Thanks Poof. I've read the thread and it looks like the remedy could be worse than the disease. I'm tempted by the challenge though...

E_M

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=Error_Msg]Thanks Poof. I've read the thread and it looks like the remedy could be worse than the disease. I'm tempted by the challenge though...

E_M[/QUOTE]

It will be fixed in Breezy.

---

### Post by TristanMike on 2005-06-24
Hi, I also had the same issue with add/remove, to fix it you must downgrade the package python-xdg.  Open Synaptic Package Manager and search for python-xdg.  When you find it you have to Force Downgrade to the original Hoary package.  It has worked for me but be careful when updating that you don't update it with everything else.  Check out here for more info [https://bugzilla.ubuntu.com/show_bug.cgi?id=11871](https://bugzilla.ubuntu.com/show_bug.cgi?id=11871) and check out comment 5.
Hope that helps
TristanMike

---

### Post by Error_Msg on 2005-06-24
BINGO!
2 for 1 Tristan, what a deal!

E_M

---

### Post by Error_Msg on 2005-06-24
[QUOTE=poofyhairguy]It will be fixed in Breezy.[/QUOTE]

Breezy...ahhhh, sounds much better than grey porcupine!

E_M

---

