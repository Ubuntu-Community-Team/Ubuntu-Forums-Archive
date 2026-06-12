---
title: "Programs start up when not on list"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by Gibran on 2007-03-31
Hello. I had a program set up to load on startup (uTorrent through Wine), it had some issues so I removed it from the startup list and added another one (Azureus) which I didn't like much so I also removed it and then I finally added the one I needed (KTorrent) and when I restarted all 3 loaded on startup! I made sure the other two were no longer on the list but they are still loading. Is there any other way to control startup programs other than the Sessions window?

---

### Post by berylator on 2007-03-31
I have a similar problem here; I have several programs that start up after booting although they are not on the list. However, I have **never** added them! The programs are: Openoffice Word Processor / my Home Folder / a Terminal / gaim messenger.

Could it be that Ubuntu somehow loads a saved session every time I boot? I don't believe this since not all the programs are always being started.

Does someone have an idea what this could be? I would appreciate it.


thanks

berylator

PS: Hello Ubuntu Forums, glad to be here :guitar:

---

### Post by zvacet on 2007-04-01
This is very primitive procedure but it works.Delete torrents you don´t use and be sure that their folders are deleted too.Folders are in your home directory but hidden.Home folder>view>show hidden folders.

---

### Post by Gibran on 2007-04-01
I don't see any torrents on the folder... I uninstalled azureus, but I have no idea how to uninstall uTorrent from Wine (I don't want to delete the .exe as it may come in handy if I ever use my Windows partition again). Any insights on how I could uninstall it?

---

### Post by Clay_Banger on 2007-04-01
when you log off are they all still running? by default the session manager will load the programs that you had running when you logged off, when you log on.

try closing all three of them, make sure they are not in the tray on the bottom right, and reboot.

---

### Post by Gibran on 2007-04-02
I already tried closing everything before startup, and now, interestingly, none of the programs boot up properly; kTorrent is stalling the computer for around 5 minutes and then crashes, and Azureus closes as soon as I open it, just flashes on screen.... Does Ubuntu have a System Restore???

---

### Post by Gibran on 2007-04-02
To further expand the Ktorrent issue: > The application KTorrent crashed and caused the signal 6 (SIGABRT)

There is a tab that says "Backtrace" on the dialog, but it says

 > This backtrace appears to be of no use.
This is probably because your packages are built in a way which prevents creation of proper backtraces, or the stack frame was seriously corrupted in the crash.

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".

I used BitTorrent for testing and it worked perfectly, but it has an awful interface. Other apps work with no issues (I'm Running 6.10 from the Ultimate Edition build)

---

### Post by zvacet on 2007-04-02
In your home hidden folders it is folder named .azureus.Delete it.In .wine folder in C>program files is utorrent folder.You can drag exe somewhere and delete utorent folder.

---

### Post by Gibran on 2007-04-02
> **zvacet said:**
> In your home hidden folders it is folder named .azureus.Delete it.In .wine folder in C>program files is utorrent folder.You can drag exe somewhere and delete utorent folder.
I did that and it seems to work! I'll restart a couple of times and hopefully that will be that. Thank you!

---

### Post by berylator on 2007-04-03
the same thing worked here, too; Weird but true!

Thanks for the fix :)

---

