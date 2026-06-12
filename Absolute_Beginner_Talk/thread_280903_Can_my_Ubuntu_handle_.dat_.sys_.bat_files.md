---
title: "Can my Ubuntu handle .dat .sys .bat files?"
date: 2006-10-20
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-10-20
Hi all,

I downloaded an .iso Boot CD file which requires patching in order to have the needed keyboard layout.
Here is what the README says:
> This Patch support following keyboard settings:





 BELGIQUE - belgique clavier AZERTY

 BULGARIAN

 BULGARIAN PHONETIC

 BRAZIL - portuguese keyboard

 BRAZIL EXTENDED - portuguese keyboard

 DENMARK - daenish keyboard

 FRANCAIS - clavier AZERTY

 GERMAN - deutsche Tastatur

 GERMAN2 - deutsche Tastatur mit internatinalen Umlauten

 HEBREW - hebrew keyboard

 ITALY - tastiera italiana

 LATIN AMERICAN - keyboardo espanolo latino americano

 NETHERLANDS - dutch keyboard

 NORVEGIAN - norske keyboard

 POLISH - polska klawiatura

 PORTUGAL - portugese keyboard

 RUSSIA - Russian keyboard

 SWISS FRENCH

 SWISS GERMAN - schweizer deutsches Keyboard

 SLOVENIAN keyboard

 SPANISH - keyboard

 SUOMI - finnish Keyboard

 SWEDISH - swedish Keyboard

 UNITED KINGDOM Keyboard

 UNITED STATES Keyboard (no patch needed)



-----------------------------------------------------------------

Patch Notes:

-----------------------------------------------------------------



Step 1

Extract all three files(KEYB.DAT, KEYB.SYS, PATCH.BAT) to Desktop 



Step 2

Copy "Hiren's.BootCD.8.5.iso" to Desktop



Step 3

Dubble click on "patch.bat"



Step 4

Burn The new file called "XX Patched Hiren's.BootCD.8.5.iso"



Done.



Can I do this under my Ubuntu or do I have to go back to windows? It's these .dat .sys .bat files I'm wondering about.
Thanks for reading.

---

### Post by pay on 2006-10-20
You could try using wine. [www.winehq.org](www.winehq.org)

---

### Post by xyz on 2006-10-20
> **pay said:**
> You could try using wine. [www.winehq.org](www.winehq.org)
I was afraid you'd say that...
Thank you for replying.

---

### Post by caravel on 2006-10-20
A .bat is an M$-DOS batch file, to be run under command.com or cmd.exe, it won't run from a bash console, you may as well go windows to do it, if possible.

---

### Post by Patb on 2006-10-20
Xyz, if you post the contents of patch.bat someone may be able to add a further suggestion.  Cheers, Pat.

---

### Post by xyz on 2006-10-20
Thanks Patb! So here it is...this is WAY over my head:
> @ECHO OFF

set iso=Hiren's.BootCD.8.5

echo.

echo -------------------------------------------------

echo %iso% Custom Keyboard Settings Patch

echo -------------------------------------------------

echo.

if not exist keyb.dat goto error

if not exist keyb.sys goto error

if exist tmpfile1.com del tmpfile1.com

if exist tmpfile.exe del tmpfile.exe

goto start

:error

echo file missing keyb.dat or keyb.sys

echo.

echo View Readme.txt for more information.

echo.

echo.

echo.

echo Press any key to EXIT...

goto AA

:start

if exist "%iso%.iso.iso" ren "%iso%.iso.iso" "%iso%.iso"

if exist "%iso%.iso" goto ask

echo.

echo FILE NOT FOUND "%iso%.iso"

echo.

echo Make sure you have "%iso%.iso" in current directory.

echo.

echo View Readme.txt for more information.

echo.

echo. 

pause

goto end

:ask

echo   A.  BELGIQUE - belgique clavier AZERTY

echo   B.  BULGARIAN 

echo   C.  BULGARIAN PHONETIC

echo   D.  BRAZIL - portuguese keyboard 

echo   E.  BRAZIL EXTENDED - portuguese keyboard

echo   F.  DENMARK - daenish keyboard

echo   G.  FRANCAIS - clavier AZERTY

echo   H.  GERMAN - deutsche Tastatur

echo   I.  GERMAN2 - deutsche Tastatur mit internatinalen Umlauten

echo   J.  HEBREW - hebrew keyboard

echo   K.  ITALY - tastiera italiana

echo   L.  LATIN AMERICAN - keyboardo espanolo latino americano

echo   M.  NETHERLANDS - dutch keyboard

echo   N.  NORVEGIAN - norske keyboard

echo   O.  POLISH - polska klawiatura

echo   P.  PORTUGAL - portugese keyboard

