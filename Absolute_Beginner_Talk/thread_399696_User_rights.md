---
title: "User rights"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Liam1964 on 2007-04-02
I have just done something stupid can anyone help me fix it please.

I have just turned off the Admin rights of my only user. Can I turn them back on with a SUDO command?

Also, why can I not log in as root? I have set the password, but when I try to log in I am told I cant log in from there as an administrator. "There" being the initial startup screen.

---

### Post by justin whitaker on 2007-04-02
> **Liam1964 said:**
> I have just done something stupid can anyone help me fix it please.

I have just turned off the Admin rights of my only user. Can I turn them back on with a SUDO command?

Also, why can I not log in as root? I have set the password, but when I try to log in I am told I cant log in from there as an administrator. "There" being the initial startup screen.

You have to enable Root login via the admin tools. It's under the GDM/Sessions (I forget which). You could Sudo it, but it might be easier to do it via GUI.

---

### Post by Liam1964 on 2007-04-02
Sorry I think you have missed the first part of my question/statement. I have turned off the admin rights of my only user, so now I have no admin tools.

Can meone please tell me if I can adjust a users rights using a command line and not a gui

---

### Post by justin whitaker on 2007-04-02
> **Liam1964 said:**
> Sorry I think you have missed the first part of my question/statement. I have turned off the admin rights of my only user, so now I have no admin tools.

Can meone please tell me if I can adjust a users rights using a command line and not a gui

Yeah, I did miss that. 

Try this:

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

At the bottom, psychocats walks you through how to repair a broken sudo situation.

---

### Post by Liam1964 on 2007-04-02
Thank You! That looks like a great site, I shall read some more!!!

So glad nobody asked why I turned it off in the first place.

---

