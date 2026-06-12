---
title: "How to install SW:Empire at war with wine"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by ~~Tito~~ on 2007-07-07
how do I do it?

---

### Post by ~~Tito~~ on 2007-07-07
bump

---

### Post by Qwerty_ on 2007-07-07
[http://appdb.winehq.org/appview.php?iAppId=3164](http://appdb.winehq.org/appview.php?iAppId=3164)

Does not look like it runs.

have you tried wine installer.exe installer is whatever the installer is.

---

### Post by Vague on 2007-07-07
There's a short guide on it's page at winehq: [http://appdb.winehq.org/appview.php?iVersionId=7955](http://appdb.winehq.org/appview.php?iVersionId=7955)

First post there.  Sorry I can't really be of more help.  I've never done it myself.

---

### Post by ~~Tito~~ on 2007-07-07
How do i install the cd. I read the guide but i want to know how to install the cd.

---

### Post by Vague on 2007-07-07
It doesn't work if you cd to the directory on the CD where the installer is and then ```
wine whateverthenameoftheinstalleris.exe
```?

---

### Post by ~~Tito~~ on 2007-07-07
huh??

---

### Post by Vague on 2007-07-07
> **~~Tito~~ said:**
> huh??

In other words ```
cd /mnt/cdrom0
wine Installer.exe
``` adding the appropriate folder to the end of "/mnt/cdrom0" and changing "Installer.exe" to the actual name of the installer.  Is that not working?

---

### Post by ~~Tito~~ on 2007-07-07
So it would be

cd /mnt/cdrom0/EAW_1
wine InstallEAW.exe

?

---

### Post by Vague on 2007-07-07
Sounds reasonable to me, but I've never installed it.  If that's the right directory and installer name, it should work, though, since the guide says just to install it normally at first.

---

### Post by ~~Tito~~ on 2007-07-07
nope didnt work

---

### Post by Vague on 2007-07-07
> **~~Tito~~ said:**
> nope didnt work

Hmm, what did it say?

---

### Post by ~~Tito~~ on 2007-07-07
bash something not a valid directory or something

---

### Post by Vague on 2007-07-07
> **~~Tito~~ said:**
> bash something not a valid directory or something

Yeah, sorry, I should have specified.  If your CD-ROM isn't mounted to /mnt/cdrom0, you'll have to replace that with the actual location.  You can probably figure out what it is pretty easily in your file manager of choice.

---

### Post by ~~Tito~~ on 2007-07-07
which is. (Sorry for being a noob)

---

### Post by ~~Tito~~ on 2007-07-07
bump**

---

### Post by Vague on 2007-07-07
> **~~Tito~~ said:**
> which is. (Sorry for being a noob)

Oh, sorry.  Uh, Nautilus if you're using Ubuntu, Konqueror for Kubuntu.

---

### Post by ~~Tito~~ on 2007-07-07
Ok i checked and mine should be right.

---

### Post by ~~Tito~~ on 2007-07-07
Oh wait it says media/cd0 and its launcheaw.exe

---

### Post by ~~Tito~~ on 2007-07-07
ok i got everything right but is says "bad exe for"

---

### Post by ~~Tito~~ on 2007-07-07
bump***

---

### Post by MyR on 2007-07-07
instructions are here
[http://appdb.winehq.org/appview.php?iVersionId=7955](http://appdb.winehq.org/appview.php?iVersionId=7955)

---

### Post by ~~Tito~~ on 2007-07-07
thats not enogh detail all it says is "Install the game like normal" what is normal"?????

---

### Post by ~~Tito~~ on 2007-07-07
bump

---

### Post by Vague on 2007-07-07
> **~~Tito~~ said:**
> ok i got everything right but is says "bad exe for"

Unmounting and remounting your CD drive might fix that.  If not, I'm not sure, but if I think of something else that might help, I'll let you know.

---

### Post by ~~Tito~~ on 2007-07-07
Ok, do i do this by right click or terminal. If terminal code please?

---

### Post by Vague on 2007-07-07
> **~~Tito~~ said:**
> Ok, do i do this by right click or terminal. If terminal code please?

Actually, you can just eject the CD and then put it back in.

---

### Post by ~~Tito~~ on 2007-07-08
Here is exaclty what the terminal shows

tito@TITOS-LAPTOP:~$ cd /media/cdrom0
tito@TITOS-LAPTOP:/media/cdrom0$ wine launcheaw.exe
wine: could not load L"E:\\launcheaw.exe": Bad EXE format for 
tito@TITOS-LAPTOP:/media/cdrom0$ wine LaunchEAW.exe
wine: could not load L"E:\\LaunchEAW.exe": Bad EXE format for 
tito@TITOS-LAPTOP:/media/cdrom0$

---

### Post by MyR on 2007-07-08
first you need wine 0.9.37 .. available here: [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)
install it
then run
```
wine /media/cd0/GameData/setup.exe
```
and install the game as you would on windows.. i did have some troubles with various windows not coming into focus... so i just used beryl's handy window previews [apparently beryl isn't all just eyecandy].

---

### Post by ~~Tito~~ on 2007-07-08
so i have to downgrade from 0.9.40

---

### Post by MyR on 2007-07-08
you can try it. but it is known to work on 0.9.37

---

### Post by ~~Tito~~ on 2007-07-08
That code doesnt work. I need some help. Here is what it said:

tito@TITOS-LAPTOP:~$ wine /media/cd0/GameData/setup.exe
wine: cannot find '/media/cd0/GameData/setup.exe'
tito@TITOS-LAPTOP:~$ wine /media/cdrom0/LaunchEAW.exe
wine: could not load L"E:\\LaunchEAW.exe": Bad EXE format for 

Why cant i do this. Every one else can. . . . . . . . .

---

### Post by ~~Tito~~ on 2007-07-08
BumP*****

---

### Post by MyR on 2007-07-08
> **~~Tito~~ said:**
> That code doesnt work. I need some help. Here is what it said:

tito@TITOS-LAPTOP:~$ wine /media/cd0/GameData/setup.exe
wine: cannot find '/media/cd0/GameData/setup.exe'
tito@TITOS-LAPTOP:~$ wine /media/cdrom0/LaunchEAW.exe
wine: could not load L"E:\\LaunchEAW.exe": Bad EXE format for 

Why cant i do this. Every one else can. . . . . . . . .

sorry, should be wine /media/cdrom0/GameData/setup.exe

---

### Post by ~~Tito~~ on 2007-07-08
wine: Unhandled page fault on write access to 0x00000000 at address 0x40ce17 (thread 0042), starting debugger...
Unhandled exception: page fault on write access to 0x00000000 in 32-bit code (0x0040ce17).
Register dump:
 CS:0073 SS:007b DS:007b ES:007b FS:0033 GS:003b
 EIP:0040ce17 ESP:0033ff0c EBP:0033ffe8 EFLAGS:00010246(   - 00      -RIZP1)
 EAX:00000000 EBX:7b8ae888 ECX:00000000 EDX:00000000
 ESI:0040ce17 EDI:7ffdf000
Stack dump:
0x0033ff0c:  7b873d5e 7ffdf000 00000000 00000000
0x0033ff1c:  00000000 00000000 00000000 00000000
0x0033ff2c:  ffffffff 7b82ef70 7b843e50 7b8ae888
0x0033ff3c:  7ffdc000 00001000 0033ffe8 ff39ff10
0x0033ff4c:  848d3cd0 00000001 10012a03 00000000
0x0033ff5c:  00000000 00000000 00000000 00000000
Backtrace:
=>1 0x0040ce17 EntryPoint() in setup (0x0033ffe8)
  2 0xb7e9f877 wine_switch_to_stack+0x17() in libwine.so.1 (0x00000000)
0x0040ce17 EntryPoint in setup: addb    %al,0x0(%eax)
Modules:
Module  Address                 Debug info      Name (16 modules)
PE        400000-  41f000       Export          setup
ELF     7b800000-7b927000       Deferred        kernel32<elf>
  \-PE  7b820000-7b927000       \               kernel32
ELF     7bc00000-7bc97000       Deferred        ntdll<elf>
  \-PE  7bc10000-7bc97000       \               ntdll
ELF     7bf00000-7bf03000       Deferred        <wine-loader>
ELF     7efaa000-7efb5000       Deferred        libnss_files.so.2
ELF     7efb5000-7efcc000       Deferred        libnsl.so.1
ELF     7efcc000-7eff3000       Deferred        libm.so.6
ELF     7eff6000-7f000000       Deferred        libnss_nis.so.2
ELF     b7d24000-b7d2d000       Deferred        libnss_compat.so.2
ELF     b7d2e000-b7d32000       Deferred        libdl.so.2
ELF     b7d32000-b7e73000       Deferred        libc.so.6
ELF     b7e74000-b7e8b000       Deferred        libpthread.so.0
ELF     b7e98000-b7fa9000       Export          libwine.so.1
ELF     b7fab000-b7fc6000       Deferred        ld-linux.so.2
Threads:
process  tid      prio (all id:s are in hex)
00000034 (D) E:\GameData\setup.exe
        00000042    0 <==
0000000a 
        0000000c    0
        0000000b    0
00000008 
        00000041    0
        00000040    0
        0000003f    1
        0000003e    0
        0000003d    1
        0000003c    0
        0000003b    1
        0000003a    0
        00000039    1
        00000038    0
        00000037    1
        00000036    0
        00000035    1
        0000002b    0
        00000028    0
        00000027    0
        00000026    0
        00000025    0
        00000024    0
        00000020    0
        0000001f    0
        0000001d    0
        0000001c    1
        0000001a    0
        00000019    0
        00000017    0
        00000016    0
        00000015    1
        00000014    0
        00000013    0
        00000012    0
        00000011    0
        00000010    0
        0000000f    0
        0000000e    0
        0000000d    0
        00000009    0
tito@TITOS-LAPTOP:~$ 

It didnt work.

---

### Post by ~~Tito~~ on 2007-07-08
People, Please Help me!! I want to install that game!

---

### Post by ~~Tito~~ on 2007-07-08
BUMPETY BUMP BUMP BUMP!!!!bump

---

### Post by ~~Tito~~ on 2007-07-08
bump******

---

### Post by BL00dFox on 2007-07-08
Off-topic, but... If you want to play games on Linux, I strongly urge you tget a copy of Cedega. It works like wine only its code is optimized to run games.

Good Luck

---

### Post by ~~Tito~~ on 2007-07-08
I tryed it by getting it off of demonid but i dont know how to get it to install games.:confused::confused:

---

### Post by Vague on 2007-07-08
Well, I did a little bit of looking around, and it seems like you might be running into a problem with the copy protection.  I assume the crack they talk about on winehq addresses this, although they seem to have gotten it to install first without it.  Your problem just seems a lot like other copy protection problems, and the game is copy protected.  Anyway, I'm not exactly sure how to resolve the problem (other than applying the crack they talk about) but that might give you a good direction to start looking in.

---

### Post by ~~Tito~~ on 2007-07-08
More hints please. :)

---

### Post by ~~Tito~~ on 2007-07-08
Bump**

---

### Post by ~~Tito~~ on 2007-07-08
Bump**

---

### Post by ~~Tito~~ on 2007-07-08
Bump***

---

### Post by ~~Tito~~ on 2007-07-08
bump****

---

### Post by ~~Tito~~ on 2007-07-08
Can someone help me??
Bump***

---

### Post by ~~Tito~~ on 2007-07-08
Bump***

---

### Post by ~~Tito~~ on 2007-07-08
bump

---

### Post by SirNuke on 2007-08-20
In case you are still interested, I wrote up detailed instructions on [Petroglyph's forums](http://www.petroglyphgames.com/forums/index.php?showtopic=4682).

Your problems are likely due to EaW's copy protection.  You will need a no-cd patch in order to get it to run on Windows.  Due to legal issues, I cannot post specifics here (as noted on the Petroglyph post).  PM or email me if you want discuss the no-cd further.

For any other questions, I have gotten both EaW and FoC working correctly, so I can try to answer them.

---

### Post by ~~Tito~~ on 2007-08-20
Awesome thanks I will pm you later. Its just that I am not on my computer I am at my dads on his windows one. For some reason though I feel no difference in using windows after 3 months???

---

