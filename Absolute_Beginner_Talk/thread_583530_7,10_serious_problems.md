---
title: "7,10 serious problems"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by guiltymilkshake on 2007-10-20
Hi, I just installed 7.10 yesterday. Every time I start it up everything is fine but after a while I cant open up any programs, and every time I open up a folder I get a "The folder contents could not be displayed." I have the desktop version on a 64 bit system. Any help you can give me would really help a lot seeing as how this is getting annoying having to restart after about 1-2 hours after it being on.

---

### Post by Thumper! on 2007-10-20
did you download the 64 bit OS? or just the standard one?

---

### Post by guiltymilkshake on 2007-10-20
Im pretty sure I downloaded the 64 bit OS


is there anyway to check after the fact?

---

### Post by guiltymilkshake on 2007-10-20
anybody? this is a seriously annoying problem.

---

### Post by Jermski on 2007-10-20
When booting up the kernel selections should show (64 bit) next to them.

---

### Post by chalex on 2007-10-20
or you can type 'uname -a'

e.g. mine says: Linux e521 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

If it was 32-bit, the 'x86_64' would say 'i586' or something like that.

Are there any unusual messages in /var/log/syslog?  Are you sure your hardware works fine?

---

### Post by guiltymilkshake on 2007-10-20
2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64 GNU/Linux

thats what it says so I guss its a 64 bit




and for some reason when I try to open syslog it wont open at all. It just says its opening and then it dissapears off the task bar

---

### Post by guiltymilkshake on 2007-10-20
alright I opened up the system log file and wouldnt even know how to read it. So much information. 


I did see this though


Oct 20 16:17:37 chris-laptop gdmgreeter[5537]: Gtk-CRITICAL: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed 
Oct 20 16:17:37 chris-laptop gdmgreeter[5537]: Gtk-CRITICAL: gtk_tree_selection_unselect_all: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Oct 20 16:17:37 chris-laptop gdmgreeter[5537]: Gtk-CRITICAL: gtk_tree_selection_select_iter: assertion `GTK_IS_TREE_SELECTION (selection)' failed 
Oct 20 16:17:37 chris-laptop gdmgreeter[5537]: Gtk-CRITICAL: gtk_tree_view_scroll_to_cell: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

---

### Post by Officer Dibble on 2007-10-20
Are you dual booting? If so, does it happen with your other OS?

There is also the coincidental possibility of your beginning to have some thermal issues with your hardware too. Have you made any hardware changes recently or just had a look in your case that may have caused a disturbance in your systems airflow or power demands?

What are your system specs, please? Have you made any changes to anything other than just installing Gutsy?

---

### Post by MockY on 2007-10-22
Just want to say that you are not alone with this issue. After only 20 minutes of use (sometimes longer and sometimes shorter), nothing can be accessed. No folder or drive. The error message looks like this:

[IMG]http://www.sotd.se/Screenshotnautilus.png[/IMG]

This does not happen with Feisty and the system runs cool. So it seems like we found am annoying bug in a supposed stable release which makes the OS impossible to run. So it seems like all we can do is wait another 6 months and hope the issue is resolved by then and use Feisty until then.

Sidenote, I run the 32 version

---

