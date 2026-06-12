---
title: "I know I posted but it's not here anymore?"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by HellionDarkLord on 2007-04-22
WHy is it that I can post something and then it disappears?  This will be my third attempt.  This is what I wrote the second time:

.................................................................................

I just played Delta Force Black Hawk down for the first time on Ubuntu this morning.  It took all night to get it running and I only wasted all that time because I thought it would be fun.

Then when I actually started playing the game and had everything figured out and working properly.  (even the graphics)  I started seeing things that I'd never seen before with the explosions and shrapnel.  

First thing I noticed was that if a jeep with a 50 cal mounted on it were blown up,  the 50 cal blew up into the air.  Cool huh?  Never did it before under windows, and the 50 cal was even usable in windows.  The next thing I noticed was when I blew up a ship with satchel charges parts of the ship flew into the air and landed in the water.   When the pieces hit the water they flipped and rolled changing direction like they would have done in real life.

The fire from the 50 cal and mini don't blind you as much when you are using them as they did in Windows, and  explosions themselves are a lot more fun.

I think that this is all due somehow to the 3d engines in wine.  I do not have directx for wine.

There are some things I haven't worked out yet...

There  is a no-CD crack which is essential to running DFBHD because it is (as far as I can tell) impossible to hard-link /media/cdrom to f: and DFBHD thinks that you do not have a CD in the drive.

I haven't yet been able to upgrade to Team Saber yet, and I don't know how to try and proceed.  The firearms in team Saber are available without installing the upgrade, but some are limited to a simple cross-hairs in the center of the screen and do not display a picture of the weapon.  The G3 does not have iron sights and does not show anything for a sight if the secondary fire button is used, but it will still fire.  (kinda fun for a little while)

Last, but decidedly not least, the textures need to be set st the lowest setting in the options menu or there will be patches of ground that display black and white characters and rainbows.  I do not know why this is.  In a terminal, you get an echo saying :

~$:cd ~/.wine/drive_c/Program\ Files/NovaLogic/Delta\ Force\ Black\ Hawk\ Down
~/.wine/drive_c/Program Files/NovaLogic/Delta Force Black Hawk Down$ wine dfbhd
fixme:win:WIN_CreateWindowEx Parent is HWND_MESSAGE
fixme:d3d:IWineD3DDeviceImpl_GetAvailableTextureMem (0x193880) : stub, simulating 64MB for now, returning 64MB left
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d8:ValidatePixelShader (0x12a3668 (nil) 0 (nil)): stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x193880) : stub
fixme:d3d:IWineD3DStateBlockImpl_Release Releasing primary stateblock

This is my very first attempt at using Wine.  I have no Idea what the fixme stuff is all about.

Could someone please explain???

Thank you 

Hellion DarkLord of Darker Enter Prize

---

### Post by n3tfury on 2007-04-22
[http://ubuntuforums.org/showthread.php?t=419055](http://ubuntuforums.org/showthread.php?t=419055)

---

