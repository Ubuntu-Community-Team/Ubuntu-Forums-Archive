---
title: "MacBook Santa Rosa Hibernate"
date: 2008-05-05
forum: Apple Hardware Users
---

### Post by ShareBuntu on 2008-05-05
Hi, my MacBook told me that I should come on here to try and get hibernation fixed. It threatened to end the world if we can't get hibernate working. Help?

---

### Post by cyberdork33 on 2008-05-05
do you have a swap partition?

---

### Post by ShareBuntu on 2008-05-05
> **cyberdork33 said:**
> do you have a swap partition?
Yes, 1.5 times my RAM; per order.

---

### Post by cyberdork33 on 2008-05-05
do you have any details about what is happening? does it successfully shutdown? any error messages?

---

### Post by ShareBuntu on 2008-05-05
> **cyberdork33 said:**
> do you have any details about what is happening? does it successfully shutdown? any error messages?
The almighty MacBook exists X as to pretend to hibernate, then abruptly wakes up returning to X without any errors or warnings. I fear it is most displeased.

---

### Post by cyberdork33 on 2008-05-05
> **ShareBuntu said:**
> The almighty MacBook exists X as to pretend to hibernate, then abruptly wakes up returning to X without any errors or warnings. I fear it is most displeased.

It sounds like it. Are you Hibernating, or suspending?

are there any messages in the output of dmesg?

---

### Post by ShareBuntu on 2008-05-05
I'm trying to hibernate. Suspension doesn't work either. I haven't changed any settings, so this is all out of the box - which evidently has never worked for me before. There is also nothing in dmesg pertaining hibernation, just a bunch of messages about applesmc waiting for a status that failed. No ill effects caused by that module though.

I do believe I tried to install suspend2 through aptitude, however.

---

### Post by cyberdork33 on 2008-05-05
Sorry, I don't know what to tell you. I was under the impression that suspend worked on your model (for the most part). I would guess that the lack of suspend is linked to the hibernation problem though.

---

### Post by ShareBuntu on 2008-05-06
> **cyberdork33 said:**
> Sorry, I don't know what to tell you. I was under the impression that suspend worked on your model (for the most part). I would guess that the lack of suspend is linked to the hibernation problem though.
Oh, the humanity! :(

---

### Post by Eniak on 2008-05-31
I have an older MBP, the core 2 duo 2.33

I'm managing to suspend, but I'm having the exact same problem to hibernate... Can it b related to the fact that I have swap file instead of a swap partition?

---

### Post by ShareBuntu on 2008-05-31
> **Eniak said:**
> I have an older MBP, the core 2 duo 2.33

I'm managing to suspend, but I'm having the exact same problem to hibernate... Can it b related to the fact that I have swap file instead of a swap partition?
I don't think it is, I have a swap partition; and the problem persists.

---

### Post by dustynus on 2008-05-31
Try doing as shown in MISC 
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Worked for me, I had the same problem as you, and doing that enabled hibernation for me.

---

### Post by cyberdork33 on 2008-05-31
> **Eniak said:**
> I'm managing to suspend, but I'm having the exact same problem to hibernate... Can it b related to the fact that I have swap file instead of a swap partition?
i was under the impression that hibernate would not work with a swapfile, but I may be wrong.

---

### Post by russo.mic on 2008-10-24
Instructions on how to hibernate with a swapfile

[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)

Under MISC.

Russo

---

### Post by jwhendy on 2008-10-24
Same problem with MacBook 2,1... I use Zenwalk so for me it's standby vs. hibernate. Standby works, hibernate does not.

My hibernate script actually runs standby if hibernate fails. As this was the case I never really saw the hibernate errors, I just assumed it was working. One thing that tipped me off was the first time I ran the hibernate script from the terminal vs. a gui option. It does sound like you've seen some error output, but I wonder if you could get more by opening a terminal and running whatever your hibernate binary is. For me it's: ```
sudo /usr/sbin/hibernate
```

When I ran that I finally saw all of it's vomit and realized that it wasn't working as I thought. I haven't tried to fix it... I just settled for standby. I'm interested in seeing if there's a resolution, though!

-John

---

