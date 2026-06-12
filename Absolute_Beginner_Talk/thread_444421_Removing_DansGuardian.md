---
title: "Removing DansGuardian"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by ThePolemistis on 2007-05-15
I want to remove DansGuardian completely
I have read other threads, and they said I need to unlock the proxy settings for firefox before I uninstall it

How do i unlock the firefox proxy settings without a download? CUrrently, my DansGuardian doesnt even let me download anything. 

And secondly, what commands do I type in to remove DansGuardian? will sudo apt-get remove dansguardian suffice after this?

Thanks

---

### Post by ThePolemistis on 2007-05-15
OKay i have decided to remove dansGuardian via sudo apt-get remove DansGuardian
BUT!!!
Firefox no longer works

I can ping google.com and it works fine, with no packets lost (in the terminal).... but firefox is no longer working....

Anyone know how i should proceed???

---

### Post by JoshHendo on 2007-08-19
```

sudo firehol stop

```

This will stop the firewall, which is what is blocking Firefox when you stop DansGuardian. It is what makes sure that you don't bypass DansGuardian. You should be able to remove it, though you will need to restart your computer.

If for some reason you can't access the Internet in Firefox, reinstall both firehol and dansguardian.

- Josh

---

### Post by Achetar on 2008-02-28
Thanks JoshHendo!

---

### Post by Oldsoldier2003 on 2008-02-28
> **ThePolemistis said:**
> OKay i have decided to remove dansGuardian via sudo apt-get remove DansGuardian
BUT!!!
Firefox no longer works

I can ping google.com and it works fine, with no packets lost (in the terminal).... but firefox is no longer working....

Anyone know how i should proceed???

in the future to perform a cleaner uninstall (get rid of configuartion files) you can do apt-get purge <packagename> if you are really sure you want to get rid of a package

---

