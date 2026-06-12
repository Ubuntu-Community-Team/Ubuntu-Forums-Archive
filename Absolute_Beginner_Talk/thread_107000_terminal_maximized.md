---
title: "terminal maximized"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by o_owd on 2005-12-22
hello,
how can i open the terminal maximized ?

thanks

---

### Post by Kethinov on 2005-12-22
Assuming you mean you want to switch from X11 to a fullscreen terminal, you can press ctrl+alt+f1 (through f6) to get a fullscreen terminal. You can switch between then with alt+arrowkey. Press ctrl+alt+f7 to return to X11, or just alt+arrowkey back to it when you want X11 back. Not sure why you need this though. Opening gnome-terminal and hitting the maximize button works well enough for me. :)

---

### Post by o_owd on 2005-12-22
[QUOTE=Kethinov]Assuming you mean you want to switch from X11 to a fullscreen terminal, you can press ctrl+alt+f1 (through f6) to get a fullscreen terminal. You can switch between then with alt+arrowkey. Press ctrl+alt+f7 to return to X11, or just alt+arrowkey back to it when you want X11 back. Not sure why you need this though. Opening gnome-terminal and hitting the maximize button works well enough for me. :)[/QUOTE]

yes, i know. but how do i set (something like "default") when i click on it to open maximized ?

something like setting in windows "open maximized"

thanks.

---

### Post by patrick295767 on 2005-12-22
[QUOTE=o_owd]yes, i know. but how do i set (something like "default") when i click on it to open maximized ?

something like setting in windows "open maximized"

thanks.[/QUOTE]
  
try maybe the :
ALT + left mouse : move window

