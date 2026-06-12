---
title: "VNC viewer COLLEGE"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by ritterrav on 2007-08-24
Ok,  i installed ubuntu on my gf's laptop and im trying to get her to use it rather then vista, she likes it, but there are things she does not know how to do, and i need to do for her. So i want to use VNC viewer i have used it before to fix her laptop with ubuntu updates and a sound card issue, so my question is now, she is in COLLEGE and she is (i think) behind a router, because the IP is a little wierd, but i want to know how i can still access her ubuntu if she is in college and she is behind a router and it is most likely that she cannot access the router to make any changes to port forward...

sooo... what can i do?

---

### Post by beercz on 2007-08-24
Have you tried ssh -X ?

---

### Post by ritterrav on 2007-08-24
what is that? also, if i port scan her IP and find a open port can i use that for VNC?

---

### Post by beercz on 2007-08-24
ssh is Secure SHell - it allows remote access to another machine running the ssh deamon (i.e. the machine becomes an ssh server).

I think in vnc passwords are not encrypted, and therefore not secure, and not recommended for use over the internet.

ssh is much more secure.

See [https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29]("https://help.ubuntu.com/community/SSHHowto?highlight=%28ssh%29")

Ask if you need more specific help.

---

