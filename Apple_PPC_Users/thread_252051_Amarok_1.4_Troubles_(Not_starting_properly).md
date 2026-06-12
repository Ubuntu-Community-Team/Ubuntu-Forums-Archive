---
title: "Amarok 1.4 Troubles (Not starting properly)"
date: 2006-09-06
forum: Apple PPC Users
---

### Post by TDave on 2006-09-06
Hi

Just recently reinstalled Kubuntu 6.06 on my PowerBook G4 15" after a hard drive failure.

Installation went smoothly and no problems installing extra codecs and the like for Multimedia playback.

The only negative is that amarok appears to be broken.

By this I mean that I can go to start the application, it goes for startup and then seems to stop. No error messages, no system tray, no amarok window. Nothing.
If I look in SysGuard at the running processes I can clearly see that amarok and amarokapp are both running (as would be expected) but there is no audio playback occurring and, like I say, no visual clue that the program is running.

I have tried removing amarok, cleaning the apt cache, and reinstalling, so far without success.

Where else can I look to try and find any more information that would help, or can anyone reccommend some way of fixing the problem?

Many thanks

---

### Post by ntwrkguy on 2006-09-06
I am having the same problem!

---

### Post by Doobie9 on 2006-09-10
I am having problems opening Amarok as well. I typed in amarokapp in a terminal and this is the message I got:

>  amarok: END__: App::App() - Took 0.033s
amarok: BEGIN: void App::continueInit()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 26 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] != 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-version] == 26 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] == 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Trying to load: libamarok_void-engine_plugin
amarok:
amarok:     PluginManager Service Info:
amarok:     ---------------------------
amarok:     name                          : <no engine>
amarok:     library                       : libamarok_void-engine_plugin
amarok:     desktopEntryPath              : amarok_void-engine_plugin.desktop
amarok:     X-KDE-Amarok-plugintype       : engine
amarok:     X-KDE-Amarok-name             : void-engine
amarok:     X-KDE-Amarok-authors          : (Max Howell,Mark Kretschmann)
amarok:     X-KDE-Amarok-rank             : 1
amarok:     X-KDE-Amarok-version          : 1
amarok:     X-KDE-Amarok-framework-version: 26
amarok:
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0.28s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0.007s
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: podcastchannels
amarok:       [CollectionDB] [ERROR!] on query: SELECT COUNT( url ) 
 After that, this repeats forever and ever until I close the terminal window:

> 
FROM podcastchannels LIMIT 1 OFFSET 0;
amarok:       [CollectionDB] [ERROR!] [virtual QStringList SqliteConnection::query(const QString&)]  sqlite3_compile error:
amarok:       [CollectionDB] [ERROR!] no such table: podcastchannels
 
And when I run top in a console it tells me that amarokapp is always running, and it's taking up as much cpu as possible (So that the computer is always using 100% cpu, which can slow kde down to a crawl). I've tried killing the app and restarting but I get the same unending error message. Even after an apt-clean and reinstall! I'm so frustrated.

Please help us, this is an awful problem. ](*,)

---

### Post by Doobie9 on 2006-09-10
UPDATE: I have since fixed this problem by updating to 1.4.3 from outside the official Ubuntu repositories. Apprently this is a bug with the 1.4.2 version of amarok.

Here is where you go, just follow their instructions: [http://kubuntu.org/announcements/amarok-1.4.3.php](http://kubuntu.org/announcements/amarok-1.4.3.php)

It's a bug. At least that was what caused my problem. Hope it fixes yours :).

---

### Post by TDave on 2006-09-10
Great!

Problem solved! Thanks for your help.

---

