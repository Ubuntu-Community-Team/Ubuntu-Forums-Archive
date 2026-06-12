---
title: "Burnt disk not accessable."
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by JoBangles on 2007-06-20
Hi all ye of Linolage,
Have archived for backup using "tar.gz" , 1.8GB file to dvd which I could not access until with K3b I clicked on "Media Info"  in the listed drives, now I can access disk sometimes when loaded, other times it shows "No medium present" . The second backup disk containing two files approx. 2.1GB could not be accessed at all. I just want to back up some archives. Tried "Simple Backup" all seemed O.K. until I tried to select dvd as backup option.
Thanks in Advance.

---

### Post by FleetAdmiral74 on 2007-06-20
First thing I would do is attempt to use another program. Try burning some data using Gnomebaker and report back.

---

### Post by JoBangles on 2007-06-20
Thanks FleetAdmiral74,

Tried GnomeBaker as root received the following report:

...............................................................................................

grm@HAL:~$ sudo GnomeBaker
Password:
sudo: GnomeBaker: command not found
grm@HAL:~$ sudo gnomebaker

(process:6820): GStreamer-WARNING **: The GStreamer function gst_init_get_option_group() was
        called, but the GLib threading system has not been initialised
        yet, something that must happen before any other GLib function
        is called. The application needs to be fixed so that it calls
           if (!g_thread_supported ()) g_thread_init(NULL);
        as very first thing in its main() function. Please file a bug
        against this application.
libnotify-Message: Unable to get session bus: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

** (gnomebaker:6820): WARNING **: dataproject_add_to_compilation - failed to stat file [/home/grm/Desktop/B1.tar.gz] with ret code [-1] error no [Value too large for defined data type]

** (gnomebaker:6820): WARNING **: dataproject_add_to_compilation - failed to stat file [/home/grm/Desktop/B2.tar.gz] with ret code [-1] error no [Value too large for defined data type]

** (gnomebaker:6820): WARNING **: dataproject_add_to_compilation - failed to stat file [/home/grm/Desktop/B1.tar.gz] with ret code [-1] error no [Value too large for defined data type]

** (gnomebaker:6820): WARNING **: dataproject_add_to_compilation - failed to stat file [/home/grm/Desktop/B2.tar.gz] with ret code [-1] error no [Value too large for defined data type]

** (gnomebaker:6820): WARNING **: dataproject_add_to_compilation - failed to stat file [/home/grm/Desktop/B1.tar.gz] with ret code [-1] error no [Value too large for defined data type]
grm@HAL:~$ 

............................................................................................................

B1 & B2 are 2.1GB

---

### Post by JoBangles on 2007-06-21
I ran gnomebaker in Terminal which reported some glib files missing. Took a guess and used Synaptic to install some glib files and reduced backup files to less than 2 Gig. Works OK now, thanks anyway.

---

