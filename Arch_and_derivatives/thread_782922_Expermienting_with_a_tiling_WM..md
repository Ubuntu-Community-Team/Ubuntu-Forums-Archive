---
title: "Expermienting with a tiling WM."
date: 2008-05-05
forum: Arch and derivatives
---

### Post by Barrucadu on 2008-05-05
I've decided to experiment with xmonad. I'll be keeping Openbox around as I need to use The GIMP occasionally, which I imagine would be a bugger to use in a tiling WM. Anyway, anything I should know, other than to expect that nothing I know currently about window management will help me at all?

---

### Post by finferflu on 2008-05-05
From my experience, I think wmii is the better middle ground in between. It has auto-tiling, but it's not as "aggressive" as the dwm family. After you get the grip of how auto-tiling works, you will much more happily appreciate how more complex WMs work. 

Of course, this is only what I have gathered from my experience.

---

### Post by chucky chuckaluck on 2008-05-05
both gimp and mplayer are set to float in xmonad's default settings, no matter what mode you're in. if you want to change any of the setting, you can first make a .xmonad/xmonad.hs file and then change the settings to whatever you like (the haskell settings are odd, but easily figured out/faked). just put the following into a file *.xmonad/xmonad.hs*...

```

import XMonad
import System.Exit
 
import qualified XMonad.StackSet as W
import qualified Data.Map        as M
 
-- The preferred terminal program, which is used in a binding below and by
-- certain contrib modules.
--
myTerminal      = "xterm"
 
-- Width of the window border in pixels.
--
myBorderWidth   = 1
 
-- modMask lets you specify which modkey you want to use. The default
-- is mod1Mask ("left alt").  You may also consider using mod3Mask
-- ("right alt"), which does not conflict with emacs keybindings. The
-- "windows key" is usually mod4Mask.
--
myModMask       = mod1Mask
 
-- The mask for the numlock key. Numlock status is "masked" from the
-- current modifier status, so the keybindings will work with numlock on or
-- off. You may need to change this on some systems.
--
-- You can find the numlock modifier by running "xmodmap" and looking for a
-- modifier with Num_Lock bound to it:
--
-- > $ xmodmap | grep Num
-- > mod2        Num_Lock (0x4d)
--
-- Set numlockMask = 0 if you don't have a numlock key, or want to treat
-- numlock status separately.
--
myNumlockMask   = mod2Mask
 
-- The default number of workspaces (virtual screens) and their names.
-- By default we use numeric strings, but any string may be used as a
-- workspace name. The number of workspaces is determined by the length
-- of this list.
--
-- A tagging example:
--
-- > workspaces = ["web", "irc", "code" ] ++ map show [4..9]
--
myWorkspaces    = ["1","2","3","4","5","6","7","8","9"]
 
-- Border colors for unfocused and focused windows, respectively.
--
myNormalBorderColor  = "#dddddd"
myFocusedBorderColor = "#ff0000"
 
-- Default offset of drawable screen boundaries from each physical
-- screen. Anything non-zero here will leave a gap of that many pixels
-- on the given edge, on the that screen. A useful gap at top of screen
-- for a menu bar (e.g. 15)
--
-- An example, to set a top gap on monitor 1, and a gap on the bottom of
-- monitor 2, you'd use a list of geometries like so:
--
-- > defaultGaps = [(18,0,0,0),(0,18,0,0)] -- 2 gaps on 2 monitors
--
-- Fields are: top, bottom, left, right.
--
myDefaultGaps   = [(0,0,0,0)]
 
------------------------------------------------------------------------
-- Key bindings. Add, modify or remove key bindings here.
--
myKeys conf@(XConfig {XMonad.modMask = modMask}) = M.fromList $
 
    -- launch a terminal
    [ ((modMask .|. shiftMask, xK_Return), spawn $ XMonad.terminal conf)
 
    -- launch dmenu
    , ((modMask,               xK_p     ), spawn "exe=`dmenu_path | dmenu` && eval \"exec $exe\"")
 
    -- launch gmrun
    , ((modMask .|. shiftMask, xK_p     ), spawn "gmrun")
 
    -- close focused window 
    , ((modMask .|. shiftMask, xK_c     ), kill)
 
     -- Rotate through the available layout algorithms
    , ((modMask,               xK_space ), sendMessage NextLayout)
 
    --  Reset the layouts on the current workspace to default
    , ((modMask .|. shiftMask, xK_space ), setLayout $ XMonad.layoutHook conf)
 
    -- Resize viewed windows to the correct size
    , ((modMask,               xK_n     ), refresh)
 
    -- Move focus to the next window
    , ((modMask,               xK_Tab   ), windows W.focusDown)
 
    -- Move focus to the next window
    , ((modMask,               xK_j     ), windows W.focusDown)
 
    -- Move focus to the previous window
    , ((modMask,               xK_k     ), windows W.focusUp  )
 
    -- Move focus to the master window
    , ((modMask,               xK_m     ), windows W.focusMaster  )
 
    -- Swap the focused window and the master window
    , ((modMask,               xK_Return), windows W.swapMaster)
 
    -- Swap the focused window with the next window
    , ((modMask .|. shiftMask, xK_j     ), windows W.swapDown  )
 
    -- Swap the focused window with the previous window
    , ((modMask .|. shiftMask, xK_k     ), windows W.swapUp    )
 
    -- Shrink the master area
    , ((modMask,               xK_h     ), sendMessage Shrink)
 
    -- Expand the master area
    , ((modMask,               xK_l     ), sendMessage Expand)
 
    -- Push window back into tiling
    , ((modMask,               xK_t     ), withFocused $ windows . W.sink)
 
    -- Increment the number of windows in the master area
    , ((modMask              , xK_comma ), sendMessage (IncMasterN 1))
 
    -- Deincrement the number of windows in the master area
    , ((modMask              , xK_period), sendMessage (IncMasterN (-1)))
 
    -- toggle the status bar gap
    , ((modMask              , xK_b     ),
          modifyGap (\i n -> let x = (XMonad.defaultGaps conf ++ repeat (0,0,0,0)) !! i
                             in if n == x then (0,0,0,0) else x))
 
    -- Quit xmonad
    , ((modMask .|. shiftMask, xK_q     ), io (exitWith ExitSuccess))
 
    -- Restart xmonad
    , ((modMask              , xK_q     ),
          broadcastMessage ReleaseResources >> restart "xmonad" True)
    ]
    ++
 
    --
    -- mod-[1..9], Switch to workspace N
    -- mod-shift-[1..9], Move client to workspace N
    --
    [((m .|. modMask, k), windows $ f i)
        | (i, k) <- zip (XMonad.workspaces conf) [xK_1 .. xK_9]
        , (f, m) <- [(W.greedyView, 0), (W.shift, shiftMask)]]
    ++
 
    --
    -- mod-{w,e,r}, Switch to physical/Xinerama screens 1, 2, or 3
    -- mod-shift-{w,e,r}, Move client to screen 1, 2, or 3
    --
    [((m .|. modMask, key), screenWorkspace sc >>= flip whenJust (windows . f))
        | (key, sc) <- zip [xK_w, xK_e, xK_r] [0..]
        , (f, m) <- [(W.view, 0), (W.shift, shiftMask)]]
 
 
------------------------------------------------------------------------
-- Mouse bindings: default actions bound to mouse events
--
myMouseBindings (XConfig {XMonad.modMask = modMask}) = M.fromList $
 
    -- mod-button1, Set the window to floating mode and move by dragging
    [ ((modMask, button1), (\w -> focus w >> mouseMoveWindow w))
 
    -- mod-button2, Raise the window to the top of the stack
    , ((modMask, button2), (\w -> focus w >> windows W.swapMaster))
 
    -- mod-button3, Set the window to floating mode and resize by dragging
    , ((modMask, button3), (\w -> focus w >> mouseResizeWindow w))
 
    -- you may also bind events to the mouse scroll wheel (button4 and button5)
    ]
 
------------------------------------------------------------------------
-- Layouts:
 
-- You can specify and transform your layouts by modifying these values.
-- If you change layout bindings be sure to use 'mod-shift-space' after
-- restarting (with 'mod-q') to reset your layout state to the new
-- defaults, as xmonad preserves your old layout settings by default.
--
-- The available layouts.  Note that each layout is separated by |||,
-- which denotes layout choice.
--
myLayout = tiled ||| Mirror tiled ||| Full
  where
     -- default tiling algorithm partitions the screen into two panes
     tiled   = Tall nmaster delta ratio
 
     -- The default number of windows in the master pane
     nmaster = 1
 
     -- Default proportion of screen occupied by master pane
     ratio   = 1/2
 
     -- Percent of screen to increment by when resizing panes
     delta   = 3/100
 
------------------------------------------------------------------------
-- Window rules:
 
-- Execute arbitrary actions and WindowSet manipulations when managing
-- a new window. You can use this to, for example, always float a
-- particular program, or have a client always appear on a particular
-- workspace.
--
-- To find the property name associated with a program, use
-- > xprop | grep WM_CLASS
-- and click on the client you're interested in.
--
-- To match on the WM_NAME, you can use 'title' in the same way that
-- 'className' and 'resource' are used below.
--
myManageHook = composeAll
    [ className =? "MPlayer"        --> doFloat
    , className =? "Gimp"           --> doFloat
    , resource  =? "desktop_window" --> doIgnore
    , resource  =? "kdesktop"       --> doIgnore ]
 
-- Whether focus follows the mouse pointer.
myFocusFollowsMouse :: Bool
myFocusFollowsMouse = True
 
------------------------------------------------------------------------
-- Status bars and logging
 
-- Perform an arbitrary action on each internal state change or X event.
-- See the 'DynamicLog' extension for examples.
--
-- To emulate dwm's status bar
--
-- > logHook = dynamicLogDzen
--
myLogHook = return ()
 
------------------------------------------------------------------------
-- Now run xmonad with all the defaults we set up.
 
-- Run xmonad with the settings you specify. No need to modify this.
--
main = xmonad defaults
 
-- A structure containing your configuration settings, overriding
-- fields in the default config. Any you don't override, will 
-- use the defaults defined in xmonad/XMonad/Config.hs
-- 
-- No need to modify this.
--
defaults = defaultConfig {
      -- simple stuff
        terminal           = myTerminal,
        focusFollowsMouse  = myFocusFollowsMouse,
        borderWidth        = myBorderWidth,
        modMask            = myModMask,
        numlockMask        = myNumlockMask,
        workspaces         = myWorkspaces,
        normalBorderColor  = myNormalBorderColor,
        focusedBorderColor = myFocusedBorderColor,
        defaultGaps        = myDefaultGaps,
 
      -- key bindings
        keys               = myKeys,
        mouseBindings      = myMouseBindings,
 
      -- hooks, layouts
        layoutHook         = myLayout,
        manageHook         = myManageHook,
        logHook            = myLogHook
    }

```

