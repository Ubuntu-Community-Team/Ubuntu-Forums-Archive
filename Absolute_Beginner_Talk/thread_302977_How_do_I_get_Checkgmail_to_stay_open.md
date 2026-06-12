---
title: "How do I get Checkgmail to stay open?"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by voodoonirvana on 2006-11-19
I changed my password for my gmail account, and then a little box popped open with something having to do with the password. So I typed in the new password and made sure to keep "remember password" checked. Well now the little icon isn't even in my toolbar thing anymore, and I don't think checkgmail has a GUI. It will stay open when I open it with the terminal, but obviously when you close the terminal the program closes too. What should I do?

---

### Post by jordanmthomas on 2006-11-19
Press Alt + F2 and run it from there.
It should live for your entire Gnome session.

---

### Post by Perfect Storm on 2006-11-19
```
gnome-session-properties
```

Go to Startup programs tab and add:

```
gmail-notify
```

Then gmail notify will start everytime you login.

---

### Post by voodoonirvana on 2006-11-19
> **Artificial Intelligence said:**
> ```
gnome-session-properties
```

Go to Startup programs tab and add:

```
gmail-notify
```

Then gmail notify will start everytime you login.

Thanks! :)

---

