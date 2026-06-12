---
title: "xmms problem"
date: 2007-08-30
forum: Absolute Beginner Talk
---

### Post by sauravbhaumik on 2007-08-30
Ive recently installed a fresh copy of feisty.
And installed xmms, xmms-xmmplayer as well.

But when I open xmms, it causes some problems with configuration; when I right click on it, strange things appear; but I can't show it, because when the menu (without names - I can't locate where `preference', `open' etc are) appears on right clicking, the print screen doesn't work.

May be you understand what I mean.
Please help.

Saurav

---

### Post by splintercellguy on 2007-08-30
Dunno, and probably off-topic, but I like VLC :).

---

### Post by abhilash82 on 2007-08-30
perhaps for some odd reason maybe you lost your menurc

in your home directory

     ```

     cd .xmms
    
```then

     ```

     gedit menurc
    
```copy and paste this

     > 
                                                 ; xmms GtkItemFactory rc-file         -*- scheme -*-
; this file is an automated menu-path dump
;
;(menu-path "<Main>/Sort List/By Path + Filename" "")
;(menu-path "<Main>/Selection/Sort By Date" "")
;(menu-path "<Main>/Delete" "")
;(menu-path "<Main>/Analyzer Falloff/Slow" "")
;(menu-path "<Main>/Always On Top" "<Control>a")
;(menu-path "<Save>/By extension" "")
;(menu-path "<Main>/Playback/Stop" "v")
;(menu-path "<Main>/Repeat" "r")
;(menu-path "<Main>" "")
;(menu-path "<Save>/-" "")
;(menu-path "<Main>/WindowShade VU Mode" "")
;(menu-path "<Main>/Visualization" "")
;(menu-path "<Main>/Analyzer Mode/Peaks" "")
;(menu-path "<Main>/Load/From WinAMP EQF file" "")
;(menu-path "<Main>/Add/File" "")
;(menu-path "<Main>/Graphical EQ" "<Alt>g")
;(menu-path "<Main>/Analyzer Mode/Fire" "")
;(menu-path "<Main>/Play Directory" "<Shift>l")
;(menu-path "<Main>/Playlist" "")
;(menu-path "<Main>/Peaks Falloff/Medium" "")
;(menu-path "<Main>/Peaks Falloff/Fast" "")
;(menu-path "<Main>/Save" "")
;(menu-path "<Main>/Visualization Mode/Analyzer" "")
;(menu-path "<Main>/Configure Equalizer" "")
;(menu-path "<Main>/Save/Default" "")
;(menu-path "<Main>/Visualization Mode" "")
;(menu-path "<Main>/Playback" "")
;(menu-path "<Main>/Visualization Mode/Scope" "")
;(menu-path "<Main>/Peaks Falloff/Slow" "")
;(menu-path "<Main>/Peaks Falloff/Fastest" "")
;(menu-path "<Main>/View File Info" "<Control>3")
;(menu-path "<Main>/Playback/Start of List" "<Control>z")
;(menu-path "<Main>/Add" "")
;(menu-path "<Main>/Playlist Editor" "<Alt>e")
;(menu-path "<Main>/Delete/Auto-load preset" "")
(menu-path "<Main>/Time Elapsed" "")
;(menu-path "<Main>/Autoscroll Song Name" "")
;(menu-path "<Main>/Load/From file" "")
;(menu-path "<Main>/Playlist/Save List" "")
;(menu-path "<Main>/Remove/All" "")
;(menu-path "<Main>/Selection" "")
;(menu-path "<Main>/Load" "")
;(menu-path "<Main>/Playlist WindowShade Mode" "<Shift><Control>w")
;(menu-path "<Main>/Playback/Jump to Time" "<Control>j")
;(menu-path "<Main>/Selection/Randomize" "")
;(menu-path "<Main>/Remove Dead Files" "")
;(menu-path "<Main>/Peaks Falloff" "")
;(menu-path "<Save>/pls" "")
;(menu-path "<Main>/About XMMS" "")
;(menu-path "<Main>/Reload skin" "F5")
;(menu-path "<Main>/Peaks Falloff/Slowest" "")
;(menu-path "<Main>/Reverse List" "")
;(menu-path "<Main>/Sort List/By Title" "")
;(menu-path "<Main>/Selection/Select None" "")
;(menu-path "<Main>/Analyzer Mode/-" "")
;(menu-path "<Main>/Playback/Jump to File" "j")
;(menu-path "<Main>/Save/Preset" "")
;(menu-path "<Main>/Save/Auto-load preset" "")
;(menu-path "<Main>/Remove/Crop" "")
;(menu-path "<Main>/Scope Mode/Line Scope" "")
;(menu-path "<Main>/Queue - Unqueue" "q")
;(menu-path "<Main>/Scope Mode/Solid Scope" "")
;(menu-path "<Main>/Skin Browser" "<Alt>s")
;(menu-path "<Main>/Refresh Rate/Full (~50 fps)" "")
;(menu-path "<Main>/Playback/Pause" "c")
;(menu-path "<Main>/Selection/Sort By Title" "")
;(menu-path "<Main>/Playback/Next" "b")
;(menu-path "<Main>/Analyzer Mode/Vertical Lines" "")
;(menu-path "<Main>/Analyzer Falloff/Fastest" "")
;(menu-path "<Main>/Playback/Back 5 Seconds" "")
;(menu-path "<Main>/Analyzer Mode/Lines" "")
;(menu-path "<Main>/Load/Default" "")
;(menu-path "<Main>/Playback/10 Tracks Fwd" "")
;(menu-path "<Main>/Save/-" "")
;(menu-path "<Main>/Save/To file" "")
;(menu-path "<Main>/Playback/-" "")
;(menu-path "<Main>/Sort List" "")
;(menu-path "<Main>/Sort List/By Date" "")
;(menu-path "<Main>/WindowShade VU Mode/Normal" "")
;(menu-path "<Main>/DoubleSize" "<Control>d")
;(menu-path "<Main>/Remove" "")
;(menu-path "<Main>/No Playlist Advance" "<Control>n")
;(menu-path "<Main>/Exit" "<Control>q")
;(menu-path "<Main>/Selection/-" "")
;(menu-path "<Save>" "")
;(menu-path "<Main>/Sort List/By Filename" "")
;(menu-path "<Main>/Analyzer Mode" "")
;(menu-path "<Main>/Playback/10 Tracks Back" "")
;(menu-path "<Main>/Time Remaining" "<Control>r")
;(menu-path "<Main>/Analyzer Mode/Normal" "")
;(menu-path "<Main>/Selection/Sort By Path + Filename" "")
;(menu-path "<Main>/Load/-" "")
;(menu-path "<Main>/WindowShade Mode" "<Control>w")
;(menu-path "<Main>/Analyzer Falloff/Slowest" "")
;(menu-path "<Main>/Easy Move" "<Control>e")
;(menu-path "<Main>/Load/Auto-load preset" "")
;(menu-path "<Main>/Add/Url" "")
;(menu-path "<Main>/Queue manager" "<Alt>q")
;(menu-path "<Main>/Playback/Previous" "z")
;(menu-path "<Main>/Add/Directory" "")
;(menu-path "<Main>/Analyzer Falloff" "")
;(menu-path "<Main>/Remove/Misc" "")
;(menu-path "<Main>/Playback/Fwd 5 Seconds" "")
;(menu-path "<Main>/File Info" "")
;(menu-path "<Main>/Remove/Selected" "")
;(menu-path "<Main>/Refresh Rate/Half (~25 fps)" "")
;(menu-path "<Main>/Selection/Sort By Filename" "")
;(menu-path "<Main>/Play Location" "<Control>l")
;(menu-path "<Main>/Import" "")
;(menu-path "<Main>/Scope Mode/Dot Scope" "")
;(menu-path "<Main>/Show on all desktops" "<Control>s")
;(menu-path "<Main>/Refresh Rate/Eighth (~6 fps)" "")
;(menu-path "<Main>/Randomize List" "")
;(menu-path "<Main>/Scope Mode" "")
;(menu-path "<Main>/Playback/Clear Queue" "<Shift>q")
(menu-path "<Main>/Jump To Time" "")
;(menu-path "<Main>/Visualization plugins" "<Control>v")
;(menu-path "<Save>/m3u" "")
;(menu-path "<Main>/Equalizer WindowShade Mode" "<Control><Alt>w")
;(menu-path "<Main>/Selection/Read Extended Info" "")
;(menu-path "<Main>/Physically Delete Files" "")
;(menu-path "<Main>/Options" "")
;(menu-path "<Main>/Import/WinAMP Presets" "")
;(menu-path "<Main>/Load/Preset" "")
;(menu-path "<Main>/Selection/Select All" "")
;(menu-path "<Main>/Playlist/Load List" "")
;(menu-path "<Main>/Play File" "l")
;(menu-path "<Main>/Refresh Rate/Quarter (~13 fps)" "")
;(menu-path "<Main>/Selection/Invert Selection" "")
;(menu-path "<Main>/Preferences" "<Control>p")
(menu-path "<Main>/Jump To File" "")
;(menu-path "<Main>/Refresh Rate" "")
;(menu-path "<Main>/Shuffle" "s")
;(menu-path "<Main>/Load/Zero" "")
;(menu-path "<Main>/Analyzer Falloff/Medium" "")
;(menu-path "<Main>/Visualization Mode/Off" "")
;(menu-path "<Main>/Playlist/New List" "")
;(menu-path "<Main>/Analyzer Falloff/Fast" "")
;(menu-path "<Main>/Save/To WinAMP EQF file" "")
;(menu-path "<Main>/WindowShade VU Mode/Smooth" "")
;(menu-path "<Main>/Time Display (MMM:SS)" "<Shift><Control>l")
;(menu-path "<Main>/Analyzer Mode/Bars" "")
;(menu-path "<Main>/Playback/Play" "x")
;(menu-path "<Main>/Delete/Preset" "")
;(menu-path "<Main>/-" "")
;(menu-path "<Main>/Sort" "")
;(menu-path "<Main>/Main Window" "<Alt>w")
 then save the file.

