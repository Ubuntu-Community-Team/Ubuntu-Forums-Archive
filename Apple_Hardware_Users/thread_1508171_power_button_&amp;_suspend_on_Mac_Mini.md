---
title: "power button &amp; suspend on Mac Mini"
date: 2010-06-12
forum: Apple Hardware Users
---

### Post by robertbub on 2010-06-12
When I suspend on my intel-based Mac Mini (running Karmic), I must hit the power button to break out of the suspend.

Is there a way so that I can hit a key on the keyboard or move the mouse to wake the machine out of its sleep?

---

### Post by jnorthr on 2010-06-12
my non-mac minnow wakes up if i tickle  it's enter key, but you might try choosing a different power setting rather than suspend, just to see what happens. are u trying to save power ?

---

### Post by robertbub on 2010-06-13
Yes, I'm trying to save power.

---

### Post by david stevenson on 2010-06-29
Bump.
I also would like to know how to leave my mac mini 3.1 in low power mode and have it wake up on keypress/mouse move.
I note macOSX does this fine on the same machine.
I also note that OSX normally draws 11watts when running and ubuntu draws 19watts.
In both cases machine in use but near idle ( say reading emails ).
Can anyone point me to documentation for the power control options.
David

---

### Post by david stevenson on 2010-07-29
To reply to my own post - for anyone else looking to fix this.
I have found acpitool a command line tool to control many acpi functions.
sudo apt-get install acpitool
Then 
sudo acpitool -w
to see what is enabled
sudo acpitool -W
to change it
I tried enabling items 1 2 3 4 and 5 and now the keyboard wakes the system from suspend. Suspend now draws a little more than it used to, around 2watts instead of 1.9watts.

David

---

