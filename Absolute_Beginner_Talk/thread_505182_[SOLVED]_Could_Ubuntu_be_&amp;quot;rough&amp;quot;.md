---
title: "[SOLVED] Could Ubuntu be &amp;quot;rough&amp;quot; on my CD-ROM?"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by keyboardashtray on 2007-07-20
OK for questions like this, you really can't talk your way around how little you actually know about how computers actually work....

To preface my question here, my understanding (which may be completely wrong) is that Ubuntu uses generic drivers whenever possible as an alternative to proprietary ones (like how my resolution can only be set to  1024x768 by default because of my Intel 915).

Well, since I started using Ubuntu, I've been slowly reimporting a lot of my CDs as .ogg, and right from the beginning, I noticed it made a pretty heavy clicking sound right at the end of ripping, just prior to eject. Then when I'd listen really carefully, I'd hear what sounded like the laser trying to move, making a sound like my old crappy CD players would when I'd put in Nine Inch Nails "Broken" (which had 99 tracks) back in the 90's.

The last few  CDs I ripped skipped, and now when I put in a disc, I hear the laser sound but it doesn't even recognize that there is a disc in there.

Could the driver possibly not be "optimized" to my CD rom, and running it but running it harshly, kind of like when you put a donut on a car in lieu of a real tire?

I'm not blaming Ubuntu at this point, just curious - I am a somewhat heavy smoker and live in a dusty environment, the computer is about 4 years old. Still, I've gotta wonder if it is coincidence or not, to use another car analogy it's kind of like when you loan someone a car for a trip and it comes back with a transmission problem - it may have been on the fritz before you loaned it but for all you know it was working fine and came back in worse shape.

---

### Post by Motoxrdude on 2007-07-20
So your asking if ubuntu screwed up your cd drive? Simply, absolutly not. There is not way for it to ruin it in anyway since it doesn't actually control the "seeking".

---

### Post by w4ett on 2007-07-20
The Short answer is No, Ubuntu didn't bork your CD Drive.  Like anything mechanical, all are prone to failure in extreme environments, (Heat, Dust, Smoke Chemicals...etc)...you can try using one of the laser eye cleaning disks on it, but if you are a smoker, nicotine tars are just about impossible to clean, they also will adhere to the drive gears and will slow rotation speed and cause heatbuildup.

Just invest in a new drive....Way less trouble.

---

### Post by ramjet_1953 on 2007-07-20
As far as your screen resolution is concerned, you can get it to optimum, if you follow this link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

It works fine on my Acer laptop which has the same chipset as yours and gives me full 1280 X 800 @ 24 bit.
It is a little more work, but the 915resolution option is still a bit more stable than the newer driver, which baulks at dynamic resolution changes, as is often the case with full screen games.

As far as your CD woes are concerned, I'm not aware of any problems with CD's or DVD's.

Have you tried cleaning the lens on your drive with one of those lens cleaning CD's?

There is also the possibility that the drive is failing.

Regards,
Roger :cool:

---

### Post by keyboardashtray on 2007-07-20
> **Motoxrdude said:**
> So your asking if ubuntu screwed up your cd drive? Simply, absolutly not. There is not way for it to ruin it in anyway since it doesn't actually control the "seeking".

What does the driver for a CD rom do then? I put in a CD now, and it makes a little noise, like the laser trying to move or something, but ultimately, it doesn't show that a disc is still in there...does that just sound like it finally crapped out and needs to be replaced?

---

### Post by Ptero-4 on 2007-07-20
Since you said that you smoke and you live in a dusty environment. It may be that the CD drive is failing due to heat problems caused by dust and smoke. The best you can do is to open up your PC and clean it out, check if the fan is clobbered or dead and check the internal components to see if anything needs to be replaced.

---

### Post by keyboardashtray on 2007-07-20
> **ramjet_1953 said:**
> As far as your screen resolution is concerned, you can get it to optimum, if you follow this link:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

It works fine on my Acer laptop which has the same chipset as yours and gives me full 1280 X 800 @ 24 bit.
It is a little more work, but the 915resolution option is still a bit more stable than the newer driver, which baulks at dynamic resolution changes, as is often the case with full screen games.

As far as your CD woes are concerned, I'm not aware of any problems with CD's or DVD's.

Have you tried cleaning the lens on your drive with one of those lens cleaning CD's?

There is also the possibility that the drive is failing.

Regards,
Roger :cool:

Thank you, I've bookmarked the guide - I was going to be content with the 1024x768 because I find I don't lean forward so much for the small text, but perhaps I should optimize if you think I may have trouble in the future with full screen games.

No, I haven't tried the lens cleaning CD's - I will get one tomorrow when I go to the store - I hope that is the problem.

---

### Post by Frak on 2007-07-20
The scanning of a CD is completely Hardware controlled, it is invoked by a program asking the Linux Kernel to tell the CD to seek.

---

### Post by keyboardashtray on 2007-07-20
> **Ptero-4 said:**
> Since you said that you smoke and you live in a dusty environment. It may be that the CD drive is failing due to heat problems caused by dust and smoke. The best you can do is to open up your PC and clean it out, check if the fan is clobbered or dead and check the internal components to see if anything needs to be replaced.

