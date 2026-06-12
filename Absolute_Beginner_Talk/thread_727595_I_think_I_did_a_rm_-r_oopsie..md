---
title: "I think I did a rm -r oopsie."
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by BetterSense on 2008-03-17
I had created a directory in my home called dvdrip-data. I wanted to get rid of it so I cd to home, ls showed dvdrip-data. I tried to rm dvdrip-data, but it complained that it was a directory. So I rm -r dvdrip data. tada, it disappeared with all its files.

Now, in something that appears completely unrelated, my taskbar and K menu are gone. Poof. No taskbar. I had to run a command to open this firefox. So how can I get my taskbar back, and could it possibly have something to do with my rm -r?

---

### Post by Austin_KW on 2008-03-17
Sounds like you have deleted the .kde directory. Login again and it should recreate it.

---

### Post by BetterSense on 2008-03-17
I already restarted the xserver. Do I need to reboot? I checked with ls -a and there is a .kde directory in my home.

---

### Post by Austin_KW on 2008-03-18
restarting the xserver should have been enough after the login.
Maybe there is a partial kde directory. Try renaming the .kde directory **mv ~/.kde ~/.kde.sav** and restarting the xserver. It should then recreate .kde (you may notice the longer login time)

---

### Post by BetterSense on 2008-03-18
I did

```
mv .kde .kde.bu 
```

and restarted the Xserver. It took a bit longer and I have my taskbar back.....but everything else is all messed up. Basically I'm back to a stock Kubuntu desktop and all my coolness is removed. Do I have to laboriously customise everything back the way I want it, or can I use the contents of .kde.bu to somehow restore my stuff?

Also, how exactly did removing dvdrip-data cause this, or did it cause it in the first place, being an amazing coincidence?

---

### Post by BetterSense on 2008-03-18
Bump for great justice. I would really like to know how i caused this problem and how I can restore my settings back to what they were.

---

### Post by Austin_KW on 2008-03-18
We can only assume that you deleted or corrupted something in the .kde directory.

I have corrupted mine a few time, usually by playing with kde4 etc.

Once you set it up again you can backup and just restore the next time ;)

---

### Post by BetterSense on 2008-03-18
So I basically should have known to backup .kde?  If I understand right, I have a backup now, but it's already been corrupted, so it would probably rebreak if I just restored .kde.bu.

 I'll have to take a look at .kde.bu and see if it's like a config file and I can copy stuff over, but really it will only take a couple minutes to reconfigure it how I had it. 

Is there anything else I should know to backup, so I don't do this again? I still don't understand how the rm -r had anything to do with it, could there have been some kind of link in .kde that linked to something in dvdrip-data?

---

