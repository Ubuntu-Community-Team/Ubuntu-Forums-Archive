---
title: "MouseKeys: Additional Keyboard Mappings"
date: 2009-03-28
forum: Assistive Technology &amp; Accessibility
---

### Post by Steven Edwards on 2009-03-28
For reference, I use a mouthstick to type and MouseKeys to control the keyboard.  One of the things I like about Ubuntu (as a five day newbie) is its leveraging of X11, which lets us remap keys.

Reaching the keypad to move the mouse is a bit of a pain for me, so I set about modifying it to be more convenient&#8212;and I thought I'd share my new mappings.  (Please read the caveats at the bottom before using this.)

In addition to the standard keypad mousekeys, the following key mappings exist:

[indent]**u** - move up ten pixels, left ten pixels
**i** - move up ten pixels
**o** - move up ten pixels, right ten pixels
**j** - move left ten pixels
**l** - move right ten pixels
**m** - move down ten pixels, left ten pixels
**,** - move down ten pixels
**.** - move down ten pixels, right ten pixels

**b** - left mouse click
**n** - right mouse click

**g** - begin, end drag left mouse button
**h** - begin, end drag right mouse button

**t** - scroll up
**y** - scroll down[/indent] /usr/share/X11/xkb/compat/mousekeys:

```
// mousekeys, v 1.5b 2009/03/28

// $Xorg: mousekeys,v 1.3 2000/08/17 19:54:34 cpqbld Exp $

// Interpretations for arrow keys and a bunch of other 
// common keysyms which make it possible to bind "mouse" 
// keys using xmodmap and activate or deactivate them 
// from the keyboard.

default partial xkb_compatibility "mousekeys" {

    // Keypad actions.
    //
    interpret.repeat= True;

    interpret KP_1 { 
	action = MovePtr(x=-1,y= +1); 
    };
    interpret KP_End { 
	action = MovePtr(x=-1,y= +1); 
    };
    interpret m { 
	action = MovePtr(x=-10,y= +10); 
    };

    interpret KP_2 { 
	action = MovePtr(x=+0,y= +1); 
    };
    interpret KP_Down { 
	action = MovePtr(x=+0,y= +1); 
    };
    interpret comma { 
	action = MovePtr(x=+0,y= +10); 
    };

    interpret KP_3 { 
	action = MovePtr(x=+1,y=+1); 
    };
    interpret KP_Next { 
 	action = MovePtr(x=+1,y=+1); 
    };
    interpret period { 
	action = MovePtr(x=+10,y=+10); 
    };

    interpret KP_4 { 
	action = MovePtr(x=-1,y=+0); 
    };
    interpret KP_Left { 
	action = MovePtr(x=-1,y=+0); 
    };
    interpret j { 
	action = MovePtr(x=-10,y=+0); 
    };

    interpret KP_6 { 
	action = MovePtr(x=+1,y=+0); 
    };
    interpret KP_Right { 
 	action = MovePtr(x=+1,y=+0); 
    };
    interpret l { 
 	action = MovePtr(x=+10,y=+0); 
    };

    interpret G { 
	action = LockPointerButton(button=1,affect=lock); 
    };
    interpret H { 
	action = LockPointerButton(button=3,affect=lock); 
    };

    interpret KP_7 {
	action = MovePtr(x=-1,y=-1); 
    };
    interpret KP_Home { 
	action = MovePtr(x=-1,y=-1); 
    };
    interpret u { 
	action = MovePtr(x=-10,y=-10); 
    };

    interpret KP_8 { 
	action = MovePtr(x=+0,y=-1); 
    };
    interpret KP_Up { 
	action = MovePtr(x=+0,y=-1); 
    };
    interpret KP_i { 
	action = MovePtr(x=+0,y=-10); 
    };

    interpret KP_9 { 
	action = MovePtr(x=+1,y=-1); 
    };
    interpret KP_Prior { 
	action = MovePtr(x=+1,y=-1); 
    };
    interpret o { 
	action = MovePtr(x=+10,y=-10); 
    };

    // Button clicks/actions
    interpret b { 
	action = PointerButton(button=1); 
    };
    interpret n { 
	action = PointerButton(button=3); 
    };
    interpret B { 
	action = PointerButton(button=1); 
    };
    interpret N { 
	action = PointerButton(button=3); 
    };
    interpret g { 
	action = LockPointerButton(button=1); 
    };
    interpret h { 
	action = LockPointerButton(button=3); 
    };
    interpret G { 
	action = LockPointerButton(button=1); 
    };
    interpret H { 
	action = LockPointerButton(button=3); 
    };
    interpret t { 
	action = PointerButton(button=4); 
    };
    interpret y { 
	action = PointerButton(button=5); 
    };
    interpret T { 
	action = PointerButton(button=4); 
    };
    interpret Y { 
	action = PointerButton(button=5); 
    };
    // End clicks/actions

    interpret KP_5 { 
	action = PointerButton(button=default); 
    };
    interpret KP_Begin { 
	action = PointerButton(button=default); 
    };

    interpret KP_F2 { 
	action = SetPtrDflt(affect=defaultButton,button=1); 
    };
    interpret KP_Divide { 
	action = SetPtrDflt(affect=defaultButton,button=1); 
    };

    interpret KP_F3 { 
	action = SetPtrDflt(affect=defaultButton,button=2); 
    };
    interpret KP_Multiply { 
	action = SetPtrDflt(affect=defaultButton,button=2); 
    };

    interpret KP_F4 { 
	action = SetPtrDflt(affect=defaultButton,button=3); 
    };
    interpret KP_Subtract { 
	action = SetPtrDflt(affect=defaultButton,button=3); 
    };

    interpret KP_Separator { 
	action = PointerButton(button=default,count=2); 
    };
    interpret KP_Add { 
	action = PointerButton(button=default,count=2);
    };

    interpret KP_0 { 
	action = LockPointerButton(button=default,affect=lock); 
    };
    interpret KP_Insert { 
	action = LockPointerButton(button=default,affect=lock); 
    };

    interpret KP_Decimal { 
	action = LockPointerButton(button=default,affect=unlock); 
    };
    interpret KP_Delete { 
	action = LockPointerButton(button=default,affect=unlock); 
    };


    // Additional mappings for Solaris keypad compatibility
    interpret F25 { // aka KP_Divide
	action = SetPtrDflt(affect=defaultButton,button=1); 
    };
    interpret F26 { // aka KP_Multiply
	action = SetPtrDflt(affect=defaultButton,button=2); 
    };
    interpret F27 { // aka KP_Home
	action = MovePtr(x=-1,y=-1); 
    };
    interpret F29 { // aka KP_Prior
	action = MovePtr(x=+1,y=-1); 
    };
    interpret F31 { // aka KP_Begin
	action = PointerButton(button=default); 
    };
    interpret F33 { // aka KP_End
	action = MovePtr(x=-1,y= +1); 
    };
    interpret F35 { // aka KP_Next
 	action = MovePtr(x=+1,y=+1); 
    };

    interpret.repeat= False;


    // New Keysym Actions.
    //
    interpret Pointer_Button_Dflt {
	action= PointerButton(button=default);
    };
    interpret Pointer_Button1 {
	action= PointerButton(button=1);
    };
    interpret Pointer_Button2 {
	action= PointerButton(button=2);
    };
    interpret Pointer_Button3 {
	action= PointerButton(button=3);
    };
    interpret Pointer_DblClick_Dflt {
	action= PointerButton(button=default,count=2);
    };
    interpret Pointer_DblClick1 {
	action= PointerButton(button=1,count=2);
    };
    interpret Pointer_DblClick2 {
	action= PointerButton(button=2,count=2);
    };
    interpret Pointer_DblClick3 {
	action= PointerButton(button=3,count=2);
    };
    interpret Pointer_Drag_Dflt	{
	action= LockPointerButton(button=default);
    };
    interpret Pointer_Drag1 {
	action= LockPointerButton(button=1);
    };
    interpret Pointer_Drag2 {
	action= LockPointerButton(button=2);
    };
    interpret Pointer_Drag3 {
	action= LockPointerButton(button=3);
    };

    interpret Pointer_EnableKeys {
	action= LockControls(controls=MouseKeys);
    };
    interpret Pointer_Accelerate {
	action= LockControls(controls=MouseKeysAccel);
    };
    interpret Pointer_DfltBtnNext {
	action= SetPtrDflt(affect=defaultButton,button= +1);
    };
    interpret Pointer_DfltBtnPrev {
	action= SetPtrDflt(affect=defaultButton,button= -1);
    };


    // Allow an indicator for MouseKeys.
    indicator "Mouse Keys" {
//	!allowExplicit;
	indicatorDrivesKeyboard;
	controls= MouseKeys;
    };
};
``` I also added F7 as an additional toggle mousekeys on/off key by creating $HOME/.Xmodmap and inserting:

```
keysym F7 = MouseKeys_Enable
``` **Caveat:** This setup currently causes all non-specified keys to move the pointer up when MouseKeys are on, so remember to disable MouseKeys before trying to use them.  If I learn how to prevent that behavior, I'll update this message.

**Caveat 2:** This works with Pointer "1 2 3" and ZAxisMapping "4 5" set.  If you use other settings, I doubt this will work for you.

I hope this is useful to someone.

Steven

---

### Post by me.kame on 2009-03-29
Test

---

### Post by Luc 284 on 2010-08-01
I think the file name should be /usr/share/X11/xkb/compat/mousekeys, and you may need to install xkbset.

---

### Post by ImaWestie on 2011-07-23
I'm looking to use mousekeys with a Microsoft Arc keyboard to control a Media focussed PC.

This keyboard does not have a numlock button (because there is no number pad).
I understood that mousekeys should be activated with ctrl+alt+numlock, but when i look at the keyboard shortcuts it's not listed there.

What file am I looking at to find this keymap?

Thanks

---

### Post by Nyght on 2011-10-10
I have been looking into existing assistive technologies and I have a very noobish question.

Are pixels as big as I remember them? Wouldn't moving a few left or right, up or down with a single click or keystroke not accomplish much? What applications are there for moving a few pixels at a time (seriously I am not trying to be a smart-alek [a mod just spanked me for saying <snip>] I just am not as familiar with the technology as some)? Z/Z