I opened up the computer and cleaned best I could, but I didn't actually remove the CD rom or the DVD/CD RW ROM...as bad as the areas I could clean were I'm guessing it isn't very nice inside/behind the CD ROMs.

OK, I guess it's not the drivers that were the straw that broke the camels back, I guess I just was curious if they could have contributed. I will chalk it up to pure coincidence.

Thank you everyone, I will mark it solved.

---

### Post by keyboardashtray on 2007-07-20
> **Frak said:**
> The scanning of a CD is completely Hardware controlled, it is invoked by a program asking the Linux Kernel to tell the CD to seek.

Ahh ok, that must be what motoxrdude meant. It's good to know how that works. Thanks everyone for the great insight, I will just try a CD cleaner and cross my fingers.

---

### Post by spur on 2007-07-20
I found cd and dvd drives don't last even under ideal conditions and I don't use mine a lot either and I'm not in a dusty environment or smoke. So I would guess you cd has gone to the place where all cd drives go when done.
New ones are cheap, as well, so why go to a whole lot of bother?

---

### Post by kittyhawk63 on 2007-07-20
> **Frak said:**
> The scanning of a CD is completely Hardware controlled, it is invoked by a program asking the Linux Kernel to tell the CD to seek.

Glad to have this cleared up in my mind. I had a CD-Rom drive go bad the first week I tried burning some ISOes. I had hardly used the drive and never had a problem with Windows when I did. In fact, I had used it with Windows that day to burn my LiveCD.

Well, I needed to buy a DVD player anyway, and that served as an excuse to my sweetie.
kh

---

### Post by keyboardashtray on 2007-07-20
> **w4ett said:**
> The Short answer is No, Ubuntu didn't bork your CD Drive.  Like anything mechanical, all are prone to failure in extreme environments, (Heat, Dust, Smoke Chemicals...etc)...you can try using one of the laser eye cleaning disks on it, but if you are a smoker, nicotine tars are just about impossible to clean, they also will adhere to the drive gears and will slow rotation speed and cause heatbuildup.

Just invest in a new drive....Way less trouble.

Ahh, that doesn't sound encouraging but I appreciate the advice. Maybe I can get a protective case for my computer or something, I didn't know smoking was that rough on it, I used to work in a granite factory with diamond dust and grime and water everywhere, the PCs there were filthy and yet they seemed fine.

---

### Post by kittyhawk63 on 2007-07-20
Smoke is far finer than dust. It finds niches that dust never heard of.

---

### Post by Frak on 2007-07-20
Oh, and when/if you do buy a new drive, buy a LiteON DVD/CD burner. Great value, and its drivers are open source.
Oh yes, that may be your problem is the drivers and firmware controlling the device and how the Kernel recieves the information, if its not what the kernel wants, it instructs the CD Drive to rerun, but I don't see how it can cause damage. Plus, most drives exercise self-preservation in case anything bad happens.

---

### Post by keyboardashtray on 2007-07-20
> **kittyhawk63 said:**
> Smoke is far finer than dust. It finds niches that dust never heard of.

LOL - I see myself in some future anti-tobacco ad: 
Camera zoomed in on my face, single tear on cheek.
"Second-hand smoke killed my best friend." 
Camera pans out, me cradling my PC.

---

### Post by Frak on 2007-07-20
> **keyboardashtray said:**
> LOL - I see myself in some future anti-tobacco ad: 
Camera zoomed in on my face, single tear on cheek.
"Second-hand smoke killed my best friend." 
Camera pans out, me cradling my PC.

:lolflag:

---

### Post by keyboardashtray on 2007-07-20
> **Frak said:**
> Oh, and when/if you do buy a new drive, buy a LiteON DVD/CD burner. Great value, and its drivers are open source.
Oh yes, that may be your problem is the drivers and firmware controlling the device and how the Kernel recieves the information, if its not what the kernel wants, it instructs the CD Drive to rerun, but I don't see how it can cause damage. Plus, most drives exercise self-preservation in case anything bad happens.

I went and looked up those LiteONs, and you're right they are pretty cheap - I definitely want to buy open source supporting hardware.

It was my CD-ROM that just started acting up, my DVD/CD RW still works. Assuming the worst and I have to replace, should I just buy another CD-ROM and save a couple bucks, or should I go ahead and get another DVD/CD RW (maybe assuming that if my CD-ROM just went, my DVD/CD RW might not be far behind)?

---

### Post by kittyhawk63 on 2007-07-20
> **keyboardashtray said:**
> LOL - I see myself in some future anti-tobacco ad: 
Camera zoomed in on my face, single tear on cheek.
"Second-hand smoke killed my best friend." 
Camera pans out, me cradling my PC.

Yeah, that would make a good commercial. =D>

---

### Post by Frak on 2007-07-20
Frankly, it based on your needs, I have one just because I don't see the reason to have more than one, but I also have a CD ROM drive, and a DVD ROM drive, just in case.

---

