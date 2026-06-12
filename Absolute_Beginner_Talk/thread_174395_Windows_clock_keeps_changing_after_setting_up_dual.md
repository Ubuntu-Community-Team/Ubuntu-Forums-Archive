---
title: "Windows clock keeps changing after setting up dual boot with Ubuntu."
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by KillrBuckeye on 2006-05-11
The title says it all.  The clock in Windows gets really messed up when I boot to Ubuntu, then don't boot back to Windows for a while.  It says 11:37pm right now, when it's actually 7:37pm (I had reset the Windows clock to the proper time just this morning).  Is this common, and how do I stop it from happening?

---

### Post by halfvolle melk on 2006-05-11
[QUOTE=KillrBuckeye]The title says it all.  The clock in Windows gets really messed up when I boot to Ubuntu, then don't boot back to Windows for a while.  It says 11:37pm right now, when it's actually 7:37pm (I had reset the Windows clock to the proper time just this morning).  Is this common, and how do I stop it from happening?[/QUOTE]

Hi,
I've read about this and did a forum search. It would appear to be a problem with etc/default/rcS. You will have to set UTC=no.
So open a terminal (Apps -> Accs - Terminal) and type:
```
sudo gedit /etc/default/rcS
```
Change "UTC=yes" to "UTC=no".

---

### Post by Ptero-4 on 2006-05-11
You have to change the clock from GMT to UTC.

---

### Post by Clay85 on 2006-05-11
I'm having the same problem, I"ll try this out.

Thanks :)

---

### Post by KillrBuckeye on 2006-05-11
This seems to have worked!  Thanks for the quick replies.

---

### Post by hotani on 2006-05-30
I seem to have the opposite problem. I keep correcting the clock in Ubuntu, but it continues to be incorrect (by 6 hours).

Yes, I am set to the correct time-zone and using time servers.

BTW: I don't think "open a terminal and sudo....." is the right answer for something so basic as the correct time.

---

### Post by Pigsflew on 2007-07-30
> **hotani said:**
> I seem to have the opposite problem. I keep correcting the clock in Ubuntu, but it continues to be incorrect (by 6 hours).

Yes, I am set to the correct time-zone and using time servers.

BTW: I don't think "open a terminal and sudo....." is the right answer for something so basic as the correct time.

I disagree. I usually hate the terminal and would always prefer a graphical solution, but we're talking about a basic and fundamental difference between how Windows and Unix treats the system clock. A mechanism exists for changing the functionality in Ubuntu to be more like Windows, but please note that either way, Ubuntu *does* keep correct time, it just keeps it *differently*.

I don't think any effort should be made to guify making the system clock agree with the way Windows does things, there are a lot more important things to deal with to help people just stay in Ubuntu--without dual booting at all.

(I also had this problem, changing rcS seems to work.)

---

### Post by monoufo on 2008-07-19
if you dont like the command line why even use linux?

---

