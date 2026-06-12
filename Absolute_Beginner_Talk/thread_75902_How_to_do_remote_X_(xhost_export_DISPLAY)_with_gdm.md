---
title: "How to do remote X (xhost /export DISPLAY) with gdm/xdm/wdm...?"
date: 2005-10-14
forum: Absolute Beginner Talk
---

### Post by patrick295767 on 2005-10-14
How to do remote X (xhost /export DISPLAY) with installing gdm/xdm/wdm...?

thank you 

patrick

---

### Post by patrick295767 on 2005-10-14
[QUOTE=patrick295767]How to do remote X (xhost /export DISPLAY) with installing gdm/xdm/wdm...?

thank you 

patrick[/QUOTE]

ERRATA ; Sorry; it should be read WITHOUT installing gdm/xdm/wdm...?

(very sorry of messing in the title of the thread)

---

### Post by jimcooncat on 2005-10-14
For all of these, substitute your own info for stuff shown in *italics*. Machines can be referenced by IP address, or machine name if available. Hopefully I got all this stuff correct.

Easy safe way is to use SSH's X forwarding:
ssh -X *me*@*remotemachine*

Your display will look to the remote machine like:
echo $DISPLAY
localhost:10.0

Some apps, notably firefox, doesn't get the display from the environment, you have to specify it.
firefox --display=$DISPLAY &

-------------------
On a slow connection you use often, it may be worth installing FreeNX for performance. Search "freenx" in these forums for good advice.

-------------------
If you really want xhost /export DISPLAY, I'd advise (and I'm no security guru) to just do this on a local network, not over the internet.

On your local machine:
xhost + *remotemachine*

On the remote machine:
export DISPLAY=*localmachine*:0.0

Firefox, etc.:
firefox --display=*localmachine*:0.0 &

After you're done, remove remote machine access from your xhost:
xhost -

-------------
Note, sometimes you'll see just "xhost +" without a machine name in forum posts. Personally, I wouldn't do that as it means that **any** machine that can see your port 6000 can use your X server.

---

