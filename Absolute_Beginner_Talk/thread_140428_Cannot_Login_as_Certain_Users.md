---
title: "Cannot Login as Certain Users"
date: 2006-03-06
forum: Absolute Beginner Talk
---

### Post by Pudwud on 2006-03-06
When I try to login as certain users that I have created I get this kind of message:

“Your session only lasted less than 10 sec. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one off the failsafe sessions to see if you can fix the problem.”

I seem to be able to get into the Terminal Failsafe screen but I do not know what to do next to fix the problem.

Any suggestions?

Thanks.

---

### Post by alamba on 2006-03-06
run the command df on a terminal screen and see how much diskspace you have left.

---

### Post by codejunkie on 2006-03-06
[QUOTE=Pudwud]When I try to login as certain users that I have created I get this kind of message:

“Your session only lasted less than 10 sec. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one off the failsafe sessions to see if you can fix the problem.”

I seem to be able to get into the Terminal Failsafe screen but I do not know what to do next to fix the problem.

Any suggestions?

Thanks.[/QUOTE]
it's most likely a permissions issue with **.ICEauthority** or **.Xauthority**
try running
```

sudo chown nameofyouruser:nameofyouruser /home/nameofyouruser/.ICEauthority

```
```

sudo chown nameofyouruser:nameofyouruser /home/nameofyouruser/.Xauthority

```

```

sudo chmod 600 /home/nameofyouruser/.ICEauthority

```
```

sudo chmod 600 /home/nameofyouruser/.Xauthority

```

---

### Post by Pudwud on 2006-03-08
If I am reading this correctly I have lots of disk space:

...:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             37017868   3228296  31909168  10% /
tmpfs                   249960         0    249960   0% /dev/shm
tmpfs                   249960     12588    237372   6% /lib/modules/2.6.12-9-386/volatile

I tried codejunkie's proposed solution but had no luck.

All other suggestions gratefully accepted.

---

### Post by Xian on 2006-03-08
Try creating another user and logging in under that name. If the session appears normal then there is something amiss with your own user prefs. If you can at least get to the Ubuntu login screen then your gfx settings should be fine. If not, then I'd look at your X log and review for any error messages.

---

### Post by Pudwud on 2006-03-08
I have been able to create new users.  How do I change the user prefs, how do I look at my X log and what are gfx settings?

Thanks.

---

