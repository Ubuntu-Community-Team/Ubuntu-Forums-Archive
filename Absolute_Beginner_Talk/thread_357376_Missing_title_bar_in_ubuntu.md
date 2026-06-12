---
title: "Missing title bar in ubuntu"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by Garren1138 on 2007-02-09
I'm missing a the option to use the close button minimize button and the maximize button I don't know why they disappeared the only thing I did was boot up compiz and then compiz froze I have rebooted my computer a few times now and it hasn't brought back the boarders Here's a pick of what it looks like:

[http://www.flickr.com/photo_zoom.gne?id=384873166&size=o](http://www.flickr.com/photo_zoom.gne?id=384873166&size=o)

I don't know how to get this back. I do have the boarder on my other logins but this one does not have it.

Please help me get this back.  Thanks for any feedback.

---

### Post by riven0 on 2007-02-09
Alright, go to Applications >> Accessories >> Terminal and type: **metacity --replace**

If that doesn't work, try to close down compiz and then replace with metacity:

**sudo killall compiz && metacity --replace**

---