---

### Post by coffeecat on 2011-10-10
Old thread.

If anyone needs help with this issue it would be better to start a new thread.

Thread closed.

---

### Post by coffeecat on 2011-10-12
Thread re-opened.

---

### Post by wv9k on 2012-02-16
Had this working for a friend who has MS in deb5.  Building her a new machine using Ubuntu 10.04 using the Trinity DE (was kde3) and I am having no luck with getting this going.

The new mousekeys that uses the numpad is too far away for her to reach and she is used to this one.

I have had NO luck getting rid of the new built in mousekeys and no luck replacing it with this one.

Been at it for 3 days now and google has been no help.  Disabled it in the control panel and commented it out in 3 separate directories under /usr/share/X11/ and it is still there.

Now that there is no xorg.conf will this even work anymore?

This really helps my friend and if there is any way to get this going I'd very VERY much appreciate any ideas, comments or pointers to get this working on the new machine.

Thanks for any help!!!!!!!!!!!

---

### Post by wv9k on 2012-02-24
> **wv9k said:**
> Had this working for a friend who has MS in deb5.  Building her a new machine using Ubuntu 10.04 using the Trinity DE (was kde3) and I am having no luck with getting this going.

The new mousekeys that uses the numpad is too far away for her to reach and she is used to this one.

I have had NO luck getting rid of the new built in mousekeys and no luck replacing it with this one.

Been at it for 3 days now and google has been no help.  Disabled it in the control panel and commented it out in 3 separate directories under /usr/share/X11/ and it is still there.

Now that there is no xorg.conf will this even work anymore?

This really helps my friend and if there is any way to get this going I'd very VERY much appreciate any ideas, comments or pointers to get this working on the new machine.

Thanks for any help!!!!!!!!!!!

 Started over from scratch and just renamed the original compat/mousekeys and copied in the other one and somehow it worked this time.  Never a dull moment :-)!

---

