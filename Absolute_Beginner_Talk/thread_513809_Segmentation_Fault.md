---
title: "Segmentation Fault"
date: 2007-07-30
forum: Absolute Beginner Talk
---

### Post by nhandler on 2007-07-30
When I first started using Ubuntu, I often got segmentation faults when trying to launch a program from the terminal. After a few weeks, they stopped. All of a sudden, they came back. I went to launch audacity from my applications menu, and it wouldn't launch. So I then tried launching from the terminal. Here is the output:
> (audacity:18792): Gtk-CRITICAL **: gtk_widget_ensure_style: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault
 

I get that error with and without sudo (I know not to run programs as sudo normally). I have tried removing and reinstalling audacity using apt-get numerous times. I have also used the purge option. None of these things work. I'm running gutsy, so I have the newest version of everything. Any ideas on how to fix this?

---

### Post by DBStevens on 2007-07-30
That is why it is called testing,  I'd check launch pad and see if it has been reported if not report it.

---

### Post by heimo on 2007-07-30
> **Cheater said:**
>  I'm running gutsy, so I have the newest version of everything. Any ideas on how to fix this?

Try strace, see where it hangs, ask other test users if they can reproduce it (also search forums), if it's repeatable, file a bug report.

---

### Post by heimo on 2007-07-30
> **DBStevens said:**
> That is why it is called testing,  I'd check launch pad and see if it has been reported if not report it.

And here it already is:
[https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/128542](https://bugs.launchpad.net/ubuntu/+source/audacity/+bug/128542)

---

