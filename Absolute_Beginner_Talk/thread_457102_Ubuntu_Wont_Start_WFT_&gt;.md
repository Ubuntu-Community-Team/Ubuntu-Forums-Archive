---
title: "Ubuntu Wont Start WFT &gt;?"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by joelcont on 2007-05-28
[B][COLOR="DarkOrange"]Today in the morning i opened ubuntu i put my username my pasword but my desktop wont show ... i just c an orange background and sometimes i see the orange background plus a white square on my left top corner .. lol      
  i had had like 1 month without using xp and im back again :(  is there a repair mode to ubuntu or something ?
Thank you[/COLOR][/B]

---

### Post by viciouslime on 2007-05-28
> **joelcont said:**
> [B][COLOR="DarkOrange"]Today in the morning i opened ubuntu i put my username my pasword but my desktop wont show ... i just c an orange background and sometimes i see the orange background plus a white square on my left top corner .. lol      
  i had had like 1 month without using xp and im back again :(  is there a repair mode to ubuntu or something ?
Thank you[/COLOR][/B]

When you get to the login screen, click the button in the bottom right... I can't rememebr what it says now, options maybe? Anyway change your session to safe mode and see if that works.

Have you enabled compiz/beryl?

---

### Post by joelcont on 2007-05-28
nope no beryl no compiz
i will don dat rite now 1 min .......;)

---

### Post by joelcont on 2007-05-28
naaaaaaaw men not working i tried the failmode thing and this other types of session ...same thing ...:(

---

### Post by Lucifiel on 2007-05-28
What software did you install before you shut down Ubuntu?

Also, did you make any changes to Ubuntu like editing xorg.conf ?

---

### Post by joelcont on 2007-05-28
installed a new theme ..but went back to the regular ...before restarting

and i did not edited the config thing

---

### Post by joelcont on 2007-05-28
no help ? just reinstall ubuntu ?

---

### Post by Hobo Joe on 2007-05-28
Did you get the new kernel update?

Becuase it's causing lots of problems with graphics drivers.

---

### Post by joelcont on 2007-05-28
i might ...i always update with out question ...

---

### Post by Hobo Joe on 2007-05-28
Ok, then you should reinstall your graphics drivers.

First, boot into recovery mode, then type:
```

sudo aptitude install envy

```
Then run it with:
```

envy -t

```
Then use the on-screen instructions to uninstall, and then reinstall your drivers with respect to the manufacturer.(ATi, nVidia)

EDIT:
Ok, don't use capitals on Envy, I just realized that.

---

### Post by joelcont on 2007-05-28
ok im going to try rite now

---

### Post by bone43 on 2007-05-28
> **joelcont said:**
> i might ...i always update with out question ...


 check here..

[http://ubuntuforums.org/showthread.php?t=456662](http://ubuntuforums.org/showthread.php?t=456662)

 It would seem that 2-6-20-16 is causing a lot of problems.

---

### Post by joelcont on 2007-05-28
:(:( i read and i read but i cant manage to understand ..im sorry ..well if theres no more to do and u tell me to reinstall i will do it ....thank you

---

### Post by Outrunner on 2007-05-28
Well you probably still have your other kernel installed so when you boot up, a grub menu should show up(if not, there will be a promp to press ESC for a few seconds before the system boots up). Now choose your previous kernel(2-6-20-15 most likely)

---

