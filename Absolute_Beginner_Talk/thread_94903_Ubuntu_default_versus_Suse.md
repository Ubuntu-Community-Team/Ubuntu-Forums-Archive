---
title: "Ubuntu default versus Suse"
date: 2005-11-25
forum: Absolute Beginner Talk
---

### Post by markr on 2005-11-25
Hi all,

I have Breezy installed (Gnome) and can work in it ver happily (I have some ACPI issues, but I'm working on that; it's a laptop).

However,  I recently stuck opensuse 10.0 on my laptop from a magazine just to see how it was looking.  Although I've now gone back to Ubuntu, a couple of things on suse really impressed me and I was wondering why Ubunutu does not do it as welll...

1. Detect your cpu and install the best kernel - suse installed the 686smp kernel as default on my laptop as I have a P4;  Ubuntu only installed the 386 kernel.

2. I also noticed that a lot of the packages where .686.rpm; 

I know you can download the 686smp kernel (which I intend to do soon). But the fact that suse installed 686 application packages must mean that it performs much better on a P4 than Ubuntu?

I'm not trying to start a flame war here,  I just want to get the best possible performance out of my hardware (or what's the point of paying the extra ££££).

I look forward to the discussion.

Mark.

---

### Post by Chayak on 2005-11-25
There is a few things, SUSE might have detected hyperthreading on your P4 and installed the SMP because of it (If you have an HT P4 that is)

1. The X86 install does that by default I believe, someone correct me if I'm wrong.

2. I'm not sure about the packages being 686

If you want the best performance I'd suggest going into [HTML]http://doc.gwos.org/index.php/2.6.14_Vanilla[/HTML] and install a kernel customized to your system.  If you want a more responsive desktop rather than server functions you can always turn on preempting in the kernel and adjust the kernel timing to suit your needs.  Personally I used partial preempting and 1000 timing.  My desktop is a lot more responsive but the tradeoff is that server processes will take the hit, then again I'm not doing much other than sharing some files on my workstation.

---

### Post by markr on 2005-11-25
If you build a custom kernel,  does that not mean I will have to reinstall nvidia drivers and ndiswrapper everytime I upgrade?  I suppose I have to make a choice between ease of upgrade (i.e. stick with the default ubuntu options from synaptic) or tweak my system and allow for the fact I will have additional maintenance at upgrades.

---

