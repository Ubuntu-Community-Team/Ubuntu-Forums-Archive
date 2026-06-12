---
title: "Dapper 6.06 dvdrip problem"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by flobadobblibblobbleep on 2007-09-17
Heregos
I am new to this and could do with a pointer. I installed dvdrip and after a couple of gos got all the dependencies sorted out mainly by trawling the forums. the problem that I have now is : cdrecord device [n,n,n or filename]: 0,x,0 has not format n,n,n and is no file: NOT ok
I am sure that this is really simple but would sure appreciate some help

---

### Post by nonewmsgs on 2007-09-18
ill be honest mate, i never did well with the native dvd ripping tools.  i would recomend getting dvd decryptor and wine and set dvd decrpytor to run as winnt40.  if you need me to go into more detail, just ask.

---

### Post by kfrance on 2007-09-19
I usually use acidrip. It works for me. I never got dvdrip to work well for me.

---

### Post by flobadobblibblobbleep on 2007-09-19
Thanks guys its nice to know that I am not on my own with this. If I do find a fix I will post it and failing that will try your recommendations tarra-a-bit

---

### Post by flobadobblibblobbleep on 2007-09-20
I have now got past the problem. On dvdrips edit preferences tab there is another tab called CD burning, the first line says: 
Writer device file /dev/cdrom
the second line says:
cdrecord device [n,n,n or filename] 0,x,0
I substituted /dev/cdrom for 0,x,0 and everything worked.
Now all I have to do is figure out how to drive it, now seriously I ripped and transcoded my first DVD it wasn't in quite the format that I expected but it did work.
Thank you once again for your suggestions I might still come back to them
Tarrabit

---

