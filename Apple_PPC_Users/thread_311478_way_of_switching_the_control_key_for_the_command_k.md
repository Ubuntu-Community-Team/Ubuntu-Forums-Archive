---
title: "way of switching the control key for the command key?"
date: 2006-12-02
forum: Apple PPC Users
---

### Post by albesan on 2006-12-02
hello team,

Yes, it's me again...
I was wondering, so, ism't there a way of switching the control key for the command key to use the keyboard like on Mac OS?
Switching betwen systems is slowing me down when getting shotcuts wrong.

I looked at the keyboard setting but I saw no ovius way of doing it. It strikes like a pretty obvious customization for ppc users...

any comments would be appreciated.

a.

---

### Post by hod139 on 2006-12-02
You can go to System->Preferences->Keyboard
Then select the Layout Options tab,
Then switch the Ctrl and Capslock keys there.

---

### Post by funk19 on 2006-12-03
> **hod139 said:**
> You can go to System->Preferences->Keyboard
Then select the Layout Options tab,
Then switch the Ctrl and Capslock keys there.

Forgive my ignorance but this doesn't make much sense to me. All this does for me is swap caps lock with ctrl which is not what I want.

I want to be able to replace ctrl with apple command key so copying and pasting is as simple as command+c or command+v

---

### Post by 3rdalbum on 2006-12-03
What happens if you go into System > Preferences > Keyboard, then click the Layouts tab, and select the "Macintosh" keyboard model? (I'm away from my PPC so I can't try it)

---

### Post by handylinux on 2006-12-03
> **3rdalbum said:**
> What happens if you go into System > Preferences > Keyboard, then click the Layouts tab, and select the "Macintosh" keyboard model?
Well, I just tried this on my iBook (6.10), then opened Firefox and tried command-N for a new window, and it did it -- or at least I thought it did, but everything I've tried since then hasn't worked; the ctrl key is still required. After 18 years exclusively on the Mac, I too find it hard to remember to use ctrl instead of command. Shouldn't be too hard to make the Macintosh keyboard model work like, well, a Macintosh keyboard, I would think. Unfortunately, though, I don't know how to modify it to that end.

In the meantime, I've learned what Ubuntu does when the battery runs down. The iBook went to sleep like it's supposed to, but Ubuntu apparently didn't understand; it crashed. (And just now I noticed that Firefox's spell checker flags "Ubuntu" as suspicious.)

Just discovered that fn+delete = forward delete, just like in Mac OS; I guess it's a hardware function.

---

### Post by funk19 on 2006-12-04
> **3rdalbum said:**
> What happens if you go into System > Preferences > Keyboard, then click the Layouts tab, and select the "Macintosh" keyboard model? (I'm away from my PPC so I can't try it)

Changing the keyboard also didn't work for me on my iBook G4 (6.10).

---

### Post by Gen2ly on 2006-12-04
I was also hoping to find out something about this.  I would like to use the apple key instead of control and also on my iBook F11 and isn't mapped.  I found an xmodmap but I understand there may better options and plus I DON"T KNOW how to use it!

---

### Post by tjr on 2006-12-05
Even worse, xmodmap didn't work for me (ubuntu 6.06.1LTS on ibook G4), so I manually exchanged Apple (aka win) and option (aka alt) keys to work as in OS X at the lowest level X supports:

exchanged in /etc/X11/xkb/keycodes/xfree86:
option       <LALT> = 115 <=> apple       <LWIN> = 64;
fn-option    <RALT> = 116 <=> fn-apple    <RWIN> = 113;
fn-control   <RCTL> = 109 <=>left_of_arrow<KPEN> = 108;

This solution automatically changes menu key bindings and control-alt-backspace/F1, even if you aren't logged in. 

Later it turned out I would have had to remove these keys from X modifiers, change their binding, and then re-add them with xmodmap to get it working. Not exactly clicking on a gnome assistant or reading the man pages.

Come on, Ubuntu policy makers, nobody is going to confuse keybindings with a windows-style alt key because - surprise, surprise - there isn't even a windows version for PowerPC! Please make it default to OS X behavior.

---

### Post by albesan on 2006-12-05
well I guess there is no easy way to go about it then...
Would your solution actually work if you went through with all that modifying? Would any wiser readers know how to automate the process and packing it into a script?... I guess that is a lot to ask...

a.

---

### Post by dbuzi123 on 2006-12-17
This worked for me using an edgy install on a powerbook g4:

Create a file in your home directory called .Xmodmap

In this file put these two lines:

keycode 115 = Control_L
add Control = Control_L

from a console type:

xmodmap ~/.Xmodmap

Restart your computer.  When you log in Ubuntu will prompt you to load your .Xmodmap file, select it and load it, I think you have to move it to the other side of the window.  You are set!  The left apple key is now a ctrl key.  I also went into keyboard shortcuts in gnome to change Alt-Tab app switching to Ctrl-Tab to make it a little more maclike

---

### Post by albesan on 2006-12-17
well, that was easy!!!
thanks a lot for that.

a.

---

### Post by dbuzi123 on 2006-12-17
you can use xev from the console to determine keycodes.  I also swapped out the small enter key by the arrows for delete.

---

### Post by albesan on 2006-12-21
dbuzi123,

Thanks for the tips, this kind of thing should be on a Sticky post on the ppc forum I can't believe ppc users don't miss this kind of functionality.

Anywa, I was wondering if the same can be done for the right cmd key.
Even though I'm on a laptop I use an external keyboard so, I do have a right cmd key.
Looking at how it was done I could try to guess the syntax of the code but if you could clarify this I might not mess up my keyboard.

thanks again.

a.

---

### Post by sciurus on 2006-12-21
Here's what I've been using. It's a little confusing because things you are used to doing with the control key (eg sending SIGINT) now have to be done with the apple key. Using xmodmap does not interfere with the keycodes for mouseemu, so you can still use control for right-click.
!
! This is an `xmodmap' input file for 
!   PC 105 key, wide Delete, tall Enter (XFree86; US) keyboards.
! Automatically generated on Thu Dec 21 17:14:01 2006 by brian with
! XKeyCaps 2.47; Copyright (c) 1991-1999 Jamie Zawinski; 2005-2006 Christoph Ber
g.
! [http://www.jwz.org/xkeycaps/](http://www.jwz.org/xkeycaps/)
!
! This file presupposes that the keyboard is in the default state, and
! may malfunction if it is not.
!
remove Control = Control_L
remove Mod4    = Meta_L

keycode 0x25 =  Meta_L
keycode 0x73 =  Control_L

add    Control = Control_L Control_L
add    Mod4    = Meta_L

---

### Post by merado on 2007-10-06
Thanks! Works really well.

When opening a link in a new tab in Firefox I still have to use ctrl. Command key + left click opens the link in the same window.

I'd appreciate any tip how to to fix that.

---

### Post by anabelle on 2008-06-15
I can't believe this is so hard to do in gnome, in KDE, you go:

System settings -> Mouse and keyboard -> Shortcuts -> Mac Theme

:D :lolflag:

---

