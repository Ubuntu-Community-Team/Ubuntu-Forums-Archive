---
title: "[SOLVED] MythTV [Feisty] - Black Screen, no TV..."
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by armin00as on 2007-08-04
Hi!
I'm happily hooked on Feisty for a couple of weeks now and I'm thrilled! I'd love to get rid of using XP for the most part and switch over to Ubuntu, but the last thing that keeps me 'shackled' to XP is watching TV on my PC - which is running like a charm in XP using Snapstream's 'BeyondTV'.

After successfully installing MythTV again now [the first time, I must have made a major mistake with the MySQL settings, and I had to level my Feisty HDD since I could only get restricted access to my files... some dumb permission issue... ](*,) ] I am still not able to watch TV now. All I get is a black screen, for a few seconds, and the the Frontend Main Menu shows again... - Sound familiar? :confused:

I apologize for the rather long post at this point already, but I hope that the exact description of my troubleshooting efforts will be of help for someone to tell me what my problem is with MythTV:

My system specs:  Desktop PC / Dual-boot with Windows XP & Ubunty Feisty (v7.04/Kernel 2.6.20-16-generic) on 3 HDD (XP/Feisty/Storage) / Gigabyte P965-DS3 / NVIDIA 8800GTS / 2GB RAM / Hauppauge PVR-150 w/ MPEG2 Hardware Decoder / M Audio  Revolution-7.1 

