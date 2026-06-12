---
title: "Powerbook G4 pbbuttonsd Keyboard problem"
date: 2016-11-26
forum: Apple Hardware Users
---

### Post by monkeyisland on 2016-11-26
I successfully installed Ubuntu Mate 16.04. LTS on my Powerbook G4. 
Pbbuttonsd is installed Screen Dimming, Sound, Ecect Button work.
The backlight of the keyboard cant turn on or off or dimming.

here is my /etc/pbbuttonsd.cnf
                                                                                # Configuration file for pbbuttonsd >= version 0.8.0
# For complete list of options please see pbbuttonsd.cnf man-page.
# For description of the file format please see
#    [http://freedesktop.org/Standards/desktop-entry-spec](http://freedesktop.org/Standards/desktop-entry-spec).


[SYSTEM]
#userallowed=paranoid
CmdTimeout=8
autorescan=false


[MODULE DISPLAY]
#LCD_Brightness=90
LCD_FadingSpeed=448
LCD_AutoadjMode=linear
LCD_AutoadjParm_onBattery=0,1,94,54
LCD_AutoadjParm_onAC=0,1,94,100
KBD_Brightness=100
KBD_OnBrightness=100
KBD_FadingSpeed=0
#KBD_AutoadjMode=linear
KBD_AutoadjParm_onBattery=10,100,28,0
KBD_AutoadjParm_onAC=10,100,28,0
Device_FB=/dev/fb0
UseFBBlank=false
DimFullyDark=false
CRT_MirrorKey=65 + ctrl
[MODULE CDROM]
Device=/dev/cdrom
EjectCDKey=161
EjectCDKeyDelay=0
[MODULE MIXER OSS]
Device=/dev/mixer
Channels=volume, speaker
[MODULE MIXER ALSA]
Card=default
Channels=Master, PC Speaker
[MODULE PMAC]
TPModeUpKey=225 + alt


Second Problem i am German so i use the German Keymap all is good except the third row of a keyboard. 
So email Euro symbol.
i need a easy solve to switch the right Apple Key in "AltGR"  in Windows ?
I testes the various keyboards in the preferences but i cant activate the third row of the keyboard.
):P

---

### Post by ernsteiswuerfel on 2016-12-07
Can't help you with your keyboard dimming problen, 'cause it works flawlessly on my PowerBook 5,6 and 5,8. I use the Function-Key + F8/F9. This is the default behavious of my PBs, I don't need a config file. I had a PowerBook 5,4 before where keyboard dimming didn't work, but this was some kind of hardware fault.

I can help you with the 2nd problem. Have had the same annoying problem too and worked it out. ;)

On the desktop use the menu, goto Sytem->Einstellungen->Geräte->Tastatus. I used the following options:
Belegungen: "Deutsch Deutsch (Macintosh)"
Tastaturmodell: Generische PC-Tastatur mit 105 Tasten (Intl)
Optionen: Taste zum Wechsel in die dritte Tastaturebene - Rechte Windows Taste (whichs is the right Apple-Button next to the space bar)

On my PBs the @-sign is printed on the the letter L-key where I can reach it now via right Apple + L.
~ is right Apple + +
| is right Apple + <

---

