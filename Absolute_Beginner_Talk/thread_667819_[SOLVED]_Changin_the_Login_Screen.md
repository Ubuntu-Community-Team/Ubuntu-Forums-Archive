---
title: "[SOLVED] Changin the Login Screen"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by x02flash on 2008-01-14
Right now the Kubuntu login screen is the one that shows up, regardless of the fact that i'm using Ubuntu.
How do I change it?

---

### Post by nikoPSK on 2008-01-14
System->Administration->Logion Window

Enjoy,
nikoPSK

---

### Post by Pevichaey5 on 2008-01-14
System>>Administration>>Login Window

---

### Post by nikoPSK on 2008-01-14
> **thexero said:**
> System>>Administration>>Login Window
:p, you can add things too. there are login windows available at the many -look.org sites.

nikoPSK

---

### Post by sumguy231 on 2008-01-14
I'm pretty sure this will work:
1.)Go to a terminal.
2.)Run
```
sudo dpkg-reconfigure gdm
```
3.)Press tab and enter to select ok, then select gdm and select ok again.
4.)Done.

[QUOTE=everyone else]System>>Administration>>Login Window[/QUOTE]
I'm pretty sure that will only configure GDM, it sounds like the problem is that KDM is being used instead of GDM. Correct me if I'm wrong and that does allow you to change login managers.

---

### Post by nikoPSK on 2008-01-14
> **sumguy231 said:**
> I'm pretty sure this will work:
1.)Go to a terminal.
2.)Run
```
sudo dpkg-reconfigure gdm
```3.)Press tab and enter to select ok, then select gdm and select ok again.
4.)Done.

It's better to give him gui before he gets into this. :)

nikoPSK

---

### Post by x02flash on 2008-01-14
> **nikoPSK said:**
> It's better to give him gui before he gets into this. :)

nikoPSK

I've actually had to use the terminal quite a lot, and have gotten more familiar with it

The problem is that I don't have Login Window under System>Administration

I tried the terminal code, and selected GDM and it came up with the following:
```
alex@alex-laptop:~$ sudo dpkg-reconfigure gdm
 * Reloading GNOME Display Manager configuration...                              * Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.
```

And i don't know if that means it worked or not, I'm going to restart my laptop and see

---

### Post by sumguy231 on 2008-01-14
> It's better to give him gui before he gets into this. 

Perhaps, but I really don't think our suggestions do the same thing. I don't have a copy of GNOME handy to verify this, so I would appreciate it if you could tell me what that configuration screen actually does. It sounds like the equivalent configuration screen for KDM in Kubuntu, which doesn't allow you to switch login managers, only to configure a specific login manager.

> I tried the terminal code, and selected GDM and it came up with the following:
I don't think it worked, and I wouldn't reboot if I were you or you might be left without graphics. Try the same thing but like this instead:
```
sudo dpkg-reconfigure kdm
```

---

### Post by x02flash on 2008-01-14
> **sumguy231 said:**
> Perhaps, but I really don't think our suggestions do the same thing. I don't have a copy of GNOME handy to verify this, so I would appreciate it if you could tell me what that configuration screen actually does. It sounds like the equivalent configuration screen for KDM in Kubuntu, which doesn't allow you to switch login managers, only to configure a specific login manager.


I don't think it worked, and I wouldn't reboot if I were you or you might be left without graphics. Try the same thing but like this instead:
```
sudo dpkg-reconfigure kdm
```

Well, I did reboot, and I did get something, its now the Xubuntu login screen....
I'll give the kdm code a try

---

### Post by nikoPSK on 2008-01-14
> **x02flash said:**
> Well, I did reboot, and I did get something, its now the Xubuntu login screen....
I'll give the kdm code a try

LOL, yes, that should help :)

nikoPSK

---

### Post by x02flash on 2008-01-14
> **nikoPSK said:**
> LOL, yes, that should help :)

nikoPSK

I ran that and rebooted again
Nothing seemed the same, so I went to go see if I needed to download Login Screen in Synaptic, and there it was,

So, everything's all changed back now

Thanks Guys

---

### Post by nikoPSK on 2008-01-14
> **x02flash said:**
> I ran that and rebooted again
Nothing seemed the same, so I went to go see if I needed to download Login Screen in Synaptic, and there it was,

So, everything's all changed back now

Thanks Guys

No problem, please mark this thread as "SOLVED"

Regards,
nikoPSK

---

