---
title: "What does it mean to compile a kernel?"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by Romanus81 on 2007-09-22
I've just been wondering, I guess it means you make your own kernel? What are the downsides to compiling a kernel? And should I wait until I upgrade to Gutsy next month and use the Gutsy kernel? (I tried upgrading just the kernel in advance, but it broke XGL, meaning no compiz effects.

---

### Post by click4851 on 2007-09-22
my freshman understanding is that compiling your own kernel allows you to configure the kernel so it supports and loads only the features and modules you desire. I'm led to believe when space is tight, this is very popular.

---

### Post by master_kernel on 2007-09-25
It can also speed up your desktop and bootup time. See the Master Kernel Thread (and KernelCheck) in my signature for more details.

---

### Post by stmiller on 2007-09-25
The default Ubuntu kernel is very generic to work on all machines. But there are literally hundreds of options to make a custom kernel just for your machine. You can specify AMD or Intel (or any other applicable arch), choose recent wifi and HD tuner options, and tons of other stuff. You can also increase the kernel timing, and enable a low-latency desktop for better video and audio performance. I wish Ubuntu would do this by default, being that they are a desktop-oriented distro.

---

### Post by MicroChris on 2007-11-01
> **stmiller said:**
> The default Ubuntu kernel is very generic to work on all machines. But there are literally hundreds of options to make a custom kernel just for your machine. You can specify AMD or Intel (or any other applicable arch), choose recent wifi and HD tuner options, and tons of other stuff. You can also increase the kernel timing, and enable a low-latency desktop for better video and audio performance. I wish Ubuntu would do this by default, being that they are a desktop-oriented distro.

They used to. I don't know what happened to architecture-specific kernels in Synaptic.

---

