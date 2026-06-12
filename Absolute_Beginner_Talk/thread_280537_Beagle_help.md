---
title: "Beagle help"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by CanonD on 2006-10-19
I installed beagle, and when i run beagled, i get this error: any help would be great!



** (/usr/lib/beagle/BeagleDaemon.exe:16941): WARNING **: The following assembly referenced from /usr/lib/beagle/Filters/Filters.dll could not be loaded:
     Assembly:   ICSharpCode.SharpZipLib    (assemblyref_index=7)
     Version:    0.6.0.0
     Public Key: 1b03e6acf1164f73
The assembly was not found in the Global Assembly Cache, a path listed in the MO NO_PATH environment variable, or in the location of the executing assembly (/usr /lib/beagle/Filters).


** (/usr/lib/beagle/BeagleDaemon.exe:16941): WARNING **: Could not load file or assembly 'ICSharpCode.SharpZipLib, Version=0.6.0.0, Culture=neutral, PublicKeyTo ken=1b03e6acf1164f73' or one of its dependencies.

** (/usr/lib/beagle/BeagleDaemon.exe:16941): WARNING **: Could not load file or assembly 'ICSharpCode.SharpZipLib, Version=0.6.0.0, Culture=neutral, PublicKeyTo ken=1b03e6acf1164f73' or one of its dependencies.

Unhandled Exception: System.NullReferenceException: Object reference not set to an instance of an object
  at System.IO.StreamWriter.LowLevelWrite (System.String s) [0x0000e] in /home/j ms/Projects/monodevelop-backport/working/mono-1.1.17.1/mcs/class/corlib/System.I O/StreamWriter.cs:263
  at System.IO.StreamWriter.Write (System.String value) [0x0001c] in /home/jms/P rojects/monodevelop-backport/working/mono-1.1.17.1/mcs/class/corlib/System.IO/St reamWriter.cs:311
  at System.IO.TextWriter.WriteLine (System.String value) [0x00000] in /home/jms /Projects/monodevelop-backport/working/mono-1.1.17.1/mcs/class/corlib/System.IO/ TextWriter.cs:276
  at Beagle.Util.Log.WriteLine (LogLevel level, System.String format, System.Obj ect[] args, System.Exception ex) [0x001d2] in /build/buildd/beagle-0.2.6/Util/Lo g.cs:258
  at Beagle.Util.Log.Warn (System.String message, System.Object[] args) [0x00000 ] in /build/buildd/beagle-0.2.6/Util/Log.cs:299
  at Beagle.Util.Logger.Warn (System.String message, System.Object[] args) [0x00 000] in /build/buildd/beagle-0.2.6/Util/Logger.cs:79
  at Beagle.Util.ExceptionHandlingThread.ThreadStarted () [0x00097] in /build/bu ildd/beagle-0.2.6/Util/ExceptionHandlingThread.cs:57
  at (wrapper delegate-invoke) System.MulticastDelegate:invoke_void ()

---

