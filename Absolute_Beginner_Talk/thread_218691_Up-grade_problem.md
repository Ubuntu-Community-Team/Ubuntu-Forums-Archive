---
title: "Up-grade problem"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by sarum on 2006-07-18
Hi, I've followed these infos: to upgrade

To perform the upgrade: 
1.Update your system to ensure that you have the latest version of Update Manager and associated packages. The necessary versions are available from the breezy-updates repository, which is enabled by default. 
2.Run the following command (either via ALT-F2 or a terminal): 
gksudo "update-manager -d"
The "-d" switch instructs Update Manager to consider pre-release versions, including this Beta release. Without this switch, only official, final releases will be considered. 

And got this reply

fawcett@ubuntu:~$ gksudo "update-manager -d"
Reading package lists... Done
Building dependency tree... Done
(synaptic:9749): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion ` gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9749): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion ` gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(synaptic:9749): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET ( widget)' failed
Reading package lists... Done
Building dependency tree... Done
fawcett@ubuntu:~$ ==

I dont understand quite what it all means and I wonder if anyone can help please. Breezey does all I want it to do and am wondering if a Newby upgrade is worth the risk. My thanks to all who may reply...Sarum.

---

