---
title: "From freash install -&gt; Eclipse working with Sun's JDK 1.5"
date: 2005-05-26
forum: Absolute Beginner Talk
---

### Post by kentl on 2005-05-26
Hi!

I hope that I do not offend someone by creating this thread, as both issues of how to install Eclipse and Sun's Java SDK 1.5 has been discussed.

Then why do I create another thread? As a new user I really must say that I am confused on how to proceed. As a lot of the suggestions in the threads/web pages are quite different.

First of all, what I do have: A working fresh install of Ubuntu Linux 5.04
What I have done so far: Nothing at all!

From what I have read (and as I said above, I have read the previous material I found around these forums) it seems like these things has to be done (in the given order):

[list=1]
[*] Install Sun's SDK version 1.5
[list=0]
[*] Find the SDK, add a repository and just use apt for a nice and simple install?
[*] Download directly from Sun? And how install in that case?
[*] Get it to work as a plugin for FireFox, to execute Java applets?
[/list]
[*] Install Eclipse
[list=0]
[*] Find Eclipse, add a repository and just use apt for a nice and simple install?
[*] Download directly from its home page? And how install in that case?
[*] Will it detect the installed Java SDK and use it?
[/list]
[/list]

The above questions have been answered one way or another around the forums, but quite differently.

It seems to me like it would be best if I could install both as packages through apt, so that I can easily get updates. But I am the novice and you are probably (if qualified to answer) a lot more experienced using Ubuntu and Linux than me.

If we get some nice defenite answers that people think are good (and easy to follow). Then perhaps this could act as a guide for future questions?

A last question is how to get J2ME going, but I'll save it for later in case it gets to complicated for one thread otherwise.

Best regards,
Kent - A confused novice eager to learn

---

### Post by butterball23 on 2005-05-26
I just got Java and Eclipse working 5 minutes ago.

Although, I used JRE 1.4.2 build 08 and Eclipse 3.1 M7 

This is what I did here:
=> [http://ubuntuforums.org/showthread.php?p=188453](http://ubuntuforums.org/showthread.php?p=188453)

When you install apps, there's more than 1 way.

I suggest using repositories.
(You could also install JRE by hand...Which is what I did).

For JAVA, use the repository and get JDK or JRE 1.5

Follow the instructions in the Wiki Ubuntu documentation:
The first option in this wiki ( ubuntu.tower-net.de )
=> [http://www.ubuntulinux.org/wiki/Java](http://www.ubuntulinux.org/wiki/Java)

For Eclipse, you don't install anything. You just download, uncompress and run it.

Follow the instructions in the Wiki Ubuntu documentation: 
=> [http://www.ubuntulinux.org/wiki/EclipseIDE](http://www.ubuntulinux.org/wiki/EclipseIDE)

If you run into issues, just look at my thread for hints.

I find Eclipse with CDT (C/C++ plug-in) pretty funky...Using it on both Linux and Windows setups, passing source code back and forth. :)

---

