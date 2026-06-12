---
title: "Amarok Troubles"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by mitchbones on 2006-12-05
I am in the second day of using Ubuntu (loving it so far), and I have heard tons of things about Amarok. I dled it using the "Add/Remove Programs" and I *may* have dled the kde librarys. I did the aptitude install earlier but I don't belive it did anything. When I run it in the terminal I get this.

> mitch@mitch-desktop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokap p.
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
amarok: BEGIN: App::App()
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
amarok: BEGIN: void App::fixHyperThreading()
amarok:     Workaround not enabled
amarok: END__: void App::fixHyperThreading() - Took 0.0011s
amarok: END__: App::App() - Took 0.92s
amarok: BEGIN: void App::continueInit()
amarok: BEGIN: EngineBase* EngineController::loadEngine(const QString&)
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-ve rsion] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] ! = 'void-engine' and [X-KDE-Amarok-rank] > 0
amarok:     [PluginManager] Plugin trader constraint: [X-KDE-Amarok-framework-ve rsion] == 27 and [X-KDE-Amarok-plugintype] == 'engine' and [X-KDE-Amarok-name] = = 'void-engine' and [X-KDE-Amarok-rank] > 0
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
amarok:     X-KDE-Amarok-framework-version: 27
amarok:
amarok: END__: EngineBase* EngineController::loadEngine(const QString&) - Took 0 .025s
amarok: BEGIN: CollectionDB::CollectionDB()
amarok: BEGIN: void CollectionDB::initialize()
amarok:       [ThreadWeaver] Creating pthread key, exit value is 0
amarok: BEGIN: SqliteConnection::SqliteConnection(const SqliteConfig*)
amarok: END__: SqliteConnection::SqliteConnection(const SqliteConfig*) - Took 0. 0014s
amarok:       [CollectionDB] Updating DEVICES table
amarok: END__: void CollectionDB::initialize() - Took 0.062s
amarok:     [CollectionDB] INotify not available, using QTimer!
amarok: END__: CollectionDB::CollectionDB() - Took 0.072s
amarok: BEGIN: void CollectionDB::checkDatabase()
amarok:     [CollectionDB] Beginning database update
amarok:     [CollectionDB] Different database stats version detected! Stats tabl e will be updated or rebuilt.
amarok:     [CollectionDB] [ERROR!] Database statistics version too new for this  version of Amarok. Quitting...
amarok: BEGIN: virtual CollectionDB::~CollectionDB()
amarok:       [CollectionDB] Running VACUUM
amarok: END__: virtual CollectionDB::~CollectionDB() - Took 0.07s
amarok:     [virtual EngineController::~EngineController()]


Thanks!

---

### Post by adamkane on 2006-12-05
You may need to install an engine. I would install libxine, and try again.

Try this:
```

sudo apt-get install libxine

```

If that doesn't work, I would re-install amarok:
```

sudo apt-get remove amarok libxine
sudo apt-get install amarok libxine

```

---

### Post by mitchbones on 2006-12-05
anything I type with libxine returns "E: Couldn't find package libxine"

I looked at Synpaptic and It shows that I have them.

---

### Post by adamkane on 2006-12-05
Oops...

Try this:
```

sudo apt-get install libxine1c2 libxine-extracodecs

```Then:
```

sudo apt-get remove amarok libxine1c2 libxine-extracodecs
sudo apt-get install amarok libxine1c2 libxine-extracodecs

```

---

### Post by mitchbones on 2006-12-05
It didn't fix it :( I vaguly rember starting it yesterday but quiting out of it, when it asked to set up everything (settings,etc)

---

### Post by adamkane on 2006-12-05
Basically your amarok is hosed.

You can try this:
[http://www.groupsrv.com/linux/about30483.html](http://www.groupsrv.com/linux/about30483.html)
```

amaroK --engine xine

```Also this:
[http://amarok.kde.org/forum/index.php?topic=12828.msg14555](http://amarok.kde.org/forum/index.php?topic=12828.msg14555)
Delete your amarok database:
```

rm ~/.kde/share/apps/amarok/collection.db

```Also you can try installing an earlier version of amarok, removing it, then installing the newer version.

Last resort is an Ubuntu re-install.

---

### Post by mitchbones on 2006-12-05
> **adamkane said:**
> 
```

rm ~/.kde/share/apps/amarok/collection.db

```l.

This worked!!! Thanks for all your help adam, much appreciated.

---

### Post by sysko on 2007-03-09
After a fresh install of Ubuntu 6.10 I installed amarok with:

```
sudo apt-get install amarok
```

and I ended up with the same error as you did.

I little 
```
rm -Rf ~/.kde/
``` 
fixed the issue for me. I am running Gnome and I had no valuable data in that .kde/ directory. Like I said I was running on a fresh install. Never the less, this was how I solved that error.


Sysko

---

### Post by Steve H on 2007-04-22
> **adamkane said:**
> 
```

rm ~/.kde/share/apps/amarok/collection.db

```

That worked brilliantly, Thanks. I´ve been having all sorts of problems with KDE apps running under Gnome since the Feisty upgrade. So I reinstalled all the KDE stuff (libs, apps etc), and then i started getting Amarok probs. It is all sorted after following your instruction above.

Thanks again for the help.

---

