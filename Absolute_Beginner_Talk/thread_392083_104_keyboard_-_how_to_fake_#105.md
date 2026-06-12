---
title: "104 keyboard - how to fake #105??"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by freebird54 on 2007-03-24
I noticed during one the (several) runs through **dpkg-reconfigure xserver-xorg** that there is a item suggesting that Caps Lock can be reconfigured to be a second CTRL key  (**ctrl:nocaps**  -  or something like that).  I haven't yet seen any documentation that suggests that a Windows (Tux) key can be faked.  Is this possible?  Where would I look for the magic incantation?  It doesn't seem that **super:nocaps** works - is there another designation for the key in question?

I've been using this keyboard (Fujitsu) since 1999 or earlier, and I would hate to give it up just to get another key.... (it is very heavy/solid/tolerant of abuse/fast)

Thanks if you can help!

---

### Post by adam.tropics on 2007-03-24
In your System-->Preferences-->Keyboard-->Layout options menu, you can change the behaviour of said keys. (Alt/Win key, and many others)

---

### Post by freebird54 on 2007-03-24
Yeah - I went through all that.  There are a lot of ways to set a Win key to something else.... but I still don't see a way to set something else to 'be' a Win key.

Strange that there seems to be something that CAN'T be configured on a LInux system!  (when I say [can't] - I mean without programming.  Presumably if I find the keyboard handler,  I could wedge some code in to handle it.  Problem is to keep it from being updated away constantly...

Thanks,  though!  It is not as if I could find a way to do it in any other OS I've tried either!

---

### Post by adam.tropics on 2007-03-24
> **freebird54 said:**
> Yeah - I went through all that.  There are a lot of ways to set a Win key to something else.... but I still don't see a way to set something else to 'be' a Win key.

Strange that there seems to be something that CAN'T be configured on a LInux system! 

Sorry, misunderstood what you were after I think, You might want to look into xbindkeys....there must be a way! The only time I have used it is actually in setting up my mouse buttons, so I can't be much help with it I am afraid, but I can't see a reason for it to be impossible.

---

### Post by rusty4r on 2007-03-24
I would just like for the "F" buttons to work on mine

---

### Post by freebird54 on 2007-03-24
Thanks - I'll have a look.  I suspect that it comes a little too late in the key-handling process - but then again all I was after was to able use Beryl features without having to reconfigure all the commands every update :D

Xbindkeys looks neat in its own right, though.

---

### Post by freebird54 on 2007-03-24
rusty4r - they don't do anything at all?  Laptop?  Desktop?  Intended key layout?  I *MIGHT* be able to help with some more info - as I've been digging around in there a little bit lately...

(trying to get the beans the hard way?)

---

### Post by adam.tropics on 2007-03-24
> **freebird54 said:**
> Thanks - I'll have a look.  I suspect that it comes a little too late in the key-handling process - but then again all I was after was to able use Beryl features without having to reconfigure all the commands every update :D

Xbindkeys looks neat in its own right, though.

Which version of Beryl are you using? The settings manager saves profiles, I don't know if that includes the keybindings, but you'd think...since it does set them up....

---

### Post by freebird54 on 2007-03-24
That's probably an answer that will work for Beryl.  I haven't put a lot of time into Beryl yet, on the principle that it isn't quite ready for prime time yet.  It *DOES* seem pretty stable on my system though, and I liked adding smoke to the fire :D

Into every life a little rain must fall....  (that's the 'goal')

---

### Post by rusty4r on 2007-03-24
> **freebird54 said:**
> rusty4r - they don't do anything at all?  Laptop?  Desktop?  Intended key layout?  I *MIGHT* be able to help with some more info - as I've been digging around in there a little bit lately...

(trying to get the beans the hard way?)

No not at all. I have a Micro Innovations EZ-8000 Smart Office Keyboard and I dont really care about the extra buttons just wish the "F" buttons would work so I could "Alt+F2" and such.

Also tried My wifes old Compaq keyboard its really nice but its USB and it doesnt work either. So I'm using my kids keyboard and its terrible.

---

### Post by rusty4r on 2007-03-24
OK its been a while since I tried them so I just tried them again. The micro still doesn't work but I discovered that one of my USB ports must be bad because I unplugged my printer and plugged the compaq keyboard into that port and it works.

But will it work before boot? like in supergrub or gparted live or even a Ubuntu live cd?

---

### Post by freebird54 on 2007-03-24
Does the Innovations keyboard normally require some sort of driver under Windows?  Whenever I see 'Smart' in the name, I start worrying :)

There may be a 'mode' change capability as well - if so choose the 'dumb compatability mode' option if available...  I'll go Google that and see if I see anything...

BTW - I meant *I* was after beans the hard way..  lovely how easy it is to mislead by accident - especially when attempting to amuse.. :oops:

---

### Post by rusty4r on 2007-03-24
> Does the Innovations keyboard normally require some sort of driver under Windows?
Yes it does and I have contacted the manufacturer to request Linux drivers and got this real nice apologetic email informing me that "for now" I'm out of luck.

And now I've found this "compaq internet keyboard (17 Keys)" in the keyboard layout choices that is working well with my wife's old keyboard. So that is a major improvement.

---

### Post by timschaller on 2007-10-17
I'm also using an EZ-8000. I found a button on the top left that toggles between the "F" functions and whatever the "alternate" functions are.

I guess I should mention that it is the medium sized round button above the escape ("Esc") key.

Hope this helps.

---

