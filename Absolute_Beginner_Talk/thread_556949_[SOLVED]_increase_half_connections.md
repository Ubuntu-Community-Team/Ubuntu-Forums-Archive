---
title: "[SOLVED] increase half connections"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by NaSiO6 on 2007-09-22
hey!
i am experiencing some speed issues with my net, even more while i am downloading torrents. Is it possible that number of half connection are limited(like windows)?
if so, how can i increase the limit.
i haven't thought of any other reason for this, so, as of now, increasing the half connections seems to be the most sensible thing...
Could you please suggest what else could be wrong?

Thanks

---

### Post by dpar on 2007-09-22
I don't believe there are any restrictions.....what torrent client are you using??

---

### Post by jimrz on 2007-09-22
> **NaSiO6 said:**
> hey!
i am experiencing some speed issues with my net, even more while i am downloading torrents. Is it possible that number of half connection are limited(like windows)?
if so, how can i increase the limit.
i haven't thought of any other reason for this, so, as of now, increasing the half connections seems to be the most sensible thing...
Could you please suggest what else could be wrong?

Thanks

it is possible that your isp is "capping" torrent traffic. here Comcast Cable is, at least on a rolling basis.

---

### Post by Soarer on 2007-09-22
> **jimrz said:**
> it is possible that your isp is "capping" torrent traffic. here Comcast Cable is, at least on a rolling basis.

That is common here in the UK as well. Torrents also run much faster (so I am told :)) if you forward the torrent ports from your router to the PC doing the down/upload.

---

### Post by NaSiO6 on 2007-10-02
hey!
thanks a lot for the replies.
well, i had not noticed but my firefox speeds were extremely bad too(I have just started using Ubuntu).
I disabled ipv6 and things are working fine as of now...[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html]("http://www.ubuntugeek.com/speed-up-firefox-web-browser.html")

or maybe its just an illusion of a download fanatic!!
i just want to make sure i have disabled ipv6 for the _whole_ system and not just firefox(if that makes sense), but i am not sure how to do that.

Thanks in advance!

---

### Post by NaSiO6 on 2007-10-19
ok.. incase any other people are facing the speed issue(and reading this thread)

[http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798) - this thread shows you how to disable ipv6 of your system, which speeds up the internet.

basically you need to 
```
create file named bad_list in /etc/modprobe.d containing this line:
alias net-pf-10 off
```

and then reboot

---

