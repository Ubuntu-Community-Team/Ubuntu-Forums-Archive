---
title: "Attempting to use Ubuntu for the first time but it can't seem to see my mouse."
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by victorcrane on 2007-11-02
Hi folks, apologies if this question exists a million times already in these threads somewhere, but I'm having a crack at using Ubuntu for the very first time and have found that when it loads up from the cd (which it appears to be doing perfectly well) it simply doesn't see the mouse. Keyboard shortcuts work ok and I can get around the menu's but I just can't find a way to make it recognise the mouse is there. 

It's a bog standard PS2 scroll mouse so I would have thought it should be pretty straightforward. 

Please let me know if I'm being a complete ****. 

Vic. :)

---

### Post by philinux on 2007-11-02
Is it the live cd your using .

Is it Gutsy?

---

### Post by victorcrane on 2007-11-02
I'm not 100% certain what version it is by name, I can't see anything which would tell me which it is, but it's version 7.04 if thats helps at all? I've just noticed there's a 7.10 which I'm downloading now and I'll give that a shot. 

:)

---

### Post by philinux on 2007-11-02
ok 7.04 is codenamed Feisty 
     7.10 Gutsy. 7.1 has better hardware detection but I would not have thought the mouse to be a problem at all. Very strange.

What are your pc specs by the way.

---

### Post by erginemr on 2007-11-02
I'd like nominate this for the strangest problem award that anyone has come across. Blank screen due to graphics cards yes, kernel error messages ok, but an issue with a standard mouseware? I am eagerly awaiting from upcoming suggestions what this error forebodes to.

Good luck, by the way, on your problem.

---

### Post by victorcrane on 2007-11-02
lol, yes I thought it rather bizarre that a simple mouse should not be detected. I'm just burning 7.1 and I'll let you guys know how I get on. 

My system is a P4 1.6ghz, 640mb ram, 40gb hard disc and 128mb nvidia gfx. It's slow by todays standards I know but I'm one of these guys who hates throwing serviceable technology away. I'll run it until it dies and only then will I begrudgingly consider some form of replacement, 

;)

Oh and would you look at that... 'Burn process failed'....  I'm having an awesome day for computing. 

:)

---

### Post by victorcrane on 2007-11-02
Ok, just got my 7.1 cd burned and fired it up.... exactly the same problem! Mouse pointer just sits right there in the centre and the mouse doesn't do a thing. This is very frustrating, I've been wanting to try this out and when I finally find a few hours to have a look at it.... 

Typical. Suggestions anyone??? 

I may have another mouse but since I know this one works perfectly well I'm loathe to start digging through my drawers in the garage to find it.

:confused:

---

### Post by alwiap on 2007-11-02
> **victorcrane said:**
> Ok, just got my 7.1 cd burned and fired it up.... exactly the same problem! Mouse pointer just sits right there in the centre and the mouse doesn't do a thing. This is very frustrating, I've been wanting to try this out and when I finally find a few hours to have a look at it.... 

Typical. Suggestions anyone??? 

I may have another mouse but since I know this one works perfectly well I'm loathe to start digging through my drawers in the garage to find it.

:confused:

have you tried the mouse you are using RECENTLY on another computer?  perhaps something happened (it fell etc.) just before you installed ubuntu? i would try out several mice to see if that is the problem, or maybe there's something wrong with the ps2 port.  good luck and i hope you can resolve the problem

---

### Post by alwiap on 2007-11-02
p.s. have you tried starting ubuntu in safe graphics mode ?

---

### Post by erginemr on 2007-11-02
> **alwiap said:**
> have you tried the mouse you are using RECENTLY on another computer?  perhaps something happened (it fell etc.) just before you installed ubuntu? i would try out several mice to see if that is the problem, or maybe there's something wrong with the ps2 port.  good luck and i hope you can resolve the problem

I agree. Either your mouse or your ps2 port should be broken. And the only way is to connect your backup mouse to see if it works or not.

Does it work under Windows? (Stupid question, it probably does. Otherwise you would notice that.)

On a last resort, can you check how your "/etc/X11/xorg.conf" file looks like (even if it is still a live cd that runs) by issuing:
"less /etc/X11/xorg.conf" from the console and checking the mouse section. 

For instance, mine looks like as follows:
...
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
...

---

### Post by victorcrane on 2007-11-04
All is revealed! 

After running a few tests it is now apparent my ps2 port is well and truly faulty. I don't know quite why this hasn't affected windows but after some consideration I recall when I first put this pc together I did have problems with the mouse pointer running around the screen at random. This issue ironed itself out at some point years back and I'd forgotten all about it. Obviously it's part functional, how exactly this occurs I have no clue as my technical expertise is limited. 

I'm now running the live cd on my laptop with a view to installing it and using it as my main OS once I get my head round it. I like it very much so far.

Many thanks to those of you who have offered valuable advice. 

All the best.

Vic :)

---

### Post by Ripfox on 2007-11-04
For the record, I had a desktop that wanted to do this too, and i just hooked up a usb mouse and it worked swimmingly.

---

### Post by erginemr on 2007-11-04
> **victorcrane said:**
> All is revealed! 

After running a few tests it is now apparent my ps2 port is well and truly faulty. I don't know quite why this hasn't affected windows but after some consideration I recall when I first put this pc together I did have problems with the mouse pointer running around the screen at random. This issue ironed itself out at some point years back and I'd forgotten all about it. Obviously it's part functional, how exactly this occurs I have no clue as my technical expertise is limited. 

I'm now running the live cd on my laptop with a view to installing it and using it as my main OS once I get my head round it. I like it very much so far.

Many thanks to those of you who have offered valuable advice. 

All the best.

Vic :)

You are most welcome Vic. Same advice here. If you have a spare USB slot, you may consider grabbing a USB mouse (there are plenty) from a local market and using it instead of using your ps2 port.

Take care.

---

