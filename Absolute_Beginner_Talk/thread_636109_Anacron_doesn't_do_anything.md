---
title: "Anacron doesn't do anything"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Majorix on 2007-12-09
I have a script that I coded that I want to be exec'ed daily. To do this, I decided to use anacron.

I read a little, and found out that I had to edit /etc/anacrontab to include a launcher to my script. So I went ahead and added this line in it:
"1	0	dt	"python /path/to/script.pyc -arguments""
When I tried to test this with
"anacron -n"
nothing happened. The input passed to the next prompt in a blink. I also tried:
"anacron -n -t /etc/anacron"
"anacron -nf"
but again nothing happened. I tried removing the quotes in the /etc/anacrontab entry too.

Anacron doesn't even give errors. It is like the program exists, but it has an empty source code. I don't really understand.

Can somebody clarify this for me please?

---

### Post by bsell on 2007-12-09
Can you set it as a cron job and place it in your /etc/cron.daily directory?

---

### Post by Majorix on 2007-12-09
Didn't work.

---

### Post by Majorix on 2007-12-09
*bump*

---

### Post by Majorix on 2007-12-11
Another bump.

---

### Post by Majorix on 2007-12-15
Honestly does nobody know anything related to this? Help please :(

---