ALT + right mouse : resize window
  [http://www.ubuntuforums.org/showthread.php?t=64557&page=7](http://www.ubuntuforums.org/showthread.php?t=64557&page=7)
I use it in fvwm & it's very great !
   
my ~.fvwm/.fvwm2rc:```

  # This file is copied to a new user's FVWM_USERDIR by FvwmForm-Setup form.
# This file contains the commands fvwm reads while starting.
#

EdgeResistance 0 0
EdgeScroll 100 100
ClickTime 0

DeskTopSize 5x0
MenuStyle * fvwm, Foreground maroon, Background grey60, Greyed grey40
MenuStyle * Font -adobe-times-bold-r-*-*-14-*-*-*-*-*-*-*

DestopName 0 Main
DesktopName 1 Apps

ColormapFocus FollowsMouse

# default Styles:
# make sure these fonts exist on your system:
Style *           Font -adobe-times-bold-r-*-*-12-*-*-*-*-*-*-*
Style *           IconFont -adobe-times-bold-r-*-*-12-*-*-*-*-*-*-*
Style *           HilightFore black, HilightBack palevioletred
Style *           BorderWidth 7, HandleWidth 7
Style *           Icon unknown1.xpm, Color lightgrey/dimgrey
Style *           MWMFunctions, MWMDecor, HintOverride
Style *           DecorateTransient, NoPPosition
Style *           IconBox 0 -10 -280 -1
Style *           FocusFollowsMouse
Style *           TileCascadePlacement



## patrick add to menu
# Irix-5.2 like pager
Style "FvwmPager" Handles, NoTitle
FvwmPagerGeometry 20x20-1-1
FvwmPagerFore Black
FvwmPagerBack LightGray
FvwmPagerHilight Yellow
FvwmPagerLabel 0 Global





# Styles for various Fvwm modules:
Style Fvwm*       NoTitle,  Sticky, WindowListSkip
Style Fvwm*       BorderWidth 2, CirculateSkipIcon, CirculateSkip
Style FvwmPager   ClickToFocus
Style FvwmBanner  StaysOnTop
Style FvwmButtons Icon toolbox.xpm, ClickToFocus

# Styles for your common terminal emulator programs.
# xterms and rxvts in a separate icon box:
Style XTerm       Icon xterm.xpm, SloppyFocus, IconBox -70 1 -1 -140
Style rxvt        Icon term.xpm, SloppyFocus, IconBox -70 1 -1 -140
Style rxvt        MWMBorder, MWMButtons

# Styles for various common programs:
Style *lock       NoTitle, NoHandles, Sticky, WindowListSkip, ClickToFocus
Style xbiff       NoTitle, Sticky, WindowListSkip, ClickToFocus
Style xcalc       Icon xcalc.xpm, NoButton 2,ClickToFocus
Style xmh         Icon mail1.xpm, NoIconTitle,StickyIcon
Style xmh         NoButton 2
Style xman        Icon xman.xpm, ClickToFocus
Style xmag        Icon mag_glass.xpm, ClickToFocus
Style xgraph      Icon graphs.xpm, ClickToFocus
Style xmosaic     Color Green/Yellow, ClickToFocus

## patrick add to menu
AddToMenu "System"
+       "Are you sure to logout ? " Title 
+       ""      Nop
+       "Restart" Restart
+       "Quit"  Quit

## patrick
DestroyFunc WindowMoveControl
AddToFunc WindowMoveControl
+ M Move 

Mouse 1 W M Function WindowMoveControl



## patrick add to menu
AddToFunc "Resize-or-Raise" "M" Resize
+              "M" Raise
+              "C" Raise
+              "D" RaiseLower


# some simple default key bindings:
Key Next         A       SCM     Next[*] Focus
Key Prior        A       SCM     Prev[*] Focus

# some simple default mouse bindings:
#   for the root window:
Mouse 1 R       A       Menu MenuFvwmRoot Nop
Mouse 2 R       A       Menu MenuFvwmWindowOps Nop
Mouse 3 R       A       WindowList

#   for the title bar buttons:
Mouse 0 1       A       Menu MenuFvwmWindowOps2 Close
Mouse 0 2       A       FuncFvwmMaximize
Mouse 0 4       A       Iconify

#   for other parts of the window/borders/icons:
Mouse 1 F       A       FuncFvwmResizeOrRaise
Mouse 1 S      A       FuncFvwmMoveOrRaise

# M meta = meta_alt
# A      = normal

Mouse 1 T	A Raise
Mouse 1 T	M RaiseLower


Mouse 1		WFS	M	FuncFvwmMoveOrRaise
#Mouse 1		WFST	12	FuncFvwmMoveOrRaise

#Mouse 1 I       A       FuncFvwmMoveOrIconify

Mouse 2 W	A Iconify

Mouse 2 W	M RaiseLower


Mouse 2 I       A       Iconify
Mouse 2 FST     A       Menu MenuFvwmWindowOps2 Nop

## Mouse 3 TSIF    A       RaiseLower
#Mouse 3		FST	1	FuncFvwmResizeOrRaise
#Mouse 3		FST	12	FuncFvwmResizeOrRaise

#Mouse 3 W M Resize direction SE WarpToBorder
DestroyFunc WindowpatrickResize
AddToFunc WindowpatrickResize
+ M Resize direction SE

Mouse 3 W M Function  WindowpatrickResize



Mouse 3	I	A	Move
Mouse 1	I	A	Iconify
Mouse 1	I	M	Move


## patrick keys 

Key Left        A       M       Desk -1 0
#Key Left        A       1       Desk -1 0
Key Right       A       M       Desk 1 0
#Key Right       A       1       Desk 1 0



######################## Initialization Functions ############################ startup ###
AddToFunc StartFunction
## + I Module FvwmAnimate
+ I Module FvwmPager 0 1
+ I Exec exec gdeskcal
#Module FvwmPager 0 1
#+ I Module FvwmBanner
#+ I Module FvwmButtons
#+ I Exec exec xclock -digital

AddToFunc InitFunction
+ I exec xsetroot -mod 2 2 -fg rgb:55/40/55 -bg rgb:70/50/70

# For some SM-s (like gnome-session) there is an internal background setter.
AddToFunc SessionInitFunction
+ I Nop




######################## Menus ###################
Read /etc/X11/fvwm/menudefs.hook Quiet
Read menudefs.hook Quiet
#patrickmenu

DestroyMenu MenuFvwmRoot
AddToMenu MenuFvwmRoot  "$[gt.Root Menu]"             Title
+                       "&1. XTerm"             Exec exec xterm
+                       "&E. Rox"             Exec exec rox
+                       "&2. Rxvt"            Exec exec rxvt
+                       "&Z. Mozilla"              Exec exec mozilla-firefox
+                       "&O. Opera"              Exec exec opera
+                       ""              Nop
+                       "&D. Debian Menu"             Popup "/Debian"
+                       ""              Nop
+                       "&R. $[gt.Remote Logins]"     Popup MenuFvwmLogins
+                       ""              Nop
+                       "&U. $[gt.Utilities]"         Popup MenuFvwmUtilities
+                       ""              Nop
+                       "&M. $[gt.Fvwm Modules]"      Popup MenuFvwmModules
+                       "&W. $[gt.Fvwm Window Ops]"   Popup MenuFvwmWindowOps
+                       "&S. $[gt.Fvwm Config Ops]"   Popup MenuFvwmConfig
+                       ""              Nop
+                       "&F. $[gt.Refresh Screen]"   Refresh
+                       "&C. $[gt.Recapture Screen]" Recapture
+                       ""              Nop
+                       "&L. Xlock"             Exec exec xlock -mode dclock
+                       "&X. $[gt.Exit Fvwm]" Popup MenuFvwmQuitVerify

DestroyMenu MenuFvwmUtilities
AddToMenu MenuFvwmUtilities     "$[gt.Utilities]" Title
+                       "&T. Top"       Exec exec xterm -T Top -n Top -e top
+                       "&C. Calculator" Exec exec xcalc
+                       "&M. Xman"      Exec exec xman
+                       "&G. Xmag"      Exec exec xmag
+                       "&R. Editres"   Exec exec editres
+                       ""              Nop
+                       "&E. XEmacs"    Exec exec xemacs
+                       "&A. Xmh Mail"  FuncFvwmMailXmh xmh "-font fixed"
+                       ""              Nop
+                       "&L. XLock"     Exec exec xlock -mode random
+                       ""              Nop
+                       "&D. $[gt.Reset X defaults]" Exec xrdb -load $HOME/.Xdefaults

DestroyMenu MenuFvwmConfig
AddToMenu MenuFvwmConfig "$[gt.Fvwm Config Ops]" Title
+ "&S. $[gt.Sloppy Focus]"        FuncFvwmFocusPolicyChange SloppyFocus
+ "&C. $[gt.Click To Focus]"      FuncFvwmFocusPolicyChange ClickToFocus
+ "&F. $[gt.Focus Follows Mouse]" FuncFvwmFocusPolicyChange FocusFollowsMouse
+ "" Nop
+ "&1. $[gt.Colormap Follows Mouse]" ColormapFocus FollowsMouse
+ "&2. $[gt.Colormap Follows Focus]" ColormapFocus FollowsFocus
+ "" Nop
+ "&3. $[gt.Full Paging ON]"           EdgeScroll 100 100
+ "&4. $[gt.All Paging OFF]"           EdgeScroll 0 0
+ "&5. $[gt.Horizontal Paging Only]"   EdgeScroll 100 0
+ "&6. $[gt.Vertical Paging Only]"     EdgeScroll 0 100
+ "&7. $[gt.Partial Paging]"           EdgeScroll 50 50
+ "&8. $[gt.Full Paging && Edge Wrap]" EdgeScroll 100000 100000

# The window Ops menus exhibit a different HotKey style.
# There are 2 versions of the WindowOps Menu, meant to be bound to different
# things.  Here is the "common" part:
DestroyFunc FuncFvwmWindowCommon
AddToFunc FuncFvwmWindowCommon
+ I AddToMenu $0 "$[gt.&Move]"              Move
+ I AddToMenu $0 "$[gt.&Resize]"            Resize
+ I AddToMenu $0 "$[gt.R&aise]"             Raise
+ I AddToMenu $0 "$[gt.&Lower]"             Lower
+ I AddToMenu $0 "$[gt.(De)&Iconify]"       Iconify
+ I AddToMenu $0 "$[gt.(Un)&Stick]"         Stick
+ I AddToMenu $0 "$[gt.(Un)Ma&ximize]"      Maximize
+ I AddToMenu $0 ""                 Nop
+ I AddToMenu $0 "$[gt.&Delete]"            Delete
+ I AddToMenu $0 "$[gt.&Close]"             Close
+ I AddToMenu $0 "$[gt.Destroy]"            Destroy
+ I AddToMenu $0 ""                 Nop

# First windowops menu, bound to:
# mouse 2 on root
# Root menu
DestroyMenu MenuFvwmWindowOps
AddToMenu MenuFvwmWindowOps     "$[gt.Window Ops]"    Title
FuncFvwmWindowCommon MenuFvwmWindowOps
+ "$[gt.Re&fresh Window]" RefreshWindow

# Second windowops menu, bound to:
# any mouse on titlebar button 1
# mouse 2 on frame, side or titlebar
DestroyMenu MenuFvwmWindowOps2
AddToMenu MenuFvwmWindowOps2
FuncFvwmWindowCommon MenuFvwmWindowOps2
+ Scroll&Bar       Module FvwmScroll 2 2
+ "&$[gt.Print]"           FuncFvwmPrint
+ "$[gt.Print Re&verse]" FuncFvwmPrintReverse

# 3 different ways to log on, take your pick:
DestroyFunc FuncFvwmRloginXterm
AddToFunc FuncFvwmRloginXterm \
  I Exec xterm -name $0 -title "$USER @ $0" -e rlogin $0
DestroyFunc FuncFvwmRloginRxvt
AddToFunc FuncFvwmRloginRxvt \
  I Exec rxvt -name $0 -n $0 -title $USER@$0 -e rlogin $0
DestroyFunc FuncFvwmRloginRshRxvt
AddToFunc FuncFvwmRloginRshRxvt \
  I Exec Exec rsh $0 rxvt -display $HOSTDISPLAY

# be sure to fill these in with your correct machine names:
DestroyMenu MenuFvwmLogins
AddToMenu MenuFvwmLogins
+ &dopey  FuncFvwmRloginXterm dopey
+ &snoopy FuncFvwmRloginXterm snoopy
+ s&ignal Exec rxterm signal

DestroyMenu MenuFvwmModules
AddToMenu MenuFvwmModules "$[gt.Fvwm Modules]"        Title
+ "&1. $[gt.Control Animation]" Popup  MenuFvwmAnimate
+ "&B. Button-Bar"        Module FvwmButtons
+ "&O. IconBox"           FuncFvwmConfigureIconBox
+ "&F. Forms"             Popup  MenuFvwmForms
+ "&I. Identify"          Module FvwmIdent
+ "&M. IconMan"           Module FvwmIconMan
+ "&N. Banner"            Module FvwmBanner
+ "&C. Console"           Module FvwmConsole
+ "&P. Pager"             Module FvwmPager 0 0
+ "&2. Pager (2 $[gt.desks])"   Module FvwmPager 0 1
+ "&R. Backer"            Module FvwmBacker
+ "&S. ScrollBar"         Module FvwmScroll 50 50
+ "&T. FvwmTaskBar"       Module FvwmTaskBar
+ "&U. AutoRaise"         Module FvwmAuto 200 Raise Nop
+ "&W. WinList"           Module FvwmWinList
+ "&X. $[gt.Stop Module Menu]"  Popup  MenuFvwmStopModule

DestroyMenu MenuFvwmStopModule
AddToMenu MenuFvwmStopModule "$[gt.Stop Fvwm Modules]" Title
+ "&B. $[gt.Stop] Button-Bar"  KillModule FvwmButtons
+ "&O. $[gt.Stop] IconBox"     KillModule FvwmIconBox
+ "&M. $[gt.Stop] IconMan"     KillModule FvwmIconMan
+ "&P. $[gt.Stop] Pager"       KillModule FvwmPager
+ "&R. $[gt.Stop] Backer"      KillModule FvwmBacker
+ "&S. $[gt.Stop] ScrollBar"   KillModule FvwmScroll
+ "&T. $[gt.Stop] FvwmTaskBar" KillModule FvwmTaskBar
+ "&U. $[gt.Stop] AutoRaise"   KillModule FvwmAuto
+ "&W. $[gt.Stop] WinList"     KillModule FvwmWinList

DestroyMenu MenuFvwmForms
AddToMenu MenuFvwmForms
+ "&C. Capture"       Module FvwmForm FvwmForm-Capture
+ "&D. Form Defaults" Module FvwmForm FvwmForm-Form
+ "&R. Rlogin"        Module FvwmForm FvwmForm-Rlogin
+ "&P. RootCursor"    Module FvwmForm FvwmForm-RootCursor
+ "&S. Setup"         Module FvwmForm FvwmForm-Setup
+ "&T. Talk Form"     Module FvwmForm FvwmForm-Talk
+ "&Q. QuitVerify"    Module FvwmForm FvwmForm-QuitVerify

# Configure and start using an iconbox on the fly
DestroyFunc FuncFvwmConfigureIconBox
AddToFunc FuncFvwmConfigureIconBox
+ I Module FvwmIconBox
+ I Style     *  NoIcon

DestroyMenu MenuFvwmQuitVerify
AddToMenu MenuFvwmQuitVerify "$[gt.Really Quit Fvwm?]" Title
+ "&Q. $[gt.Yes, Really Quit]" Quit
+ ""                     Nop
+ "&R. $[gt.Restart]"          Restart
+ ""                     Nop
+ "&T. $[gt.Start] twm"        Restart twm
+ "&C. $[gt.Start] ctwm"       Restart ctwm
+ "&2. $[gt.Start] tvtwm"      Restart tvtwm
+ "&V. $[gt.Start] vtwm"       Restart vtwm
+ "&M. $[gt.Start] mwm"        Restart mwm
+ "&O. $[gt.Start] olwm"       Restart /usr/openwin/bin/olwm
+ ""                     Nop
+ "&X. $[gt.Just an Xterm]"    Restart xterm -n '"X Console"' -T '"X Console"'
+ ""                     Nop
+ "&N. $[gt.No, Don't Quit]"   Nop

######################## Sample Functions ##########################

DestroyFunc FuncFvwmMailXmh
AddToFunc FuncFvwmMailXmh
+ I Next [$0] Iconify false
+ I Next [$0] Focus
+ I None [$0] Exec $0 $1

DestroyFunc FuncFvwmMoveOrRaise
AddToFunc FuncFvwmMoveOrRaise
+ I Raise
+ M Move
+ D Lower

DestroyFunc FuncFvwmMaximize
AddToFunc FuncFvwmMaximize
+ M Maximize   0 100
+ H Maximize   0 100
+ C Maximize   0  80
+ D Maximize 100 100

DestroyFunc FuncFvwmMoveOrIconify
AddToFunc FuncFvwmMoveOrIconify
+ I Raise
+ M Move
+ D Iconify

DestroyFunc FuncFvwmResizeOrRaise
AddToFunc FuncFvwmResizeOrRaise
+ I Raise
+ M Resize
+ D Lower

DestroyFunc FuncFvwmPrint
AddToFunc FuncFvwmPrint
+ I Raise
+ I Exec xdpr -id $w

DestroyFunc FuncFvwmPrintReverse
AddToFunc FuncFvwmPrintReverse
+ I Raise
+ I Exec xdpr 1/2 -h -rv -id $w

DestroyFunc FuncFvwmFocusPolicyChange
AddToFunc FuncFvwmFocusPolicyChange
+ I Style * $0
+ I Recapture

# Read config files for modules:
read ConfigFvwmBacker
read ConfigFvwmButtons
read ConfigFvwmIconBox
read ConfigFvwmIconMan
read ConfigFvwmIdent
read ConfigFvwmPager
read ConfigFvwmScroll
read ConfigFvwmTaskBar
read ConfigFvwmWinList
```

---

### Post by o_owd on 2005-12-23
i don't have a clue what your taliking about... :)
i am really just a newbie....

---

### Post by elemental666 on 2005-12-23
[QUOTE=o_owd]hello,
how can i open the terminal maximized ?

thanks[/QUOTE]

GOTO: APPLICATIONS -> SYSTEM TOOLS -> APPLICATIONS MENU EDITOR
 Inside the editor goto: Accessories
find Terminal in the list, right click on it and click on preferences.

If you have put the terminal link the Gnome Panel you can just right click on the icon in the panel and go to preferences.

This brings up the entry Editor for gnome-terminal, in which you will find the Command box, that probably says something like this:

```
 gnome-terminal --working-directory=%f
```

you want to add a switch for geometry here ( --geometry WIDTHxHEIGHT+XOFF+YOFF)

Where:
  WIDTHxHEIGHT = the size of the window, you'll just have to play with it to get it right
  +XOFF = offset from the left edge of the screen
  -XOFF = offset from the right edge of the screen
  +YOFF = offset from the top edge of the screen
  -YOFF = offset from the bottom edge of the screen

resulting in something like this:
```
gnome-terminal --working-directory=%f --geometry=150x40+0+0
```

it appears, now that I actually try this, that gnome or ubuntu's implementation of gnome uses Chars instead of pixels for the geometry settings, so start small and work up, lik 60x60 and adjust from there

I'me running 1400x1050 resolution and to get full screen with the gnome panels visible I set mine to 172x55+0+0, this gave me full width and just a sliver of desktop at the bottom

see man gnome-terminal and man X (scroll down to the geometry section) for more info

---

### Post by o_owd on 2005-12-23
thanks man, it works.

---

### Post by elemental666 on 2005-12-23
groovy ;P

I still prefer just switching Virtual Terminals tho, I figure if your gonna be in the shell, be in the shell, ya know!

cheers

---

