---
title: "xmodmap not working correctly"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Venerence on 2008-02-05
So what I'm trying to do is make qweras, when modified by alt, to use KP_7,8,4,5,1, and 2. I use a laptop, and one of my apps use these keypad hotkeys, so I'm trying to reassign them to <alt>qweras.

So anyway, no matter how often I try it, I can't get the xmodmap to work as planned. if I do ```
xmodmap -e "keycode 24 = q Q NoSymbol KP_7"
``` <alt>q doesn't change at all, let alone printing numpad 7.

I know it's not an issue with my config, because ```
xmodmap -e "keycode 24 = q KP_7"
``` will print out numpad 7 correctly when modified with shift. It's not an issue with the mod assignment because ```
xmodmap
``` prints out ```
shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x6d)
mod1        Alt_L (0x40),  Alt_L (0x7d),  Meta_L (0x9c)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x7f),  Hyper_L (0x80)
mod5        M2 (0x5d),  ISO_Level3_Shift (0x7c)

```, and I can't figure out what else it could be. Below is my xmodmap -pke output, and if anybody could help me figure out why it won't work (or an alternative way to do it), that would be really helpful.


```
keycode   8 =
keycode   9 = Escape
keycode  10 = 1 exclam
keycode  11 = 2 at
keycode  12 = 3 numbersign
keycode  13 = 4 dollar
keycode  14 = 5 percent
keycode  15 = 6 asciicircum
keycode  16 = 7 ampersand
keycode  17 = 8 asterisk
keycode  18 = 9 parenleft
keycode  19 = 0 parenright
keycode  20 = minus underscore
keycode  21 = equal plus
keycode  22 = BackSpace Terminate_Server
keycode  23 = Tab ISO_Left_Tab
keycode  24 = q Q NoSymbol PK_7
keycode  25 = w W
keycode  26 = e E
keycode  27 = r R
keycode  28 = t T
keycode  29 = y Y
keycode  30 = u U
keycode  31 = i I
keycode  32 = o O
keycode  33 = p P
keycode  34 = bracketleft braceleft
keycode  35 = bracketright braceright
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
keycode  46 = l L
keycode  47 = semicolon colon
keycode  48 = apostrophe quotedbl
keycode  49 = grave asciitilde
keycode  50 = Shift_L
keycode  51 = backslash bar
keycode  52 = z Z
keycode  53 = x X
keycode  54 = c C
keycode  55 = v V
keycode  56 = b B
keycode  57 = n N
keycode  58 = m M
keycode  59 = comma less
keycode  60 = period greater
keycode  61 = slash question
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
keycode  91 = KP_Delete KP_Decimal
keycode  92 =
keycode  93 = M2
keycode  94 = less greater bar brokenbar bar brokenbar
keycode  95 = F11 XF86_Switch_VT_11
keycode  96 = F12 XF86_Switch_VT_12
keycode  97 = Home
keycode  98 = Up
keycode  99 = Prior
keycode 100 = Left
keycode 101 =
keycode 102 = Right
keycode 103 = End
keycode 104 = Down
keycode 105 = Next
keycode 106 = Insert
keycode 107 = Delete
keycode 108 = KP_Enter
keycode 109 = Control_R
keycode 110 = Pause Break
keycode 111 = Print Sys_Req
keycode 112 = KP_Divide XF86_Ungrab
keycode 113 = Alt_R Meta_R
keycode 114 =
keycode 115 = Super_L
keycode 116 = Super_R
keycode 117 = Menu
keycode 118 =
keycode 119 =
keycode 120 =
keycode 121 =
keycode 122 =
keycode 123 =
keycode 124 = ISO_Level3_Shift
keycode 125 = NoSymbol Alt_L
keycode 126 = KP_Equal
keycode 127 = NoSymbol Super_L
keycode 128 = NoSymbol Hyper_L

```

---

