---
title: "Multiple Mouse buttons"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by americanneo on 2007-03-28
Hey I'm an absolute new user to ubuntu and linux, and i'm not very good at this. I have a mouse that has 10 buttons (left, right two wheels-one with button, back, forward buttons, and one "office switch"button) here is my mouse- [http://image.003.ru/xpics/13020-193.jpg]("http://image.003.ru/xpics/13020-193.jpg")
Its called A4tech NB 90.
I am trying to get all the buttons to work. I want the back and forward buttons to function as back, forward in firefox. I want the to 2nd Side Wheel to work as either one of the 4 functions:horizontal scrolling, zoom in/out, page up/down, or previous/next document. Oh and I want the "office Switch button to work as a button that closes the window. I used it like that in windows. I have the driver cd, but obviously i can't install it here. So if i can get any help that would be appreciated. Please elaborate, because i don't know much about linux.

---

### Post by kittyhawk63 on 2007-03-29
[quote=americanneo;2369377]Hey I'm an absolute new user to ubuntu and linux, and i'm not very good at this. I have a mouse that has 10 buttons (left, right two wheels-one with button, back, forward buttons, and one "office switch"button) here is my mouse- [http://image.003.ru/xpics/13020-193.jpg](http://image.003.ru/xpics/13020-193.jpg)
Its called A4tech NB 90.

Have you tried contacting the manufacturer to see if it will do all these things in Linux? That would be my first step, especially if you fail to find a solution on the forum. I hope you get it working, however. I am keeping a tag on you to see if you can get it to work.
kh

---

### Post by tonyr1988 on 2007-03-29
I need you to do a couple of things to get some more information about your mouse (hope we can get it working soon):

1) Open a Terminal. Applications >> Accessories >> Terminal. Type:

> xev

It will open a tiny box. Put your mouse in the box. You need to pay attention to what the Terminal is saying. Anytime you push a button, scroll a wheel, press a key, or move the mouse, it will show something. Push the buttons on the mouse you wish to configure and see what the button numbers are. For example, this is what shows up when I push the left-mouse button (button #1):

> ButtonPress event, serial 29, synthetic NO, window 0x2e00001,
    root 0x1a5, subw 0x0, time 2614652686, (177,170), root:(182,243),
    state 0x10, **button 1**, same_screen YES

Make note of the button numbers for all the buttons you wish to configure and post them here.

When done, just close that little box like normal (X in the corner). Don't close the Terminal window, though.

2) Still in the terminal, type:

> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gedit /etc/X11/xorg.conf

(Press Enter after the first command, type your password, then type the second command)

The first command makes a backup of the xorg.conf file. It's a very important file, so backups are a good decision (we won't be editing it yet, though). The second command will open that file in the text editor. Scroll down until you see something like:

> Section "InputDevice"
    Identifier     "Configured Mouse"

Once you've found that section, copy and paste the "block" into your reply (along with the button numbers). (The last line you need to copy is EndSection).

Hope those make sense.

---

### Post by h0ax on 2007-03-29
Hey there tony, great post.
In the first quote section you have an error that someone typing this verbatim may not understand "xorg.cong" instead of "xorg.conf"

Here's mine and I'm trying to map button 8 to a back button in firefox.
Help? :P

> 
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection


---

### Post by americanneo on 2007-03-29
> **tonyr1988 said:**
> I need you to do a couple of things to get some more information about your mouse (hope we can get it working soon):

1) Open a Terminal. Applications >> Accessories >> Terminal. Type:



It will open a tiny box. Put your mouse in the box. You need to pay attention to what the Terminal is saying. Anytime you push a button, scroll a wheel, press a key, or move the mouse, it will show something. Push the buttons on the mouse you wish to configure and see what the button numbers are. For example, this is what shows up when I push the left-mouse button (button #1):



Make note of the button numbers for all the buttons you wish to configure and post them here.

When done, just close that little box like normal (X in the corner). Don't close the Terminal window, though.

2) Still in the terminal, type:



(Press Enter after the first command, type your password, then type the second command)

The first command makes a backup of the xorg.conf file. It's a very important file, so backups are a good decision (we won't be editing it yet, though). The second command will open that file in the text editor. Scroll down until you see something like:



Once you've found that section, copy and paste the "block" into your reply (along with the button numbers). (The last line you need to copy is EndSection).

Hope those make sense.

When I try to back up the file it gives me this response cp: cannot stat `/etc/X11/xorg.cong': No such file or directory

Also here is the text in the box
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Thank you very much for your help
PS. When i was mapping the button to see what their numbers were, it gave me the same number for different buttons, because right now they are performing the same function, but as you know i want to change that.

---

### Post by h0ax on 2007-03-29
americanneo,

he had a typo in his code
it should be:
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
Also - be sure to put what buttons you got from running his suggested 1st test.

---

### Post by NiGHTS7041 on 2007-03-29
I have a small problem with my mouse. I am using a laptop and I don't like it where I touch the pad to click. How do I disable it? I am using feisty fawn

---

### Post by h0ax on 2007-03-29
> **NiGHTS7041 said:**
> I have a small problem with my mouse. I am using a laptop and I don't like it where I touch the pad to click. How do I disable it? I am using feisty fawn

Hey Nights, that's kind of a different issue, I would suggest posting your own thread with a more apt title.  This way you could get more direct help.

---

### Post by americanneo on 2007-03-29
PS. PS.
Left mouse button-Number 1
Right mouse button-Number 3
Primary wheel click-Number 2
Primary wheel Up-Number 4
Primary wheel Down-Number 5
"Office Switch" button-Number 1
Secondary wheel up-Number 5
Secondary wheel down-Number 4
Back button-Number 8
Forward button-Number 9

---

### Post by h0ax on 2007-03-30
by the way I got mine working myself with a little tinkering

I added
> 
Button    "8"
ButtonMapping "1 2 3 6 8"


This is what I did to add the back functionality to the button on the side of my mouse

Now that I think about it, I may have only needed to map 1 2 3 4 5 8 instead of 6, but good luck to you.
I would google for more help if you can't figure it out.

---

### Post by D-Force on 2007-04-23
Hi Hoax,
I have the same problem like you had..
where did you configure your mouse ?
Did you just add those lines in the xorg.conf ?

thx for the help..

d-force

---

