---
title: "Hoe to change the keyboard layout"
date: 2010-01-01
forum: Apple Hardware Users
---

### Post by flummiht on 2010-01-01
I downloaded and installed Ubuntu Linux 9.10 in English. The system uses a US keyboard layout and this is the only one I can choose in preferences.

Does anyone happen to know how I can get a German keyboard?

And how can I set the numeric keypad to numeric permantly?

Thanks for your help.

---

### Post by SuperSonic4 on 2010-01-01
You could try changing ```
/etc/locale.gen
```

uncomment the DE lines and comment the US ones

---

### Post by flummiht on 2010-01-01
> **SuperSonic4 said:**
> You could try changing ```
/etc/locale.gen
```uncomment the DE lines and comment the US ones

It says ... /etc/locale.gen: No such file or directory

---

### Post by flummiht on 2010-01-02
Okay, found it. 

For those who have the same problem, here's how:

Got to 'System' --> 'Preferences' --> 'Keyboard'

Select the tab 'Layouts'

From there on you should be able to select the German keyboard.

Good luck.


> **flummiht said:**
> I downloaded and installed Ubuntu Linux 9.10 in English. The system uses a US keyboard layout and this is the only one I can choose in preferences.

Does anyone happen to know how I can get a German keyboard?

And how can I set the numeric keypad to numeric permantly?

Thanks for your help.

---

### Post by buschi on 2010-01-02
> **flummiht said:**
> I downloaded and installed Ubuntu Linux 9.10 in English. The system uses a US keyboard layout and this is the only one I can choose in preferences.

Did you do Systen -- Preferences -- Keyboard -- Layouts -- **Add...** ?

You should be able to add the German layout there. Then remove the US one, set the DE as default and it should work.....

---

### Post by buschi on 2010-01-02
> **flummiht said:**
> 
how can I set the numeric keypad to numeric permantly?


does
[https://help.ubuntu.com/community/NumLock]("https://help.ubuntu.com/community/NumLock")
help?

---

### Post by flummiht on 2010-01-02
> **buschi said:**
> Did you do Systen -- Preferences -- Keyboard -- Layouts -- **Add...** ?

You should be able to add the German layout there. Then remove the US one, set the DE as default and it should work.....

Yes, I did and the keyboard is now available. I removed the US keyboard but after reboot it's there again.

---

