---
title: "Internet Connection Problems?"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by Deaf_Head on 2005-12-13
Firefox acts slow, and loads pages slow. Konqueror is about the same .. wtf? Is there some settings i should play with or what?

---

### Post by cwaldbieser on 2005-12-13
[QUOTE=Deaf_Head]Firefox acts slow, and loads pages slow. Konqueror is about the same .. wtf? Is there some settings i should play with or what?[/QUOTE]
[http://ubuntuforums.org/showthread.php?t=87643]("http://ubuntuforums.org/showthread.php?t=87643")
Check out the section on IPv6.
Also, in Firefox, put about:config in the URL bar, and then search for IPv6 and turn that option off.
For Konqueror, add the following to /etc/environment (you might have to create the file if it doesn't exist):
```

KDE_NO_IPV6=true

```

---

