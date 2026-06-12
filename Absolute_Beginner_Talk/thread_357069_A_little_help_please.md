---
title: "A little help please"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by marshall.robert on 2007-02-09
Hey, im really new to Ubuntu (installed it fresh last night).

i booted from the live cd and chose a resolution of 1280 x 1024 with 24bit colour, that worked fine, but when i went to go and run ubuntu it reverts to 800x600 and wont go past.

my card is an ATI Radeon 7something00 with 32mb and capable of a much higher resolution than (its on 1600 x 1200 on my xp boot), i am also aware that there are issues with ati and linux. my monitor is 19 inch and 800 x 600 is quite ugly, and i cant see some of the buttons especially during the install when they where hidden behind the bars

i did not have the same problem with my laptop though, its very much older than my desktop (about 8 years or so old) and has an ati rage with 8mb and happily sits at the laptops max res of 1024 x 768  :confused: 

i have looked on the ati site and the lowest card they supply drivers for is radeon 8500.

can anyone please help me with this nagging problem?

many thanks -rob xx

---

### Post by goatflyer on 2007-02-09
Sounds like you could have missed a step in the install...  (easy to fix)

Open a terminal and run this command:
```

sudo dpkg-reconfigure xserver-xorg

```

(it will ask you for your password)
This will re-run the reconfiguration portion of the install procedure.

Go through the questions, accepting the default answers, until you come to the screen resolution part.  On that screen, scroll through the resolutions offered, and be sure to select 1024x768. (press spacebar to toggle selections).  Continue answering the rest of the questions until you reach the end.   Then restart your computer.

---

### Post by laidback on 2007-02-09
I couldn't get it to accept 1280x1024 either, even though my screen is up to it, I found that the install just hung with a screen splash telling me that the resolution wasn't supported. 

What I did was to install at the default and then change it once Ubuntu was running. System>Preferences>Screen resolution. That worked fine. I'm now in 1280x1024 all the time.

---

### Post by marshall.robert on 2007-02-09
> **laidback said:**
> I couldn't get it to accept 1280x1024 either, even though my screen is up to it, I found that the install just hung with a screen splash telling me that the resolution wasn't supported. 

What I did was to install at the default and then change it once Ubuntu was running. System>Preferences>Screen resolution. That worked fine. I'm now in 1280x1024 all the time.

yeah, i couldnt do that and get it into 1280x 1024^^

thanks for the help, and the quick reply, ill try it tonight when i get home

cheers :smile:

-rob xxx

---

### Post by marshall.robert on 2007-02-10
> **goatflyer said:**
> Sounds like you could have missed a step in the install...  (easy to fix)

Open a terminal and run this command:
```

sudo dpkg-reconfigure xserver-xorg

```

(it will ask you for your password)
This will re-run the reconfiguration portion of the install procedure.

Go through the questions, accepting the default answers, until you come to the screen resolution part.  On that screen, scroll through the resolutions offered, and be sure to select 1024x768. (press spacebar to toggle selections).  Continue answering the rest of the questions until you reach the end.   Then restart your computer.

^^ that worked a treat, thanks alot ^^

-Rob xx

---

