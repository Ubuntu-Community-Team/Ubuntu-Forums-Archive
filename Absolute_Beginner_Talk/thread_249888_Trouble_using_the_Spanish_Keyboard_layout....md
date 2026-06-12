---
title: "Trouble using the Spanish Keyboard layout..."
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by UberIcarus on 2006-09-03
My default language for Ubuntu is English, but I need the spanish keyboard layout for my spanish class, only I can't get the keyboard to use accents. I'm on a laptop and neither Control, alt, nor function (super) work.


Anyone have a clue how to get the accents to work?

Note: I did change the keyboard layout under system preferences to latin america.

---

### Post by Rebeca on 2006-09-03
Ctrl + Shift + [a combination of letters and numbers] will allow you to use accents. If you want to know the specific codes, you can go to Accessories > Character Map. (You can use the English keyboard, and just memorize the code -- which you should be able to do if you were able to memorize the Alt + codes in windows.)

Example: 

Ctrl + Shift + E9 = é



However, if what you want to do is switch to different keyboards, then you could use kxkb: [http://docs.kde.org/stable/en/kdebase/kxkb/index.html](http://docs.kde.org/stable/en/kdebase/kxkb/index.html) or find something similar to that.

If you are not using KDE, you might have to download some extra kde files.

---

### Post by UberIcarus on 2006-09-03
Not using KDE, where can I download kxkb? I didn't see it in synaptic package manager.

Edit: Nevermind, found it under kbswitch

---

### Post by Rebeca on 2006-09-03
It isn't there... or, at least, it wasn't last time I checked.

BUT since you are using gnome (?), you should already have a keyboard selector too. Just right click on any of your gnome panels > Add to Panel > Utilities - Keyboard Indicator. So, just select that one and then click on Add.

In there (the "add to panel" window), you will also see a character pallette that you can add if you don't want to memorize any codes.

---

### Post by UberIcarus on 2006-09-03
Okay, tried using either of them, but I still can't get it to use specialized characters. Does this mean I have to manually input all of the unicode for each accented letter? Is there any program that will remap my keyboard so I can use accents without having to remember all the damn unicode?

Discovered I can do all the special characters, I was just doing it wrong, unfortunately it seems the accents aren't mapped for any of the spanish keyboards.

this is going to be a pain.

---

### Post by Rebeca on 2006-09-03
You said you had tried changing keyboard layouts before, did you also try this: [http://homepage.sunrise.ch/mysunrise/ekeller00/ubuntu/UiW_USkeyboard_intChars.html](http://homepage.sunrise.ch/mysunrise/ekeller00/ubuntu/UiW_USkeyboard_intChars.html)

?

---

### Post by ricardisimo on 2006-10-06
> **UberIcarus said:**
> Okay, tried using either of them, but I still can't get it to use specialized characters. Does this mean I have to manually input all of the unicode for each accented letter? Is there any program that will remap my keyboard so I can use accents without having to remember all the damn unicode?

Discovered I can do all the special characters, I was just doing it wrong, unfortunately it seems the accents aren't mapped for any of the spanish keyboards.

this is going to be a pain.

I'm using the layout US-International with dead keys which I find (so far) to be the best option for typing in both English and Spanish. Take a look. There is one very annoying aspect, which is that ¨ and ´ won't simply type onto the page; they wait to see what the next letter is going to be, which is fine if you want to type á, but not so fine when you want to type "Harvey's" and instead you get "Harvey&#347;". Or you want "I'm" and instead you get just "I". Test it out and you'll see what I'm talking about.
Would anyone know the easiest way to modify the standard US layout to include á as <ALT>a, ñ as <ALT>n, € as <ALT><SHIFT>4, etc... ? I think modifying the standard US layout might be the best option for both of us.

---

### Post by Alan Stancliff on 2007-10-08
> **UberIcarus said:**
> My default language for Ubuntu is English, but I need the spanish keyboard layout for my spanish class, only I can't get the keyboard to use accents. I'm on a laptop and neither Control, alt, nor function (super) work.


Anyone have a clue how to get the accents to work?

Note: I did change the keyboard layout under system preferences to latin america.

Hi UberIcarus,

I hope this is not too late, but you don't have to use the control, alt, or super-function keys to get the accented characters. You use what are called "dead keys." Several other keys are in positions where you would not expect them. For a step-by-step way to see how native Spanish speakers get these accents in speed touch typing, [**_[COLOR="Blue"]click on this link[/COLOR]_**]("http://www.alanstancliff.com/spanish/spanishkeys.pdf").

I hope this helps.

---

