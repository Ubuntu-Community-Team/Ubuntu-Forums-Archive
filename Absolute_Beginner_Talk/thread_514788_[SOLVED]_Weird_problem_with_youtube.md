---
title: "[SOLVED] Weird problem with youtube"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by zeta on 2007-08-01
Hi, 
please help me with my youtube-problem. For several weeks now only one in maybe 10 videos works. Firefox simply downloads forever, but doesn't get anything. Same thing when I try to get it manually: 
```
youtube-dl http://www.youtube.com/watch?v=_ImW0-MgR8I
Retrieving video webpage... done.
Extracting video URL parameters... done.
failed.
Error: unable to download video data.
Try again several times. It may be a temporal problem.
Other typical problems:

        Video no longer exists.
        Video requires age confirmation but you did not provide an account.
        You provided the account data, but it is not valid.
        The connection was cut suddenly for some reason.
        YouTube changed their system, and the program no longer works.

Try to confirm you are able to view the video using a web browser.
Use the same video URL and account information, if needed, with this program.
When using a proxy, make sure http_proxy has http://host:port format.
Try again several times and contact me if the problem persists.

```

---

### Post by atomkarinca on 2007-08-01
can you paste the video link so that i can double check?

---

### Post by zeta on 2007-08-01
Hi atomkarinca,
most links don't work, but this is the last I tried:
[http://www.youtube.com/watch?v=_ImW0-MgR8I](http://www.youtube.com/watch?v=_ImW0-MgR8I)

---

### Post by atomkarinca on 2007-08-01
well, i couldn't think of a solution but i guess you can go step by step.

are you having problem viewing other flash sites? if no, then this could be a youtube specific problem.

and you can't view this video with the browser, right?

---

### Post by zeta on 2007-08-01
Never had problems with other flash-sites. But the link itself seems to be good, since other people can open it just fine. And no, it is not just viewing through the browser, the download itself does not seem to work. Otherwise I should be able to download it with youtube-dl, right?

---

### Post by atomkarinca on 2007-08-01
it seems it's nothing to do with the flashplayer. so i'm assuming your connection with youtube is somehow corrupted (i may be wrong). can you try using 4.2.2.1 as your dns server?

---

### Post by zeta on 2007-08-01
Ok, this was (probably) it! My Laptop connected through two routers in repeater-mode, so they probably messed something up. I still don't understand why some videos worked - but it seems to be fine now. Thanks a lot for your ideas & support!:KS

---

