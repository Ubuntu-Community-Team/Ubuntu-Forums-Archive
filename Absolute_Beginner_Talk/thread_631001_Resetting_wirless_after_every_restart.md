---
title: "Resetting wirless after every restart"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by HappyEisentrout on 2007-12-03
Every time I restart my laptop I need to set up my wireless card all over again.  It's not too big of a problem as I've memorized the code that i need to put in everytime, but is there anyway of making it just activate everytime i turn on my computer?

---

### Post by Sarteck on 2007-12-04
Well, what type of card is it, and what do you do now to get it running?

---

### Post by NullHead on 2007-12-04
What driver are you using? ndiswrapper ? bcm43xx?

---

### Post by HappyEisentrout on 2007-12-04
well i've had to actually use both to get it to work.

---

### Post by NullHead on 2007-12-04
wow ... well I would do the following. 

edit /etc/rc.local ```
sudo nano /etc/rc.local
```
add the line ```
sudo modprobe ndiswrapper(or bcm43xx ... witch ever you prefer) 
```
and press ctrl+x and then press "y" and then press "enter" then the driver should load up automatically when the computer loads up.

---

### Post by HappyEisentrout on 2007-12-04
where exactly do i add that last line?

this is what it says:

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

exit 0


where do i add it?

---

### Post by NullHead on 2007-12-04
In the middle of the #s and before the exd 0 ... just copy in modprobe "driver"  and it should load up.

---

### Post by HappyEisentrout on 2007-12-04
I still have to manually load it up

---

### Post by dje on 2007-12-04
Hi
have a look [here]("http://www.ubuntu1501.com/2007/07/akabreks-fix-for-people-having-trouble.html"). hope that helps :)

---

