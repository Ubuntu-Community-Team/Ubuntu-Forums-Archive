---
title: "WINE doesn't seme to save my WoW settings on re-entry"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by ruadatha on 2007-10-09
OK, i've had a look around, an can't seem to find anything. I recently switched to Ubuntu, which is working fine. now i have WoW installed, works fine, it works everytime (except voice chat, but i can hear that.. not sure why, still working on it though)

My problem is that when i enter wow, i always get the eula,etc etc, and have to reconfigure it every single time. even after exiting the game, the Config.wtf file has my settings in there, but when i start wow back up again, it's back to absolute defaults, and it's beginning to get a lil annoying. 

basically, i've so far set the file to execute/read only using chmod, have deleted the contents of the WTF directory and tried again, /console reloadui (think that was the command) and it's still doing the same thing. So i chmod'd to 777 in the hopes that it would fix this, same deal. 


that's about it so far, im still getting used to it all. WoW patches fine, plays fine, there's no registry tweaks applied, followed the main entry for installing WoW under WINE. so im really not sure, but would honestly appreciate any and all information anyone could throw out please.


thanks in advance

---

### Post by Faud on 2007-10-09
Hello. First questions first =)

What version of Wine are you using...I can post now that WoW is down for maintenace  =P

---

### Post by ruadatha on 2007-10-09
according to synaptic, 0.9.46, i also have the wine-dev pakage installed as well

---

### Post by Faud on 2007-10-09
Ok, when you are going to edit your config.wtf are there two copies or only one ?

Also, when you shut down the game does it shut down properly ? as in you can log off to the character screen and then the start screen and then quit to the wine desktop ?

Please let me know what you are trying to keep the same ? Something with an addon like Bongos or is it something like your ingame screen resouliton.

For you voice chat I have gotten mine to work fine with the ALSA drivers and a wee bit of tweaking with the ALSAmixer

---

### Post by ruadatha on 2007-10-09
ok, easiest way to answer i think is to post the contents of my Config.wtf file (will be at bottom)

i am having to re-accept the EULA (both, i have bc) every time, re-enable all addons, recustomise UI.
can't change advanced graphics features, as that requires game restart, which in turn drops the config file again

no crashes on exit, can do it fine every time i exit.. sometimes hangs and i have to kill process and relaunch, but that's ok, still better average than windows.

Oh, it may (or may not) help to know that i have tested with a fresh install from files, and also copying the entire directory from my windows install (dualboot xp/ubuntu)

oh, and while game is running, there is a Config.wtf file, and a Config.wtf~ file, not sure if that's the temp file while open or not..


heres the config file contents

SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
SET locale "enUS"
SET coresDetected "4"
SET processAffinityMask "3"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "1024x768"
SET gxRefresh "60"
SET gxCursor "0"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "32"
SET farclip "417"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET accountName "<snip>"
SET movie "0"
SET expansionMovie "0"
SET checkAddonVersion "0"
SET mouseSpeed "1"
SET Gamma "1.000000"
SET lastCharacterIndex "2"
SET readTOS "1"
SET readEULA "1"
SET profanityFilter "0"
SET spamFilter "0"
SET showToolsUI "0"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET Sound_OutputDriverName "dmix:0"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.40000000596046"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "1"
SET Sound_MusicVolume "0.40000000596046"
SET Sound_AmbienceVolume "0.60000002384186"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "2"
SET realmName "Nagrand"
SET gameTip "2"
SET ChatBubblesParty "1"
SET OutboundChatVolume "2"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET EnableVoiceChat "1"
SET PushToTalkButton "NUMPADMULTIPLY"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET uiScale "1"
SET deselectOnClick "0"
SET assistAttack "1"
SET ShowTargetCastbar "1"
SET ShowVKeyCastbar "1"
SET UnitNameOwn "1"
SET UnitNameNPC "1"
SET autoSelfCast "1"
SET guildMemberNotify "1"

hope that helps

---

### Post by Faud on 2007-10-09
delete Config.wtf~

---

### Post by Faud on 2007-10-09
and to give you an idea; here is a copy of my config.wtf

