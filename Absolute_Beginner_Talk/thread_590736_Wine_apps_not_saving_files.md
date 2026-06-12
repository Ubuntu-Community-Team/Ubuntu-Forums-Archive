---
title: "Wine apps not saving files"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Alan Stancliff on 2007-10-25
Several Wine applications I have installed seem to be unable to save files. I'm pretty new at this. Should I only save files in Wine's My Documents? I have to kill the programs because they just keep trying to save.

---

### Post by magicman5421 on 2007-10-25
I think this is a question for wine's forums, not ubuntu's.

---

### Post by TeaSwigger on 2007-10-25
> **Alan Stancliff said:**
> Several Wine applications I have installed seem to be unable to save files. I'm pretty new at this. Should I only save files in Wine's My Documents? I have to kill the programs because they just keep trying to save.

Yes. In a terminal (or the "run" box) enter

```
winecfg
```

Take a look over the tabs "Desktop Integration" and "Drives" - it might start to make sense what's going on. WINE is sort of a go-between of the linux OS and windows programs, translating for instance your home in linux ( /home/your_id ) to the equiv to a windows program ( C:\Documents and Settings\your_id\My Documents ) so they'll work in it. Well that's simplifying a ton but you get the idea. You can customize those settings in winecfg once you understand what is going on. Luck :)

---

### Post by Alan Stancliff on 2007-10-25
> **TeaSwigger said:**
> Yes. In a terminal (or the "run" box) enter

```
winecfg
```

Take a look over the tabs "Desktop Integration" and "Drives" - it might start to make sense what's going on. WINE is sort of a go-between of the linux OS and windows programs, translating for instance your home in linux ( /home/your_id ) to the equiv to a windows program ( C:\Documents and Settings\your_id\My Documents ) so they'll work in it. Well that's simplifying a ton but you get the idea. You can customize those settings in winecfg once you understand what is going on. Luck :)

Thanks for the hint, TeaSwigger. I did as you suggested and did not see anything in those settings that shed any light on my problem. I am tempted to uninstall and then reinstall Wine to see if that makes a difference. It seems that every app I tested in Wine has this problem, and I have been googling and searching for the answer. 


> **magicman5421 said:**
> I think this is a question for wine's forums, not ubuntu's.

Hi MagicMan. I went to the Codeweaver's site and poked around for about a half hour, dazed by data overload. Eventually I came up to their "forum," which is not really usable for general-purpose questions such as I posed above. The sections all seem to be around specific applications, and the ones I was having difficulty with had not been tested. In short, posting there was impractable. Any links to other more-helpful forums you may know about would be most appreciated.

---

