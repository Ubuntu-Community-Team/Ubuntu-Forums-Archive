---
title: "Set time/date via command line"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by Wardazo on 2007-05-19
Hi

What's the command to set the time and date. I can't find it anywhere.

Thanks

Ward

---

### Post by yabbadabbadont on 2007-05-19
Wait for it.....   date  :D

"man date" for details on the format of its arguments.

---

### Post by Metacarpal on 2007-05-19
> **yabbadabbadont said:**
> Wait for it.....   date  :D

"man date" for details on the format of its arguments.

date's man pages are something of a maze at first glance.

Here's the skinny: type in the following command, replacing *nn* with the two-digit month (01 - 12), *dd* with the two-digit day, *hh* with the two-digit hour (00 - 23), *mm* with the two-digit minute (00 - 59).  Optionally, you can then follow that with either a two-digit or four-digit year, and/or the two-digit second.  If you're adding the seconds, put a . (period) before the seconds.

```
date *nnddhhmm*
```
or
```
date *nnddhhmmyy*
```
or
```
date *nnddhhmm.ss*
```

For instance, to set the date/time for May 19th, 2007, 6:00pm (and 0 seconds), you would type:

```
date 051918002007.00
```

---

### Post by enopepsoo on 2007-05-19
is there a command line for resynching with the NNTP server?:confused:

---

### Post by Bachstelze on 2007-05-19
```
sudo ntpdate NTPServerURLHere
```

But it is not usually done. Most people prefer to have ntpd running in the background and doing this automatically.

---

### Post by yabbadabbadont on 2007-05-19
> **enopepsoo said:**
> is there a command line for resynching with the NNTP server?:confused:

/etc/network/if-up.d/ntpdate

---

