---
title: "acroread launching problem"
date: 2006-08-20
forum: Absolute Beginner Talk
---

### Post by qsc on 2006-08-20
Hi there,
I just found that I can't lauch acroread from my system. Previously it worked all right. But this evening, I can't open an .pdf file with it, I can't lauch it from Applications button, and I can't launch it from the command line. What's wrong? How can I find it out? Thanks for your time, and feed back.

---

### Post by croak77 on 2006-08-20
When you launch it from a terminal, what error message do you see?

---

### Post by qsc on 2006-08-20
Yeah, I should have said that. No matter which way I take to launch acroread, simply NOTHING happen. From the terminal, it just hold for one or two second before the new prompt symbol appears.

Yesterday, as far as I remember, the only unusual thing that I did with the system is to force the system shut down by turning off the power. At first I let the system go to hibernate, and then I can't find a way to wake it up. So I shut it down in the hard way:(  I am not sure, and can't understand, if this cause the problem.

---

### Post by sjl on 2006-11-07
I have reported this as a bug #70699. In case you'd like to see where this leads (I suspect it leads to absolutely nothing), please see [https://launchpad.net/distros/ubuntu/+source/acroread/+bug/70699]("https://launchpad.net/distros/ubuntu/+source/acroread/+bug/70699") .

In the meanwhile, you can use evince or xpdf to view PDF-files. Or if you really have to fill in some interactive forms, use wine and windows version of Acrobat Reader.

---

### Post by rlozano on 2006-11-07
> **qsc said:**
> Hi there,
I just found that I can't lauch acroread from my system. Previously it worked all right. But this evening, I can't open an .pdf file with it, I can't lauch it from Applications button, and I can't launch it from the command line. What's wrong? How can I find it out? Thanks for your time, and feed back.

why not try to unistall it and try to re-install. there could have been some files that were corrupted along the process that is causing your problem.

just use synaptic and remove completely.

hope this helps

---

### Post by sdhoigt on 2006-11-18
I have the same problem.

Typing acroread on the command line shows the start-up image for a split second, and that's it.

This is what I see:
$ acroread
GTK Accessibility Module initialized
$

I've tried blowing away the ~/.adobe directory and reinstalling, but that hasn't helped.

SD

---

