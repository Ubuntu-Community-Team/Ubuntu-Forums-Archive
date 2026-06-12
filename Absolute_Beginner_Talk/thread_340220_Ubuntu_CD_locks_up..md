---
title: "Ubuntu CD locks up."
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by InTheFlow on 2007-01-16
I downloaded the iso for 6.10, burned it to a 700Mb CD with Nero and Verify data checked and put it in the DVD drive. I made sure it was set as the first boot device and rebooted the machine.

I got all excited when I saw the opening menu where you can choose to start Ubuntu, Check CD for defects, memory test etc.

I decided to run the check on the CD to make sure it was OK. I highlighted that option, pressed enter and the first time it locked up the system after it got to a black screen with a flashing cursor in the top left.

I hard reset the system, got to the menu again and made the same choice. This time after the flashing cursor was there for a little while, the Ubuntu loading progress bar came up. The progress thing started in the middle of the area where it goes back and forth, moved all the way to the right and started going back the other way. After moving just two 'sections' to the left, it locked up.

I rebooted, and tested the memory tester. Worked like a champ.

I rebooted again and tried to just start ubuntu instead of checking the CD. Same thing happened here; after the load bar moved a little to the left it locked up on me. Ctrl-Alt-Del wouldn't restart it so I had to hard reset again.

My motherboard is an Asus A8N-VM CSM with a AMD 3700+ chip running at the stock speed of 2.2 Ghz. I have 1 Gig of Corsair RAM (2 x 512) also running at stock speeds and latency timings of 3-3-3-8

Any ideas?:confused:

---

### Post by riven0 on 2007-01-16
When you burned the iso, did you burn it at the lowest speed? 4 - 6kbs is a good speed. Otherwise, you will get errors even if your verification goes through fine. 

If that still doesn't work, try one of the Other Options, such as the noapic option and see if that works at all.

---

### Post by InTheFlow on 2007-01-16
> **riven0 said:**
> When you burned the iso, did you burn it at the lowest speed? 4 - 6kbs is a good speed. Otherwise, you will get errors even if your verification goes through fine. 

If that still doesn't work, try one of the Other Options, such as the noapic option and see if that works at all.

The first time I burned it at 48x speed and it failed the verification. The 2nd time I tried 4x speed. I'll try burning it at the slowest speed the drive will let me and post back if it works.

Thanks for the help!

---

### Post by riven0 on 2007-01-16
> **InTheFlow said:**
> The first time I burned it at 48x speed and it failed the verification. The 2nd time I tried 4x speed. I'll try burning it at the slowest speed the drive will let me and post back if it works.

Thanks for the help!

Hold on! Don't burn it at something like 1 or 2kbs. That'll give you errors, too! If you burned it at 4kbs it's probably okay. Try the Other Options on the LiveCD and see if you have any luck there.

---

### Post by InTheFlow on 2007-01-16
> **riven0 said:**
> Hold on! Don't burn it at something like 1 or 2kbs. That'll give you errors, too! If you burned it at 4kbs it's probably okay. Try the Other Options on the LiveCD and see if you have any luck there.

Thanks for the warning. Although, Nero wouldn't let me burn at anything lower than 4x anyway. I wound up re-burning it anyway though thinking maybe something got corrupted.

But, it turned out to be a bad stick of RAM! 

When I ran the memory test on the entire 1 Gig, I got Test #5 errors in the 900-1000 range. So I swapped the memory sticks to the slot the other one was in and ran the test again. Again, I got errors at test #5 but this time it was in the 400-500MB range.

So, now when I take it out of the machine, both CDs work properly. They also both pass the CD check w/o issue. The weird thing about it all is that if I tested each memory module by itself, the bad one would pass every time. Kind of odd.

Thanks again for the help.

---

### Post by mainstang on 2007-01-17
i am having the same problem i am very new to ubuntu or linux in general and would really like to get away from my other expensive os.  I upgraded my memory 1x128 and 1x256.  I did burn it a little fast.  But how to you check the memory?

---

### Post by riven0 on 2007-01-17
> **mainstang said:**
> i am having the same problem i am very new to ubuntu or linux in general and would really like to get away from my other expensive os.  I upgraded my memory 1x128 and 1x256.  I did burn it a little fast.  But how to you check the memory?

When you boot up the LiveCD it gives you the option to do a memory test. Just scroll down to the entry that says **memtest** and let it does its thing.

---

### Post by mainstang on 2007-01-17
Ok i tried that and everything seemed to be ok.  Do i need to partion with windows 98se or will ubuntu automaticaly do this when installing.  Sorry im still new to ubuntu. thanks for your help thus far.  Is ubuntu alot better than 98se in your opinion.

---

### Post by InTheFlow on 2007-01-17
> **mainstang said:**
> Is ubuntu alot better than 98se in your opinion.

Sorry that I can't answer your technical question about the formating but I'd say ubuntu is better than Win98se for sure.  For one thing, ubuntu is actually stable! LOL:D I guess it all comes down to what you are going to use the computer for...

---

