---
title: "Can't update because of incorrect timestamp?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-12-30
Hi all, I've been having a weird time. Lots of really odd things have gone wrong but fisrt and foremost - my system won't allow me to
 > buddha@Rubaiyat-desktop:~$ sudo aptitude update
because - 
> sudo: timestamp too far in the future: Dec 31 02:05:08 2006
but my system time shows as normal.
This is not so much of a surprise as it might otherwise be as for the last couple of days my system clock keeps resetting itself. Of course I have no idea.
I tried to reset it to an earlier date to try to work around this particular problem but no go.
Any ideas??
I'm kinda desperate at the moment as I had to reinstall my system just when the earthquake killed net access for me and I've been waiting since then to get back on.

---

### Post by Patrick K on 2006-12-30
Just a thought and it may not be the problem but the CMOS battery running down often first shows itself by problems with the clock. They are cheap and easy to replace.

---

### Post by PartisanEntity on 2006-12-30
I had that issue right after installing Dapper, but all I was advised to do was to restart Ubuntu and I have not had it since.

---

### Post by carloslosgrande on 2006-12-30
Well maybe, but my computer isn't that old, not even a year yet. I've been restarting ubuntu but it hasn't fixed it.
What I'm really after is how to adjust it in the system, ie via the terminal?

---

### Post by carloslosgrande on 2006-12-31
Ok, I've finally had some success in getting the system setup with all the codecs etc,etc. and this seems to have fixed the problem. How and why I don't know. The net connection here is getting back to normal now, although still slow.
thanks for your replies, appreciated.
Carlos.

---

### Post by carloslosgrande on 2007-02-05
[I]Righto, back to this problem. I've had another reinstall and got everything up and running.
The timestamp still shows too far in the future after every restart. 8 hours _exactly_. Never the minutes and only the date is changed when the 8 hours takes it into the next day.
I loaded ntp and set the synchro with several servers in my time range.
I've checked these forums and haven't seen anything quite like this.
If it was the CMOS battery I assume it wouldn't be consistently 8 hours ahead and there isn't any speeding up or slowing down of the system time while its running.
I assume there is some problem in the initial startup but I don't know how or where to look for that.
All assistance appreciated, as usual.:guitar: 
[/I]

---

### Post by carloslosgrande on 2007-02-10
Ok, further searching and found what seems to be the answer
I made sure that the desktop time and the system time are the same, ie when the terminal error says > 'timestamp too far in the future (..date..time etc)' I set the clock to this time,
then I enter ```
sudo -K
```
then reset my clock and haven't had any trouble since, even after several restarts.
Sorry to whoever wrote the answer as I've forgotten who it was. But thanks!:lolflag:

---

