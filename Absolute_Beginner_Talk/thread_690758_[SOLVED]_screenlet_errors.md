---
title: "[SOLVED] screenlet errors"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-02-07
ok. so i made my ubuntu box look like a mac cuz i got bored.
i've never had screenlets before but i decided i wanted some cuz i taught they'd look nice with the theme. so i installed the screenlets through synaptic and now when i open it i get the error shown it the first screen shot and when i try to install a screenlet i get another error shown in the second one. can someone please help me resolve this problem?

thank you!

---

### Post by ferdostar on 2008-02-07
> **RadiationHazard said:**
> ok. so i made my ubuntu box look like a mac cuz i got bored.
i've never had screenlets before but i decided i wanted some cuz i taught they'd look nice with the theme. so i installed the screenlets through synaptic and now when i open it i get the error shown it the first screen shot and when i try to install a screenlet i get another error shown in the second one. can someone please help me resolve this problem?

thank you!

Go to System -> Sessions -> Start up programs -> Add, than add "screenlets" for name and that command
 ```
/usr/local/share/screenlets-manager/screenlets-daemon.py
```

than restart, it should work

---

### Post by RadiationHazard on 2008-02-07
thanks!
the first error is fixed
the second one still remains though unfortunately...

---

### Post by ferdostar on 2008-02-07
> **RadiationHazard said:**
> thanks!
the first error is fixed
the second one still remains though unfortunately...
Where have you extracted the tar.gz files? You shold extract them in /usr/local/share/screenlets it will add them automaticly.
Secondly which version of screenlet do you have?

---

### Post by RadiationHazard on 2008-02-07
thank you so much!!!
now how do i make these come up on start up?

---

### Post by ferdostar on 2008-02-07
> **RadiationHazard said:**
> thank you so much!!!
now how do i make these come up on start up?

Just when you hit on a screenlet to enable/disable it in the screenlet manager, you chose "automaticly start at login"

ps if everything is fine mark that the thread is solved and have fun! ;)

---

### Post by RadiationHazard on 2008-02-07
i always do! =]
and thanks for all your help!!!!!!!

---