after you make changes, do modkey+q and they'll take effect.

---

### Post by Barrucadu on 2008-05-05
I'm finding it an interesting experience. I copied the sample xmonad.hs file from the xmonad website, and edited it a little. My mod key is now the Windows key, which is what I tend to include in all of my keyboard shortcuts, in any WM/DE. I actually have my xmonad.hs file open in nano on tty2, as I keep forgetting the keyboard shotcuts. I'm enjoying it so far though.

---

### Post by chucky chuckaluck on 2008-05-05
> **Barrucadu said:**
> I actually have my xmonad.hs file open in nano on tty2, as I keep forgetting the keyboard shotcuts.

at one point, i had xmonad, awesome, wmii, dwm and ratpoison all installed, all with different shortcuts. that was a little confusing.

---

### Post by Barrucadu on 2008-05-05
Now, I seem pretty good at adapting to new software, but that would just confuse the hell out of me :lolflag:
Why did you try to learn so many WM's at once?

---

### Post by chucky chuckaluck on 2008-05-05
> **Barrucadu said:**
> Now, I seem pretty good at adapting to new software, but that would just confuse the hell out of me :lolflag:
Why did you try to learn so many WM's at once?

it's the 'buffet' approach.

---

### Post by Barrucadu on 2008-05-05
Wow, I've just found that it is using less RAM than Openbox, and as my laptop does not have much RAM, using as little as possible is a priority.

