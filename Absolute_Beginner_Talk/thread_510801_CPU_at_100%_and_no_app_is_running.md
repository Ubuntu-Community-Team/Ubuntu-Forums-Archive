---
title: "CPU at 100% and no app is running"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by rrkryder on 2007-07-27
I just installed Dapper on to my Fujitsu Lifebook A series.
The notebook is brand new, came with Vista. Wanted to give MS the bird, for they are bullies.
Install took 6 hours. Ubuntu is now running, but I noticed it was going very slow.
So I finally ran system moniter and saw the CPU was at 100%. No other apps running.
Any solutions?
Thanks,
Rob

---

### Post by KyleBrandt on 2007-07-27
In system monitor, you can click View : Show All Processes , if you had not done this, there might be a process using your cpu that was not shown before.

---

### Post by ev5unleash1 on 2007-07-27
When you installed Ubuntu though the CD did you start it up with Safe Graphics mode if so you are most likly running a Generic Video card meaning the CPU is doing all the work to make your visual instead of the video card it self. Make sure you install with Start or install Ubuntu on the CD boot. If not this problem may of been corrected in newer versions of Ubuntu like 7.04 try upgrading to that version.

---

### Post by rrkryder on 2007-07-27
Kyle,
It goes from a few active processes to 10 and back again
the one that is taking up 93 to 100% of the CPU seems to be something called event/0

EV,
When I booted the live cd ( Dapper is a combo cd) it was running really slow then....then I doubleclicked on the install icon on the desktop...six hours later it was installed....

---

### Post by Phosphoric on 2007-07-27
6 hours to install Ubuntu?  Looks like you have a fundamental problem with your laptop.  Were you dual booting?  Is vista still in place?

When you boot in to Vista, how's the CPU load then?

---

### Post by KyleBrandt on 2007-07-27
rrkryder:  Looks like there is no easy answer, read this: [http://www.linuxquestions.org/questions/showthread.php?t=441837](http://www.linuxquestions.org/questions/showthread.php?t=441837)
Especially: "If you want to try and find the cause, have a look at the output of your kernel and the boot process. See if there is any hardware that is throwing up errors."

You can view this by typing dmesg... let us know if you see any alarming errors from that.  What are you basic specs for your laptop as well?

Do try ev5unleash1's recommendation of safe graphics mode as well to see what happens.

---

