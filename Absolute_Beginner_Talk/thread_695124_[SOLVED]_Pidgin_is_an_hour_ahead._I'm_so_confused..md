---
title: "[SOLVED] Pidgin is an hour ahead. I'm so confused."
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by Nerdriot on 2008-02-12
Hello,

I didn't know where else to ask this (I've look everywhere).

When I initially installed Ubuntu, I wasn't too clear on the time zone selection (it didn't show CST, ET, etc.). I selected a city that appeared closest to me time zone-wise, but apparently, I was wrong. I adjusted the clock, at which time, after rebooting, Ubuntu corrected this "in the future" issue.

Anyway, now when I use Pidgin, it shows I've been logged in since, say, 6pm, and it's only 5pm here. I've completely removed Pidgin, and compiled the newest version, hoping that would fix it, but to no avail.

Anyone know how I can adjust this manually within Pidgin? Or some other fix? It's driving me insane (I hate when things aren't fixed).

Thanks in advance!

---

### Post by p_quarles on 2008-02-12
Let's start by checking if this is a problem with the computer's clock or not. Run the following commands:
```
date -u
```
and 
```
date
```
The first will give UTC time and date (i.e., Greenwich Mean Time), and the second will show what the computer thinks your local time is.

---

### Post by Nerdriot on 2008-02-12
Thank you for the fast reply!

Here's what I got:

```
ben@ub3ntu:~$ date -u
Tue Feb 12 22:48:06 UTC 2008
ben@ub3ntu:~$ date
Tue Feb 12 17:48:13 EST 2008

```

It's set to EST, but my time zone is actually CST. I'm REALLY confused now, since I googled the area I selected (Vincennes, Indiana) and it said it was CST.

---

### Post by p_quarles on 2008-02-12
Sounds like the easiest way of fixing this will be:
```
sudo tzselect
```
It's a CLI app, but it presents you with numbered options, so isn't difficult to figure out.

---

### Post by Nerdriot on 2008-02-12
Thank you so much! You've been more than helpful. It's corrected (finally!)

It says this:

```
You can make this change permanent for yourself by appending the line
        TZ='America/Chicago'; export TZ
to the file '.profile' in your home directory; then log out and log in again.

Here is that TZ value again, this time on standard output so that you
can use the /usr/bin/tzselect command in shell scripts:
America/Chicago

```

Will the change not be permanent unless I do that, or by doing it 'as root' make it permanent for me?

(Sorry, I'm a total noob0rcycle.)

---

### Post by Nerdriot on 2008-02-12
Hah, I just realized the blatant stupidity of that question I just asked you, since it clearly states that's the case.

I should re-word it. What I mean is, if I log off, and log back in, will the timezone issue revert back to the incorrect one?

---

### Post by p_quarles on 2008-02-12
I think that using sudo will make it permanent, but not sure (haven't used that app much). But, changing .profile in the way it suggests is probably the better bet.

You can also set the time manually:
```
sudo date 021218mm
```
Where 0212 is the date, 18 is 6:00pm, and mm should be replaced with the current minute.

---

### Post by Nerdriot on 2008-02-12
Thank you again :)

Well, I sincerely hope that sudo'ing it made it perm., since I'm completely at a loss as to where the .profile is. Says it's in my home dir., but I've not been able to locate it.

It's funny, really. I spent the last few weeks writing lame scripts and such to do tons of things for me (like downloading videos my friends made from YouTube to my home dir, etc.), and yet, I can't locate the .profile.

I have a lot to learn...

---

### Post by p_quarles on 2008-02-12
Files that begin with "." are hidden. In Nautilus, you can set it to show hidden files. In the terminal, you can show hidden files with the "-a" option for ls:
```
ls -a
```
If it's still not there, you can always just create it, too.

---

### Post by Nerdriot on 2008-02-12
I just found it.

I'm sorry, lol. I'll stop bothering you now... ;)

---