---

### Post by finferflu on 2008-05-05
Hence the question again: why doesn't everyone use a tiling window manager?

---

### Post by Barrucadu on 2008-05-05
Because they are completely weird to someone who has never used one before, and take dteermination to get used to. Can you imagine if all distros used a tiling wm? Half of us would never have switched from Windows, I know I wouldn't.

---

### Post by chucky chuckaluck on 2008-05-05
> **finferflu said:**
> Hence the question again: why doesn't everyone use a tiling window manager?

you know, that's a very good question. we should start a thread about it. i'm sure we'll convert 99% of the folk who read it.

---

### Post by Barrucadu on 2008-05-05
I'm not so sure about 99%... Quite a lot of people care about aesthetics, and lets face it, a floating WM can, and usually does, look much better than a tiling WM.

On a completely unrelated side note, how do I make xmonad automatically run a command when started up?

---

### Post by chucky chuckaluck on 2008-05-05
> **Barrucadu said:**
> I'm not so sure about 99%... Quite a lot of people care about aesthetics, and lets face it, a floating WM can, and usually does, look much better than a tiling WM.

i was being coy - [http://ubuntuforums.org/showthread.php?t=752119](http://ubuntuforums.org/showthread.php?t=752119)

> On a completely unrelated side note, how do I make xmonad automatically run a command when started up?

i guess you could just put it in .xinitrc. you know, *exec feh --bg-scale uglyashell.png & xmonad*
(something like that...)

---

### Post by Barrucadu on 2008-05-05
I was hoping for something within xmonad itself - I made a .desktop file for xmonad so I can choose between xmonad and openbox (though I am trying to resist openbox) at GDM. And I'm pretty sure that a .xinitrc is ignored when starting a session through GDM.

---

### Post by chucky chuckaluck on 2008-05-05
> **Barrucadu said:**
> I was hoping for something within xmonad itself - I made a .desktop file for xmonad so I can choose between xmonad and openbox (though I am trying to resist openbox) at GDM. And I'm pretty sure that a .xinitrc is ignored when starting a session through GDM.

gdm is something i never got the point of. (could be just my anti-gui fascism.)

---

### Post by cardinals_fan on 2008-05-06
How about Evilwm? :twisted:

---

### Post by chucky chuckaluck on 2008-05-06
> **cardinals_fan said:**
> How about Evilwm? :twisted:

i couldn't remember what it was like, so i tried it again. it's much more in the vein of 9wm/aewm, which i don't think of as tiling wm's (i've never gotten them to tile anything).

---

### Post by ynnhoj on 2008-05-06
evilwm isn't a tiling window manager, but it's a really good, lightweight (almost invisible, in terms of gui) window manager.

if you've created a desktop file for xmonad, you ought to be able to specify a script to run upon login; you can put any start-up commands that you want in that file.  or you could create a custom session (i think), which would run your ~/.xsession script upon login.  that way you can have one ~/.xinitrc or ~/.xsession and simply sym-link one to the other.

---

### Post by Barrucadu on 2008-05-06
> **ynnhoj said:**
> evilwm isn't a tiling window manager, but it's a really good, lightweight (almost invisible, in terms of gui) window manager.

if you've created a desktop file for xmonad, you ought to be able to specify a script to run upon login; you can put any start-up commands that you want in that file.  or you could create a custom session (i think), which would run your ~/.xsession script upon login.  that way you can have one ~/.xinitrc or ~/.xsession and simply sym-link one to the other.

I had this exact same though earlier today at school. During a boring maths lesson, I suddenly thought "If I can specify the path to the executable file to run when that session starts - surely a script rather than a binary could be used!".
I guess that shows how much I pay attention in maths...

---

### Post by ynnhoj on 2008-05-06
yip -- just write the script, use *chmod* to make it executable, and you're good.

---

### Post by corney91 on 2008-05-06
> **finferflu said:**
> From my experience, I think wmii is the better middle ground in between. It has auto-tiling, but it's not as "aggressive" as the dwm family. After you get the grip of how auto-tiling works, you will much more happily appreciate how more complex WMs work. 

Of course, this is only what I have gathered from my experience.
+1

I went from GNOME to AwesomeWM and, as much as I loved it, I couldn't use it to it's full tiling potential 'til I tried wmii.

I personally find customizing minimalistic WMs is more fun than full-blown, compiz-enhanced DEs - it takes a different approach:)

---

### Post by chucky chuckaluck on 2008-05-06
> **corney91 said:**
> I personally find customizing minimalistic WMs is more fun than full-blown, compiz-enhanced DEs - it takes a different approach:)

