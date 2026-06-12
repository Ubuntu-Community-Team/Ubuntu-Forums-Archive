---
title: "Can't access some sites"
date: 2007-02-12
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-02-12
I am trying to fix somebody else's computer right now. For some reason, this Windows XP PC can't access some sites.

In another computer which is connected to the same DSL where this PC is connected to, there are some sites that it can access that this PC cannot.

What could the reason be?

What additional information can I give for you to have an idea on what the problem is?

Thanks! 

:guitar:

---

### Post by arochester on 2007-02-12
Is there a firewall capable of rejecting/blacklisting some sites?

---

### Post by al1b1 on 2007-02-12
I had the same problem with my windows too. When irang hp support the only thing they recommended was reinstallin windows. Worked for me

---

### Post by Trance Gemini on 2007-02-12
In windows the problem may be in hosts file located in Windows/System32/drivers/etc/hosts. There may be rows like:
127.0.0.1 [www.somesite.com](www.somesite.com)

They mean that when you write an address like [www.somesite.com](www.somesite.com) you get to 127.0.0.1 whih is a loopback to your own network card. In result you get "no page found".

---

### Post by highneko on 2007-02-12
My router is able to block urls that match a pattern. It would be kinda obvious sometimes tho because it says administer blocked access or something. Just an idea.

---

