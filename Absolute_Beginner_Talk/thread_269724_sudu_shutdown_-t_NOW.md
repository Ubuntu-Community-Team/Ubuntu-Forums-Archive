---
title: "sudu shutdown -t NOW"
date: 2006-10-02
forum: Absolute Beginner Talk
---

### Post by firebirdworks on 2006-10-02
If this code would shut the computer down immediately, then would it be possible to have a code like:
sudu shutdown -t 5:00
To have the computer shut down in five minutes?
Does anyone know the code, or is there one?

---

### Post by tkiesel on 2006-10-02
The code to shut down the computer in 5 minutes would be:

```
sudo shutdown -h 5
```

---

### Post by Scorpuk on 2006-10-02
I would guess that this would work:

```
sudo shutdown -t 300
```

5 minutes = 300 seconds


check it out by typing:

```
man shutdown
```

---

### Post by Scorpuk on 2006-10-02
> **tkiesel said:**
> The code to shut down the computer in 5 minutes would be:

```
sudo shutdown -h 5
```

-h     Halt or poweroff after shutdown.


I'm guessing that would not work. :neutral:

---

### Post by firebirdworks on 2006-10-02
humm...
What of five hours?
sudu shutdown -t 18000?
Or what is the code for that?

---

### Post by Scorpuk on 2006-10-02
> NAME
       shutdown - bring the system down

SYNOPSIS
       /sbin/shutdown [-t sec] [-arkhncfFHP] time [warning-message]


hmm you could probably then tell it to shutdown at a particular time


maybe

```
sudo shutdown 15:00
```

edit:

>        The  time  argument  can  have  different formats.  First, it can be an
       absolute time in the format hh:mm, in which hh is the hour (1 or 2 digâ€
       its)  and mm is the minute of the hour (in two digits).  Second, it can
       be in the format +m, in which m is the number of minutes to wait.   The
       word now is an alias for +0.

---

### Post by Scorpuk on 2006-10-02
> **firebirdworks said:**
> humm...
What of five hours?
sudu shutdown -t 18000?
Or what is the code for that?

I think you are right as 5 hours = 18000 seconds. :cool:

---

### Post by Scorpuk on 2006-10-02
Ahh so you could do this for 5 minutes

```
sudo shutdown +5
```


and this for 5 hours


```
sudo shutdown +300
```


Edit: lol My maths sucks, even though i done it once already on post. :-k

---

