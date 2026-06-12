---
title: "Programs Shut Down"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by justinreeves16 on 2007-09-06
Hello, I am new to Ubuntu, been using it for a few weeks now, I really only have been using the internet (Firefox) and Gimp.
The programs seem to randomly shutdown, I use Firefox mostly and it seems to shut down a lot.
I am not sure why this might be happening, any suggestions. I would say in 2 hours it shuts down 10 times or so.

My kids used Gimp a few times and it was doing the same thing.

---

### Post by reckless2k2 on 2007-09-06
you'll need to post system specs and we can go from there.

---

### Post by SOULRiDER on 2007-09-06
Ive never heard of such a thing. Try running them from a console by typing
```
firefox
``` and ```
gimp
```

When they shutdown see if they print any errors and post them if possible.

---

### Post by justinreeves16 on 2007-09-06
1.7 Gig AMD Athlon
Nvidea GeForce4 Ti4600
1Gig Ram
20Gig HD

---

### Post by justinreeves16 on 2007-09-06
I didnt receive anything in the terminal, firefox shut down but only once, ill try gimp also.

---

### Post by asmoore82 on 2007-09-06
I would test the RAM with the LiveCD.

---

### Post by Beggar on 2007-09-06
I doubt it is the ram as there would be other telltale behavior, like the computer locking up at random times. Have you installed any additional desktop packages like beryl/compiz, etc.? These packages can be a bit unstable and I have seen this behavior with certain features enabled in Beryl specifically.

---

### Post by Dr Small on 2007-09-06
On my other system, which has an intel pentium 4 processor in it, Firefox would crash at times, and I think the processor in that system is bad. It has been like that since day 1 of using it. Maybe a processor problem?

Dr Small

---

### Post by justinreeves16 on 2007-09-06
error in terminal Firefox shut down.
"Segmentation fault (core dumped)"

---

### Post by justinreeves16 on 2007-09-06
It was doing it from the initial install, and the only thing I have installed was a bunch of stuff to try to get the sysytem to play dvd,s, it turned out to just need the CSS decryption installed.Soknow there is a few things installed befor that that didnt help the dvdv,s play.

---

### Post by justinreeves16 on 2007-09-06
Also I have a user made theme loaded, but I think it was doing it befor that also, unsure.
Do themes screw things up in Linux, like in Win, screensavers, themes...crash SW in WIN, Ubuntu to?

---

### Post by justinreeves16 on 2007-09-07
My system spocantiously powers off everyonce in a while, Im not sure what that is from but it has done that since I bought the system. Thing is though I never had any problems like with windows software shutting down.

---

### Post by LowSky on 2007-09-07
> **justinreeves16 said:**
> My system spocantiously powers off everyonce in a while, Im not sure what that is from but it has done that since I bought the system. Thing is though I never had any problems like with windows software shutting down.

dude computers shouldnt just shut down when ever. It seems you have a bad power supply or possibly a heat sink issue. Why didn't you call the manufacturer when it started to just turn off spontanously? that is what warrenties are for.

---

### Post by Beggar on 2007-09-07
Moving the topic back to original, yes a poorly made user theme could cause crashes, and would also explain the lack of an error message (if the problem was not firefox then it might not print an error message). Can you try using one of the default themes?

---

### Post by justinreeves16 on 2007-09-09
Ok I switched to a default theme, but I didia google on the error for Firefox"Segmentation Fault(Core Dumped)" and there have been more than just me with this prob with Firefox.
I couldnt find a solution though.
Anyone know.

---

### Post by lukav on 2008-01-11
I have a similar problem, it occurs when I try to type (spacebar) or 
paste into the forums.

The error message I get is:




/usr/lib/firefox/firefox-bin: symbol lookup error: 
/usr/lib/firefox/components/libmyspell.so: undefined symbol:   _ZN8Hunspell5spellEPKc
[1]+  Done                    firefox


for background i'm using fiesty and firefox 2.0.0.11
on a sony pcg-384 
thanks.

---

