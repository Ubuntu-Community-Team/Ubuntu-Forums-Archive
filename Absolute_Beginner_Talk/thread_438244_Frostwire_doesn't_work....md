---
title: "Frostwire doesn't work..."
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by volksolwagen57 on 2007-05-09
it doesn't work ever since i installed beryl. it starts up and and appears to be running but the screen is totally blank. what do i do?

---

### Post by cmost on 2007-05-09
This is a common bug with Frostwire (and Limewire) when Beryl is running.  Here's how to fix it.

First, do the following in a terminal:
code:
sudo apt-get install libgcj7-awt

Next, create a little script to launch Frostwire instead of using the standard launcher.
Howto:
1.  Open up gedit
2.  Paste in the following:
#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/bin/frostwire

or
#!/bin/bash
export AWT_TOOLKIT=MToolkit
export HOSTNAME=localhost
/usr/lib/frostwire/runFrostwire.sh

(or whatever the path to your runFrostwire.sh file...do a search if you can't find it.)

3.  Save the file as "Frostwire_beryl_fix"
4.  Right-click on the file, select properties
5.  Go to the permissions tab and tick the box to allow the file to be executed.
6.  Click 'ok' to accept the changes.
7.  Double-click the file and select 'run', or, create a new launcher with /path/to/Frostwire_beryl_fix.

Enjoy!

---

