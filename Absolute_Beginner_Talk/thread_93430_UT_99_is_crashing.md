---
title: "UT 99 is crashing"
date: 2005-11-22
forum: Absolute Beginner Talk
---

### Post by norair on 2005-11-22
So whenever i try to get into the preferences or start and online game UT crashes.  It works fine on the offline game play

the log shows and e4rro, but i dont know what it is trying to tell me:


Log: Log file open, Mon Nov 21 22:39:30 2005
Init: Name subsystem initialized
Init: Version: 436
Init: Compiled: Oct 30 2000 11:53:24
Init: Command line: -log
Init: Base directory: 
Init: Character set: ANSI
Log: Bound to Engine.so
Log: Bound to Core.so
Init: Object subsystem initialized
Init: CPU Speed=1527.480820 MHz
Init: Unreal engine initialized
Log: Bound to SDLDrv.so
Init: Joystick [0] : Unknown Joystick
Init: SDLClient initialized.
Log: Bound to Render.so
Init: Lighting subsystem initialized
Init: Rendering initialized
Log: LoadMap: Entry
Log: Bound to Fire.so
Log: Case-insensitive search: Botpack -> ..\System\BotPack.u
Log: Bound to IpDrv.so
Log: Game class is 'UTIntro'
Log: Level is Level Entry.MyLevel
Log: Bringing Level Entry.MyLevel up for play (0)...
ScriptLog: InitGame: 
ScriptLog: Base Mutator is Entry.Mutator0
Log: Browse: CityIntro.unr?Name=Player?Class=Botpack.TMale2?team=255?skin=SoldierSkins.blkt?Face=SoldierSkins.Othello
Log: LoadMap: CityIntro.unr?Name=Player?Class=Botpack.TMale2?team=255?skin=SoldierSkins.blkt?Face=SoldierSkins.Othello
Log: Case-insensitive search: genfluid -> ..\Textures\GenFluid.utx
Log: Collecting garbage
Log: Purging garbage
Log: -0.0ms Unloading: Package Render
Log: Garbage: objects: 16417->16416; refs: 224677
Log: Game class is 'UTIntro'
Log: Level is Level CityIntro.MyLevel
Log: Bringing Level CityIntro.MyLevel up for play (0)...
ScriptLog: InitGame: ?Name=Player?Class=Botpack.TMale2?team=255?skin=SoldierSkins.blkt?Face=SoldierSkins.Othello
ScriptLog: Base Mutator is CityIntro.Mutator1
Init: Initialized moving brush tracker for Level CityIntro.MyLevel
Log: Created and initialized a new SDL viewport.
Log: Bound to UWeb.so
ScriptLog: Team 255
ScriptLog: Login: Player
Log: Case-insensitive search: SoldierSkins -> ..\Textures\Soldierskins.utx
Log: Possessed PlayerPawn: TMale2 CityIntro.TMale0
Init: Input system initialized for SDLViewport0
Log: Opening SDL viewport.
Log: Bound to SDLSoftDrv.so
Log: Loaded render device class.
Log: Resizing SDL viewport. X: 640 Y: 480
Log: SDLSoftDrv.SDLSoftwareRenderDevice
Log: Bound to ALAudio.so
Init: OpenAL Audio subsystem initialized.
Init: Game engine initialized
Log: Startup time: 1.717394 seconds.
Log: Entering main loop.
Log: URL: Adding default option Name=Player
Log: URL: Adding default option Class=Botpack.TMale2
Log: URL: Adding default option team=255
Log: URL: Adding default option skin=SoldierSkins.blkt
Log: URL: Adding default option Face=SoldierSkins.Othello
Log: Browse: Index.unr?entry?Name=Player?Class=Botpack.TMale2?team=255?skin=SoldierSkins.blkt?Face=SoldierSkins.Othello
Log: Failed; returning to Entry
Init: Shut down moving brush tracker for Level CityIntro.MyLevel
Log: Spawning new actor for Viewport SDLViewport0
ScriptLog: Team 255
ScriptLog: Login: Player
Log: Possessed PlayerPawn: TMale2 Entry.TMale1
ScriptLog: Creating root window: UMenu.UMenuRootWindow
Critical: appError called:
Critical: ReadFile beyond EOF 0+4/0
Exit: Executing UObject::StaticShutdownAfterError
Exit: Executing USDLClient::ShutdownAfterError
Exit: UALAudioSubsystem::ShutdownAfterError
Exit: Executing USDLViewport::ShutdownAfterError
Exit: Exiting.
Uninitialized: Name subsystem shut down
Uninitialized: Log file closed, Mon Nov 21 22:40:03 2005

---

