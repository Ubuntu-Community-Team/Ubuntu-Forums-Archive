---
title: "New to Ubuntu/Linux - a few simple questions"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by jondecker76 on 2006-12-19
Hello

I just installed Ubuntu yesterday and I'm extremely impressed - enough that I'm going to ditch Windows all together on all computers in my house. I am new to Linux in general (aside from doing some routine things on web servers such as CHModdding etc). However, I have also been programming c/c++ for over 10 years so I'm by no means computer illiterate.

So here is my question..  I was looking through gnome-look for some new themes..  I noticed that there were GTK 1 and GTK 2 themes.. How do I know which one I have?  I am running Ubuntu 6.10

thanks all

Jon

---

### Post by LookTJ on 2006-12-19
> **jondecker76 said:**
> So here is my question..  I was looking through gnome-look for some new themes..  I noticed that there were GTK 1 and GTK 2 themes.. How do I know which one I have?  I am running Ubuntu 6.10

thanks all

Jon

Ubuntu 6.10 has GTK 2

---

### Post by ArtechnikA on 2006-12-19
> **Taylor said:**
> Ubuntu 6.10 has GTK 2

That's good to know, and thanks for posting the response - but it's the answer to a different question.  I'm actually interested in knowing the answer to the original question, too, which was: How do I -know- which version I've got?

More generally - for a system component like GTK - what is the process by which one verifies the actual installed and running version?

---

### Post by Bachstelze on 2006-12-19
```
dpkg -l | grep gtk
```

Will give you several infos of all packages whose names contain "gtk", including version numbers. Mind it's a lowercase L - for list - not au uppercase i.

---

### Post by LookTJ on 2006-12-19
> **ArtechnikA said:**
> That's good to know, and thanks for posting the response - but it's the answer to a different question.  I'm actually interested in knowing the answer to the original question, too, which was: How do I -know- which version I've got?

More generally - for a system component like GTK - what is the process by which one verifies the actual installed and running version?

try

```
sudo apt-cache policy libgtk2.0-0
```

---

