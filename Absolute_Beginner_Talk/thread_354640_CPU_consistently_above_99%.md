---
title: "CPU consistently above 99%"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by in_flu_ence on 2007-02-06
Hi,

   I am wondering why my CPU is always running at 100% even when all activities in the activity list shows 'sleeping' or 0% usage.  I have compared that with my laptop and my laptop is using just 5% of CPU for the same case.

   My desktop should not be considered too old since it has a amd64bit chip with 2gb ram.

SOme info might be useful is that i have installed boinc manager before but uninstalled it. Any chance that I have not removed everything? I use sympatic to install & uninstall

Thanks.

---

### Post by engineer on 2007-02-06
go to a terminal and type

```

top

```

you'll see all processes sorted by cpu usage

maybe you saw only processes that are owned by your user.
a process owend by root could use 100% of your cpu.

---

### Post by jonnyburns on 2007-02-06
i fixed that problem by reseting all of my desktop options to default in gnome and now im getting low cpu usage, so try and resetting all of your desktop option to default... maybe tha twill work

---

### Post by in_flu_ence on 2007-02-06
Where can I set the desktop options?

Thanks for all the prompt reply

---

### Post by kanha on 2007-02-06
hi all,
i m facing same problem
on running "top"
i found that a service named "apport" is using 95% cpu
what is that?
is it any important service or should i shut it down

---

### Post by apjone on 2007-02-06
fyi

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

### Post by in_flu_ence on 2007-02-06
top works great. It is that I haven't removed the boinc core and it has been running non stop.

Thanks

---

### Post by lonoy on 2007-06-15
You can download a newer version of the Boinc Manager here which will allow you to adjust your CPU usage:

[http://www.getdeb.net/app.php?name=Boinc](http://www.getdeb.net/app.php?name=Boinc)

It is for Feisty, 32 & 64 bit systems

Cheers
Lonoy

---

