---
title: "Getting Xming to work on PowerPC Ubuntu"
date: 2008-12-27
forum: Apple Hardware Users
---

### Post by SalemMA on 2008-12-27
Hello,

I have installed Xming and XLaunch on my Windows XP box and I have, I believe, set things correctly to allow Remote Login on my Ubuntu Hardy PowerPC machine.

But I run XLaunch: 
[LIST]
[*]choose the One Window option (Display 0)
[*]open session via XDMCP
[*]connect to host 192.168.1.222, use indirect connection
[*]check to enable clipboard manager
[*]Click Finish
[/LIST]

I get a window, and in the window I see my Ubuntu host listed showing the correct linux version.

But when I choose the Ubuntu host and try to connect, I just get a blank window. No login field is offered.

When I check the Xming log, I get the following:

[SIZE="2"][INDENT]Welcome to the Xming X Server
Vendor: Colin Harrison
Release: 6.9.0.31
FreeType2: 2.3.4
Contact: [http://sourceforge.net/forum/?group_id=156984](http://sourceforge.net/forum/?group_id=156984)

Xming :0 -indirect 192.168.1.222 -clipboard 

XdmcpRegisterConnection: newAddress 192.168.1.127
glWinInitVisuals:1596: glWinInitVisuals
glWinInitVisualConfigs:1503: glWinInitVisualConfigs glWinSetVisualConfigs:1581: glWinSetVisualConfigs
init_visuals:1055: init_visuals
glWinScreenProbe:1390: glWinScreenProbe
fixup_visuals:1303: fixup_visuals
init_screen_visuals:1336: init_screen_visuals
(--) 5 mouse buttons found
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409) 
(--) Using preset keyboard for "English (USA)" (409), type "4"
Could not init font path element C:\Program Files\Xming/fonts/100dpi/, removing from list!
Could not init font path element C:\Program Files\Xming\fonts\dejavu, removing from list!
Could not init font path element C:\Program Files\Xming\fonts\cyrillic, removing from list!
Could not init font path element C:\WINDOWS\Fonts, removing from list!
winProcEstablishConnection - Hello
winProcEstablishConnection - Xdmcp enabled, waiting to start clipboard client until fourth call.
winProcEstablishConnection - Hello
winProcEstablishConnection - Xdmcp enabled, waiting to start clipboard client until fourth call.
winProcEstablishConnection - Hello
winProcEstablishConnection - Xdmcp enabled, waiting to start clipboard client until fourth call.
winInitClipboard ()
winProcQueryTree - winInitClipboard returned.
winClipboardProc - Hello
DetectUnicodeSupport - Windows XP
winClipboardProc - DISPLAY=127.0.0.1:0.0
winProcEstablishConnection - Hello
winProcEstablishConnection - Clipboard client already launched, returning.
winClipboardProc - XOpenDisplay () returned and successfully opened the display.

winClipboardIOErrorHandler!

winClipboardProc - setjmp returned for IO Error Handler.
glWinResetExtension:1489: glWinResetExtension
winDeleteNotifyIcon
(==) FontPath set to "built-ins,C:\Program Files\Xming/fonts/misc/,C:\Program Files\Xming/fonts/TTF/,C:\Program Files\Xming/fonts/Type1/,C:\Program Files\Xming/fonts/75dpi/,C:\Program Files\Xming/fonts/100dpi/,C:\Program Files\Xming\fonts\dejavu,C:\Program Files\Xming\fonts\cyrillic,C:\WINDOWS\Fonts"
(==) Logfile set to "C:\Documents and Settings\Douglas Denholm\Local Settings\Temp\Xming.0.log"
glWinInitVisuals:1596: glWinInitVisuals
glWinInitVisualConfigs:1503: glWinInitVisualConfigs glWinSetVisualConfigs:1581: glWinSetVisualConfigs
init_visuals:1055: init_visuals
glWinScreenProbe:1390: glWinScreenProbe
fixup_visuals:1303: fixup_visuals
init_screen_visuals:1336: init_screen_visuals
(--) 5 mouse buttons found
(--) Setting autorepeat to delay=500, rate=31
(--) winConfigKeyboard - Layout: "00000409" (00000409) 
(--) Using preset keyboard for "English (USA)" (409), type "4"
Could not init font path element C:\Program Files\Xming/fonts/100dpi/, removing from list!
Could not init font path element C:\Program Files\Xming\fonts\dejavu, removing from list!
Could not init font path element C:\Program Files\Xming\fonts\cyrillic, removing from list!
Could not init font path element C:\WINDOWS\Fonts, removing from list![/INDENT][/SIZE]


I get this sort of message, or something very similar, regardless of whether I have my WinXP box's Firewall enabled.

Nothing in the log messages (except maybe the "winClipboardIOErrorHandler!" seems to explain why I get a blank screen and no login message.

Any suggestions on how to get Xming to work, would be appreciated.

TIA, SalemMA

---

