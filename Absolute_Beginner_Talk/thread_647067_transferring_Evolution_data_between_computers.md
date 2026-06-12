---
title: "transferring Evolution data between computers"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by aam-aadmi on 2007-12-21
Hi,

I am trying to shift all my evolution mail client data from one computer to another. I searched the evolution FAQs and found this very helpful advice:

> How can I transfer all my Evolution data between computers/to a new partition/to a new computer?

Make sure you haven't started Evolution on the new computer/new partition yet. First of all, shut Evolution and its background processes (Evolution Data Server, Evolution Alarm Notify) completely down by using evolution --force-shutdown. Then copy the contents of $HOME/.evolution/, $HOME/.gnome2_private/Evolution, $HOME/.camel_certs. Then dump your Evolution settings stored in GConf by running gconftool-2 --dump /apps/evolution > some-file.xml where some-file.xml is the name of the file the information is written to. On the new computer, make sure you are not running gconf (by ps ax | grep gconf for example; you normally have to leave gnome for that and then run gconftool-2 --shutdown). Then import those settings by running gconftool-2 --load some-file.xml and log in to gnome again.

The first line says "Make sure you haven't started Evolution on the new computer/new partition yet"; but I have already started Evolution on the new computer. So, now what do I do?

Should I uninstall evolution and re-install it and then follow the above advice? Any other suggestions.

Aam-aadmi

---

### Post by blueridgedog on 2007-12-22
Since no one has replied, I will hazzard a guess.  I suspect you could simply shut down evolution on the new machine, then do the migration per the documents.  If it fails for some reason, you still have the option of uninstalling/reinstalling.

---

