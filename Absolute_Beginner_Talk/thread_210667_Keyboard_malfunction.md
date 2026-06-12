---
title: "Keyboard malfunction"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by acretinmelon on 2006-07-07
I posted a while ago about my new keyboard on my new Linux system failing to understand certain keys.  I was told not to blame Linux.

Now, I have the same problem with TWO keyboards: now and then, they both fail to recognize s, w, and p.  They start and stop working inconsistently regardless of which keyboard is swapped in.  After changing the keyboard to ACPI standard and Dell the p started working again, but this seems to be a fluke.  The s and w started working shortly after.  What's the deal?  How can I make my keyboard work consistently?

---

### Post by richbarna on 2006-07-07
This sounds like an intermittent fault with your keyboard connection.

1. Do the keyboards work with windows?
2. Have you installed any keyboard affecting software (xgl/compiz)?
3. You could reconfigure your xorg.conf file.
4. Check your keyboard socket on the back of the pc.(clean it)

---

### Post by acretinmelon on 2006-07-07
1.  I haven't tried it in Windows during one of the malfunctions, but never had this problem until I loaded Linux (so, possibly--but unlikely).

2.  Not that I know of.

3.  I don't know how--any advice?

4.  Done!

---

### Post by richbarna on 2006-07-07
3. You could reconfigure your xorg.conf file.
3.  I don't know how--any advice?

Ok you will basically go through the system config again by answering yes or no etc to the questions.

First backup your xorg.conf file (always do this before changing anything)

> [SIZE=-1]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup[/SIZE] 
you need to get to the console by clicking Ctrl + Alt + F4 (the same again with F7 to get back to desktop)

In console , login, then at the prompt type this command :-

> sudo dpkg-reconfigure xserver-xorg

You can use the TAB button to move from the selection and "ok" or "no", and enter to continue.
I suggest you just continue through with defaults until you get to keyboard.

---

### Post by acretinmelon on 2006-07-07
Okay, the roblem i definitely Linux.  A you can ee, the key I mentioned before have agained toed working--but work fine in Window.

---

### Post by T700 on 2006-07-07
> **acretinmelon said:**
> Okay, the roblem i definitely Linux.  A you can ee, the key I mentioned before have agained toed working--but work fine in Window.

No offense, but I'd guess the problem is more likely user error.  Millions of people use their keyboards successfully under Linux.  Perhaps you selected the wrong keyboard mapping when you installed? 

Paul

---

### Post by acretinmelon on 2006-07-07
> **T700 said:**
> No offense, but I'd guess the problem is more likely user error.  Millions of people use their keyboards successfully under Linux.  Perhaps you selected the wrong keyboard mapping when you installed? 

Paul

Believe me, I entertained the possibility that it was my error, but this is an intermittent problem that remains when I swap out my keyboard and disappears when I boot Windows.  It sure seems like a bug to me, and I'm stumped.

---

### Post by richbarna on 2006-07-07
> **acretinmelon said:**
> Okay, the roblem i definitely Linux.  A you can ee, the key I mentioned before have agained toed working--but work fine in Window.

Lol, i'm sorry, I had to laugh, because the same thing happened to me.(see thread)
[http://www.ubuntuforums.org/showthread.php?t=168727&highlight=keyboard+problem](http://www.ubuntuforums.org/showthread.php?t=168727&highlight=keyboard+problem)

Ok, I really don't know what to suggest, other than checking the keyboard config again, sorry. I really think it is a hardware problem (where you connect the keybord to the mother board).
Maybe you could check inside the box, just in case the connector has come loose.

PS: lol, ps sorry :)
Could you post this section of your xorg.conf file :-
> Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc104"
    Option        "XkbLayout"    "es"
EndSection
Mine is a Spanish keyboard layout, hence the "es".

To do this, open the terminal and copy and paste :-

> gksudo gedit /etc/X11/xorg.conf

A password box will come up and then "gedit" will open, scroll down to the keyboard section.

---

### Post by T700 on 2006-07-07
> **acretinmelon said:**
> Believe me, I entertained the possibility that it was my error, but this is an intermittent problem that remains when I swap out my keyboard and disappears when I boot Windows.  It sure seems like a bug to me, and I'm stumped.

I missed the intermittent part in your orginal post; sorry.  If it's not all the time, I'd bet US$50 it's a hardware issue.  If not with the keyboard, something with the connecter.  

The only other thing I can think of is some background process seizing control now and then.  Have you considered doing a full reinstall, as crazy as that seems for a keyboard issue!

Paul

---

### Post by richbarna on 2006-07-07
> **T700 said:**
> I'd bet US$50 it's a hardware issue. 
Paul
  Me too. I'll have a look at his xorg.conf first, but I'm pretty sure it's hardware.

---

### Post by acretinmelon on 2006-07-07
> **richbarna said:**
> Me too. I'll have a look at his xorg.conf first, but I'm pretty sure it's hardware.

I agree that's the most tempting solution, but I don't have these problems in Windows at all.......how does this xorg.conf business work exactly?

---

### Post by acretinmelon on 2006-07-07
Okay, here it is:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"inspiron"
	Option		"XkbLayout"	"us"
EndSection



> **richbarna said:**
> Lol, i'm sorry, I had to laugh, because the same thing happened to me.(see thread)
[http://www.ubuntuforums.org/showthread.php?t=168727&highlight=keyboard+problem](http://www.ubuntuforums.org/showthread.php?t=168727&highlight=keyboard+problem)

Ok, I really don't know what to suggest, other than checking the keyboard config again, sorry. I really think it is a hardware problem (where you connect the keybord to the mother board).
Maybe you could check inside the box, just in case the connector has come loose.

PS: lol, ps sorry :)
Could you post this section of your xorg.conf file :-

Mine is a Spanish keyboard layout, hence the "es".

To do this, open the terminal and copy and paste :-



A password box will come up and then "gedit" will open, scroll down to the keyboard section.

---

### Post by richbarna on 2006-07-07
> **acretinmelon said:**
> I agree that's the most tempting solution, but I don't have these problems in Windows at all.......how does this xorg.conf business work exactly?

Hey! you got your p's and your s's back. So basically it works in linux now. But in your other post it didn't. So either your keyboard/xorg setup is being changed every five minutes, or you have a hardware problem.
Why not let windows warm up a bit and then see how the keyboard performs. Heat normally seperates broken tracks on motherboards, hence the intermittent fault. I could be wrong. but for this to happen on two keyboards is a bit strange.

Your xorg file is what controls the connected hardware, it tells your computer what you've got plugged in and which driver and settings to use. Similar to the Windows registry (i'm going to get some pedantic s*d complain about this, but it's a very basic comparison).

---

