---
title: "Newer than a new thing"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by rob2nd9th on 2005-11-19
Hello - Just got my Ubuntu 5.10 instaled but have no idea how to set up my internet? (managed in on suse 9.3) but did not like suse as my touch pad used to go wild.

Rob
(If you can't go to sea - mend your nets)

---

### Post by erikpiper on 2005-11-19
Um, dialup? DSL? Networked? Wireless? cell phone?

---

### Post by 4plus2 on 2005-11-19
You will probably find that the touchpad will be weird in Ubuntu too (I did) unless you disable tapping and scrolling plus slow things down by applying the follow patch.

sudo gedit /etc/X11/xorg.conf 

and ensure these lines are present in this section:

Section "InputDevice"
Identifier "Synaptics Touchpad"

Option "HorizScrollDelta" "0"
Option "VertScrollDelta" "0"
Option "MaxTapTime" "0"
Option "MaxTapMove" "0"
Option "MaxSpeed" "0.10"

---

### Post by erikpiper on 2005-11-19
Just in case- the "sudo gedit......" thing in the post has to be typed into a terminal- (command line) It is in "Applications-accessories-terminal"

---

### Post by rob2nd9th on 2005-11-19
Sorry iv got Speedtouch adsl - thanks for the touch pad advise will try that later

---