For the MythTV Backend/Frontend setup, I closely followed the installation instructions as posted at ([https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop#](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop#))

Moroever, I tried to find help at [https://help.ubuntu.com/community/MythTV/Install/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Troubleshooting), but nothing does seem to come close to my problem. One of the posts in this forums, however,  [http://ubuntuforums.org/showthread.php?t=438640&highlight=MythTV+black+screen](http://ubuntuforums.org/showthread.php?t=438640&highlight=MythTV+black+screen), seems to be similar, but the suggested solutions unfortunately didn't work for me... 

Following some of my settings and other info, which may be helpful to shed some light on the problem.
**MythTV Backend:**
> "Port the server runs on" is the same as the "Port the master server" runs on
> "Port the server shows status on" is different from the above
> Channel frequency selected: "us-cable" [note: I have Comcast Digital Cable]
> Card Type: MPEG-2 encoder card (PVR-x50, PVR-500)
> Default Input: "Tuner"  
> XMLTV listings set up using "Data Direct"

> Backend Status doesn't show any (obvious) errors
> Frontend System /TunerStatus reads "Tuner 1 is not recording"

I can see channel listings, but I don't have a TV picture... After selecting "Life TV", the screen turns black for 20-30 seconds and then goes back to the Main Menu overview.
TV runs perfectly under XP and BeyondTV, which tells me that this problem is not related to Hardware, or TV/Cable signal receiption.

Also, I cannot capture an MPEG file as suggested in MythTV Troubleshooting guide, using the cat /dev/video0>test.mpg command. When I try to play the cpatured file, I get a "The file you tried to play is an empty file" error message. 

> Checked ITVT Troubleshooting Guide for help and possible Firmware Errors... - but this doesn't seem to be the problem (or does it?):

Tried the following:
$ dmesg |grep Initialized
[   17.435997] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
...and also...
$ dmesg | tac | sed -n '/=\ \ END INIT IVTV\ \ =/,/= START INIT IVTV =/p;/= START INIT IVTV =/q' | tac
Result:
```
[   14.313299] ivtv:  ==================== START INIT IVTV ====================
[   14.313301] ivtv:  version 0.10.1 (tagged release) loading
[   14.313302] ivtv:  Linux version: 2.6.20-16-generic SMP mod_unload 586 
[   14.313303] ivtv:  In case of problems please include the debug info between
[   14.313304] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[   14.313305] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[   14.313339] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   14.319781] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 20 (level, low) -> IRQ 21
[   14.319790] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   14.998024] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[   15.216315] ivtv0: Encoder revision: 0x02050032
[   15.216316] ivtv0: Recommended firmware version is 0x02060039.
[   15.281386] tveeprom 0-0050: Hauppauge model 26552, rev F1A3, serial# 9933251
[   15.281388] tveeprom 0-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[   15.281389] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[   15.281390] tveeprom 0-0050: audio processor is CX25843 (idx 37)
[   15.281391] tveeprom 0-0050: decoder processor is CX25843 (idx 30)
[   15.281393] tveeprom 0-0050: has radio, has no IR receiver, has no IR transmitter
[   15.281394] ivtv0: Autodetected Hauppauge WinTV PVR-150
[   15.305630] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   15.305646] tda9887 0-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   15.310144] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   15.325423] NET: Registered protocol family 17
[   15.337869] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[   15.527064] sky2 eth0: Link is up at 100 Mbps, full duplex, flow control both
[   20.339392] cx25840 0-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[   20.464324] wm8775 0-001b: chip found @ 0x36 (ivtv i2c driver #0)
[   20.531670] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   20.531807] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   20.531960] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   20.532048] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   20.532212] ivtv0: Registered device radio0 for encoder radio
[   20.532223] tuner 0-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[   20.933034] ivtv0: Initialized Hauppauge WinTV PVR-150, card #0
[   20.933049] ivtv:  ====================  END INIT IVTV  ====================

```
> I also edited the MySQL configuration, as suggested in the setup instructions by using 'sudo nano /etc/mysql/my.cnf' and and blanking out the bind address to #bind-address= 127.0.0.1 
...which I then changed back (= deleted the '#' again) as it didn't seem to make a difference. -- Or does it??

**My hunch/questions:**
- Could this be a problem of Backend/Frontend not communicating with each other - even though I don't get an error message?
- Or, could this problem be related to IVTV?
- The one file that is stored in my "var/lib/MythTV/recodings" folder is empty and named "nfslockfile.lock" -- is that normal?


All other troubleshooting I could find on the web and especially in this forum relates to older Ubuntu versions...- and that's why I'm putting my problem out on the board, hoping that you guys can help me get MythTV running in Feisty.

*Many thanks* for your help and suggestions!!!
:confused:

---

### Post by NT4usB on 2007-08-04
It's a common problem. I had it when I did my install a year ago. Don't remember what the fix was though... crs is a bitch.
Run the frontend from a terminal:```
mythfrontend -v all
``` and Alt+Tab soon as it launches so you can see the terminal.  Should be some info as to why it won't run. After it crashes, you can copy paste the output. 
Might read these threads in the meantime.[black screen]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+mythtv+%22black+screen%22+playback+-dvd&btnG=Search")

---

### Post by armin00as on 2007-08-04
Thanks for responding, NT4usB!

I'll give it a shot and let you know...
As far as your link is concerned, I'm pretty sure I've read most of them already since I've been searching high and low for solutions before I posted. Also, many of them relate to older Ubuntu versions and may not even apply anymore for v7.04 (which is supposed to be much better with MythTV... Oh well!)

Thanks! :KS

---

### Post by armin00as on 2007-08-04
...mmmh... Interesting!

Here's the output after starting Frontend from the terminal:

```

2007-08-04 21:57:39.008 MSqlQuery: SELECT data FROM settings WHERE value = 'AggressiveSoundcardBuffer' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.008 MSqlQuery: SELECT data FROM settings WHERE value = 'MythControlsVolume' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.009 MSqlQuery: SELECT data FROM settings WHERE value = 'MixerDevice' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.009 MSqlQuery: SELECT data FROM settings WHERE value = 'MixerControl' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.009 MSqlQuery: SELECT data FROM settings WHERE value = 'MasterMixerVolume' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.009 MSqlQuery: SELECT data FROM settings WHERE value = 'PCMMixerVolume' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.010 MSqlQuery: SELECT data FROM settings WHERE value = 'IndividualMuteControl' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.010 MSqlQuery: SELECT data FROM settings WHERE value = 'AllowQuitShutdown' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.010 MSqlQuery: SELECT data FROM settings WHERE value = 'NoPromptOnExit' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.010 MSqlQuery: SELECT data FROM settings WHERE value = 'HaltCommand' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.011 MSqlQuery: SELECT data FROM settings WHERE value = 'LircKeyPressedApp' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.011 MSqlQuery: SELECT data FROM settings WHERE value = 'UseArrowAccels' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.011 MSqlQuery: SELECT data FROM settings WHERE value = 'NetworkControlEnabled' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.011 MSqlQuery: SELECT data FROM settings WHERE value = 'NetworkControlPort' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.012 MSqlQuery: SELECT data FROM settings WHERE value = 'SetupPinCodeRequired' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.014 MSqlQuery: SELECT data FROM settings WHERE value = 'SetupPinCode' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.014 MSqlQuery: SELECT data FROM settings WHERE value = 'MonitorDrives' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.014 MSqlQuery: SELECT data FROM settings WHERE value = 'EnableXbox' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.015 MSqlQuery: SELECT data FROM settings WHERE value = 'LogEnabled';
2007-08-04 21:57:39.015 MSqlQuery: SELECT data FROM settings WHERE value = 'LogPrintLevel' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.015 MSqlQuery: SELECT data FROM settings WHERE value = 'LogCleanEnabled' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.015 MSqlQuery: SELECT data FROM settings WHERE value = 'LogCleanPeriod' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.015 MSqlQuery: SELECT data FROM settings WHERE value = 'LogCleanDays' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.016 MSqlQuery: SELECT data FROM settings WHERE value = 'LogCleanMax' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.016 MSqlQuery: SELECT data FROM settings WHERE value = 'LogMaxCount' AND hostname = 'E6400-UBUNTU';
2007-08-04 21:57:39.016 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillEnabled';
2007-08-04 21:57:39.016 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillDatabasePath';
2007-08-04 21:57:39.016 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillDatabaseArgs';
2007-08-04 21:57:39.017 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillDatabaseLog';
2007-08-04 21:57:39.017 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillPeriod';
2007-08-04 21:57:39.017 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillMinHour';
2007-08-04 21:57:39.017 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillMaxHour';
2007-08-04 21:57:39.017 MSqlQuery: SELECT data FROM settings WHERE value = 'MythFillGrabberSuggestsTime';
2007-08-04 21:57:39.030 MSqlQuery: SELECT data FROM settings WHERE value = 'SchedMoveHigher';
2007-08-04 21:57:39.030 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultStartOffset';
2007-08-04 21:57:39.030 MSqlQuery: SELECT data FROM settings WHERE value = 'DefaultEndOffset';
2007-08-04 21:57:39.030 MSqlQuery: SELECT data FROM settings WHERE value = 'ComplexPriority';
2007-08-04 21:57:39.030 MSqlQuery: SELECT data FROM settings WHERE value = 'PrefInputPriority';
2007-08-04 21:57:39.031 MSqlQuery: SELECT data FROM settings WHERE value = 'OnceRecPriority';
2007-08-04 21:57:39.031 MSqlQuery: SELECT data FROM settings WHERE value = 'HDTVRecPriority';
2007-08-04 21:57:39.031 MSqlQuery: SELECT data FROM settings WHERE value = 'CCRecPriority';
2007-08-04 21:57:39.031 MSqlQuery: SELECT data FROM settings WHERE value = 'SingleRecordRecPriority';
2007-08-04 21:57:39.031 MSqlQuery: SELECT data FROM settings WHERE value = 'OverrideRecordRecPriority';
2007-08-04 21:57:39.032 MSqlQuery: SELECT data FROM settings WHERE value = 'FindOneRecordRecPriority';
2007-08-04 21:57:39.032 MSqlQuery: SELECT data FROM settings WHERE value = 'WeekslotRecordRecPriority';
2007-08-04 21:57:39.032 MSqlQuery: SELECT data FROM settings WHERE value = 'TimeslotRecordRecPriority';
2007-08-04 21:57:39.032 MSqlQuery: SELECT data FROM settings WHERE value = 'ChannelRecordRecPriority';
2007-08-04 21:57:39.032 MSqlQuery: SELECT data FROM settings WHERE value = 'AllRecordRecPriority';
2007-08-04 21:57:39.034 MSqlQuery: SELECT data FROM settings WHERE value = 'Theme' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.034 MSqlQuery: SELECT data FROM settings WHERE value = 'RandomTheme' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.034 MSqlQuery: SELECT data FROM settings WHERE value = 'UseVideoModes' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.034 Total desktop dim: 1280x1024, with 1 screen[s].
2007-08-04 21:57:39.034 MSqlQuery: SELECT data FROM settings WHERE value = 'RunFrontendInWindow' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.034 Running in a window
2007-08-04 21:57:39.034 Using screen 0, 1280x964 at 0,30
2007-08-04 21:57:39.035 MSqlQuery: SELECT data FROM settings WHERE value = 'Style' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.047 Switching to square mode (blue)
2007-08-04 21:57:39.047 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetX' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.047 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiOffsetY' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.047 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.047 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiResolution' AND hostname IS NULL;
2007-08-04 21:57:39.048 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiWidth' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.048 MSqlQuery: SELECT data FROM settings WHERE value = 'GuiHeight' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.048 MSqlQuery: SELECT data FROM settings WHERE value = 'MenuTheme' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.049 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontBig' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.049 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontMedium' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.049 MSqlQuery: SELECT data FROM settings WHERE value = 'QtFontSmall' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.070 MSqlQuery: SELECT data FROM settings WHERE value = 'ThemePainter' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.070 Using the OpenGL painter
2007-08-04 21:57:39.071 MSqlQuery: SELECT data FROM settings WHERE value = 'HideMouseCursor' AND hostname = 'E6400-UBUNTU' ;
[B]mythtv: could not connect to socket
mythtv: No such file or directory[/B]
**lirc_init failed for mythtv, see preceding messages**
2007-08-04 21:57:39.276 /home/armin/.mythtv/joystickmenurc not found.
2007-08-04 21:57:39.276 Joystick disabled.
2007-08-04 21:57:39.291 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'UP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.291 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'DOWN' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.293 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'LEFT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.293 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'RIGHT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.293 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'SELECT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.294 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'ESCAPE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.294 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'MENU' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.294 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'INFO' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.295 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'PAGEUP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.295 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'PAGEDOWN' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.295 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'PREVVIEW' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.295 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'NEXTVIEW' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.296 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'HELP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.296 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = 'EJECT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.296 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = '0' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.296 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = '1' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.297 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = '2' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.297 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = '3' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.297 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = '4' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.298 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = '5' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.298 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = '6' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.298 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = '7' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.298 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = '8' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.299 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Global' AND action = '9' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.325 MSqlQuery: SELECT data FROM settings WHERE value = 'ThemeFontSizeType' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.350 Loading from: /usr/share/mythtv/themes/default/base.xml
2007-08-04 21:57:39.468 MSqlQuery: DELETE FROM settings WHERE value = 'Language' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.469 MSqlQuery: INSERT INTO settings ( value, data, hostname ) VALUES ( 'Language', 'EN', 'E6400-UBUNTU' );
2007-08-04 21:57:39.469 Clearing Settings Cache for 'Language'.
2007-08-04 21:57:39.469 Clearing Settings Cache.
2007-08-04 21:57:39.493 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Reload Theme' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.493 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Main Menu' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.493 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Program Guide' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.494 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Program Finder' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.494 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Manage Recordings / Fix Conflicts' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.494 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Program Recording Priorities' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.494 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Channel Recording Priorities' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.494 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'TV Recording Playback' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.495 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'TV Recording Deletion' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.495 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Live TV' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.495 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Live TV In Guide' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.495 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Manual Record Scheduling' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.495 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Status Screen' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.496 MSqlQuery: SELECT keylist FROM jumppoints WHERE destination = 'Previously Recorded' and hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.496 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGEUP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.496 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGEDOWN' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.496 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'DELETE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.497 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'PLAYBACK' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.497 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'TOGGLERECORD' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.497 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'DAYLEFT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.497 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'DAYRIGHT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.498 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGELEFT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.498 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'PAGERIGHT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.498 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'TOGGLEFAV' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.498 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'NEXTFAV' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.499 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'CHANUPDATE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.499 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'RANKINC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.499 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'RANKDEC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.499 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'UPCOMING' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.500 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'DETAILS' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.500 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'VIEWCARD' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.500 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Frontend' AND action = 'CUSTOMEDIT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.500 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'CLEAROSD' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.500 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'PAUSE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.501 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'DELETE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.501 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SEEKFFWD' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.501 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SEEKRWND' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.501 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'ARBSEEK' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.502 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'CHANNELUP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.502 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'CHANNELDOWN' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.502 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTFAV' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.502 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVCHAN' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.503 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPFFWD' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.503 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPRWND' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.503 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPBKMRK' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.503 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'FFWDSTICKY' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.504 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'RWNDSTICKY' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.504 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEINPUTS' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.504 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SWITCHCARDS' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.504 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SKIPCOMMERCIAL' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.505 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SKIPCOMMBACK' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.505 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPSTART' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.505 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEBROWSE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.505 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLERECORD' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.506 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEFAV' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.506 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'VOLUMEDOWN' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.506 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'VOLUMEUP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.507 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'MUTE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.508 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEPIPMODE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.508 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEPIPWINDOW' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.508 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SWAPPIP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.508 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEASPECT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.509 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLECC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.509 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLETTC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.509 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLESUBTITLE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.509 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLECC608' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.510 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLECC708' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.510 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLETTM' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.510 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTAUDIO_0' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.511 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTAUDIO_1' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.511 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTSUBTITLE_0' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.511 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTSUBTITLE_1' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.511 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC608_0' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.511 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC608_1' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.512 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC608_2' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.512 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC608_3' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.512 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC708_0' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.512 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC708_1' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.512 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC708_2' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.513 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SELECTCC708_3' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.513 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTAUDIO' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.513 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVAUDIO' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.513 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTSUBTITLE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.514 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVSUBTITLE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.514 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTCC608' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.514 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVCC608' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.514 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTCC708' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.514 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'PREVCC708' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.515 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTCC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.515 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'NEXTSCAN' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.515 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'QUEUETRANSCODE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.515 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SPEEDINC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.516 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SPEEDDEC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.516 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'ADJUSTSTRETCH' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.516 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'STRETCHINC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.516 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'STRETCHDEC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.517 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLESTRETCH' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.517 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEAUDIOSYNC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.517 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEPICCONTROLS' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.517 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLECHANCONTROLS' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.517 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLERECCONTROLS' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.518 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLEEDIT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.518 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'CYCLECOMMSKIPMODE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.518 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'GUIDE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.518 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'FINDER' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.519 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'TOGGLESLEEP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.519 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'PLAY' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.519 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPPREV' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.519 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPREC' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.519 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'SIGNALMON' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.520 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'JUMPTODVDROOTMENU' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.520 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Editing' AND action = 'CLEARMAP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.520 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Editing' AND action = 'INVERTMAP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.520 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Editing' AND action = 'LOADCOMMSKIP' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.521 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Editing' AND action = 'NEXTCUT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.521 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Editing' AND action = 'PREVCUT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.521 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Editing' AND action = 'BIGJUMPREW' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.521 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Editing' AND action = 'BIGJUMPFWD' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.522 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Editing' AND action = 'TOGGLEEDIT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.522 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'NEXTPAGE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.522 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'PREVPAGE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.522 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'NEXTSUBPAGE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.526 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'PREVSUBPAGE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.526 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'TOGGLETT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.526 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENURED' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.526 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUGREEN' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.527 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUYELLOW' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.527 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUBLUE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.527 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'MENUWHITE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.527 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'TOGGLEBACKGROUND' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.528 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'Teletext Menu' AND action = 'REVEAL' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.528 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'ITV Menu' AND action = 'MENURED' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.528 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'ITV Menu' AND action = 'MENUGREEN' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.528 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'ITV Menu' AND action = 'MENUYELLOW' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.529 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'ITV Menu' AND action = 'MENUBLUE' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.529 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'ITV Menu' AND action = 'TEXTEXIT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.529 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'ITV Menu' AND action = 'MENUTEXT' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:39.529 Registering Internal as a media playback plugin.
2007-08-04 21:57:39.529 MSqlQuery: DELETE FROM inuseprograms WHERE hostname = 'E6400-UBUNTU' and recusage = 'player' ;
2007-08-04 21:57:39.543 MSqlQuery: SELECT data FROM settings WHERE value = 'Theme' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:40.048 MSqlQuery: SELECT data FROM settings WHERE value = 'EnableXbox' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:40.048 MSqlQuery: SELECT data FROM settings WHERE value = 'idleTimeoutSecs' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:40.048 MSqlQuery: SELECT data FROM settings WHERE value = 'idleTimeoutSecs' AND hostname IS NULL;
2007-08-04 21:57:40.048 MSqlQuery: SELECT data FROM settings WHERE value = 'MonitorDrives' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:40.049 MSqlQuery: SELECT data FROM settings WHERE value = 'NetworkControlEnabled' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:40.049 MSqlQuery: SELECT data FROM settings WHERE value = 'AllowQuitShutdown' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:40.063 MSqlQuery: SELECT data FROM settings WHERE value = 'ThemeFontSizeType' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:40.272 MSqlQuery: SELECT data FROM settings WHERE value = 'Language' AND hostname = 'E6400-UBUNTU' ;
2007-08-04 21:57:40.554 Using NV NPOT texture extension

```


Only problem I can see (with an untrained eye...) is this message in the first half of the output:

> [B]mythtv: could not connect to socket
mythtv: No such file or directory[/B]
**lirc_init failed for mythtv, see preceding messages**

WHY is it a problem not to have lirc installed? I don't need a remote if I run it from my Desktop (sitting right in front of it) - or do I?

What can I do about that... if it's indeed the problem?

Thanks!

---

### Post by NT4usB on 2007-08-04
You'd be surprised how many old problems are also new ones...
I spent more than a month getting MythTV going in Dapper (and learning Linux at the same time.)
Every hurdle along the way required much googling. Many of the solutions were not version, or even distro specific...

---

### Post by NT4usB on 2007-08-04
A quick google finds this:
 make sure the user you run mythtv as has read and write access to
/dev/lircd. Either chmod your /dev/lircd (or whatever it is) to 666 or
chown mythtv to it.

---

### Post by armin00as on 2007-08-04
Yep, I've made that experience (that Ubuntu needs lots of Googling for solutions) already early in the game. But I don't mind so much as I sorta like 'tweaking", and because the Linux community is great (and helpful), and I've found a solution for almost every problem thus far. Except this one maybe... :(


So, will installing lirc fix the problem? What do you think?

Thanks!

---

### Post by armin00as on 2007-08-04
...what about the "could not connect to socket"?

Any ideas??
- Thx!

---

### Post by armin00as on 2007-08-04
Oops, you were faster responding than I was with editing my post... sorry for that :-)

I'll give it a try. - THANKS!

---

### Post by armin00as on 2007-08-04
Kinda embarrassed to ask you this, NT4usB -
But how do I do this; exactly?

> chmod your /dev/lircd (or whatever it is) to 666 or chown mythtv to it.


I'm a real Ubuntu newb and I'm learning while I'm going (and reading/googeling). Haven't had that one yet...
I found out, however, that /dev is owned by *root*, and I don't have write access to it, naturally (with my Admin user).

I figure it's easier to ask you, then starting to Google again... - hope that's OK with you.

Thanks!

---

### Post by NT4usB on 2007-08-04
/dev should be root. No need to mess with that.
Lets not go blindly changing permissions and really mess things up.
Let me have a look around my mythbox and see where lircd should be.
I'm finding some other direction to look as well.

---

### Post by NT4usB on 2007-08-04
Could also be related to IP. 
is mythbackend 127.0.0.1?

look at /etc/mysql/my.cnf
If your machine has a different IP, this line should be commented out like so.```
#bind-address           = 127.0.0.1
```

---

### Post by armin00as on 2007-08-05
My IP was 127.0.0.1, and I did comment it out at first since that was suggested in the installation instructions I followed. 
Then, however, I took the '#' out again, and now it's back in the cnf file. Same result, no picture..

This is getting real frustrating; thanks for your help NT4usB!!

---

### Post by NT4usB on 2007-08-05
Have you checked the permissions on the directory where recordings are being saved? Is it the default location... /media/lib/mythtv or whatever. 
Since it starts recording soon as you start watching live tv, if it can't write to the directory it might bomb...

ps: go back and edit your two long posts. Put brackets with the word *code* '['code']' before all the pasted stuff and brackets */code* '['/code']' after it (without the**''** single quote tics.)
 That will shorten up the posts in case someone else looks at them.

---

### Post by armin00as on 2007-08-05
Makes a lot of sense what you say, NT4usB - Thanks for sharing!!

I finally managed to understand the chmod 666 command and what it's supposed to do, but I guess I f*cked that one up, too:  After I 'chmod 666' it, my mythtv (and also the 'recordings') folder contents are not accessible anymore...

I tried to pick another location to save the recordings - I chose /home/armin/mythtv-recordings - but that doesn't work either. Now I get the good, old and very familiar... 
>  "Could not connect to the master backend server - is it running? Is the IP address set for it in the setup program correct?"   

I think I have enough of this for now; I'll take a break. 
Thanks for your help! Please keep me posted if you have some more good idea, your input is much appreciated!!!

P.S.: After some more Googleing, I realize that it may have to do with me never creating a MythTV partition for the recordings. I found -yet another- document on the MythTV subject which I'll look more into tomorrow... May this also be a reason for MythTV not working for me?

Chances are, I'll start from scratch with MythTV again - or simply stay with XP and BeyondTV (which I would hate). Gotta sleep over it...
 
--THANKS!

---

### Post by NT4usB on 2007-08-05
Permissions, permissions... Gotta love Linux.
Mine are 777 but what do I know...
You must have changed the owner and/or group too, otherwise you could still access them. 
If MythTV can't access them, be sure the owner is listed and has permission in the mysql database. Can you log into mythconverg using your browser?
Are you using the mythtv username to log in? If not, did you search out all your mysql.txt files (there could be more than one) and see that they have the correct user, PW,  and IP.
You don't have to login as mythtv but mysql.txt has to be changed. 
My myth master (login: mythtv) looks like this:```
DBHostName=192.168.0.103
DBUserName=mythtv
DBName=mythconverg
DBPassword=*****
``` and the slave (login: ct), like this:```
DBHostName=192.168.0.103
DBUserName=ct
DBName=mythconverg
DBPassword=*****
```

Don't know about any mythtv partition. First I've heard of that. You do have to have a folder for the recordings and myth has to have permissions to it.

---

### Post by armin00as on 2007-08-05
Hi NT4usB!
Thanks for sticking around...! :)

Well... you seem to have hit the Jackpot, with regard to my issues: I do not login as 'MythTV', or such. The installation guide that I followed (the MythTV guide in the Ubuntu Forums / Community Documentation) didn't seem to be clear enough for me. I can't recall that it said I have to login like that...

Anyways, I found -what seems to be- a much better and more comprehensive installation guide at > [http://mythtv.org/docs/mythtv-HOWTO.html#toc1](http://mythtv.org/docs/mythtv-HOWTO.html#toc1) and I'll try to read up on my problem later.

I've also tried to find any mysql.txt files, but Desktop Search can't find any - strange! I know I could find them the last time I tried to install MythTV. Guess I'll unistall MythTV Frontend/Backend and try again from scratch... - or would you have a better idea (..as you've had a bunch good ones for me already? :-) ) 

Thanks...
A ;-)

