---
title: "Boot problems plus more"
date: 2006-07-20
forum: Absolute Beginner Talk
---

### Post by paul_magarey on 2006-07-20
I am a newbie to Linux, but have some experience with DOS some years back, so am not totally intimidated.  

I have a Pentium II with 128 MB RAM on which I want to try and instal Dapper Drake.  I have managed to get BIOS to boot from CD: what would appear to be the main menu of the disk comes up OK when I insert the disk & hit enter.  I then select 'Start or Install Ubuntu', which starts running fine and looks good - task completed generally come up OK.  The task bar is moving towards its finish.  

However...."Starting PCMIA services" is the first task to not show an 'OK', but everything else keeps on installing with an 'OK' showing until 'Starting Kernal log' and 'Starting system log' both of which are 'OK', but just after these show on the screen, the screen changes to a mainframe screen and blinks for a bit, then holds still, then goes blank and the screen shuts down.  Shortly after, the CD-ROM drive stops reading and it seems like the whole thing is hung.

A similar thing happens when I re-boot & select 'Start Ubuntu in safe graphics mode', except that it looks more hopeful - the screen has some colour (red) and the mouse appears and is moveable - but after running for about 6 hours, the CD drive eventually stops showing busy permanently and the screen is still blank.

Any advice on how to manage this problem.  I presume it is something to do with the video/screen hardware, but I really wouldn't have a clue.  Version of BIOS I use is 'ROM PCI/ISA BIOS (2A69JM49), Award Software Inc'.  Screen is an 'AST Visron 4L'.  

I'd be very for any tips.

---

### Post by swamytk on 2006-07-20
1. Your Graphics card might have not supported out of box. You have to tweak after installation. Let it be. You start installing with "start ubuntu in safe graphics mode". that will do.
2. Your problem of hanging in this mode is because of poor hardware. I too faced problem with PIII/192MB system. Yours is PII/128MB. You need minimum 256MB to run graphical installation. Let it be no problem. I have managed to install in my system. Here is the HOWTO on it.
[Ubuntu - Dapper Drake installation on Low RAM machine]("http://www.ubuntuforums.org/showthread.php?t=218036")
Just follow the HOWTO. Installation may be slow on PII/PIII system. But once installed it works like charm. All the best.

---

### Post by goodfren on 2006-07-20
Your ram are too low to run live cd, you need the low ram file to install ubuntu.

---

### Post by paul_magarey on 2006-07-20
Thanks for the advice SwamyTK and Goodfren.  Re your advice SwamyTK at [http://www.ubuntuforums.org/showthread.php?t=218036](http://www.ubuntuforums.org/showthread.php?t=218036), Ctrl + Alt + 1 doesn't do anything on my machine other than stop the count-down clock that starts installing Ubuntu automatically.  However, I can get to a 'text mode interface' which has a 'boot:' prompt by pressing the 'Esc' key.  I tried using the commands in your advice, but they always result in a response which is:  'Could not find kernel image:'.  Any further advice?  I'm not sure I'm following your instructions properly...

And Goodfren - any advice where I can get the low ram Ubuntu file?

---

### Post by goodfren on 2006-07-20
At the ubuntu main page, click download, then read each download link avaliable.

Live CD is on top, the once i said is at bottom. Read slowly what the download link said. At first impresion, this low ram file look like for pro to use but not that way, once download it, burn into cd then place your cd in the auto cd boot drive, when prompt, make sure you install by oem feature, is more easier for beginner like me, then just keep yes in the partition matter and you will have your ubuntu run in no time.

This is what i do, so hope you have the same experience.

---

