---
title: "Sound card installed ,, sound preferences test sound works, though CANT hear wav/mp3s"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by alx.joom on 2007-11-01
Hello , i have these 2 sound cards installed 

lspci | grep audio
gives :
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
02:02.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)

and
cat /proc/asound/cards
gives

 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with ALC650E at irq 23
 1 [Live           ]: EMU10K1 - SBLive 5.1 [SB0060]
                      SBLive 5.1 [SB0060] (rev.7, serial:0x80611102) at 0x9000, irq 21
 2 [UART           ]: MPU-401 UART - MPU-401 UART
                      MPU-401 UART at 0x330, irq 10



with my speakers connected in Creative Sb live card. While on System>preferences>sound>devices
i can hear the test sound in sound events and music and movies category (when i select multichannel playback option and the Sblive sound card for device) ,
i cant hear any mp3s or wav files from audacious or from the terminal

The problem started after installing some applications (till then sound worked just fine).

Any ideas on what i should look for? I ve read so many posts over the internet and still cant figure it out...

---

### Post by haldean on 2007-11-01
Does it work when you hook your speakers up to the Intel sound card?

---

