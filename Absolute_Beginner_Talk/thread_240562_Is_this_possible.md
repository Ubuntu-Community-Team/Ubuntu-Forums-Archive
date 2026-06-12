---
title: "Is this possible?"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Crash-n-Burn on 2006-08-21
This would be like a KVM switch. 

Hook up a windows pc to one moniter and a linux pc to another moniter, and have the ability to use one mouse and keyboard to control both at the same time. I would be able to just move the mouse over and have linux at my disposal and vice versa. There would need to be some kind of hardware and softare that lets each computer know when the mouse is on their side.

Like extending windows to a 2nd moniter but linux being that 2nd moniter.

Any ideas?

---

### Post by Ozitraveller on 2006-08-21
deleted

---

### Post by Burke on 2006-08-21
yup. it's called synergy.  it's a software-only solution and shares the kb/mouse cross-platform over the network connection. It's easy to set up on both linux and windows.

```
sudo apt-get install synergy
```

you'll have to enable the iniverse repository for that (google it).

Find the client for windows (google), then configure.

---

### Post by Crash-n-Burn on 2006-08-21
A KVM switch is usually for one moniter and one mouse and keyboard. I'm talking about running linux on one moniter and windows on the other at the same time with the ability to control both with a simple movement of the mouse.

Edit:

You can hook up 3 computers to one moniter and one kvm switch but you would need to hit the button in order to switch from moniter to moniter, but it would work. I wonder if you could make it a seamless scroll transition.

---

### Post by Burke on 2006-08-21
this is my synergy conf (~/.synergy.conf)
```

section: screens
  burke-gw-ubuntu:
  burke-d4400-ubuntu:
end
section: links
  burke-gw-ubuntu:
    left = burke-d4400-ubuntu
  burke-d4400-ubuntu:
    right = burke-gw-ubuntu
end

```


just run "synergys" on your linux computer, then set up your windows computer to connect to it using synergy (iirc, there's a nice GUI for windows, so it shouldn't be a problem)

(synergy provides your seamless scroll transition)

---

### Post by Crash-n-Burn on 2006-08-21
> **Burke said:**
> yup. it's called synergy.  it's a software-only solution and shares the kb/mouse cross-platform over the network connection. It's easy to set up on both linux and windows.

```
sudo apt-get install synergy
```

you'll have to enable the iniverse repository for that (google it).

Find the client for windows (google), then configure.


Damn, and I thought I was original.
I'm going to try to get my Windows, Mac, and Linux running on 3 moniters.

---

### Post by Burke on 2006-08-21
Good luck. It's sooo easy to set up, you shouldn't have any trouble. I just set it up today, and I'm loving it. ;)

---

### Post by jaybmx on 2006-08-21
synergy is very cool!

---

