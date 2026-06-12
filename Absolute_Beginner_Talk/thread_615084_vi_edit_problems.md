---
title: "vi edit problems"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by AKCaveman on 2007-11-16
I'm still learning this Linux stuff and ive hit on a somewhat big problem.

Whenever i use the *sudo vi* command it brings up whatever file but I cannot edit anything.
It looks kind of like this:

```
such and such text.....
~
~
~
~
~
~

```

Well it is impossible to edit anything in there and once i do I cannot seem to save it or do anyhting but reboot the system because i get stuck in there. What am i doing wrong and is there another program i can use?

---

### Post by mellowd on 2007-11-16
vi is not the easiest to use when first starting out. If you wanted to enter text you would need to press insert. when done you can press escape and then ```
:wq!
``` (enter) to write changes and exit. do a ```
:q!
``` to exit without making any changes. You need to ensure you are not in edit mode when typing those commands otherwise it wont work. I usually press escape a few times to ensure. 

other basic commands: r to replace one character, dd to delete a line and o to insert a new line

vi seems to be a bit buggy in ubuntu. I installed and use vim. You could use nano. It's a lot easier for someone new.

---

### Post by taurus on 2007-11-16
Don't forget to install the vim-full if you decide to use vi/vim.

```
sudo apt-get update
sudo apt-get install vim-full
```

---

### Post by AKCaveman on 2007-11-16
ohh okay at least i don't feel as stupid as i normally do over linux stuff.
yeah i downloaded vim instead and its much more intuitive. My only question with it is how the hell do you save and escape?

---

### Post by mellowd on 2007-11-16
> **AKCaveman said:**
> ohh okay at least i don't feel as stupid as i normally do over linux stuff.
yeah i downloaded vim instead and its much more intuitive. My only question with it is how the hell do you save and escape?

Press escape, then :wq! then enter. that saves the changes and exits.

---

### Post by mellowd on 2007-11-16
:q! is quit
:wq! is write, quit
:w filename  - will write the file

---

### Post by nick_h on 2007-11-17
> vi is not the easiest to use when first starting out.
vi is not the easiest but is installed on just about every unix system by default, so it can be useful to learn.  It is also quite powerful.

Google for "vi commands" and you will find some quick reference guides - for example - this [vi reference](http://www.unix-manuals.com/refs/vi-ref/vi-ref.htm).

---

### Post by LaRoza on 2007-11-17
> **AKCaveman said:**
> My only question with it is how the hell do you save and escape?

":wq" to save and exit.

I often type that by accident in any text editor and word processor, vim grows on you.

---

### Post by MegaJim on 2007-11-17
You could also try

```
vimtutor
```

if you want to get down and dirty with it

---

### Post by whitespy9 on 2007-11-17
pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico pico is so much easier.

---

### Post by mellowd on 2007-11-17
Once you know vi its easy as pie

---

### Post by tyggna1 on 2007-11-17
nano might be an easier CLI text editor for beginners--especially if your GUI isn't working and you can't browse online for vi commands.   Vim rocks when you get it down, though.

---

### Post by poudin on 2007-11-18
k...i will try and keep this simple...i use vi a lot at work...

vim works best for ubuntu

when u 1st enter sudo vim filename...u are in command mode...u can researh the shortcuts that let u modify files in command mode

if you want to edit it...hit the insert key...and it should show you INSERT at the bottom left of the screen...make your edits...and to save your chages....hit :x....equivalent to save and exit..

u can get a little vi editor cheat book at indigo/chapters..that will show u all the shortcuts....it is very powerful...once u get the hang of it.

good luck with your linux adventure! :)

---

### Post by kevdog on 2007-11-18
Hitting Shift-ZZ while in command mode does the same thing as :wq.  I find it much easier.

---

