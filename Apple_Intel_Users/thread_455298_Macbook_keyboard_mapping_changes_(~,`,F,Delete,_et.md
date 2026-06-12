---
title: "Macbook keyboard mapping changes (~,`,F*,Delete, etc)"
date: 2007-05-26
forum: Apple Intel Users
---

### Post by DucentiVigintiDuo on 2007-05-26
Hi, I've recently installed Feisty Fawn as my only OS on my Macbook and I'm really glad I did so. :)
It takes a bit of research, a lot of commands and some patience to get things working but I think it's worth it because it's an excellent solution to both Windows and Mac OS X, which I'd rather not use ever again if possible. 

I'd like to take yet another chance to thank anyone and everyone that has helped me or will help me with any of my problems, because I'd like everyone to know I'm not an ungrateful noob :P
I'm just starting from the bottom like everyone else, and I'm willing to learn :)
Hopefully I'll be able to help people with problems myself soon enough!

Now, the Macbook keyboard layout seemed to work fine (I've got a UK version because I study in England but I'm using a US layout because I need # more for programming than I do the pound sign) except for a few details.



1) The ~ and ` button is mapped to the button that normally types the plusminus sign and the paragraph sign (left top under esc button).

2) The ~ and ` button just produces > and <, which are useless since they already exist on the keyboard.

3) No delete button! Anyone know how I can substitute that? Maybe map delete to the secondary enter button? But how? :confused:

4) The super keys (Apple keys) tend to work whenever they feel like it. Some programs see them, some don't. Any info on that?

5) I want to use the F# keys without having to go through the fn key first. Is it possible to reverse its role, and only access the special functions when pressing fn?



That's all for now, if anyone knows more info on the Macbook keyboard and what I can/should do about it, I'd love to hear it!

Thanks again :)

---

### Post by ivesjd on 2007-05-27
xev will give you the key code and its function. then you can use xmodmap to remap them. There are other threads on how to do this

