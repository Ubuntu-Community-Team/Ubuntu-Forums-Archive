---
title: "Howto Set time?time zone? on xubuntu edgy"
date: 2006-10-28
forum: Absolute Beginner Talk
---

### Post by theadventuresofanidealist on 2006-10-28
i have it set to us eastern by mistake.
i want to change the time zone or at least the clock.
how do i go about it?

---

### Post by 5-HT on 2006-10-29
```
 tzconfig 
```

---

### Post by theadventuresofanidealist on 2006-10-29
thanks.

---

### Post by jackyyong on 2007-03-14
This is no good. I have no internet connection at my machine with Xubuntu Edgy. I can't sync my time online, and XFCE's interface does not seem to allow me to change the date, unlike Ubuntu's Gnome interface. Any help please?

---

### Post by pettybone on 2007-03-14
To me the time zones are a real pain to use or change. Also I am wondering why the time zones were done the way they were. Why no central or eastern pacific. I'm know I picked the right time zone but i guess I forget there are other people in the world. Maybe I should just get used to it.

---

### Post by x1a4 on 2007-03-14
Hi,

I use *date* to set time and date.

*date MMDDhhmm*

Where: MM=Month# (March=03); DD=Day#; hh=Hour; mm=Minutes

eg: *date 03141125*

read *man 1 date* and *info coreutils date* for information about *date*

---

### Post by jackyyong on 2007-03-14
I accidentally bumped into something that I didn't notice before. Go to Applications -- System -- Time and Date!!

I can now manually edit the date and time, including the time zone, with GUI!

I selected "Keep clock synchronized with Internet Servers" and I was prompted to install ntp-simple and ntp-server. And it worked from then on! Brilliant! Guess I answered my own dumb question!

---

### Post by x1a4 on 2007-03-14
Awesome.  Make sure you edit your original post and tick the 'issue is resolved' checkbox.

---

