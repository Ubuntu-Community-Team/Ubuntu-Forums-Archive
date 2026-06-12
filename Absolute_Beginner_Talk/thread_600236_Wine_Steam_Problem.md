---
title: "Wine Steam Problem"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by crayment on 2007-11-02
I'm stuck and would really appreciate it if someone could help me figure this out.

ubuntu - 7.10
wine-0.9.48

I had no problem installing Steam with some help from other forums. And it seems to run perfect until i try to launch half life 2. I first get a warning about my video driver being out of date which i also got when i installed steam on my windows machine. But i find it strange that i haven't seen anything about this from anyone else installing on linux??

Anyway when i launch it, it kind of shows a zoomed image of my desktop like it changed the resolution which i expect but then it just crashes as if it restarted x.
Like i hit ctrl-alt-bkspc. then i am back at the login screen.

I normally run compiz but have tried disabling it and have also tried closing the steam window while the game is loading.

I don't know what else it could be...

thanks for any ideas.

---

### Post by Arthur Archnix on 2007-11-02
By disabling compiz, what do you mean? My first instinct would be to try
```
metacity --replace
```
Then try running hl2.

---

### Post by crayment on 2007-11-03
> **Arthur Archnix said:**
> By disabling compiz, what do you mean? My first instinct would be to try
```
metacity --replace
```
Then try running hl2.

I have tried this but i am not sure if it is working.

~$ metacity --replace
Window manager warning: "" not found in configuration database is not a valid value for keybinding "toggle_shaded"

I am not sure if this is dropping back to compiz though.

It doesn't change anything when i try after doing this.

---

### Post by Arthur Archnix on 2007-11-03
Ok, bit strange... what about that video driver warning, what video card do you have? I'm not certain that restricted driver manager has the very latest drivers. So you may want to look at upgrading to the latest version for your card?

---

### Post by skymera on 2007-11-03
0.9.48 and 0.9.47 are buggy with steam

i have 0.9.46 and works flawless with Steam and all games i have,

[www.winehq.com](www.winehq.com)

its availible under 

download > ubuntu > older .deb

good luck :wink:

---

### Post by crayment on 2007-11-03
> **skymera said:**
> 0.9.48 and 0.9.47 are buggy with steam

i have 0.9.46 and works flawless with Steam and all games i have,

[www.winehq.com](www.winehq.com)

its availible under 

download > ubuntu > older .deb

good luck :wink:

I originally had 0.9.46 and I had the problem so I tried upgrading to 0.9.48

My video card:
Intel GMA X3100

I don't know much about updating drivers. How could i find the latest one? and could i update through the package manager?

---

### Post by Arthur Archnix on 2007-11-04
Hmm... that video card apparently has some issues with compiz. This thread here is about tweaking the video card to work well with compiz, but it could help you with running steam. It depends. If your issue is a wine issue then this video card stuff if irrelevant. 

Anyway, here's a link to the video [tweaks]("http://ubuntuforums.org/showthread.php?t=506744").

---

### Post by crayment on 2007-11-05
Thanks for the help. I'm gonna read through it but im not sure how relevant it will be just because compiz seems to run great for me. All plugins work...  The rain on the desktop used to freeze it up but when i updated to 7.10 it seemed to clear that up.

Also i dropped back down to wine 0.9.46 and did a complete reinstall of Steam and hl2.  No change.

Another thought:  Do you know how to redirect standard error output.  like redirecting stdout at the command prompt with >
I want to do something like: wine Steam.exe > outputfile. so that once i crash and log back in i can at least see what wine was ouputing.

---

### Post by crayment on 2007-11-05
> **crayment said:**
> 
Another thought:  Do you know how to redirect standard error output.  like redirecting stdout at the command prompt with >
I want to do something like: wine Steam.exe > outputfile. so that once i crash and log back in i can at least see what wine was ouputing.

nevermind i answered my own question...

1> is for stdout and 2> is for stderr

This the contents of the file err.txt after this command.

env WINEPREFIX="/home/cody/.wine" wine "C:\Program Files\Steam\steam.exe" -applaunch 220 2>err.txt

```
err:ntlm:SECUR32_initNTLMSP ntlm_auth was not found or is outdated. Make sure that ntlm_auth >= 3.0.25 is in your path.
err:ntlm:SECUR32_initNTLMSP Usually, you can find it in the winbind package of your distribution.
err:dscapture:widDsCreate DirectSoundCapture flag not set
This sound card's driver does not support direct access
The (slower) DirectSound HEL mode will be used instead.
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,103,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,103,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,177,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,224,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,197,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,140,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,83,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,83,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2002c,0x00000000,0,2): stub!
fixme:shdocvw:ViewObject_SetAdvise (0x10370310)->(1 00000002 0x147c8c0)
fixme:shdocvw:PersistStreamInit_InitNew (0x10370310)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x10370310)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x10370310)->(ffffffff)
fixme:shdocvw:ViewObject_SetAdvise (0x1ec038)->(1 00000002 0x147c928)
fixme:shdocvw:PersistStreamInit_InitNew (0x1ec038)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1ec038)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1ec038)->(ffffffff)
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:win:EnumDisplayDevicesW ((null),0,0x33c5cc,0x00000000), stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,0,2): stub!
err:systray:delete_icon invalid tray icon ID specified: 1
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
fixme:shdocvw:ViewObject_SetAdvise (0x1de018)->(1 00000002 0x147db90)
fixme:shdocvw:PersistStreamInit_InitNew (0x1de018)
fixme:shdocvw:WebBrowser_put_RegisterAsBrowser (0x1de018)->(ffffffff)
fixme:shdocvw:WebBrowser_put_RegisterAsDropTarget (0x1de018)->(ffffffff)
fixme:process:IsWow64Process (0xffffffff 0x3d6e88) stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,236,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,18,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,236,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,88,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,166,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,166,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,88,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,62,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,192,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,30,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,224,2): stub!
fixme:win:SetLayeredWindowAttributes (0x2009c,0x00000000,0,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,217,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,159,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,102,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,49,2): stub!
fixme:win:SetLayeredWindowAttributes (0x40030,0x00000000,0,2): stub!
fixme:shdocvw:OleInPlaceObject_InPlaceDeactivate (0x1de018)
fixme:shdocvw:OleInPlaceObject_UIDeactivate (0x1de018)
fixme:shdocvw:OleObject_Close (0x1de018)->(1)
fixme:win:EnumDisplayDevicesW ((null),0,0x34e174,0x00000000), stub!
fixme:keyboard:X11DRV_LoadKeyboardLayout L"00000409", 0000: stub!
X connection to :2.0 broken (explicit kill or server shutdown).
```


I would imagine this is the key to solving my problem.

---

### Post by aktiwers on 2007-11-05
Or try Wine-Doors..  it does it all for you! :)
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

---

### Post by crayment on 2007-11-07
> **aktiwers said:**
> Or try Wine-Doors..  it does it all for you! :)
[http://www.wine-doors.org/wordpress/](http://www.wine-doors.org/wordpress/)

Thanks, i hadn't even heard of wine doors...

Unfortunately it does not help me.  I tried removing everything (wine, steam, hl2, config files) and then reinstalling everything using wine doors.  But when it tries to install hl2 it wants me to locate an installer which i don't have, So i cancel and then install hl2 through steam and im back where i started.

---