i agree. i think a minimal wm is more of an open canvas than a DE would be. with openbox, for example, not only do you choose which components you want to use with it, you can customize those (usually), as well.

---

### Post by Barrucadu on 2008-05-06
I've got my startup script done :)
```
#!/bin/bash

feh --bg-scale /home/barrucadu/Wallpaper/Balloons1.png
xclock -d -update 1 -face nu &
sakura -e /home/barrucadu/term-apps/uptime.sh &
sakura -e /home/barrucadu/welcome.sh &
nm-applet &
exec xmonad

```

Yes, I have wallpaper. Why? I like it to look nice when I Mod+[1-9] to a new workspace in the second before I launch a program.

---

### Post by finferflu on 2008-05-06
> **Barrucadu said:**
> 
Yes, I have wallpaper.

Wallpapers belong to the past. Get real.

</extremism>
:D

---

### Post by chucky chuckaluck on 2008-05-06
> **finferflu said:**
> Wallpapers belong to the past. Get real.

</extremism>
:D

wallpapers are making a comeback. in fact, i'm going to open up a trendy cafe and use all my old wallpapers as decoration.

---

### Post by rjmdomingo2003 on 2008-05-07
> **chucky chuckaluck said:**
> wallpapers are making a comeback. in fact, i'm going to open up a trendy cafe and use all my old wallpapers as decoration.
Yes! Decorate the front door with the black cat..

