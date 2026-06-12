---
title: "Media Keys don't work in Quod Libet anymore."
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by sunexplodes on 2007-02-16
I upgraded from quod libet 0.23.1 to 0.24 today, and my media keys no longer work. 

They are still mapped in System>Preferences>Keyboard Shortcuts, nothing else has changed, except i now have to control Quod Libet manually.

Help?

---

### Post by sunexplodes on 2007-02-16
bump

---

### Post by sunexplodes on 2007-02-16
Anyone?

---

### Post by hugmenot on 2007-02-17
Same here. When you start it from the shell there&#8217;s an error saying that it relies on deprecated dbus functions.
I already sent an email to the mailing list but it got stuck somehow.

---

### Post by sunexplodes on 2007-02-17
pretty strange. they still don't work after i reverted to 0.23.1.

---

### Post by hugmenot on 2007-02-17
It&#8217;s not QL that has changed it is some dbus-whatever update.

---

### Post by sunexplodes on 2007-02-19
Have you heard any updates? I would really like my media keys to work!

---

### Post by hugmenot on 2007-02-19
Could you write a bug report and send it to the QL mailing list? Apparently I got blacklisted, my mail didn&#8217;t come through.

---

### Post by Omegatron on 2007-04-23
Same here after upgrading to Feisty Fawn.  Dell Inspiron 8600

---

### Post by Incie83 on 2007-05-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/quodlibet/+bug/43464](https://bugs.launchpad.net/ubuntu/+source/quodlibet/+bug/43464) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				OK, I found a possible solution (it worked for me, in Feisty) at:

[http://ronny.haryan.to/archives/2007/05/11/d-bus-multimedia-keys-plugin-for-quod-libet/](http://ronny.haryan.to/archives/2007/05/11/d-bus-multimedia-keys-plugin-for-quod-libet/)

I hope this helps you.

---

### Post by Omegatron on 2007-05-29
> **Incie83 said:**
> 
I hope this helps you.

That works.  Remember that you have to enable the plugin before it will work.

---

### Post by tom957 on 2007-06-09
Thanks a bunch for the link. Hail quod libet!

---

### Post by fearpi on 2008-05-10
Woah, woah, wait. The "solution" is to use the plugin? So you guys *weren't* using it before? Because I *have* been using the plugin, and suddenly, with Hoary, it no longer works. Has anyone had *that* issue?

---

### Post by hugmenot on 2008-05-10
The fix to the plugin has been know for a while:
[http://lists.sacredchao.net/quodlibet/msg02017.html](http://lists.sacredchao.net/quodlibet/msg02017.html)

---

### Post by fearpi on 2008-05-10
Superb, thanks. Hopefully an updated script will be hosted on the official quodlibet site.

---

