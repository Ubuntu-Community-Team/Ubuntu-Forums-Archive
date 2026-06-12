---
title: "Tiny Icons and Root access"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by okok on 2006-07-29
1. I just installed Ubuntu on my machine. I was able to solve problems of incorrect display resolution and refresh rate by editing xorg.conf, but now there is a problem I don't know how to solve: desktop items are now so tiny they are hardly visible. How do I change that?

2. I find the fact one is not supposed to be able to log in as root annoying. What is the reason for this unusual configuration, and can I change it so I can log in as root?

---

### Post by dio525i on 2006-07-29
1. i think if you right click on hte icons you can stretch/resize them from a context menu selection (stretch icon i think)

2. SYSTEM>ADMINISTRATION>LOGIN WINDOW
         then...
   Security tab...look halfway down to the Security section and you'll see "Allow...blah blah blah" and click the box and you'll be good as gold

---

### Post by okok on 2006-07-29
Thank you. I tried the 'stretch icons' option, but it just temporarily changed slighly the way they look (I can't see much, because they are about 4 pixels wide and 5 or 6 pixels wide after streching...).

---

### Post by dio525i on 2006-07-29
there's a way to do it i found from clicking around...but i'm a noob too so i can't remember right now...sorry...maybe a guru will help...sorry bud...try typing "how to resize icons ubuntu"

---

### Post by okok on 2006-07-29
I just found the solution. The desktop icon size is taken from the Nautilus icon view settings. I chnaged that from %25 to %100, and now the desktop icons are back to their normal size.

Thanks for the help.

---

### Post by jd65pl on 2006-07-29
There isn't really much need to login as root and this action gives less secure computing. Ubuntu uses the "sudo" method

---

### Post by okok on 2006-07-29
In fact, I was considering changing to a different dstribution just because of this. I suppose that your need to access root depends on the way you work. If you prefer to use gui applicaitons, then launching them from a terminal window may be annoying. As to the security question, I believe that having root as a separate user with a different password adds a measure of security, because it makes it harder for regular users to make rush decisions.

---

