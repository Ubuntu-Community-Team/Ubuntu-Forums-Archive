---
title: "Are there tips to Optimizing Ubuntu?"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by [Cyanide] on 2005-07-30
The whole KDE system just seems kinda sluggish at times? I don't know how else to explain it...

Windows will take a while to "appear" after I've clicked on them, whereas in XP Pro I've never had that problem.

Is there a way to optimize Ubuntu? My laptop isn't the best out there but it's no slouch either, should be more than capable of handling Ubuntu.

AMD Athlon 2100+ (1.79Ghz)
512mb RAM
40Gb HD

---

### Post by Xian on 2005-07-30
This might help: [How-To Enable Prelinking](http://ubuntuforums.org/showthread.php?t=1971).

---

### Post by az on 2005-07-30
Other than using the k7 kernel (search synaptic for "linux-image") Ubuntu tends to run _faster_ then windows, in my experience.

---

### Post by poofyhairguy on 2005-07-30
[QUOTE=azz]Other than using the k7 kernel (search synaptic for "linux-image") Ubuntu tends to run _faster_ then windows, in my experience.[/QUOTE]


or the 686 kernel, or the smp kernel for hyperthreading or multi processors.

---

### Post by [Cyanide] on 2005-07-30
[QUOTE=azz]Other than using the k7 kernel (search synaptic for "linux-image") Ubuntu tends to run _faster_ then windows, in my experience.[/QUOTE]

The K7 kernels don't seem to like my AMD Athlon-M. It freezes upon boot. My theory is that I don't think the K7 kernel isn't throttling the CPU frequency like it should and it's keeping the CPU on full blast at all times.

[QUOTE=poofyhairguy]or the 686 kernel, or the smp kernel for hyperthreading or multi processors.[/QUOTE]

I have the 686 kernel running right now and according to a few of my friends the K7 kernel didn't really give it much of a speed increase if any.

---

### Post by Xian on 2005-07-30
[QUOTE='[Cyanide]']I have the 686 kernel running right now and according to a few of my friends the K7 kernel didn't really give it much of a speed increase if any.[/QUOTE]
I've run three of the Ubuntu kernels and can't say I've noticed any discernible time change in the responsiveness of applications running under any of them. I have noticed that prelinking helped more significantly. I would surmise that for a kernel change to really make a substantial difference it would have to be custom compiled for your specific hardware and specs.

---

### Post by [Cyanide] on 2005-07-30
[QUOTE=Xian]I've run three of the Ubuntu kernels and can't say I've noticed any discernible time change in the responsiveness of applications running under any of them. I have noticed that prelinking helped more significantly. I would surmise that for a kernel change to really make a substantial difference it would have to be custom compiled for your specific hardware and specs.[/QUOTE]

What does prelinking do exactly? I've read that thread on how to install/configure it, but it doesn't really explain what it does...

---

### Post by Xian on 2005-07-30
[QUOTE='[Cyanide]']What does prelinking do exactly? I've read that thread on how to install/configure it, but it doesn't really explain what it does...[/QUOTE]
This is from the Gentoo Docs and I've never seen it explained better:

[i]"What is Prelink and how can it help me?

Most common applications make use of shared libraries. These shared libraries need to be loaded into memory at runtime and the various symbol references need to be resolved. For most small programs this dynamic linking is very quick. But for programs written in C++ and that have many library dependencies, the dynamic linking can take a fair amount of time. 

On most systems, libraries are not changed very often and when a program is run, the operations taken to link the program are the same every time. Prelink takes advantage of this by carrying out the linking and storing it in the executable, in effect prelinking it. 

Prelinking can cut the startup times of applications. For example, a typical KDE program's loading time can be cut by as much as 50%. The only maintenance required is re-running prelink every time a library is upgraded for a pre-linked executable."[/i]

---

### Post by Nanaki on 2005-07-30
That's my main problem with Linux. Gnome just isn't as fast or snappy as Windows. When I click in Windows, everything pops up immediatly. In gnome, it doesn't. The taskbar-menu for instance, the images always take longer to load than the menu itself. Oh well, it's free. :)

---

### Post by [Cyanide] on 2005-07-30
[QUOTE=Nanaki]That's my main problem with Linux. Gnome just isn't as fast or snappy as Windows. When I click in Windows, everything pops up immediatly. In gnome, it doesn't. The taskbar-menu for instance, the images always take longer to load than the menu itself. Oh well, it's free. :)[/QUOTE]

And it's stable!

Actually the snappiness (or lack thereof) is my only gripe with Ubuntu. I'm really impressed with everything else, especially for a n00b like me it's pretty intuitive.

---

### Post by bjourne on 2006-02-05
[QUOTE=Xian]This is from the Gentoo Docs and I've never seen it explained better:

[i]"What is Prelink and how can it help me?

...

Prelinking can cut the startup times of applications. For example, a typical KDE program's loading time can be cut by as much as 50%. The only maintenance required is re-running prelink every time a library is upgraded for a pre-linked executable."[/i][/QUOTE]

I wonder if this is true. First of, KDE has a library fetching daemon service called kcop or something that loads all useful KDE libraries in memory which is the same thing that prelinking does. So prelinking KDE apps shouldn't have any discernable effect on startup time. On GNOME apps, then maybe you can get some speedup by prelinking. When I ran GNOME and Gentoo prelinked I couldn't personally notice any speed difference. I think this is because if you start a big program that uses many GNOME libs, then those libraries will already be loaded in memory and it takes virtually no time for other programs using those libraries to dynamically fetch them.

---

