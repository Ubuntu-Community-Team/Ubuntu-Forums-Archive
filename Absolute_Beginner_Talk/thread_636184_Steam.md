---
title: "Steam"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by Velcor on 2007-12-09
Hello,

I seem to be having issues with Steam regarding installing/downloading games. 

I've searched around but haven't found anything, Steam seemed to install fine with no problems starting up or using the tabs/browsing the community. However when I go to install a game, that I purchased on steam (I don't have the CD for them) it displays 

```
err:ole:CoGetClassObject class {9a5ea990-3034-4d6f-9128-01f3c61022bc} not registered
err:ole:CoGetClassObject no class object {9a5ea990-3034-4d6f-9128-01f3c61022bc} could be created for context 0x1
Shutting down. . .
29err:ntdll:RtlpWaitForCriticalSection section 0x7e5d0920 "x11drv_main.c: X11DRV_CritSection" wait timed out in thread 0017, blocked by 0009, retrying (60 sec)
300client callback thread error
client callback thread error
wine: Critical section 7e5d0920 wait failed at address 0x7bc39b40 (thread 0017), starting debugger...
Unhandled exception: wait failed on critical section 0x7e5d0920 thread_data_tls_index+0x40
err:seh:raise_exception Unhandled exception code c0000194 flags 0 addr 0x7bc39b40
zugzug@ubuntu:~/.wine/drive_c/Program Files/Steam$ Process of pid=0008 has terminated
No process loaded, cannot execute 'echo Modules:'
Cannot get info on module while no process is loaded
No process loaded, cannot execute 'echo Threads:'
process  tid      prio (all id:s are in hex)
0000000a 
        0000000c    0
        0000000b    0
You must be attached to a process to run this command.
No process loaded, cannot execute 'detach'
```

And quits. I don't really know what to do with that and any help would be appreciated.

Thanks in advance and I apologize if this is in the wrong section. :)

---

### Post by nikoPSK on 2007-12-09
Use wine-doors to help you install it.

---

### Post by Velcor on 2007-12-09
> **nikoPSK said:**
> Use wine-doors to help you install it.

Thanks, I'll try that.

---

### Post by nikoPSK on 2007-12-09
np:popcorn: I'm here to help.

---