```

SET locale "enUS"
SET hwDetect "0"
SET gxColorBits "24"
SET gxDepthBits "24"
SET gxResolution "800x600"
SET gxRefresh "60"
SET gxMultisampleQuality "0.000000"
SET gxFixLag "0"
SET fullAlpha "1"
SET SmallCull "0.040000"
SET DistCull "500.000000"
SET trilinear "1"
SET frillDensity "24"
SET farclip "500.000000"
SET specular "1"
SET pixelShaders "1"
SET particleDensity "1.000000"
SET unitDrawDist "300.000000"
SET movie "0"
SET expansionMovie "0"
SET readTOS "1"
SET readEULA "1"
SET showToolsUI "1"
SET realmList "us.logon.worldofwarcraft.com"
SET patchlist "us.version.worldofwarcraft.com"
SET realmName "Thrall"
SET gameTip "93"
SET gxApi "opengl"
SET ffxGlow "0"
SET Gamma "1.000000"
SET accountName "MiniNightMana"
SET mouseSpeed "1"
SET MusicVolume "0.40000000596046"
SET SoundVolume "1"
SET MasterVolume "0.80000003576279"
SET MasterSoundEffects "0"
SET EnableMusic "0"
SET EmoteSounds "0"
SET cameraYawMoveSpeed "180"
SET cameraYawSmoothSpeed "180"
SET cameraDistanceMaxFactor "1"
SET ChatBubbles "0"
SET autoDismountFlying "1"
SET SoundListenerAtCharacter "0"
SET AmbienceVolume "0.60000002384186"
SET deselectOnClick "0"
SET ShowTargetCastbar "1"
SET ShowVKeyCastbar "1"
SET UnitNamePlayer "0"
SET minimapZoom "0"
SET minimapInsideZoom "0"
SET profanityFilter "0"
SET timingTestError "0"
SET scriptErrors "1"
SET readScanning "-1"
SET readContest "-1"
SET coresDetected "2"
SET checkAddonVersion "0"
SET Sound_OutputDriverName "dmix:0"
SET ChatMusicVolume "0.30000001192093"
SET ChatSoundVolume "0.30000001192093"
SET ChatAmbienceVolume "0.30000001192093"
SET Sound_MasterVolume "1"
SET Sound_SFXVolume "0"
SET Sound_MusicVolume "0"
SET Sound_AmbienceVolume "0"
SET OutboundChatVolume "2.5"
SET InboundChatVolume "1"
SET VoiceActivationSensitivity "0.40000003576279"
SET cameraView "3"
SET guildMemberNotify "1"
SET Sound_VoiceChatInputDriverName "dsnoop:0"
SET Sound_VoiceChatOutputDriverName "dmix:0"
SET TargetNearestDistance "52.000000"
SET Sound_EnableMusic "0"
SET Sound_EnableErrorSpeech "0"
SET Sound_EnableEmoteSounds "0"
SET PushToTalkButton "NUMPADMINUS"
SET readTerminationWithoutNotice "-1"
SET autojoinPartyVoice "0"
SET lastCharacterIndex "6"
SET Sound_EnableAllSound "0"

```

---

### Post by ruadatha on 2007-10-09
sorry, that Config.wtf~ is only there while playing the game, my bad.

also, the main Config.wtf file actually saves all info.. until i go intot he game again, at which point it creates the Config.wtf~ file, and i have to re-agree to the EULA etc

---

### Post by ruadatha on 2007-10-09
oh, and ty for th tip on ALSAmixer.. turns out i had my input sections set to mic, not front mic, that should fix it i think :D

---

### Post by Faud on 2007-10-09
ok brb Im gonna try and see if it will let me online and I'll see if my comp creates a 2nd config.wtf. I remember when i was first messing with WoW and Wine I had 2nd file of something, I want to say it was the config.wtf and it was messing stuff up

---

### Post by Faud on 2007-10-09
Yea, my attempt to log on doesnt give me a 2nd copy of that file

---

### Post by ruadatha on 2007-10-12
so do i delete this file while the games going? cause it's not there when it's not going, and im not sure if it will default back to the other file or not

---

### Post by ruadatha on 2007-10-14
bump

---

### Post by 001100 on 2007-10-14
check the settings in wine make sure wow has permission to read and write or check wine and make sure it has permission to read and wirt

---

### Post by Ignotser on 2008-07-13
BUMP, how do you check the read/write permissions?

---

### Post by Frippera on 2008-07-13
Check my answer here: [http://ubuntuforums.org/showthread.php?p=5376076#post5376076](http://ubuntuforums.org/showthread.php?p=5376076#post5376076)

Maybe that can help.

---

