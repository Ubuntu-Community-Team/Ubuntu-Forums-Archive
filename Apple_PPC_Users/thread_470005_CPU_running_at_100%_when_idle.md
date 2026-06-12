---
title: "CPU running at 100% when idle"
date: 2007-06-10
forum: Apple PPC Users
---

### Post by also-rr on 2007-06-10
I have a 1.5ghz AIBook running Kubuntu 7.04.

When left alone for a while it starts running at 100% CPU. Moving the mouse causes it to go back to normal after 30-60 seconds of further thrashing.

Any ideas as to the cause? I suspected a considerate root kit but it doesn't seem to be generating any network traffic.

Thanks,

Richard

---

### Post by eugoss on 2007-06-10
What did the *top* utility show? What was the most expensive process?

---

### Post by diatribe on 2007-06-10
if you have an opengl screensaver this might also be the reason

---

### Post by also-rr on 2007-06-10
I don't have a screensaver, or at least none ever shows up.

Top shows xorg as the culprit.

---

### Post by tcrroadie on 2007-06-10
Open a terminal and run the command ''top''

```
top
```

Top will list system process usage from most to least, from top to bottom.  

You can kill a process using top by pressing the letter k on you keyboard and entering the process id number or PID.

The processes that seems to be most problematic for PowerPC users is a service called mouseemu.  If mouseemu is the process that is causing you trouble, you can just remove the package altogether.

```
sudo apt-get remove mouseemu
```

---

### Post by reh4c on 2007-06-11
Greetings.  I noticed that gDesklets had some buggy issues, along with enabling desktop effects.  After disabling both of those, my CPU frequently scales down to 500 mhz and temperatures stay much lower.  Some programs (not that intensive) seem to overburden the CPU as well.

---

### Post by ssam on 2007-06-11
If xorg is the top process in top, it usually means that some other program is making it do lots of work. have a look at the next few processes while xorg is using lots of processor time.

---

