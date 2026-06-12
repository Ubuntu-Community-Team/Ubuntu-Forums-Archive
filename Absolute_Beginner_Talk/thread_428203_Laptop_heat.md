---
title: "Laptop heat"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by riminicat on 2007-04-30
Showed 71 Celsius, should I worry about it?  How hot can a Dell Latitude D620 get before I should worry.

---

### Post by Sef on 2007-04-30
From [Laptraxx]("http://www.laptraxx.com/heatproblems.html"):

> Heat can crash your laptop hard drive

Hard disk drives can overheat and crash, causing you to lose valuable data! Manufacturers recommend normal working temperature of 95-104°F  (35-40°&#1057;). At temperatures from 104-122°F  (40-50°&#1057;) you double the chance of a hard drive crash!



---

### Post by raffytaffy on 2007-04-30
my laptop goes frm 50-60 on the avg. from when i first bought it. and its been 2 years ago. had to replace HD once so far. after 1year and 9 months. should i worry?

---

### Post by riminicat on 2007-04-30
Good to know, I was running a laptop hungry background but I shut it off.  Its a school laptop, so at least I can get anything replaced if it breaks!!

---

### Post by sgarman on 2007-05-04
> **riminicat said:**
> Showed 71 Celsius, should I worry about it?  How hot can a Dell Latitude D620 get before I should worry.

I'm curious, how did you determine your laptop's temperature? I own a new D620 also and find the CPU fan is extremely quiet and never seems to speed up. Consequently, the bottom of the machine gets uncomfortably warm.

Scott

---

### Post by riminicat on 2007-05-17
I have a digital thermometer on my pc that tells me the temp

---

### Post by Hobo Joe on 2007-05-17
> **sgarman said:**
> I'm curious, how did you determine your laptop's temperature? I own a new D620 also and find the CPU fan is extremely quiet and never seems to speed up. Consequently, the bottom of the machine gets uncomfortably warm.

Scott

Don't worry, that's perfectly normal.

70C on the other hand, is very hot. I'd be careful at that temperature.

---

### Post by ramjet_1953 on 2007-05-17
I'm not sure what temprature he is talking about here.

Is it CPU or HDD?

HDD temperatures certainly are in the danger area above 55 C, but a CPU temperature of 55 C is OK.

When my laptop is doing some hard crunching the CPU temperature often goes to 65 C, for short bursts, which is also OK. 

On my Acer TravelMate 4101 the fan kicks in at around 50 C and goes into overdrive at 60 C.

However above 70 C for the CPU is geting a bit warm.

Regards,
Roger 8-)

---

### Post by DarkN00b on 2007-05-18
> **sgarman said:**
> I'm curious, how did you determine your laptop's temperature? I own a new D620 also and find the CPU fan is extremely quiet and never seems to speed up. Consequently, the bottom of the machine gets uncomfortably warm.

Scott

Most laptops these days use ACPI, so try this in a terminal window:

```
acpi -V
```

That's a capital Vee. That gives you your CPU temp and some other info if your motherboard supports it.

---

### Post by crimesaucer on 2007-05-18
My laptop would run very warm also. My conky temps were always too hot. So I got this aluminum laptop cooler that has worked perfectly: 

[http://www.coolerguys.com/llnc02.html](http://www.coolerguys.com/llnc02.html)

It's big enough that my laptop fits onto it. It stays in the very low 40's to mid 50's now, unless I use a program that uses a lot of cpu. And even if I use a program that jumps my temp up into the 70's, the minute I close the program, the 2 cooling fans and my hp's cooling fans bring the temp down quickly.

I read through so many pages of different laptop/notebook coolers, and so many of them look like they suck. This one works good for home, but I doubt it can be traveled with to the coffee shop.

---

### Post by whitefort on 2007-05-18
> **DarkN00b said:**
> Most laptops these days use ACPI, so try this in a terminal window:

```
acpi -V
```

That's a capital Vee. That gives you your CPU temp and some other info if your motherboard supports it.

WOW!  That's a handy little tip - many thanks!!

---

### Post by DarkN00b on 2007-05-18
> **whitefort said:**
> WOW!  That's a handy little tip - many thanks!!


[img]http://smileys.inzenet.org/repository/Respect/0015.gif[/img]

---

### Post by Enverex on 2007-05-18
Heat of the processor =/= Heat of the hard-drive.

My old laptop runs hot too, normally around 40-50'c. It auto-switch-offs at 80'c. Any modern machine will either clock down or shut off if it gets dangerously hot.

---

### Post by Benbow on 2007-05-18
I'll agree with the cooler posting. My laptop crashed very often until I bought a base cooler for it. Never crashes now (at least not with Ubuntu:))

---

### Post by Kal9001 on 2007-05-18
Its worth noting that Mobile CPU's can take A LOT more thermal abuse then a desktop chip. Ever wondered why they are more expensive, They are made with much finer tolerances and lower thermal output due to the nature of the environment they operate in.

The reason the bottom of a laptop will get warm when the fan id off or only slow is cos the CPU will be fine, But the memory SoDIMM's will be toasting quite nicely. There are easy mods done to allow your laptop to run cooler. Once I have done is to open up the black floppy drive  bay and I can now (When I know I'm going to be doing something very strenuous) put a duct and fan onto the "hole" which means the laptop feels cool even at 100% load.

Now this isn't always practical of course but most laptops will be designed to take a lot of heat. the key ares to try and avoid head buildup is around the Hard disk and Compact disk drives, and near the battery, If heat causes a crack in the battery then the Lithium can react with air explode. (I'm sure we all remember the headache that gave dell) thankfully mostly laptop battery's are away from the CPU and memory for this very reason and shouldn't be an issue.

As an added note a previous post was correct in saying that mobile CPU's will know they are cooking and take measures to protect themselves by under clocking themselves or just shutting down. although this is very close to the damage tolerance of the chips and if you notice this happening repeatedly then you should get your laptop serviced as there may be build up of dust/hair/fluff or whatever in the cooling system or in other vents.

---