---

### Post by NT4usB on 2007-08-05
> **armin00as said:**
> Hi NT4usB!
Thanks for sticking around...! :)

Well... you seem to have hit the Jackpot, with regard to my issues: I do not login as 'MythTV', or such. The installation guide that I followed (the MythTV guide in the Ubuntu Forums / Community Documentation) didn't seem to be clear enough for me. I can't recall that it said I have to login like that...
It's not mandatory you log in as mythtv, as long as your install is configured correctly.
> 
Anyways, I found -what seems to be- a much better and more comprehensive installation guide at  and I'll try to read up on my problem later.
superm1 has a pretty complete install. He's the resident mythtv expert here.
[http://home.eng.iastate.edu/~superm1/](http://home.eng.iastate.edu/~superm1/)
He wrote some comprehensive howtos too.
Seems like you should be able to find something here:
[https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV)
When I added my slave frontend/backend on Edgy, it installed right from the repos. Biggest pita was getting the DVB card working. I have three cards, Card 1, Card 2, and Card 17. That's 14 failed attempts to get the third card going...
> 
I've also tried to find any mysql.txt files, but Desktop Search can't find any - strange! I know I could find them the last time I tried to install MythTV. Guess I'll unistall MythTV Frontend/Backend and try again from scratch... - or would you have a better idea (..as you've had a bunch good ones for me already? :-) ) 

