---
title: "Laptop running really hot"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by defenestratos on 2008-02-12
My laptop's fan is always going in Ubuntu 64 6.06. I used  to use Xubuntu and had KPowersave installed. 

I just got home and the lappy was superhot. What can I do to cool the thing down and yet not use as much power?

---

### Post by DestroyMicroshaft on 2008-02-12
Have you tried reinstalling kpowersave?

---

### Post by KCPokes on 2008-02-12
Curious, as I've seen issues with heat, but was it actually hot or was the temperature just showing it was hot.  I've had experiences when it told me my laptop was running in the 80C range, yet the air being expelled wasn't hot nor was it to the touch.  Funny enough, as I type this my temp just shot up to 91C, yet it is not hot nor is the air from the fan.

---

### Post by emarkd on 2008-02-12
I've never had any of these issues with my laptop, but have you checked to see if you've got a stuck process pushing your processor to 100%?

```
top
```

---

### Post by KCPokes on 2008-02-12
> **emarkd said:**
> I've never had any of these issues with my laptop, but have you checked to see if you've got a stuck process pushing your processor to 100%?

```
top
```

Not sure what is causing it but it is not a process issue.  I've been through multiple versions of Ubuntu and am currently running Linux Mint, with the issue prevalent in each different version I've stepped through.  I'm to the point of moving to something completely different to verify whether it is version specific or not.  As far as I can tell, in my case, the machine is registering as hot but not actually running hot.  If it were really running at 91C, you definitely wouldn't be able to have it sitting on your leg, which it is not even warm to the touch.  

Just one of those little nuances that you learn to live with.  It is not constant, as it'll run around 40C most times, but it does flake out.

---

### Post by emarkd on 2008-02-12
Yeah, I'd think that 91C is way too hot for it to be a real result.  I can push my processor to 100% and leave it there and my laptop never exceeds 60.

---

### Post by defenestratos on 2008-02-12
> **DestroyMicroshaft said:**
> Have you tried reinstalling kpowersave?
Just reinstalled kpowersave and it really seems to help. Is there a reason why ubuntu uses the fan more than xubuntu? I am using 64 bit ubuntu whereas I used 32 bit xubuntu.
I am using 3 or 4 percent of my CPU on idle. It gets to 100 when I am loading stuff or batch processing and sometimes during flash but when its just sitting there it is ok.

---

