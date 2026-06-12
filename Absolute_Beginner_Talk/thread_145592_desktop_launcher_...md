---
title: "desktop launcher .."
date: 2006-03-16
forum: Absolute Beginner Talk
---

### Post by mlind on 2006-03-16
Can I specify "working directory" for a custom desktop launcher?
Like a path where launcher command is executed.

I'm trying to create launcher for Neverwinter Nights startup script (called nwn),
but this script needs to excedute on NWN's main directory.

---

### Post by Perfect Storm on 2006-03-16
Create a new document eg. where nwn is install and save it as nwnstart.sh

Open it and write:
> #!/bin/bash

cd /bla/bla/bla/nwn

sh /bla/bla/bla/nwn/nwn


Then chmod +x nwnstart.sh

Now make a launcher that point to the script.

---

### Post by mcduck on 2006-03-16
[QUOTE=mlind]Can I specify "working directory" for a custom desktop launcher?
Like a path where launcher command is executed.

I'm trying to create launcher for Neverwinter Nights startup script (called nwn),
but this script needs to excedute on NWN's main directory.[/QUOTE]
I think you could use something like this in your launcher: 'cd /path/to/nwn && sh nwn'

---

### Post by mlind on 2006-03-16
thanks guys, I got it working.

---

