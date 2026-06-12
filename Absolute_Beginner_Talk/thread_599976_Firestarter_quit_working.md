---
title: "Firestarter quit working ?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-11-01
Hello, I am fond fan of Firestarter, but now it appears that it is not working like it should.
I do not have port 80, 443 or 21 open, yet when I do a portscan from Network Tools, it says that I do have those ports open.

I know how to use firestarter, have checked in it, the ports are not enabled, have applied the policy, but yet the ports are still open.

Any ideas of how to resolve this, or a better firewall that I could try from the repositories ?
Thanks!

Dr Small

---

### Post by ofb on 2007-11-01
I rather like Guarddog.

Everything is locked off by default, so you have to know what protocols you wish to turn on, but the documentation is very good for guiding you through that.

If you need SMTPS for mail because your ISP has blocked 25, there is a trick until the newest Guarddog shows up at the repository.

> For future readers, the specific steps I used are:
1)in Guarddog, advanced tab,click 'New Protocol' then
create name SMTP, type TCP, port 465, click Apply.
2)next, pick 'protocol tab', 'internet zone',
expand the 'user defined' selections and check the
box for SMTP (which was created in step 1) above.
3) click 'Apply' and you should be done.

That said, you should really find out what's wrong with Firestarter.

---

