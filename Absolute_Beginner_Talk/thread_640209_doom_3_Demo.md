---
title: "doom 3 Demo"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2007-12-13
I installed the Doom 3 demo on my computer
It runs fine, but the sound is kinda "robotic"
In the terminal it says:
> idAudioHardwareALSA::Write: 4096 frames overflowed and dropped
snd_pcm_writei short write: 1880 out of 2048
snd_pcm_writei short write: 940 out of 1024
snd_pcm_writei short write: 940 out of 1024


Any ideas?

I'm using gutsy

---

### Post by piratesmack on 2007-12-13
I think the sound card is a soundblaster audigy se
or something

---

### Post by CaptainInsaneO on 2007-12-13
Go to config in the game and change your sound to OSS and see what happens.

---

### Post by piratesmack on 2007-12-13
The only sound options the game gives me is:
Surround sound speakers Y/N
and
Volume

however I did find a config file
> 
unbindall

bind "TAB" "_impulse19"

bind "ENTER" "_button2"

bind "ESCAPE" "togglemenu"

bind "SPACE" "_moveup"

bind "/" "_impulse14"

bind "0" "_impulse10"

bind "1" "_impulse0"

bind "2" "_impulse1"

bind "3" "_impulse2"

bind "4" "_impulse3"

bind "5" "_impulse4"

bind "6" "_impulse5"

bind "7" "_impulse6"

bind "8" "_impulse7"

bind "9" "_impulse8"

bind "[" "_impulse15"

bind "\\" "_mlook"

bind "]" "_impulse14"

bind "a" "_moveleft"

bind "c" "_movedown"

bind "d" "_moveright"

bind "f" "_impulse11"

bind "q" "_impulse9"

bind "r" "_impulse13"

bind "s" "_back"

bind "t" "clientMessageMode"

bind "w" "_forward"

bind "y" "clientMessageMode 1"

bind "z" "_zoom"

bind "BACKSPACE" "clientDropWeapon"

bind "PAUSE" "pause"

bind "UPARROW" "_forward"

bind "DOWNARROW" "_back"

bind "LEFTARROW" "_left"

bind "RIGHTARROW" "_right"

bind "ALT" "_strafe"

bind "CTRL" "_attack"

bind "SHIFT" "_speed"

bind "DEL" "_lookdown"

bind "PGDN" "_lookup"

bind "END" "_impulse18"

bind "F1" "_impulse28"

bind "F2" "_impulse29"

bind "F3" "_impulse17"

bind "F5" "savegame quick"

bind "F6" "_impulse20"

bind "F7" "_impulse22"

bind "F9" "loadgame quick"

bind "F12" "screenshot"

bind "MOUSE1" "_attack"

bind "MOUSE2" "_moveup"

bind "MOUSE3" "_zoom"

bind "MWHEELDOWN" "_impulse14"

bind "MWHEELUP" "_impulse15"

seta com_videoRam "256"

seta com_showFPS "0"

seta com_purgeAll "0"

seta com_machineSpec "0"

seta m_strafeSmooth "4"

seta m_smooth "1"

seta m_strafeScale "6.25"

seta m_yaw "0.022"

seta m_pitch "0.022"

seta sensitivity "5"

seta in_toggleZoom "0"

seta in_toggleCrouch "0"

seta in_toggleRun "0"

seta in_alwaysRun "0"

seta in_freeLook "1"

seta in_anglespeedkey "1.5"

seta in_pitchspeed "140"

seta in_yawspeed "140"

seta gui_configServerRate "0"

seta com_guid ""

seta net_master4 ""

seta net_master3 ""

seta net_master2 ""

seta net_master1 ""

seta net_clientMaxRate "16000"

seta net_serverMaxClientRate "16000"

seta gui_filter_idle "0"

seta gui_filter_gameType "0"

seta gui_filter_players "0"

seta gui_filter_password "0"

seta image_downSizeLimit "256"

seta image_ignoreHighQuality "1"

seta image_downSizeBumpLimit "256"

seta image_downSizeSpecularLimit "64"

seta image_downSizeBump "1"

seta image_downSizeSpecular "1"

seta image_useCache "0"

seta image_cacheMegs "20"

seta image_cacheMinK "200"

seta image_usePrecompressedTextures "1"

seta image_useNormalCompression "2"

seta image_useAllFormats "1"

seta image_useCompression "1"

seta image_preload "1"

seta image_roundDown "1"

seta image_forceDownSize "0"

seta image_downSize "1"

seta image_lodbias "0"

seta image_anisotropy "0"

seta image_filter "GL_LINEAR_MIPMAP_LINEAR"

seta r_debugArrowStep "120"

seta r_debugLineWidth "1"

seta r_debugLineDepthTest "0"

seta r_cgFragmentProfile "best"

seta r_cgVertexProfile "best"

seta r_forceLoadImages "0"

