---
title: "Script problems (output of variables) with cron"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Bluecircle on 2007-06-23
I wrote a script, which works fine manually, but when it is ran by cron there are 2 variables that do not display for some reason.

```

fort=$(fortune -u)

cpu=$(procinfo)

```


Which are written to an HTML file as:

```

<pre>$fort</pre>

	<b>System Info</b>
<br><br>
	<pre>$cpu</pre>

```

All the others work fine, and this is only a problem when running from cron. I tried changing the names around with no luck.

Any ideas?

---

### Post by gabkdlly on 2007-06-23
I think that by default, cron runs your scripts using sh. You might want to try telling cron specifically to run your scripts using bash instead. I am guessing you used bash to run your scripts when you ran them "manually".

---

### Post by Bluecircle on 2007-06-23
> **gabkdlly said:**
> I think that by default, cron runs your scripts using sh. You might want to try telling cron specifically to run your scripts using bash instead. I am guessing you used bash to run your scripts when you ran them "manually".

Ok, I tried a few things. Running procinfo through either bash or sh works fine in gnome-terminal/xterm

if I run procinfo in crontab, or fcrontab, and have it output to a file, the file is made but it is empty. 

fortune now works in in fcrontab. I don't know why...

---

### Post by keithweddell on 2007-06-23
Could be a PATH thing.  Try adding a line near the top of your script something like:

PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin


Keith

---