---

### Post by chucky chuckaluck on 2008-05-07
> **rjmdomingo2003 said:**
> Yes! Decorate the front door with the black cat..

ooh! oh...would 'black cat cafe' be a little too cliche? (rhyme not intended)

---

### Post by rjmdomingo2003 on 2008-05-07
> **chucky chuckaluck said:**
> ooh! oh...would 'black cat cafe' be a little too cliche? (rhyme not intended)
Don't think so.. ask Janet.. Ms. Jackson if you're nasty..
Sorry, I'm an 80's bum.:popcorn:

---

### Post by Barrucadu on 2008-05-07
> **chucky chuckaluck said:**
> ooh! oh...would 'black cat cafe' be a little too cliche? (rhyme not intended)

Err, I immediately misread that as "Black Hat Cafe" :P

---

### Post by chucky chuckaluck on 2008-05-07
> **Barrucadu said:**
> Err, I immediately misread that as "Black Hat Cafe" :P

oh! that means something over there, doesn't it?

---

### Post by Barrucadu on 2008-05-07
> **chucky chuckaluck said:**
> oh! that means something over there, doesn't it?

It means something no matter where you are. [http://catb.org/jargon/html/B/black-hat.html](http://catb.org/jargon/html/B/black-hat.html)

---

### Post by chucky chuckaluck on 2008-05-07
> **Barrucadu said:**
> It means something no matter where you are. [http://catb.org/jargon/html/B/black-hat.html](http://catb.org/jargon/html/B/black-hat.html)

maybe i was confusing it with *un chapeau noir*.

---

