---
title: "ndisgtk  won't run"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by spectrum48k on 2007-06-24
Ndisgtk has stopped running on my machine. So I completely removed the whole ndiswrapper suite and reinstalled...still the same problem.
I really don't want to go back to microsoft but gees this is hard work!
I just want to get my Wireless net work card to work!!

---

### Post by BobCFC on 2007-06-24
You described it as opening for a second and then closing.... if you try running it by opening a  terminal and typing ndisgtk you should be able to read any error messages.  Then you can paste anything juicy into google.

---

### Post by tava0002 on 2007-07-11
Same thing for me I am running the latest version of Xubuntu.  I also have a problem running network-manager, it clearly has to do with gnome, do I have to install gnome if it's not already?

I'm trying to install the Windows drivers for a Proxim/Orinoco gold card to see if they are better than the built in drivers.

Here's what I get when trying to run ndisgtk from command line:

(ndisgtk:5452): libglade-WARNING **: Could not load support for `gnome': libgnome.so: cannot open shared object file: No such file or directory
Traceback (most recent call last):
  File "/usr/bin/ndisgtk", line 309, in <module>
    NdisGTK()
  File "/usr/bin/ndisgtk", line 111, in __init__
    self.setup_driver_list()
  File "/usr/bin/ndisgtk", line 140, in setup_driver_list
    self.get_driver_list()
  File "/usr/bin/ndisgtk", line 168, in get_driver_list
    driver_name = p.search(line).group()[:-1]   # strip trailing space
AttributeError: 'NoneType' object has no attribute 'group'

---

### Post by tava0002 on 2007-07-11
Fixed in .07, whatever that means

[https://bugs.beta.launchpad.net/ubuntu/+source/ndisgtk/+bug/103477](https://bugs.beta.launchpad.net/ubuntu/+source/ndisgtk/+bug/103477)

---

