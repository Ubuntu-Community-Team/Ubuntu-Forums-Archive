---
title: "Watchtower Library 2006 run error"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-04-16
I just installed Watchtower library 2006 with Wine on Ubuntu, and I've been getting an error:

 ```
err:module:import_dll Library ureappshare12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library urectls12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library uresearch12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library urebo12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library ureutil12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library ure12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library mepsappshare12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library mepsctls12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library mepsbrowser12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library mepsgui12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library mepscore12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library wtappshare12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library wtmmutil12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library wtgui12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library wtctls12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library wtutil12u.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library MFC71U.DLL (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library MSVCR71.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:import_dll Library MSVCP71.dll (which is needed by L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"C:\\Program Files\\Watchtower\\Watchtower Library 2006\\e\\wtlib.exe" failed, status c0000135

```

 As far as I've seen, Watchtower works fine on Ubuntu.

 What's going on?

---

### Post by metaphor- on 2007-04-17
did you do a full install option or use the cd one? Keep in mind the 06 cd contains other programs on it.

---

### Post by ZeroWing on 2007-04-17
> **metaphor- said:**
> did you do a full install option or use the cd one? Keep in mind the 06 cd contains other programs on it.

 I did an HD install. Don't know what could be wrong....

---

### Post by zipeppe on 2007-05-11
Hi **brothers**!

try to follow the step-by-step guide provided by metaphor- 

it is working nicely for me (Ubuntu Feisty 7.04), except some "fixme" errors like these:

> 
fixme:font:WineEngCreateFontInstance Untranslated charset 228
fixme:imm:ImmGetDefaultIMEWnd (0x2004c - (nil) 0x1637f8 ): semi-stub
fixme:imm:ImmSetConversionStatus (0x1637f8, 0, 0): stub
fixme:imm:ImmReleaseContext (0x1005a, 0x1637f8): stub
fixme:imm:ImmGetDefaultIMEWnd (0x2004c - 0x1005a 0x1637f8 ): semi-stub
fixme:imm:ImmSetConversionStatus (0x1637f8, 0, 0): stub
fixme:imm:ImmReleaseContext (0x1005a, 0x1637f8): stub
fixme:commdlg:PageSetupDlgW Unicode implementation is not done yet
...
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!
fixme:tooltips:TOOLTIPS_SetFont full redraw needed!


I also have to fix some font problems....
In daily use what I see is a bit slower execution speed compared with the windows installation, 
but it's negligible respect to the advantages using Linux !!

N.B I have successfully installed the *italian* version of wtlib 2006.

Greetings from Firenze, Italy!

---

### Post by WillEyedOney on 2007-09-17
I have been trying to install this for my mother but it fails as soon as the install window opens.
Really annoying

---

### Post by greenhaven on 2007-10-08
Watchtower Library should run fine with the right Wine. 9.14 was the first I found to work without .dll overrides. My Mepis install page will help I hope.

[http://www.users.bigpond.com/telmer/wtinstl.html](http://www.users.bigpond.com/telmer/wtinstl.html)

---

### Post by sketchman on 2007-12-06
I just got the same error trying to install Library 2005. In case you're still stuck, here's how I fixed it.

Open /home/"yourname"/.wine/drive_c/Program Files/Watchtower/MEPSCommon. You'll see a ton of .dll's and one folder. 

Copy every .dll you see to /home/"yourname"/.wine/drive_c/windows/system32.

Then open that one folder and copy the .dll's you see to the same as the first ones.

Run Library as you tried to before, and it should work. It did for me, anyway.

Just a note. I don't use Ubuntu. I did this in Puppy Linux 3.01, but the above has been adjusted to work in Ubuntu, I hope. Oh, and I'm using wine 9.50. No need to go back to 9.14, unless that's just the one you have.

Well, it's meeting time. Hope it works for you.:)

---