[http://ubuntuforums.org/showthread.php?t=448812]("http://ubuntuforums.org/showthread.php?t=448812")

hope that helps!

---

### Post by DucentiVigintiDuo on 2007-05-27
Thank you for replying!
It helps quite a bit actually, at least now I know where I'm going.

Only problem is xev doesn't even recognize the press of the "fn" key so it seems like I'm doomed as far as the F* key issue is concerned.

If/when I come to a solution I'll post it here so that maybe other people that are having similar problems can benefit from it.

---

### Post by siepo on 2007-05-27
On my macbook, the fn key by itself does nothing, but it does change the meaning of some keys. So try F1 and F1+fn separately with xev.

The behavior of the fn key can be controlled by a line

options hid pb_fnmode=n

in a file in /etc/modprobe.d, eg. etc/modprobe.d/options. IIRC n=0 means ignore fn, 1 means function keys with fn and 2 means function keys without fn. It may be necessary to run update-initramfs (update-initramfs -c -k `uname -r`) and to reboot before this takes effect.

You can assign values F21 to fn+F1 etc. in .Xmodmap if you want. With a proper name, you can assign actions to these key combinations.

---

### Post by DucentiVigintiDuo on 2007-05-27
> **siepo said:**
> On my macbook, the fn key by itself does nothing, but it does change the meaning of some keys. So try F1 and F1+fn separately with xev.

Thanks for replying, **siepo**. I tried F* and F*+fn separately with xev, and it gave different codes. When I tried to map the F1, F2 functions to the non-fn pressed buttons with their codes, it didn't work. On top of that, keys F3 to F5 gave me no code whatsoever when not combined with fn.

> **siepo said:**
> The behavior of the fn key can be controlled by a line

options hid pb_fnmode=n

in a file in /etc/modprobe.d, eg. etc/modprobe.d/options. IIRC n=0 means ignore fn, 1 means function keys with fn and 2 means function keys without fn. It may be necessary to run update-initramfs (update-initramfs -c -k `uname -r`) and to reboot before this takes effect.

Does that mean that 

0 = you can't have normal F1 functions even if you press it

1 = always pressed

2 = not pressed?


> **siepo said:**
> You can assign values F21 to fn+F1 etc. in .Xmodmap if you want. With a proper name, you can assign actions to these key combinations.

I'm confused by your statement here. What do you mean by F21? And if I assign actions to those combinations, does that mean I have to change the "fn" button behavior first?

Anyway, I managed to remap ~ ` to its place, make the secondary enter button act as Delete,
and make the Right Super button (apple key) act as Insert.

The way I did it was I used

```
xev
```

in the command line, and I started pressing the keys and taking notes of the "keycode = #".

Then I saw the manual for xmodmap and I saw that this is the most useful command to list all the mappings with strings ready to be fed back to xmodmap (through the script)

```

xmodmap -pke
```

However, **benanzo**'s technique selecting it to run in the session at startup doesn't seem to work. I've got it saved as a plain script file. Do I need a special command or file extension?

Here's the script for the things I just described:
(go to the link on the second post for instructions for this script)

```
#!/bin/bash#
#set ~ key to its right place
xmodmap -e 'keycode 94 = grave asciitilde'

#make secondary enter button act as delete
xmodmap -e 'keycode 108 = Delete'

#make right super key act as insert
xmodmap -e 'keycode 116 = Insert'

xkbset m
```

[COLOR="Red"]**NOTICE:** *This setup works for me because I tested it, so test out your keys before you do any mapping or you might get **REALLY** confused. Also remember to make this file executable as a program by right clicking and going to properties.*[/COLOR]

---

### Post by siepo on 2007-05-28
Well, I ran xev again for the first time after several months, and in some cases it didn't produce the codes that I expected. It doesn't match what you describe either. Still, my keyboard does what I want.

As to the options hid stuff: value 0 means that fn makes no difference. I think in this case you get F1 etc, and the hardware control meaning is unavailable. Value 1 means that you must press fn for F1 etc, and fn+F1 etc. for hardware control. Value 2 the other way around. I hope this is clearer.

As to F21 etc: forget about it. With my windowmanager, fvwm, I needed something like this to program these key combinations, but for Gnome and KDE it may be completely useless for all I know.

---

### Post by DucentiVigintiDuo on 2007-05-28
Ok, thanks for the clarification.

Also, do you have a Macbook or a Pro? Mine is a first gen Macbook.

Could you tell me what language and keyboard layout/options you're using from 
System -> Preferences -> Keyboard? It might be this that's screwing up my buttons.

I've chosen:

Keyboard model: Apple Laptop
Layout: U.S English Macintosh

---

### Post by siepo on 2007-05-28
I also have a 1rst gen macbook.

I don't have gnome or a gnome menu. All I can tell you is some settings in my /etc/X11/xorg.conf:

  Option    "XkbModel"  "macbook79"
  Option    "XkbLayout"  "latin"

The "latin" was originally "us", but I changed this setting to enable accented letters. But that is another story.

Frankly, I stopped long ago trying to understand keyboard configuration; there are too many pieces involved. As long as I can fix any weirdess with xmodmap I leave well enough alone.

By the way: I ran xev again with any xmodmap mappings deactivated, and then I got the results that I expected. I don't understand why xmodmap mappings should make a difference to the keycodes reported by xev.

---

### Post by buschi on 2007-05-29
Just a comment to the "delete"-key: Did you ever try Fn + Backspace? This works as "delete" here...

---

### Post by Gen2ly on 2007-05-30
Function doesn't work at all for me even with F1, :(.

In System > Preferences > Keyboard > Layout, I have tried the MacBook keyboard layout which does the odd < instead of ` or ~.  The Macintosh layout works nice though.  I've don't use pommed because I hate the overhead of programs like that.  I remember using OS 9 and having half a dozen apps like that running in the background just to provide needed functionality, only to have OS 9 crash on me occasionally.

I'm positing that the driver is responsible for it:

```
     Driver          "kbd"
```

So I probably won't be able to do much about it until functionality is added.

---

