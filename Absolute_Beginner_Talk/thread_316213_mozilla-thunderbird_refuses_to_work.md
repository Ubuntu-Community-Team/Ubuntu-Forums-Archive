---
title: "mozilla-thunderbird refuses to work"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by richardfell on 2006-12-10
I am using ubuntu 6.06 and successfully installed thunderbird. For reasons I do not understand, thunderbird no refuses to work properly. When executed ot locks up. I have removed and re-installed via synaptic but that did not solve the problem. Are there suggestions one might have to solve this problem?

Thanks,
Dick Fell

---

### Post by bollix47 on 2006-12-10
Try opening a terminal and starting mozilla-thunderbird from there.  Post any error messages here.

---

### Post by baekster on 2006-12-10
> **richardfell said:**
> I am using ubuntu 6.06 and successfully installed thunderbird. For reasons I do not understand, thunderbird no refuses to work properly. When executed ot locks up. I have removed and re-installed via synaptic but that did not solve the problem. Are there suggestions one might have to solve this problem?

Thanks,
Dick Fell

I have a similar problem...although I don't know if it's the same problem.  I know mozilla stuff tend to barf when using together with "scim".  But I disabled scim by replacing the environment variables, "GTK_IM_MODULE", "QT_IM_MODULE", "XIM_PROGRAM"...(I use the stock Sunbird this way, and it works).  Also it used to work until this weekend...any help would be appreciated.  

(And I think it might be Thunderbird problem).  I tried the vanilla thunderbird and same result...

jbaek@alibi:~$ mozilla-thunderbird 
GTK Accessibility Module initialized
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 8 --> -1 
(Gecko:18523): GLib-GObject-WARNING **: gsignal.c:1019: unable to lookup signal "activate" of unloaded type `MaiAtkObject'

(Gecko:18523): GLib-GObject-CRITICAL **: g_signal_emit_valist: assertion `signal_id > 0' failed
/usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131: 18523 Segmentation fault      (core dumped) "$prog" ${1+"$@"}

---

### Post by richardfell on 2006-12-11
Thanks to those who replied to my first message. As requested, here is the output when thunderbird was started in a terminal. 

rfell@rosewall:~$ mozilla-thunderbird
DOUBLE-CLICK: 400 --> -1 THRESHOLD: 7 --> -1



When I closed the program, the prompt returned without further output.
Many thanks,
Dick Fell

---

