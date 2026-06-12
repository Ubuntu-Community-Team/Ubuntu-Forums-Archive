---
title: "Cell phone in Ubuntu Edgy?"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by jrekkedal on 2007-03-22
I had an application when I was using XP called "BitPM" that would allow me to hookup my cellphone via usb and download/upload data. I don't have a cool bluetooth phone, nor does it have any PDA abilities. Just your run of the mill generic camera phone.

I'd rather not use Wine to get that application running again if I can avoid it by installing something opensource instead.  Any ideas or suggestions to start researching?

---

### Post by dracomordag on 2007-03-22
have you tried just plugging it in?

i doubt they would configure a phone as a USB drive, but who knows? try it and see if any messages come up

---

### Post by karthikp on 2007-03-22
I remember using kmobiletools for working with my old phone. I actually used it just a couple of times and it worked flawlessly. Try it out:

```
sudo apt-get install kmobiletools
```

If it's not what you were looking for,

```
sudo apt-get remove kmobiletools
```

Good luck!

---

### Post by jrekkedal on 2007-03-22
See, this is why I'm loving Ubuntu so much... Software readily available and the community is fast/friendly. YOU GUYS ROCK

---

### Post by Liakath on 2007-06-23
> **karthikp said:**
> I remember using kmobiletools for working with my old phone. I actually used it just a couple of times and it worked flawlessly. Try it out:

```
sudo apt-get install kmobiletools
```

If it's not what you were looking for,

```
sudo apt-get remove kmobiletools
```

Good luck!

Will it work in Feisty Fawn. I have Nokia 6020 with a USB Cable

I installed kmobiletools using 

[COLOR="#ff0000"]sudo aptitude install kmobiletools[/COLOR]

and when I start it this is the output I get

[COLOR="Red"]liakath@HomePC1:~$ kmobiletools
Using KUniqueApplication

liakath@HomePC1:~$ sudo kmobiletools
Using KUniqueApplication

liakath@HomePC1:~$ [/COLOR]

Nothing seems to happen I have Ctrl C to stop it running

Any thing that is missing

---

### Post by FrancoNero on 2007-08-28
nice tool. it detects my cell (nokia e65, symbian 3) after looking up on the tools website... but i can't really use anything, all it does is show battery status... from what i can tell they're not too far into supporting latest symbian versions yet.... time will come...

---

