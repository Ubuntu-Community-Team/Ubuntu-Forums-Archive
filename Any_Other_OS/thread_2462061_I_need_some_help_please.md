---
title: "I need some help please"
date: 2021-05-12
forum: Any Other OS
---

### Post by xssllayers19460 on 2021-05-12
Im kinda new to linux just to get that out the way with,
Im currently try to build a rom/os for my lg g3 d855 and lineageOS has a how to build a os for d855 and when i follow that most of it works but when i get to the repo init command to get to base os i assume it keeps saying syntax error.
 this is what it says--> File "/home/xssllayers19460/android/lineage/.repo/repo/main.py", line 79
Then under that it says file=sys.stderr)
                                                ^
But i have had it to work twice just that the first time my internet was terrible and the second time the power wire somehow fell out &#128514;&#128514;

I have seen some forums about this expect the line 79 bit was different for instance it would say "line 152"
Anyway if someone could help me that would be greatly appreciated&#128591;&#128515;

---

### Post by QIII on 2021-05-12
Thread moved to Any Other OS.

I had debated on moving it to Mobile Technology, but this is an entirely different OS than Ubuntu on mobile.

---

### Post by TheFu on 2021-05-12
This is an extremely specific question about an Android variant and something related to python.  It is a rabbit hole and only someone attempting to do exactly the same thing you are trying to accomplish will be likely to help.

I'd ask this question on the lineageOS forums.  When you do, be very clear on these things:
[LIST]
[*]which Linux OS you are using?
[*]which release of the Linux OS you are using?
[*]which python version you are using?
[*]which lineageOS you are trying to build?
[*]when posting errors, it is best to show the exact command run, describe how the environment was setup - pointing to a how-to guide would be helpful, then show all the relevant output AS TEXT (never images).
[/LIST]
'repo' isn't a normal Ubuntu command, BTW.  I'd guess it is a short-hand 'git' command.  But git isn't written in python, so that doesn't make sense.  git is a DVCS used world-wide by developers who develop in almost any language - C, C++, Ruby, Python, Perl, C#, Java, Javascript, or any of the 500+ other languages.

While Android is based on Linux and uses a Linux kernel, it doesn't "feel" like linux at all without massive addons.

Hope this is helpful.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a beginning Linux book.  The first 10 chapters or so are important for all Linux users on every platform.

---

