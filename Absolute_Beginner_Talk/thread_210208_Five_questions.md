---
title: "Five questions"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by Heffy on 2006-07-06
Being new to using Ubuntu and so used to using Windows for years I can see I will be have some questions that seem dumb to others.

Is there maintenance to do in Ubuntu like cleaning and defrag? 
 
If so where are the utilities?
 
Can I disable the login?

What's the equivalent to the windows registry in Ubuntu where settings are stored?

I installed two programs in Ubuntu one of them I can't find at all, it's called "xvidcap" for screen recording.  I need to find it and make a shortcut to it. How do I find the .exe to it?

---

### Post by aysiu on 2006-07-06
[QUOTE=Heffy]Being new to using Ubuntu and so used to using Windows for years I can see I will be have some questions that seem dumb to others.

Is there maintenance to do in Ubuntu like cleaning and defrag?
 
If so where are the utilities?[/quote] No.

>  
Can I disable the login? How would you use Ubuntu, then...?

> 
What's the equivalent to the windows registry in Ubuntu where settings are stored? There is no direct equivalent, but the /etc folder tends to have a lot of system-wide configuration files.

> 
I installed two programs in Ubuntu one of them I can't find at all, it's called "xvidcap" for screen recording.  I need to find it and make a shortcut to it. How do I find the .exe to it? There is no .exe. Usually the name of the command itself will launch the program. Try ```
xvidcap
``` If that doesn't work, you can try find the binary by looking in /usr/bin. Or you can also do ```
sudo updatedb
locate xvidcap
```

---

### Post by matthew on 2006-07-06
[quote=Heffy]Can I disable the login?[/quote]You can automatically log a user in if you like. If that is what you want, do this:

System->Administration->Login Window

Select the Security tab

Check Enable Automatic Login and input the user's name to login automatically

---

