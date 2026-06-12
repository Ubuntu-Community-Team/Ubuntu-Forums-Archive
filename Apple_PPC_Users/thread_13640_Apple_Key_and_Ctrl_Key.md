---
title: "Apple Key and Ctrl Key"
date: 2005-02-02
forum: Apple PPC Users
---

### Post by ewaldgroup on 2005-02-02
Is there any way to turn the Apple Key into the ctrl key?

from my research:
[INDENT]Apple Key  -->  keycode 115[/INDENT] 
[INDENT]Ctrl Key  -->  keycode 37[/INDENT] 

you can find this by running "xev" in console.

Has anyone gotten this to work on a iBook, or anything else? How would I go about doing it?

My other post similar / same topic: [http://ubuntuforums.org/showthread.php?t=13373](http://ubuntuforums.org/showthread.php?t=13373)

I'm running an iBook '01 (Warty)

thanks,
ewaldgroup

---

### Post by t.rei on 2005-02-02
[QUOTE=ewaldgroup]Is there any way to turn the Apple Key into the ctrl key?

from my research:
[INDENT]Apple Key  -->  keycode 115[/INDENT] 
[INDENT]Ctrl Key  -->  keycode 37[/INDENT] 

you can find this by running "xev" in console.

Has anyone gotten this to work on a iBook, or anything else? How would I go about doing it?

My other post similar / same topic: [http://ubuntuforums.org/showthread.php?t=13373](http://ubuntuforums.org/showthread.php?t=13373)

I'm running an iBook '01 (Warty)

thanks,
ewaldgroup[/QUOTE]
 I am using xmodmap (gives a warning when starting gnome once) but it gives you full control  over your keaboard via a simple text-config-file :)

this is mine (powerbook g4 - german keyboard with some extras. Apple-Key== AltGR for me.
saved as .xmodmap in ~/ and executed by xmodmap .xmodmap
-------------------------------------------------------------------------------------------------
keycode   9 = Escape
keycode  10 = 1 exclam
keycode  11 = 2 quotedbl
keycode  12 = 3 section
keycode  13 = 4 dollar
keycode  14 = 5 percent
keycode  15 = 6 ampersand
keycode  16 = 7 slash braceleft
keycode  17 = 8 parenleft bracketleft
keycode  18 = 9 parenright bracketright
keycode  19 = 0 equal braceright
keycode  20 = ssharp question backslash
keycode  21 = dead_acute dead_grave
keycode  22 = BackSpace 
keycode  23 = Tab ISO_Left_Tab
keycode  24 = q Q at
keycode  25 = w W
keycode  26 = e E EuroSign
keycode  27 = r R
keycode  28 = t T
keycode  29 = z Z
keycode  30 = u U
keycode  31 = i I
keycode  32 = o O
keycode  33 = p P
keycode  34 = udiaeresis Udiaeresis
keycode  35 = plus asterisk asciitilde
keycode  36 = Return
keycode  37 = Control_L
keycode  38 = a A
keycode  39 = s S
keycode  40 = d D
keycode  41 = f F
keycode  42 = g G
keycode  43 = h H
keycode  44 = j J
keycode  45 = k K
keycode  46 = l L at
keycode  47 = odiaeresis Odiaeresis braceleft
keycode  48 = adiaeresis Adiaeresis braceright
keycode  49 = dead_circumflex degree
keycode  50 = Shift_L
keycode  51 = numbersign apostrophe
keycode  52 = y Y
keycode  53 = x X
keycode  54 = c C
keycode  55 = v V
keycode  56 = b B
keycode  57 = n N
keycode  58 = m M 
keycode  59 = comma semicolon bracketleft
keycode  60 = period colon bracketright
keycode  61 = minus underscore slash 
keycode  62 = Shift_R
keycode  63 = KP_Multiply XF86_ClearGrab
keycode  64 = Alt_L Meta_L
keycode  65 = space
keycode  66 = Caps_Lock
keycode  67 = F1 XF86_Switch_VT_1
keycode  68 = F2 XF86_Switch_VT_2
keycode  69 = F3 XF86_Switch_VT_3
keycode  70 = F4 XF86_Switch_VT_4
keycode  71 = F5 XF86_Switch_VT_5
keycode  72 = F6 XF86_Switch_VT_6
keycode  73 = F7 XF86_Switch_VT_7
keycode  74 = F8 XF86_Switch_VT_8
keycode  75 = F9 XF86_Switch_VT_9
keycode  76 = F10 XF86_Switch_VT_10
keycode  77 = Num_Lock Pointer_EnableKeys
keycode  78 = Scroll_Lock
keycode  79 = KP_Home KP_7
keycode  80 = KP_Up KP_8
keycode  81 = KP_Prior KP_9
keycode  82 = KP_Subtract XF86_Prev_VMode
keycode  83 = KP_Left KP_4
keycode  84 = KP_Begin KP_5
keycode  85 = KP_Right KP_6
keycode  86 = KP_Add XF86_Next_VMode
keycode  87 = KP_End KP_1
keycode  88 = KP_Down KP_2
keycode  89 = KP_Next KP_3
keycode  90 = KP_Insert KP_0
keycode  91 = KP_Delete KP_Separator
keycode  92 = Print Sys_Req
keycode  93 = Mode_switch
keycode  94 = less greater bar
keycode  95 = F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12
keycode  97 = Home
keycode  98 = Up
keycode  99 = Prior
keycode 100 = Left
keycode 102 = Right
keycode 103 = End
keycode 104 = Down
keycode 105 = Next
keycode 106 = Insert
keycode 107 = Delete
keycode 108 = Delete
keycode 109 = Control_R
keycode 110 = Pause Break
keycode 111 = Print Sys_Req
keycode 112 = KP_Divide XF86_Ungrab
keycode 113 = ISO_Level3_Shift Multi_key
keycode 114 = Pause Break
keycode 115 = Mode_switch
keycode 116 = Super_R
keycode 117 = Menu
keycode 124 = ISO_Level3_Shift
keycode 125 = NoSymbol Alt_L
keycode 126 = KP_Equal
keycode 127 = NoSymbol Super_L
keycode 128 = NoSymbol Hyper_L
keycode 156 = NoSymbol Meta_L

---

### Post by ewaldgroup on 2005-02-02
Ok. I made a new file .xmodmap and the only thing i put in was:```
keycode 115 = Control_L
``` 

That should do it right? But when i restarted, gnome said that there was a keyboard modifier file and it would be ignorred. when i tried it, it didnt work.

How can i get this to work. it has to be possible...

-ewaldgroup :confused:

---

### Post by t.rei on 2005-02-02
[QUOTE=ewaldgroup]Ok. I made a new file .xmodmap and the only thing i put in was:```
keycode 115 = Control_L
``` 

That should do it right? But when i restarted, gnome said that there was a keyboard modifier file and it would be ignorred. when i tried it, it didnt work.

How can i get this to work. it has to be possible...

-ewaldgroup :confused:[/QUOTE]
 thats right - gnome complains....

forgot about mentioning u need to add 
xmodmap .xmodmap 
as a command to your gnome-session.
(hoary: desktop->preferrences->Session->startup...)

or you run it manually from either Applications->run Application or from Terminal.

---

### Post by ewaldgroup on 2005-02-02
[QUOTE=t.rei]thats right - gnome complains....

forgot about mentioning u need to add 
xmodmap .xmodmap 
as a command to your gnome-session.
(hoary: desktop->preferrences->Session->startup...)

or you run it manually from either Applications->run Application or from Terminal.[/QUOTE]

It didnt work. Ctrl still works, apple key still doesnt function as the ctrl key. Any ideas?

this is my entire .xmodmap file. it is saved in ~/.xmodmap
```
keycode 115 = Control_L
``` 

 
-ewaldgroup

---

### Post by t.rei on 2005-02-02
shouldnt matter if thats all... it doesnt have to remap all the keys.

as long as thats definately 115 = apple-key it should work. running xmodmap .xmodmap in console give any errors?

I set up my powerbook like this: 105key generic, de_DE (nodeadkeys).
then I just execute the file as seen above. running xmodmap ~/.xmodmap

everything works like a charm

---

### Post by ewaldgroup on 2005-02-02
Ok. i did what you said and checked xev. I dont know where the logs are for xmodmap.

both the ctrl key and apple key say this in the output:

```
(keysym 0xffe3, Control_L)
``` 

The problem is that only the Ctrl key works like it should. The apple key doesnt do that same thing as the output should imply. 

What am i doing wrong?

-ewaldgroup

---

### Post by t.rei on 2005-02-03
[QUOTE=ewaldgroup]Ok. i did what you said and checked xev. I dont know where the logs are for xmodmap.

both the ctrl key and apple key say this in the output:

```
(keysym 0xffe3, Control_L)
``` 

The problem is that only the Ctrl key works like it should. The apple key doesnt do that same thing as the output should imply. 

What am i doing wrong?

-ewaldgroup[/QUOTE]
 how about trying the program "xkeycaps" - you can pick a keyboard layout and see if the keys are reponding and what function they have. :)

I use pc105 - German and saved my basic .xmodmap this way. hope that helps you get closer

---

### Post by ewaldgroup on 2005-02-03
I tried xkeycaps but i cant find a keyboard thats close to the apple ibook 2001 keyboard. pc105, is it close?

i cant believe that no one has tried mapping the Ctrl key to the Apple Key.

Thanks,
ewaldgroup

---

### Post by t.rei on 2005-02-03
[QUOTE=ewaldgroup]I tried xkeycaps but i cant find a keyboard thats close to the apple ibook 2001 keyboard. pc105, is it close?

i cant believe that no one has tried mapping the Ctrl key to the Apple Key.

Thanks,
ewaldgroup[/QUOTE]
 the layout doesnt match my keyboard either. But all important keys react on input - so I just use it as a base. *g*

---

### Post by adamw on 2005-02-03
[I] am using xmodmap (gives a warning when starting gnome once) but it gives you full control over your keaboard via a simple text-config-file 

this is mine (powerbook g4 - german keyboard with some extras. Apple-Key== AltGR for me.
saved as .xmodmap in ~/ and executed by xmodmap .xmodmap
[/I] 

I just tried your mappings.  On an English keyboard you need to switch the y and z keys, in addition to the semicolon, minus key, etc. etc. etc.

---

### Post by ewaldgroup on 2005-02-03
[QUOTE=adamw][I] am using xmodmap (gives a warning when starting gnome once) but it gives you full control over your keaboard via a simple text-config-file 

this is mine (powerbook g4 - german keyboard with some extras. Apple-Key== AltGR for me.
saved as .xmodmap in ~/ and executed by xmodmap .xmodmap
[/I] 

I just tried your mappings.  On an English keyboard you need to switch the y and z keys, in addition to the semicolon, minus key, etc. etc. etc.[/QUOTE]

So this says that you succesfully mapped the ctrl key to the apple key. If this is true can you please include your entire .xmodmap file in your next post.

thanks,
ewaldgroup

---

### Post by adamw on 2005-02-04
[I]So this says that you succesfully mapped the ctrl key to the apple key. If this is true can you please include your entire .xmodmap file in your next post.

thanks,
ewaldgroup[/I] 

I tried his mappings but I didn't try switching the command and control keys, no.  I was trying to switch the F12 and F3 keys but that didn't work.  What xmodmap DID do with his configuration was map my keyboard to a german keyboard, which was not useful to me.  The reason I was experimenting with xmodmap was to emulate the two button mouse better, but the solution I came to was to modify the /etc/sysctl.conf file as such:
dev.mac_hid.mouse_button3_keycode=126
dev.mac_hid.mouse_button2_keycode=100

which allows me to press fn-Command and fn-Option to emulate the middle and right mouse buttons.  So problem solved for me.  From what I can tell, xmodmap is not very good at switching key modifiers, but good at switching the internationalization of your keyboard (like the Y and Z key, for instance).  During this experiment, I also discovered that powerprefs is REALLY good at destroying my entire keymapping, all the way down to the lowest level of the firmware, to which I had to zap the PMU by holding down the shift-control-command-power button on my powerbook (yikes).

---

### Post by ewaldgroup on 2005-02-05
scary. Anyone else have any ideas? any other tools?

ewaldgroup

---

### Post by incandenza on 2005-02-05
[QUOTE=ewaldgroup]scary. Anyone else have any ideas? any other tools?

ewaldgroup[/QUOTE]

I believe you have to remove Control_L from the modifier keys, remap it, and then add it back.  e.g. your .xmodmap file would be

remove control = Control_L
keycode 115 = Control_L
add control = Control_L

If you don't do that, it still has the old keycode for Control_L in the modifier table.

You can do 'xmodmap -pm' to see what the modifier keys are set to.

---

### Post by ewaldgroup on 2005-02-05
[QUOTE=incandenza]I believe you have to remove Control_L from the modifier keys, remap it, and then add it back.  e.g. your .xmodmap file would be

remove control = Control_L
keycode 115 = Control_L
add control = Control_L

If you don't do that, it still has the old keycode for Control_L in the modifier table.

You can do 'xmodmap -pm' to see what the modifier keys are set to.[/QUOTE]


Thank you so much.... It worked perfectly...  :grin: 

-ewaldgroup

---

### Post by sourcedriver on 2006-08-31
> **ewaldgroup said:**
> Thank you so much.... It worked perfectly...  :grin: 

-ewaldgroup

yes thank you this worked for me also! :D 

However.. I have noticed that the apple key does not emulate the control key when I am trying to access the menus of Firefox. :( It works to access the menus of other gui based apps that came with Ubuntu.

How is Firefox different? :?:

---

### Post by Gen2ly on 2008-02-08
thanks alot :) :) :)

---

