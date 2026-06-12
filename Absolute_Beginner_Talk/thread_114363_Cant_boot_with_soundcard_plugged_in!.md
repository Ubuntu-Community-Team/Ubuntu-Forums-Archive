---
title: "Cant boot with soundcard plugged in!"
date: 2006-01-08
forum: Absolute Beginner Talk
---

### Post by Prozzy on 2006-01-08
Hey... 

I recently installed ubuntu on my notebook and it all seems to be running fine, I only have 1 problem.

I have a *Creative Audigy 2 ZS Notebook* Cardbus soundcard, but I cant get it to work :(

If i plug it in the comp wount boot, while loading the modules it just freezes. I have no problem if the card isnt plugged in, and i had no problems with the card when i was useing windows.

Any ideas what to do? I would really like to get some sound on my system.

- Greets Prozzy

---

### Post by benplaut on 2006-01-08
when you plug it in once the computer is turned on, does anything happen?

do that, then post the output of the command "dmesg"

---

### Post by Prozzy on 2006-01-08
When i plug it in, while comp is running it also freez. It responds to nothing but the big turn-off button...

---

### Post by AndyCooll on 2006-01-08
I have a similar problem, but it's related to my USB wireless. In my case, once I remove the USB wireless the box then boots up and I can then plug it back in and it's ok (which is absolutely no use of course since I want to use wireless from boot)

I'm still researching, but I believe there can be a problem with ALSA on boot-up. I read a thread which gave a fix (which looked extremely complicated) and if I can find it again I'll post the link.

---

### Post by GangBoy on 2006-01-11
I have also this problem. But in dapper i don't have this problem, because it doesn't recognize pcmcia carbuss controller :(

---

### Post by cvmostert on 2006-01-12
[QUOTE=Prozzy]When i plug it in, while comp is running it also freez. It responds to nothing but the big turn-off button...[/QUOTE]


I also have this problem with my crystal cs4614a sound card... any suggestions on a card i can use that actually works fine?

thanx

---

### Post by samk on 2006-03-02
I had this problem also, I downloaded the latest alsa driver
alsa-driver-1.0.11rc3 and compiled. You need to have build-essentials and gcc3.4.
This cleared up the problem and the card works.

---

