---
title: "New terminal command"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by adversity04 on 2006-12-20
Hi,

I was wondering if there was a command that could be used to create a new terminal from a currently opened one.  While using Windows with an x-window manager I'm able to just do a xterm & to create a new terminal, but I'm unsure how I would be able to do this in linux.  I have to ssh into a school server and would like a better method of having multiple terminals open than logging in multiple times.

Thanks!

---

### Post by riven0 on 2006-12-20
> **adversity04 said:**
> Hi,

I was wondering if there was a command that could be used to create a new terminal from a currently opened one.  While using Windows with an x-window manager I'm able to just do a xterm & to create a new terminal, but I'm unsure how I would be able to do this in linux.  I have to ssh into a school server and would like a better method of having multiple terminals open than logging in multiple times.

Thanks!

To start a new shell, (terminal), *over* your current terminal, just type:

> bash

It will suspend your previous shell and start a new one. To get back to your old shell, just type **exit**.

---

### Post by Bachstelze on 2006-12-20
screen is what you're looking for :)

---

