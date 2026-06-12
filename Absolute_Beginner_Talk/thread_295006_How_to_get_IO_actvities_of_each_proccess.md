---
title: "How to get I/O actvities of each proccess"
date: 2006-11-07
forum: Absolute Beginner Talk
---

### Post by vanthai26 on 2006-11-07
Hi...

Does any one know how to get the I/O actvities of each proccess running under Ubuntu. I want to know which process do the most writting to disk and which one does the least writing. I am absolutely new to linux and stuck on this problem..

Any hint is greatly apprecieted
Thanks for your help

Bar

---

### Post by MyAnda on 2006-11-07
I am not sure off hand...is there a larger issue you are looking into? if i was looking into it i would likely use
ps
top
vmstat

sudo apt-get install sysstat
(sar, iostat and mpstat)

also came across this [http://www.opersys.com/LTT/](http://www.opersys.com/LTT/)

post again if you need help

---

### Post by po0f on 2006-11-07
vanthai26,

[Please don't triple post](http://www.ubuntuforums.org/search.php?searchid=9587672).  Someone has answered your question several times.  Post back in the original thread what problems you are having, don't start a new thread expecting a different answer.

---

