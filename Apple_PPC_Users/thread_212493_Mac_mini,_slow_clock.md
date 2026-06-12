---
title: "Mac mini, slow clock"
date: 2006-07-10
forum: Apple PPC Users
---

### Post by leaded on 2006-07-10
I'm using Dapper Server PPC (for a 1.42GHz Mac mini). I'm using this machine to run rsync backups at night for multiple development machines. Got a nice 1TB Lacie drive to go with it :)

But, for whatever reason, the system clock is slow. It appears that it loses 2 minutes a day. For example, around 2pm today I reset the time to time.gov. I just checked, 10 hours later, and it's off by about a minute.

I'd like to maybe set up ntp to syncronize a couple times a day but I don't know over the command-line. I installed ubuntu-desktop but I won't have local access to the box for a couple of days.

What should I do?

---

### Post by mogelhead on 2006-07-11
There is a [HOWTO: Accurate timekeeping on Ubuntu]("http://www.ubuntuforums.org/showthread.php?t=97041") for this, which I found by searching the forum.

---

### Post by leaded on 2006-07-11
Thanks mogelhead, I found that too, but I was trying to see if I could perform the first set on instructions (Always On, using Gnome menus) remotely without running X. That's okay tho, I'm going to the office tomorrow and can just do it then.

---

### Post by mogelhead on 2006-07-11
There are two ways to do this. The first involves the GNOME GUI, but the second don't.

I was thinking you could go for the second (chrony) solution. 

Although the header says "If you are frequently off line or you power down your computer for several hours or more, follow these instructions" but furter down it also says: "(by the way if you later get an always-on connection to the net, chrony works great under this scenario too)"

---

### Post by leaded on 2006-07-11
Oh! Yeah I just looked at the header and scrolled down until the next header. Thanks for pointing that out! :-\

---

### Post by leaded on 2006-07-20
I tried to GUI way once I had local access and it worked, at that time. It's not working everyday though. I was hoping there was a command I could run that was the equivilent of doing the "Syncronize now" that I could run as a cron job. Since the day that I did what you suggested, the clock is off by 30 minutes.

What should I do?

---

