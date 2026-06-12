---
title: "waking from suspend, several deamons are not resuming"
date: 2008-02-14
forum: Apple Intel Users
---

### Post by wahr on 2008-02-14
I've noticed after a week of use that several daemons are not resuming after suspend.

Specifically, hal backlight keypad support breaks and samba dies.  I haven't moved beyond basic exploration and customization, so god knows what else is dying upon resume.

After some research, I found a reference to this. granted this is very old, but I figure I should mention it in case it hasn't been fixed?:

[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/72287/comments/6](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/72287/comments/6)

> It turns out that on suspend/resume, the backlight control register is clobbered to all-zeros.

The only way to fix this is to use vbetool to save/restore the BIOS state. This is currently broken on the macbook due to the init scripts being out of order (vbesave runs before acpid, and on macbook this causes vbesave to fail to detect that we're a laptop).

anyway, can someone help me fix this problem.

running 2.6.24-rc5macbook hardy kernel posted in deb package from this forum

---

### Post by GXP on 2008-02-14
I have had issues with samba in 6.06 and 6.10. I resolved my issue by creating a script to stop samba in directory:

```
/etc/acpi/suspend.d
```

Be sure to make this file executable or it won't work ;) Took a few suspends before I realized what I forgot to do.

Then I added another script in directory:

```
/etc/acpi/resume.d
```

to restart samba.

I would provide you with the numbers, which are the order the scripts are processed in, but cannot remember and my laptop is in suspend at home. If you use winbind include that in the same script too, in my experience winbind acts funny if I don't restart it after restarting samba, but ymmv.

---

### Post by wahr on 2008-02-14
thanks for the samba workaround, but the brightness keys dying is my biggest issue.  any ideas?

---

### Post by GXP on 2008-02-15
Took a look at the bug report and the file that was attached to it - 'c' code it is a bit over my head and I don't have a mac.

Did you try contacting the author of the bug Ryan Lortie and ask him how to compile his patch and where to put it? I don't do much c compiling so I am not very familiar with it.

Wish I had a better answer for you.

Another thought, and just a thought. What if you moved the scripts that start with 15- and 17- in /etc/resume.d directory to after the 72- or 98- . You may only need to move 17- but not sure.

Does it work OK after an initial boot? Just suspend and Hibernate cause problems?

FYI - After 1pm EST today (2/15) I won't be able to respond again until Wed 2/20.

---

### Post by wahr on 2008-02-16
its definitely a suspend only issue.

I've been experimenting around with the scripts, but with no luck.. It could be my ineptitude at scripting, or a serious lapse in system services., though I'm leaning toward the former.

---

### Post by GXP on 2008-02-28
Sorry for taking so long to reply back - been in training...

When you state "hal backlight keypad" in your original post are you meaning those as three separate processes - could you clarify? Not having a mac I am flying blind... So does the monitor backlight not work - and possibly the keyboard?

---

