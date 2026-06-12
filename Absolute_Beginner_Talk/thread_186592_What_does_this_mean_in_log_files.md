---
title: "What does this mean in log files"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by petef on 2006-06-02
Hi guys,

Getting loads of these in my logs each day eny idea what they mean ? Tried searching but not found anything. :( 

May 28 18:40:15 localhost -- MARK --
May 28 19:00:15 localhost -- MARK --
May 28 19:20:15 localhost -- MARK --
May 28 19:40:15 localhost -- MARK --
May 28 20:00:15 localhost -- MARK --
May 28 20:20:15 localhost -- MARK --
May 28 20:40:15 localhost -- MARK --
May 28 21:00:15 localhost -- MARK --
May 28 21:20:15 localhost -- MARK --
May 28 21:40:15 localhost -- MARK --
May 28 22:00:15 localhost -- MARK --
May 28 22:20:15 localhost -- MARK --
May 28 22:40:15 localhost -- MARK --
May 28 23:00:15 localhost -- MARK --
May 28 23:20:15 localhost -- MARK --
May 28 23:40:16 localhost -- MARK --
May 29 00:00:17 localhost -- MARK --
May 29 00:20:17 localhost -- MARK --

Cheers

Pete

---

### Post by petef on 2006-06-02
Anyone ?

---

### Post by wastern on 2006-06-02
which log is it in?


probably doesn't mean anything. are you getting some errors or issues, or are just kind of randomly looking at the logs

---

### Post by petef on 2006-06-02
Hi thanks for the reply. 

I was looking through the logs as a cron job isn't running which would perform a backup. I see this in the messages log and in a couple of the others ???? Must mean something ?

---

### Post by Arndt on 2006-06-02
[QUOTE=petef]Hi thanks for the reply. 

I was looking through the logs as a cron job isn't running which would perform a backup. I see this in the messages log and in a couple of the others ???? Must mean something ?[/QUOTE]

I interpreted this as a regular time stamp, and when I look around a little it turns out that it is. I found out this way:

% man syslog
  nothing found
% apropos syslog
 It lists syslogd
% man syslogd
 Here it says:

 ```
      -m interval
              The syslogd logs a mark timestamp regularly.  The default inter&#8208;
              val  between  two  --  MARK -- lines is 20 minutes.  This can be
              changed with this option.  Setting the interval to zero turns it
              off entirely.

```

---

### Post by petef on 2006-06-02
Oh thats cool ! Thanks for that :)

Pete

---

