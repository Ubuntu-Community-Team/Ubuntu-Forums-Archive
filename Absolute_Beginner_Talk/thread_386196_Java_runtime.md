---
title: "Java runtime"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by alphilli on 2007-03-16
I just installed Ubuntu and then installed Eclipse. When I attempted to start up Eclipse I got a message stating that I have to install Java.

I was surprised to see that Java was not already installed. Is it correct that Java is not included in the install of Ubuntu? If so, what do I have to go through to get it installed?

Thanks.

---

### Post by taurus on 2007-03-16
That's true.  Java does not install automatically so you have to do that by hand.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by alphilli on 2007-03-16
Thanks.

However, when I go to install Java I come across the statement: 

Sun Java5: In the GNOME panel, look for Applications -> Add/Remove... menu and click it. [COLOR="Red"]making sure to check the unsupported and proprietary software checkboxes[/COLOR] and search for Sun Java 5.0 Runtime in the Internet section, or install the sun-java5-bin package from a terminal (See InstallingSoftware guide).

I don't see any checkboxes on the dialog that results from selecting: Applications->Add/Remove.

What am I missing?

---

### Post by taurus on 2007-03-16
Are you using Edgy?  Go into synaptic and enable both universe and multiverse repos.  Reload it and then search for java in the Search field.

---

