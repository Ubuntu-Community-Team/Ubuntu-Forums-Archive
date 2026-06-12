---
title: "Empty Recycling Bin Periodically?"
date: 2011-04-07
forum: Any Other OS
---

### Post by dniMretsaM on 2011-04-07
My sister uses Windows 7 (yuck) and wants to have her recycling bin emptied periodically. I've looked around for something like this, but no results. She doesn't want the files to just delete themselves (which I can understand). So is there a way to do this or a task scheduler that would work? I also think this would be handy so is it possible on Ubuntu 10.10?

---

### Post by pricetech on 2011-04-07
I'm sure there are programs out there that do just that.

I like ccleaner for cleaning up a computer, but that may be more than what she wants to clean.  Look into the command line mode though and see if the switches will let you specify what to clean, then create a batch file and a scheduled task.

Our IT department has some stuff that does that, but I don't use it here.  I'll see if I can find it and pass the word along.

---

### Post by Derek Karpinski on 2011-04-07
Easy,
 
:P

---

### Post by Derek Karpinski on 2011-04-07
In all seriousness, you can set diskcleanup to run as a scheduled task with empty recycle bin as an option.
 
But, she doesn't want them to 'just delete themselves', but wants it automatically? Contradictory, no?

---

### Post by dniMretsaM on 2011-04-07
I think the reason she doesn't want the files to be automatically deleted instead of going to the recycling bin is because if she accedently deleted an important file she would lose it permanently instead of being able to restore it.

---

### Post by beew on 2011-04-08
Yeah, tell her to run CCleaner periodically, it removes other unwanted stuffs too (kind of like bleachbit)

---

### Post by dniMretsaM on 2011-04-08
After looking around some more, I found [this](http://bluefive.pair.com/recyclenow.htm). It says you can use it with a scheduler so I think I'll use that. I'll ask her if she wants to use CCleaner instead, though.

---

### Post by Grenage on 2011-04-08
> **dniMretsaM said:**
> I think the reason she doesn't want the files to be automatically deleted instead of going to the recycling bin is because if she accedently deleted an important file she would lose it permanently instead of being able to restore it.

Then an auto-cleaner isn't really the answer.  If she deletes *epicmemoirs* and the scheduler kicks in 5 minutes later, it's all gone.  Still - a cron script would do it, as could a scheduled script in Windows, I'm sure.

---

### Post by dniMretsaM on 2011-04-08
Well, my sister is being stubborn and won't use that program because you have to download it (which I think is stupid) so I'm done helping her. Thanks for all the help though guys.

---