Thanks...
A ;-)
```
sudo updatedb
``````
locate mysql.txt
```

---

### Post by armin00as on 2007-08-05
**Thank, as alway, NT4usB!!!** 

You rock!! :guitar:

Based on your yesterday's excellent advice (and some Googleing, of course :) ), I got the permission problems fixed: I simply deleted, re-created and then cmod + chown'ed the 'mythtv' and 'recordings' folders, and I hope I can now figure out where those 'mysql.txt' files went.

Feel pretty good about getting it all running (...just a hunch, he he!). I'll keep you posted.
- Thanks!

I will post my steps to recovery (??) here... maybe it'll come in handy for some other newb later:
**UPDATE (3:32 PM CDT): ** Still only get a black screen..- but at least the "Cannot connect to the master backend server..." error message is gone. ~ Yeah!!!\\:D/
**UPDATE (3:44 PM CDT): ** Followed your 'updatedb' and 'locate mysql.txt' suggestion. System found files in 3 locations: 
> /usr/share/mythtv/mysql.txt.dist
/usr/share/mythtv/mysql.txt
/etc/mythtv/mysql.txt
I picked the /usr/share...[ ] file and this is the info inside:

> DBHostName=localhost
DBUserName=mythtv
DBName=mythconverg
DBPassword=*******
Looks OK, doesn't it??  Found out that the '/etc/mythtv/mysql.txt' file shows exacty the same info...

---

### Post by armin00as on 2007-08-05
Well... applied the changes and started MythTV Frontend again. 

As far as the results go, I'd like to quote AC/DC, since it seems so appropriate: 
> **"BACK IN BLACK!"**  ....grrrrrrrr..!!!! 

Nottin' changed... still a pitch-black screen. :( 
Guess that means that I'll have to digest some more of the installation manuals for more help... - again.

---

### Post by armin00as on 2007-08-07
-- THAT'S IT, I'M THROWING IN THE TOWEL...!! :mad:

---

### Post by emkamau on 2007-08-15
This thread claims its [SOLVED]! Whats the solution? I'm I missing something here?

I'm having the same 'blackscreen' problem with 64bit Feisty, DirecTV Satellite service and a WinTv-150 capture card.

emk

---

### Post by toocoldimtold on 2007-08-17
my database was corrupt
this worked
[http://www.mythtv.org/pipermail/mythtv-users/2006-October/154172.html](http://www.mythtv.org/pipermail/mythtv-users/2006-October/154172.html)

---

