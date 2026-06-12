---
title: "My internet won't stay connected"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by meme on 2006-03-29
hello there wonderful and helpful people!

I am very new to Ubuntu, and have just got my computer set up on the internet.  however, when I don't use the internet for a while it seems to disconnect.  I remember that when I did the pppoe config (i think that was what it was) it asked me a bunch of questions and I agreed to it all, becuase I didn't know what it meant (maybe not the brightest idea).  So i think maybe I told it to do this, but i don't know how to reverse it.  it's not a problem if i'm around cause I can just do the pon thing but if i leave and want to download something whilst away from the computer it gets to be annoying.  

any help would be SOO much appreciated.

Thanks in advance :D 

meme

---

### Post by ispmarin on 2006-03-29
You can do a pppoeconf and sees if helps.

---

### Post by xlib on 2006-03-29
Are you sure it isn't your ISP dropping the connection?

---

### Post by meme on 2006-03-30
no, i'm not sure. hehe.  but I don't know why my isp would be doing that, it doesn't seem sensible.  but of course, isps aren't necessarily known for their sensibility.  how could i find out if it's the isp dropping the connection or my system?

thanks again!

---

### Post by Christmas on 2006-03-30
[QUOTE=meme]no, i'm not sure. hehe.  but I don't know why my isp would be doing that, it doesn't seem sensible.  but of course, isps aren't necessarily known for their sensibility.  how could i find out if it's the isp dropping the connection or my system?

thanks again![/QUOTE]

Call them :)

---

### Post by Mustard on 2006-03-30
[QUOTE=meme]no, i'm not sure. hehe.  but I don't know why my isp would be doing that, it doesn't seem sensible.  but of course, isps aren't necessarily known for their sensibility.  how could i find out if it's the isp dropping the connection or my system?

thanks again![/QUOTE]

My ISP has a 20 minute idle time disconnect.  To get around this I have a mail notification program running, that checks my email every five minutes.  Try to have something running that uses your connection on a frequent basis, like an instant messenger program of some kind or even log into IRC with a chat client and just idle in the channel.

---

### Post by sailor2001 on 2006-03-30
somewhere along the line:  ping -t [www.anyurl.com](www.anyurl.com) will ping that site at certain times you set up so the isp will always see you are working the machine

---

