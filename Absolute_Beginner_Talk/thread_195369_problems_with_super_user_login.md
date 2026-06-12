---
title: "problems with super user login"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Valshar on 2006-06-12
when I try to enter as a super user (su), he asks for the password (and yeah, I'm sure it's the right one) but he replies with 

su: Authentication failure

any ideas how to solve this? thanks in advance :D

---

### Post by u.b.u.n.t.u on 2006-06-12
Try sudo instead of su.

---

### Post by aysiu on 2006-06-12
You don't log in as root in Ubuntu.

[http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by Valshar on 2006-06-12
it's  like this, I'm trying to install the ati drivers file (.run), and I open the file and it tells me I have to do it as a super user, but I can't log in with the su. How can I try it with the sudo? Sorry for the newbish question =P

---

### Post by aysiu on 2006-06-12
What's wrong with "newbish questions"? What else is this forum for? Questions are always welcome.

I have no experience installing ATI drivers, but from the look of it, I'd guess it'd be something like ```
chmod +x driver.run
sudo ./driver.run
```

---

### Post by hotstovejer on 2006-06-12
You do it like this

```
sudo *command*
```

That's all there is, really. If you do anything installing wise on the command line, you have to enter sudo. Such as sudo apt-get, or sudo ./install.

After you enter that above, it will ask you for a password. Use your password. Everything should be groovy then.

Hope this helps!

Jeremy

---

### Post by Valshar on 2006-06-12
ok, it's done installing and it's a-ok, but openning the ATI Control Panel, it tells me it "doesn't provide the FireGL X11 extensions, and will operate only partially.", and my max resolution is still 1024. Is this what's supposed to happen, or what?

Thanks a lot for the help.

---

