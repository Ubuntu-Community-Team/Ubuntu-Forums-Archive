---
title: "wheel as middle button annoying"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by sunita on 2008-02-20
Friends,
I am now using Gutsy. The behaviour of my PS/2 mouse is annoying. Specially when I am editing some text, say, in Kile. I highlight a line for copying, put the cursor on a new position, and click middle button, i.e., both left and right button simultaneously. It copies as expected. The annoying thing is that after this highlighting when I use the wheel for scrolling to a new position, the highlighted text gets copied at many more positions. The scrolling of the wheel acts as the middle button. And this puts the highlighted text at many unwanted places. I am really happy about pressing both the buttons to emulate the middle button, but not the wheeel to act as the middle button. The question: How to disable this feature of the wheel scrolling as the middle button? Thanks in advance. You can also reply to me (sunitaiitm@yahoo.co.in).

---

### Post by NT4usB on 2008-02-20
You want to disable the scrolling? or the wheel copying?
You familiar with editing xorg.conf? If not, you *could* screw things up...
I use a Logitech mx310 with side buttons. I've changed the thumb button to act as middle click. The scroll wheel just scrolls.
You want to edit your xorg.conf, and have a 5 (or six, or 8 button) mouse, change your xorg so:
**_Back it up first! So you can restore it when you screw it up**_
```
Section "InputDevice"
    Identifier     "Configured Mouse" #(don't change this. yours is whatever it is)
    Driver         "mouse" #(should be the same as yours)
    Option         "CorePointer" #(should be the same as yours)
    Option         "Device" "/dev/input/mice" #(should be the same as yours)
    Option         "Protocol" "ExplorerPS/2" #(should be the same as yours)
    Option         "Buttons" "8" #(whatever your mouse is)
    Option         "ZAxisMapping" "4 5" #(this is the scroll wheel)
    Option         "Emulate3Buttons" "false" #(disables clicking both buttons to be middle click)
    Option         "ButtonMapping" "1 6 3 2 4 5" #(this is the key to the thumb button as middle click)
    Option         "Resolution" "100"  
EndSection
```
don't include the notes in #(...) those are for explaination only...

To learn what buttons make what numbers on your mouse, type:```
xev
``` in a terminal. When you click and scroll over the window, you'll get numbers.

---

### Post by Gen2ly on 2008-02-20
lol, I had this problem, as I used to go whack on the scroll wheel.  Its a windows behavior most adopt.  I asked the same question here in the forums to what seemed to be an insane concept (at the time I destoyed a good part of my document because I turned the scroll wheel like Bob Barker was there. :)  The respondee sounded kinda pained, saying something like "The middle button is used for paste and can be quite useful..." I didn't see the point and no one had a solution at the time so I eventually got to learn to use it and now use it all the time.

Now... if I can only find a what to change the scroll wheel speed....

---

### Post by sunita on 2008-02-21
Thanks NT4usB.
I want to have 
1. Scrolling by the wheel
2. Disable copying by the wheel
3. Emulate middle button by pressing both left and right buttons simultaneously..
This is how it was behaving earlier; and I liked that.
Your code in xorg.conf does not meet the third requirement. 
For that, I need EmulateMiddleButton as true. Then how to prevent wheel copying? 
The relevant portion of my xorg.conf is here:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
	Option		"EmulateWheelTimeout"	"1"
EndSection

---

### Post by NT4usB on 2008-02-22
ok, so I just tried my xorg with emulate set to true. I can click both buttons and it acts as middle click. Clicking scroll wheel does not copy (or paste, or whatever...)
Try mapping your buttons (assuming you have a three button mouse- two buttons and a wheel)
```
    Option         "Buttons" "5" 
    Option         "ZAxisMapping" "4 5" 
    Option         "Emulate3Buttons" "true" 
    Option         "ButtonMapping" "1 6 3" (or, maybe "1 6 3 4 5")
```
Not sure about the 4 5 part of the mapping. Probably have to experiment a bit with it.

Edit your xorg then restart gdm to check the change.
I switch to tty1 (Ctrl+Alt+F1), login, then sudo /etc/init.d/gdm restart

---

### Post by sunita on 2008-02-22
Using Button mapping does the job. Since I have a wheel mouse there are five jobs assigned to it. using xev, I found that number pressing the wheel is assigned number 2. Also, pressing both left and right 'clicks ' is assigned to 2. However, modifying button mapping inthe xorg.conf instead of using xmodmap -e "pointers..." does the job. It keeps 2 for pressing both left-right clicks. But removes the annoying press-wheel behaviour.
All that I did:
Added the following line to the relevant portion of xorg.conf:

Option "ButtonMapping" "1 6 3 4 5"

Essentially removing 2 from it. 

Solved!

---

