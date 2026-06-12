---
title: "Want to eliminate timeout in grub."
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by gargoyle on 2006-07-15
Want to eliminate timeout in grub.
In my grub I have something called timeout, currently it is set to 10 seconds.
What I want is to have grub wait indefinitely for me to make a selection.

Can I do this by just comment out the time out
old timeout

**timeout 10**

new timeout
**#timeout 10**

Will this work or should I just eliminate it?

---

### Post by mhancoc7 on 2006-07-15
Yes commenting it out should work just fine.
Jereme

---

### Post by Drakkor on 2006-07-15
What I want is to have grub wait indefinitely for me to make a selection.
why not just change it to 1200 seconds, I believe that's 2 hours,that should be enough time to decide.......... :mrgreen:
Kidding,wouldn't not having a time out at all just boot to ubuntu automatically?  I once had it set to 0 and it did that.

---

### Post by catlett on 2006-07-15
> **Drakkor said:**
> What I want is to have grub wait indefinitely for me to make a selection.
why not just change it to 1200 seconds, I believe that's 2 hours,that should be enough time to decide.......... :mrgreen:
Kidding,wouldn't not having a time out at all just boot to ubuntu automatically?  I once had it set to 0 and it did that.

Exactly. The timeout tels it how long to wait. 0 make sit go right in and 1 gives 1 second etc. I never commented it out but without a parameter for how long to wait, I believe it won't wait. 
Just follow the previous advice and make a high number. The value is in seconds so give yourself 5 minutes or timeout 300. That should be enough time.
Either way you can always readjust the timeout if it isn't doing what you want.

---

### Post by adam.tropics on 2006-07-15
> **catlett said:**
> Exactly. The timeout tels it how long to wait. 0 make sit go right in and 1 gives 1 second etc. I never commented it out but without a parameter for how long to wait, I believe it won't wait. 
Just follow the previous advice and make a high number. The value is in seconds so give yourself 5 minutes or timeout 300. That should be enough time.
Either way you can always readjust the timeout if it isn't doing what you want.

That's what I thought too, but no, commenting causes Grub to just wait. I learn something new everyday!

edit:but I use gfxboot so I suppose that *could* make a difference, not likely though.

---

### Post by catlett on 2006-07-15
> **adam.tropics said:**
> That's what I thought too, but no, commenting causes Grub to just wait. I learn something new everyday!

edit:but I use gfxboot so I suppose that *could* make a difference, not likely though.

You learn something all the time here. The funny thing is when I checked the Grub manual, all it said was the timeout defined in seconds the time grub waits to boot. It didn't elaborate further. 
Well another one for the bookmark.

P.S. Your new bookmark threw me off. You went from the aristocratic british symbol to a south pacific sunset look. What are you on vacation somewhere? :-D

---

### Post by Drakkor on 2006-07-15
I have mine set to 2 seconds,that's enough time for me,lol.... :p

---

### Post by adam.tropics on 2006-07-15
> **catlett said:**
> 
P.S. Your new bookmark threw me off. You went from the aristocratic british symbol to a south pacific sunset look. What are you on vacation somewhere? :-D

haha, no, I am British, but live in the tropics in Far North Queensland, Australia!

---

### Post by gargoyle on 2006-07-15
By the way I wanted it to wait is sometime I have more then one machine running and I want it to wait because sometime I may not want to boot to the default setting.

I will try both long time and commenting it out.

Thanks

---

### Post by mhancoc7 on 2006-07-16
Commenting the "timeout" option will set the grub menu to wait until you physically make a selection. 
Jereme

---

### Post by dermotti on 2006-07-16
Cool

---

### Post by gargoyle on 2006-07-17
Just want to close out this request.
I decide to comment out the timeout in menu.ls.
This work just like I wanted to. that being the system will wait until I make a selection and hit the Enter key.

Thanks for all the replies

---

