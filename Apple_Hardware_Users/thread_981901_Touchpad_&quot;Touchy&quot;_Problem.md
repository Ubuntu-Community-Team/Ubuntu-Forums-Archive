---
title: "Touchpad &quot;Touchy&quot; Problem"
date: 2008-11-14
forum: Apple Hardware Users
---

### Post by clucas on 2008-11-14
I've read tons of posts concerning the Touchpad on the MacBook but haven't found a problem such as mine. If I am moving the cursor up or down by running my finger up or down in the middle of the pad on a web site or anywhere, just the desktop even, the text will become highlighted or a program will open or an item will be moved. It's as if I'm left-clicking to highlight text or holding down to move something or even right-clicking to open something. I'm using Ubuntu 8.1. Can someone help?

---

### Post by ghosthand on 2008-11-14
I think I'm having a problem similar to yours.  If you run `xinput list-props appletouch` in a terminal you can see a lot of options to tweak.  If anyone out there can explain what all these different properties do I would appreciate it.

---

### Post by cyberdork33 on 2008-11-16
First, just a nit-pick, there is no Ubuntu 8.1... There is an Ubuntu 8.10 though.

Please check the information in the "Before You Post" link in my signature to find the proper documentation for your Mac.

---

### Post by clucas on 2008-11-16
First, the word is "nitpick" not "nit-pick". :)

But thanks. I will follow up with making the changes per the documentation.

---

### Post by clucas on 2008-11-16
I followed the MacBook_Santa_Rosa Documentation for fixing the Touchbad by adding to the xorg.conf file. But that didn't help. Again, when I move the cursor on the desktop it's as if I'm left-clicking to drag something and then releases on it's own.

---

### Post by clucas on 2008-11-17
Found the solution.

I went to System...Preferences...Mouse...Touchpad tab...and unchecked the "Enable mouse clicks with touchpad". Works like a charm!

---

