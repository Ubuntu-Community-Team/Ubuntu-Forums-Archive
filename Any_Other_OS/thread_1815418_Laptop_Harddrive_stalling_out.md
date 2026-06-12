---
title: "Laptop Harddrive stalling out"
date: 2011-07-31
forum: Any Other OS
---

### Post by slick666 on 2011-07-31
Dear Comunity

I'm running an issue that I can't seem to trace down or even know where to look. So here is whats happening.

The laptop is running
[LIST]
[*]It could be on power or off
[*]It could be running flash or not
[*]It could be running a heavy load or a light load
[/LIST]

I know there is a problem because the HD light is pegged, fully lit. The HD status panel shows that the HD IO wait is is at 100 percent. The cpu usage may be high or low and usually after a second or two is that the entire system locks up. The Audio loops, the mouse is locked, the screen doesn't update and the status applet doesn't update.

This last from half a second to 6 or 7 seconds. The system load jumps up to between 10 and 20. After the system load drops down to about 0.5 to 1.0.

I can't seem to figure what is the source of the problem. IOTop doesn't seem to show much and I cant figure out if the problem is Software of Hardware. Any pointers would be helpful.

Thanks

P.S. This is on Linux Mint so it's gnome 2.X

---

### Post by movieman on 2011-07-31
Check the kernel error logs for disk errors and run smartctl to see if it reports reallocated sectors. That's what my laptop was doing when the hard drive started getting bad sectors.

---

