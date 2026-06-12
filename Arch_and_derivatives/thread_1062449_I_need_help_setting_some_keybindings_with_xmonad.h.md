---
title: "I need help setting some keybindings with xmonad.hs"
date: 2009-02-06
forum: Arch and derivatives
---

### Post by Redrazor39 on 2009-02-06
I would like to set Fn + F2 to mute, Fn + F3 to volume down, Fn + F4 to volume up, Fn + F5 for Brightness down, Fn + F6 for Brightness up, Fn +F12 to run sudo pm-suspend, in xmonad (preferably with xmonad.hs).

I do have sound working, but no way to adjust it via keyboard (which I would like to do).

After some googling and scouring through xmonad documentation, I found something that looks like it would work, but I don't completely understand it and don't know where else to look for help. Here is what someone added to their xmonad.hs file after the keybindings part:

```
   -- multimedia keys
   --
   -- XF86AudioLowerVolume
   , ((0            , 0x1008ff11), spawn "aumix -v -2")
   -- XF86AudioRaiseVolume
   , ((0            , 0x1008ff13), spawn "aumix -v +2")
   -- XF86AudioMute
   , ((0            , 0x1008ff12), spawn "amixer -q set PCM toggle")
```
The confusing part for me is the stuff like "((0            , 0x1008ff12)", which I don't understand in the slightest. Could someone please explain this to me or adjust it to mean the keybindings in the beginning of this post I want? If there is a way to just tell which keycodes should perform which functions, that would work best for me as I have my keycodes at the bottom of this post.

Also, the last part (muting) says "amixer -q set PCM toggle", when my volume is set by the Master one. Would I just have to change "PCM" to "Master" to fix that?

Btw, here's my current xmonad.hs:

```
import XMonad
import XMonad.Hooks.DynamicLog
import XMonad.Hooks.ManageDocks
import XMonad.Util.Run(spawnPipe)
import XMonad.Util.EZConfig(additionalKeys)
import System.IO

myManageHook = composeAll
    [ className =? "Gimp"      --> doFloat
    ]

main = do
    xmproc <- spawnPipe "xmobar"
    -- make sure to edit paths to xmobar and .xmobarrc to match your system.
    -- If xmobar is in your $PATH, with config ~/.xmobarrc you don't need the
    -- xmobar path or config file, use: xmproc <- spawnPipe "xmobar"  
    xmonad $ defaultConfig
        { manageHook = manageDocks <+> manageHook defaultConfig
        , layoutHook = avoidStruts  $  layoutHook defaultConfig
        , logHook = dynamicLogWithPP $ xmobarPP
                        { ppOutput = hPutStrLn xmproc
                        , ppTitle = xmobarColor "green" "" . shorten 50
                        }
        , modMask = mod1Mask     
    , terminal = "Terminal"
        } `additionalKeys`
        [ ((mod1Mask .|. controlMask, xK_End), spawn "sudo shutdown -h now")
        , ((controlMask, xK_Print), spawn "scrot -s")
        , ((0, xK_Print), spawn "scrot")
        ]
```

If it helps, here are some of my keycodes I got from xev (s1 and s2 are special buttons on my laptop, Mouse Search button is just a button on my mouse originally intended to bring up Windows search, although I don't mind using it for something else):

```
s1 = keycode 159
s2 = keycode 151
XF86AudioMute = keycode 160
XF86AudioLowerVolume = keycode 174
XF86AudioRaiseVolume = keycode 176
Brightness Down = keycode 101
Brightness Up = keycode 212
Mouse Search Button = keycode 229
Sleep (Fn + F12) = keycode 165
```

---

### Post by crimesaucer on 2009-02-06
Keytouch is a good program for setting key bindings: [http://wiki.archlinux.org/index.php/Keytouch](http://wiki.archlinux.org/index.php/Keytouch)


I use it for my HP dv9920us and xfce4.

---

### Post by Redrazor39 on 2009-02-06
I would use keytouch, but it doesn't recognize all of my keys (brightness key combos, S1 and S2, Mouse button, etc.), at least last time I checked. Is there another reason nothing would happen in keytouch-editor when I press the keys but I can still get a keycode from xev?

---

### Post by crimesaucer on 2009-02-06
> **Redrazor39 said:**
> I would use keytouch, but it doesn't recognize all of my keys (brightness key combos, S1 and S2, Mouse button, etc.), at least last time I checked. Is there another reason nothing would happen in keytouch-editor when I press the keys but I can still get a keycode from xev?

It's been a while since I had to make my own keytouch config..... make sure you follow this part correctly: [http://wiki.archlinux.org/index.php/Keytouch#Creating_a_Keyboard_File](http://wiki.archlinux.org/index.php/Keytouch#Creating_a_Keyboard_File)

The part about: 

```
ls /dev/input/
```

then:

```
keytouch-editor /dev/input/eventX mykeyboardconfig
```


and this part for the command above:

> Replace the X by a number. KeyTouch editor will &#64257;rst show some information about the device, including its name (&#8221;Input device name&#8221;) that can tell you if you have chosen the correct event device. KeyTouch editor asks you to press one of the extra function keys. If the program continues after pressing the extra function key, you have chosen the right event device. If not terminate the program by pressing Ctrl+C and try another event device. Note that when your keyboard is connected via USB there are two event devices: /dev/input/eventA (where A is replaced by a number) for all &#8221;normal&#8221; keys and /dev/input/eventB (where B = A+1) for the extra function keys. 



..... my  "ls /dev/input/" is:

```

$ ls /dev/input/
by-path  event1   event2  event4  event6  event8  mice    mouse1
event0   event10  event3  event5  event7  event9  mouse0

```


so check out the "keytouch-editor /dev/input/eventX mykeyboardconfig" command with the different outputs from the "ls /dev/input/" command in place of "eventX".


..... I also had to disable my laptop's hotplugging in xorg.conf to allow "mykeyboardconfig" to work. (it broke when the added hotplugging to xorg so I just added the disable hotplugging line in my xorg.conf)

---

### Post by Redrazor39 on 2009-02-07
Thanks! I'm not on my Linux box right now but I'll try that as soon as I can. I'll post if I have any more problems

---