seta r_renderer "best"

seta r_brightness "1"

seta r_gamma "1"

seta r_swapInterval "0"

seta r_useIndexBuffers "0"

seta r_customHeight "486"

seta r_customWidth "720"

seta r_fullscreen "0"

seta r_mode "3"

seta r_multiSamples "0"

seta gui_mediumFontLimit "0.60"

seta gui_smallFontLimit "0.30"

seta s_numberOfSpeakers "6"

seta s_doorDistanceAdd "150"

seta s_globalFraction "0.8"

seta s_subFraction "0.75"

seta s_playDefaultSound "1"

seta s_volume_dB "0"

seta s_meterTopTime "2000"

seta s_reverse "0"

seta s_spatializationDecay "2"

seta s_maxSoundsPerShader "1"

seta sys_lang "english"

seta sys_videoRam "0"

seta in_dgamouse "1"

seta in_mouse "1"

seta s_dsp "/dev/dsp"

seta s_driver "best"

seta s_alsa_lib "libasound.so.2"

seta s_alsa_pcm "default"

seta g_decals "1"

seta g_projectileLights "1"

seta g_doubleVision "1"

seta g_muzzleFlash "1"

seta g_spectatorChat "0"

seta mod_validSkins "skins/characters/player/marine_mp;skins/characters/player/marine_mp_green;skins/characters/player/marine_mp_blue;skins/characters/player/marine_mp_red;skins/characters/player/marine_mp_yellow"

seta g_mapCycle "mapcycle"

seta g_voteFlags "0"

seta g_gameReviewPause "10"

seta g_countDown "10"

seta g_password ""

seta g_showBrass "1"

seta g_showProjectilePct "0"

seta g_showHud "1"

seta g_showPlayerShadow "0"

seta g_showcamerainfo "0"

seta g_healthTakeLimit "25"

seta g_healthTakeAmt "5"

seta g_healthTakeTime "5"

seta g_useDynamicProtection "1"

seta g_armorProtectionMP "0.6"

seta g_armorProtection "0.3"

seta g_damageScale "1"

seta g_nightmare "0"

seta g_bloodEffects "1"

seta r_aspectRatio "0"

seta ui_showGun "1"

seta ui_autoReload "1"

seta ui_autoSwitch "1"

seta ui_team "Red"

seta ui_skin "skins/characters/player/marine_mp"

seta ui_name "Player"

seta si_spectators "1"

seta si_usePass "0"

seta si_warmup "0"

seta si_teamDamage "0"

seta si_timeLimit "10"

seta si_fragLimit "10"

seta si_maxPlayers "4"

seta si_map "game/mp/d3dm1"

seta si_gameType "singleplayer"

seta si_name "DOOM Server"



---

### Post by CaptainInsaneO on 2007-12-13
Ok.

Try going into terminal and typing```
killall esd
```

and running the game again.

---

### Post by piratesmack on 2007-12-13
I ran the command and got
> 
esd: no process killed


Then I ran the game and I'm still having the same issue.
Thanks for the help so far
I guess I can try using my onboard audio instead

---

### Post by CaptainInsaneO on 2007-12-13
I'm out of ideas for right now then, sorry. I'm sure someone will be along pretty quick with their two cents, good luck. :popcorn:

---

### Post by piratesmack on 2007-12-13
I ordered the full game online and it should arrive any day now. Do you think I'll have this problem in the full version?

---

### Post by Don1500 on 2007-12-13
I was just about to open the .run file and load Doom 3 when  (in terminal) I got this request from the file.
" It is recommended to run this installation as root.
Please enter the root password, or hit return to continue as user
Password: "

I have never seen this request before and I am not sure if I want to open root.
Is this a normal thing, or is it a trap?:confused:

---

### Post by piratesmack on 2007-12-13
just sudo

> 
sudo sh doom3-linux-1.1.1286-demo.x86.run


EDIT:
Oh nevermind
I don't think it gave me that request
Download it from here to be safe:
[ftp://ftp.idsoftware.com/idstuff/doom3/linux/](ftp://ftp.idsoftware.com/idstuff/doom3/linux/)

---

### Post by CaptainInsaneO on 2007-12-14
The sudo thing is normal, you'll find yourself doing it a lot with Ubuntu. Trust me, it's a safeguard for your protection. :lolflag:

This may be a problem for you with the full version, I've actually never seen your problem before now. I was going to write a howto on running Doom3 on Linux but haven't got around to it. You can find some ok instructions on getting it running on id's website.

---

### Post by kosmo on 2007-12-14
I guess all you have to do is that in 'seta s_driver' change best to oss. Try it.:)

---

### Post by piratesmack on 2007-12-14
I found a fix, I'll post it here in case someone else has this problem

[http://forums.fedoraforum.org/archive/index.php/t-155286.html](http://forums.fedoraforum.org/archive/index.php/t-155286.html)

---

