---
title: "Linux Mint: banshee won't start"
date: 2011-10-02
forum: Any Other OS
---

### Post by jonnyboysmithy on 2011-10-02
I got linux mint just yesterday, I tried to start banshee but  alas:```
banshee
[Info  10:55:04.358] Running Banshee 2.0.0: [Ubuntu 11.04 (linux-gnu, i686) @ 2011-06-28 05:46:57 UTC]
[Error 10:55:04.927] Error initializing required service DbConnection
Exception has been thrown by the target of an invocation.
System.Reflection.TargetInvocationException: Exception has been thrown by the target of an invocation. ---> Banshee.Database.BansheeDbFormatMigrator+DatabaseVersionTooHigh: This version of Banshee was prepared to work with older database versions (=< 43) thus it is too old to support the current version of the database (44).
  at Banshee.Database.BansheeDbFormatMigrator.Migrate () [0x00000] in <filename unknown>:0 
  --- End of inner exception stack trace ---
  at System.Reflection.MonoCMethod.Invoke (System.Object obj, BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.MonoCMethod.Invoke (BindingFlags invokeAttr, System.Reflection.Binder binder, System.Object[] parameters, System.Globalization.CultureInfo culture) [0x00000] in <filename unknown>:0 
  at System.Reflection.ConstructorInfo.Invoke (System.Object[] parameters) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type, Boolean nonPublic) [0x00000] in <filename unknown>:0 
  at System.Activator.CreateInstance (System.Type type) [0x00000] in <filename unknown>:0 
  at Banshee.Gui.GtkBaseClient.Startup () [0x00000] in <filename unknown>:0 
  at Hyena.Gui.CleanRoomStartup.Startup (Hyena.Gui.StartupInvocationHandler startup) [0x00000] in <filename unknown>:0 

```I have reinstalled but still the same output.
Any ideas?

I think the useful info is: (cut and pasted of the above code)```
This version of Banshee was prepared to work with older database versions (=< 43) thus it is too old to support the current version of the database (44).
```

btw where in the home folder are the settings of banshee stored ? I looked but couldn't find them.

---

### Post by Perfect Storm on 2011-10-03
Moved to Other OS/Distro Talk.

---

### Post by Rob-e on 2011-10-09
That's pretty funny, I just switched to Mint too and I had the same problem.

I just removed ~/.config/banshee-1/banshee.db and it works again, however removing that will get rid of the list of songs in banshee and ratings and such too.

---

