---
title: "Auto-Troubles"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by isaacj87 on 2007-07-15
**Sorry! I meant to title the thread "Auto-apt troubles"**

I recently installed auto-apt to help with compiling. This is what I did exactly:

I was compiling the src for Clutter

I ran this command within the folder:

> auto-apt run ./configure

Then all this dialog boxes came up at an overwhelming pace. So I close all the terminal windows and interrupted the process. Then I ran:

> sudo dpkg --configure -a

I'm guessing to correct the interruption. But everytime I do so I get this message and auto-apt doesn't work.

> cat: /selinux/policyvers: No such file or directory
Compiling policy ...
policyvers value 0 not in range 15-21
usage:  /usr/bin/checkpolicy [-b] [-d] [-M] [-c policyvers (15-21)] [-o output_file] [input_file]
make: *** [/etc/selinux/./policy/policy.] Error 1
dpkg: error processing selinux-policy-default (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 selinux-policy-default


What is this and what does this mean...I remember it asking me about install something related to selinux-policy-default, but since I assumed this had no relevancy to what I was doing (clutter???) I immediately closed it. How is this fixable...is it even fixable?

**UPDATE:** I use "dkpg" to remove "selinux-policy-default"

---

