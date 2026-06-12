---
title: "Creating links for all files in folder?"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by HedonismBot on 2006-10-06
Hi everybody!

Is there any way to create symbolic or hard links for all the files in one folder with a single command? Using * as a catch-all doesn't work with the ln command, I I don't wanna have to manually create links for over 90 files! [-( 

So if there's either a command that'll create links for all the files in a dir or a bash/python/perl/php script that'll do it, it would really save my ***.

Thanks a million, this community is amazing :mrgreen: 

Also note: I need to do this remotely on Dapper Server, no GUI! :rolleyes:

---

### Post by CatKiller on 2006-10-06
I just tried ```
ln -s u* Desktop/
``` and that successfully made symlinks on the Desktop for the two files I had in my Home folder. In fact, I just made a directory called ~/test and ```
ln -s * test/
``` worked too - made links to all the files, but not directories, as you'd expect. So maybe you're just not doing it right? ;)

---

### Post by HedonismBot on 2006-10-10
All good, d'oh!

BUT...how does one make the links accesable to a web client? I'm simply trying to allow for links to be called from a webpage without having hardlinks to the real files. The files live on an intranet but must be called into a public DIR for download over a WWW front end. I get a "You do not have permission to access this file" error. :(

Thanks y'all!

I apologize.....FOR NOTHING!

---

### Post by mssever on 2006-10-10
> **HedonismBot said:**
> All good, d'oh!

BUT...how does one make the links accesable to a web client? I'm simply trying to allow for links to be called from a webpage without having hardlinks to the real files. The files live on an intranet but must be called into a public DIR for download over a WWW front end. I get a "You do not have permission to access this file" error. :(

Thanks y'all!

I apologize.....FOR NOTHING!

That error is undoubtedly the result of the files not being world-readable. Assuming you used symlinks instead of hard links, do ```
chmod a+r original_files
```Sometimes, you'll have to do something with too many files for a single command to handle. For that, type
```
for i in *.html; do
ln -s "$i" /destination/
done
```

---

### Post by HedonismBot on 2006-11-06
Still no luck! ! ! ](*,) 

I have follow links on in httpd.conf, I made them readable, changed chown values...nothing, still doesn't work...anyone else have any ideas :(

---

### Post by mssever on 2006-11-06
Look for errors in /var/log/apache2/error.log and other logs. If they don't pinpoint your problem, post the relevant portion of your log.

---