echo   Q.  RUSSIA - Russian keyboard

echo   R.  SWISS FRENCH 

echo   S.  SWISS GERMAN - schweizer deutsches Keyboard

echo   T.  SLOVENIAN keyboard

echo   U.  SPANISH - keyboard

echo   V.  SUOMI - finnish Keyboard

echo   W.  SWEDISH - swedish Keyboard

echo   X.  UNITED KINGDOM Keyboard        Y. UNITED STATES Keyboard      Z. EXIT

copy /y keyb.dat tmpfile1.com>nul

tmpfile1 /N /C:ABCDEFGHIJKLMNOPQRSTUVWXYZ Choose an option : 

if errorlevel 26 goto Z

if errorlevel 25 goto Y

if errorlevel 24 goto X

if errorlevel 23 goto W

if errorlevel 22 goto V

if errorlevel 21 goto U

if errorlevel 20 goto T

if errorlevel 19 goto S

if errorlevel 18 goto R

if errorlevel 17 goto Q

if errorlevel 16 goto P

if errorlevel 15 goto O

if errorlevel 14 goto N

if errorlevel 13 goto M

if errorlevel 12 goto L

if errorlevel 11 goto K

if errorlevel 10 goto J

if errorlevel  9 goto I

if errorlevel  8 goto H

if errorlevel  7 goto G

if errorlevel  6 goto F

if errorlevel  5 goto E

if errorlevel  4 goto D

if errorlevel  3 goto C

if errorlevel  2 goto B

if errorlevel  1 goto A

goto Z

:A

set key=BE 

goto patch

:B

set key=BG 

goto patch

:C

set key=BGP

goto patch

:D

set key=BR 

goto patch

:E

set key=BX 

goto patch

:F

set key=DK 

goto patch

:G

set key=FR 

goto patch

:H

set key=GR 

goto patch

:I

set key=GR2

goto patch

:J

set key=HE 

goto patch

:K

set key=IT 

goto patch

:L

set key=LA 

goto patch

:M

set key=NL 

goto patch

:N

set key=NO 

goto patch

:O

set key=PL 

goto patch

:P

set key=PO 

goto patch

:Q

set key=RU 

goto patch

:R

set key=SF 

goto patch

:S

set key=SG 

goto patch

:T

set key=SL 

goto patch

:U

set key=SP 

goto patch

:V

set key=SU 

goto patch

:W

set key=SV 

goto patch

:X

set key=UK 

goto patch

:Y

set key=US 

goto patch

:patch

echo   FILE   = hbcd.iso>temp.dat

echo   TTL    =%key%Keyboard Patch For %iso% >>temp.dat

echo   SEARCH = 0A 73 65 74 20 6B 65 79 62 6F 61 72 64 3D ?? ?? ?? 0D>>temp.dat

echo   CHANGE = 0A 73 65 74 20 6B 65 79 62 6F 61 72 64 3D "%key%" 0D>>temp.dat

copy /y "%iso%.iso" hbcd.iso>nul

copy /y keyb.sys tmpfile.exe>nul

tmpfile /p temp.dat

del temp.dat

echo !! REMEMBER !!

echo If there is NO ERROR above 

echo.

echo "%key%Patched %iso%.iso"

echo. 

echo.

if not exist "%key%Patched %iso%.iso" ren "hbcd.iso" "%key%Patched %iso%.iso"

set key=

:AA

if exist tmpfile1.com del tmpfile1.com

if exist tmpfile.exe del tmpfile.exe

pause

:Z

if exist tmpfile1.com del tmpfile1.com

if exist tmpfile.exe del tmpfile.exe

exit

---

### Post by Old Pink on 2006-10-20
Are you looking for an alternative to a .bat file, or looking to use a current batch file inside Ubuntu? 

A bat file will most likely never fully work in Ubuntu, but there may well be an alternative way of saving a list of terminal commands. :)

---

### Post by xyz on 2006-10-20
I'm looking to burn that .iso with the patch so that I can choose the appropriate keyboard layout when I'll boot on it...and I'd like to burn it in Ubuntu.
Of course I could easily burn the .iso without the patch but that would create pbms the day I need that CD.
> Step 1

Extract all three files(KEYB.DAT, KEYB.SYS, PATCH.BAT) to Desktop
Step 2

Copy "Hiren's.BootCD.8.5.iso" to Desktop

Step 3

Dubble click on "patch.bat"
Step 4

Burn The new file called "XX Patched Hiren's.BootCD.8.5.iso"


---

### Post by Ben Sprinkle on 2006-10-20
Meh, try shell script. (.sh)
```

echo "hello"

```
Etc..
There is many sites to learn the basic code. :)

---

