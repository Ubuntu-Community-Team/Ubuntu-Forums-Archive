---
title: "Synaptic Closes"
date: 2006-02-06
forum: Absolute Beginner Talk
---

### Post by dcanizar on 2006-02-06
Hi, I was looking all over these forums for this but can't seem to find it.  It seems that when I click on Synaptic to open it, the windows opens for a second and then closes immediately.  I checked the box to close window after update and now it seems to have bitten me in the rear.  Sorry for the stupid question but I can't seem to find anything that will allow me to get synaptic to stay up again.  Thanks.

---

### Post by engla on 2006-02-06
can you run synaptic in a terminal and look for error messages?

run 'sudo synaptic' in a terminal, and enter your password to run it.

If you see any error messages, post them here.

---

### Post by dcanizar on 2006-02-06
Thanks for replying quickly,  Yeah, I am getting some errors:

(synaptic:8670): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:8670): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
Segmentation fault


Not sure what to make of them.  Thanks.

---

### Post by dcanizar on 2006-02-06
Finally found a post that fixed it:
[http://ubuntuforums.org/showthread.php?t=98039&highlight=synaptic+segmentation+fault](http://ubuntuforums.org/showthread.php?t=98039&highlight=synaptic+segmentation+fault)

---