If all these things don't work then try changing your default language to English(UK).

---

### Post by sauravbhaumik on 2007-09-01
> **abhilash82 said:**
> perhaps for some odd reason maybe you lost your menurc

in your home directory

     ```

     cd .xmms
    
```then

     ```

     gedit menurc
    
```copy and paste this

     then save the file.

If all these things don't work then try changing your default language to English(UK).

It doesn't solve the problem. Please advise further.

---

### Post by abhilash82 on 2007-09-01
Then I suppose you switch over to an alternate player. The development/support for xmms player isn't being updated constantly. I can help you with some alternate players that are even compatible with winamp and are more robust.

1. beep media player or bmpx

2. audacious

3. exaile

You can use Amarok if you are running kubuntu.

---

### Post by sauravbhaumik on 2007-09-01
> **abhilash82 said:**
> Then I suppose you switch over to an alternate player. The development/support for xmms player isn't being updated constantly. I can help you with some alternate players that are even compatible with winamp and are more robust.

1. beep media player or bmpx

2. audacious

3. exaile

You can use Amarok if you are running kubuntu.

Well, I've already been using MPlayer movie player, VLC etc. But you see, in MPlayer movie player, the equalizer causes problem when you configure it to Bass mode (manually, of course). In Xmms, the problem is fixed; and in Edgy, the xmms has now been my favourite one.

And could you solve my low volume problem, which I experience in Edgy and feisty, but not in  windows. 
Please refer to [http://ubuntuforums.org/showthread.php?t=468553](http://ubuntuforums.org/showthread.php?t=468553)
and 
[http://ubuntuforums.org/showthread.php?t=375735](http://ubuntuforums.org/showthread.php?t=375735)
[http://ubuntuforums.org/showthread.php?t=371474](http://ubuntuforums.org/showthread.php?t=371474)

These are not fixed; and I can not get the enhanced sound controls in linux as I get in windows. Can you illuminate?
However, the OS I am now at is Ubuntu feisty 7.04.

---

