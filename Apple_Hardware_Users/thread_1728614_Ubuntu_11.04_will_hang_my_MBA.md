---
title: "Ubuntu 11.04 will hang my MBA"
date: 2011-04-13
forum: Apple Hardware Users
---

### Post by tualatrix on 2011-04-13
I have Ubuntu installed in my MacBook Air 3,2.

The Ubuntu 10.10 with mactel PPA is just working.

Recently I have a fresh installed Ubuntu 11.04, it doesn't need the mactel PPA and all drivers work fine. But it has an annoying problem: it will hang (or dead) unexpectly after playing a while (Maybe 10 minutes, or 1 hour). 

I can confirm the early alpha version of Ubuntu 11.04 doesn't have this problem. So it might be a kernel/driver problem (kernel panic etc.), because I can't move the mouse, it is totally down. Both i686 and amd64 have been tried.

I don't know how to debug, I can only get the dmesg message.

Does anyone have the same problem like me? Or how can I solve or report this problem?

Thank you!

---

### Post by scoddy on 2011-04-25
I'm having the same challenges on a Macbook Air 3,1 (the 11" variant).
Do you have any news on this or could you figure out the reason?

I tried a little with gentoo and grub-efi (64-bit), have you tried grub-efi or grub-pc?

---

### Post by eiler on 2011-05-11
I experience the same issue - only mine freezes after 1-5 minutes.

---

### Post by unagimiyagi on 2011-05-11
> **eiler said:**
> I experience the same issue - only mine freezes after 1-5 minutes.


How did you guys even manage to get ubuntu installed in the first place?  I have never succeeded in booting from  a usb flash drive with ubuntu installed on it despite following the directions.  I have a macbook air 3,1 and a macbook pro 5,2.  

I've got missing operating system problems.  Any detailed guides would be appreciated.  I feel like I've read everything in the forums but still have no solutions.  I like Ubuntu, but while I'm not an expert, I follow directions well and still can't figure this out.

---

### Post by unagimiyagi on 2011-05-12
> **unagimiyagi said:**
> How did you guys even manage to get ubuntu installed in the first place?  I have never succeeded in booting from  a usb flash drive with ubuntu installed on it despite following the directions.  I have a macbook air 3,1 and a macbook pro 5,2.  

I've got missing operating system problems.  Any detailed guides would be appreciated.  I feel like I've read everything in the forums but still have no solutions.  I like Ubuntu, but while I'm not an expert, I follow directions well and still can't figure this out.

So the only sane way was to use a usb external dvd drive and connect it to the mba.  Booting from the ubuntu CD, as opposed to from a usb flash drive, let things install easier.

I am noticing ridiculously GOOD battery life from the 11.6" mba in ubuntu. MORE than in mac os x, which has to be a flat out error.  I am looking at powertop and it's routinely consuming 7-8 watts at full brightness.  Is this accurate?  Because from a mere 35 watt hour battery, I'm getting between 4-5 hours of battery life.  Doing the same exact thing in mac os x, I can not get that type of battery life.  

Now on my macbook pro 5,2, I'm getting LESS battery life in Ubuntu compared with Mac OS X.  I'm using about 25 watts in Ubuntu on average at full brightness.  This laptop has a 95 watt hour battery.  I am completely befuddled as to how come the 11.6" macbook air is performing so well.

I can even do better.  There is an x220 that is new, with sandy bridge's i-5.  This consumes around 15 watts, with a 63 watt hour battery.  At full brightness, I get about 4-5 hours of battery as well.  In short, the macbook air 11" is a total battery king in terms of longevity:weight.  I had expected small laptops with puny batteries to not last long.  But not for this macbook air unless the sensors are off.
Add to this that the macbook air's battery won't die as quickly compared to the lenovo's.  I expect that the x220 will rapidly lose capacity after say, 100 charges or so, further accentuating the difference b/w the macbook air and x220.  It's a tough call.  The poor battery life that I expected in the macbook air has not been the case.  The 13" air with its 50 watt hour battery, if it still consumes just 7-8 watts, would last 6 hours at full brightness if not 7 hours.

---

### Post by notsalty on 2011-05-21
I am trying to install Ubuntu on my new Macbook Air. Can u point me in the right direction as to the installation instructions you used?

---

