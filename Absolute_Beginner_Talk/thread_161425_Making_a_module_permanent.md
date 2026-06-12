---
title: "Making a module permanent"
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by json684 on 2006-04-17
I am sure this is an easy answer, but I can't find it. Here is my situation:

I have a wireless card built into my laptop. It uses the ipw2200 module. The problem is that I have a LED that indicates when the wireless is enabled. It won't light up initially. The wireless will work but the LED won't light up. I end up doing this:
```
 rmmod ipw2200
modprobe ipw2200 led=1
```

And then all is happy and I have my little LED. So how do I make that permanent?

---

### Post by tigrux on 2006-04-17
[QUOTE=json684]I am sure this is an easy answer, but I can't find it. Here is my situation:

I have a wireless card built into my laptop. It uses the ipw2200 module. The problem is that I have a LED that indicates when the wireless is enabled. It won't light up initially. The wireless will work but the LED won't light up. I end up doing this:
```
 rmmod ipw2200
modprobe ipw2200 led=1
```

And then all is happy and I have my little LED. So how do I make that permanent?[/QUOTE]

I guess you can add
> 
options ipw2200 led=1


to /etc/modprobe.d/options

---

