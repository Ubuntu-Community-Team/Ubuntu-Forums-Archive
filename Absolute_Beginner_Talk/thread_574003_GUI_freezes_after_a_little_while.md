---
title: "GUI freezes after a little while"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by hitmyspot on 2007-10-12
Hi,

I'm a newbie running feisty fawn. Most of the distribution installed with no probs (including ATI graphics, wireless adapter and internet, but my desktop environment freezes after about an hour of use.
At first I thought it might have been Azureus causing the problem, so I made sure to update my java environment (using sun's official through the software repository) and related files.  My java still shows up as out of date on the sun site,

After leaving Azureus off and searching for a solution, I started to get freezes with firefox and pretty much anything else. I have looked through the logs (don't really know what to look for), but don't see anything that looks like an error.

Any help as to how to find or solve the problem would be appreciated.
Thanks
Frank

P.s. I use a touchpad on my laptop (from ALPS) but after downloading the touchpad app to change settings, I find I cannot load it, so am stuck with overly sensitive settings Error is: GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Do I just add that in xorg.conf in the mouse section?

Also when I try to use the Desktop effects app, I get a "The Composite extension is not available" error. On my trial dual boot I could use the effects, however now that I have no windows, I am getting these glitches!

---

### Post by hitmyspot on 2007-10-13
Just to summarise above, my desktop just freezes. I don't know what is causing the freeze as it seems to occur randomly no matter what apps I am using. I do not see any problems in the logs, but do not know where/how to look properly. All my devices appear to be installed and working correctly. I don't know how to troubleshoot and the additional information is supplied in case someone knows how they might be related.

Help Please!:confused:

---

### Post by mysurface on 2007-10-13
The fastest way to figure out what is the cause of error, I suggest you to run your gui from gnome terminal. The error will be print at the terminal. Let say running firefox at gnome-terminal, just type **firefox** at terminal prompt and hit enter. 

In case you have no idea what is the GUI's Command name, check out [here]("http://linux.byexamples.com/archives/47/get-to-know-which-command-use-to-trigger-the-gui-program/").

---

### Post by hitmyspot on 2007-10-13
OK, so I ran both firefox and azureus through terminal (my most commonly used programs). No freeze as yet, but I did find an error in azureus which is related to java. That is what I was first suspicious of, but it seems to occur even when not using azureus. Does java start automatically or is it only when requested by a java program or applet etc?

To fix, should I purge all java and then try a reinstall? Which version should I use? Most recent? Download from sun/use synaptic?

Thanks

error:
GC Warning: Out of Memory!  Returning NIL!
DEBUG::Sat Oct 13 16:38:31 GMT+10:00 2007::com.aelitis.azureus.core.diskmanager.access.impl.DiskAccessControllerInstance$2::runSupport::-1:
  java.lang.OutOfMemoryError: Cannot create additional threads
   at java.lang.Thread.start(libgcj.so.70)
   at org.gudy.azureus2.core3.disk.impl.DiskManagerImpl.setFailed(Azureus2.jar.so)
   at org.gudy.azureus2.core3.disk.impl.access.impl.DMReaderImpl$requestDispatcher.failed(Azureus2.jar.so)
   at org.gudy.azureus2.core3.disk.impl.access.impl.DMReaderImpl$requestDispatcher.requestFailed(Azureus2.jar.so)
   at com.aelitis.azureus.core.diskmanager.access.impl.DiskAccessRequestImpl.runSupport(Azureus2.jar.so)
   at com.aelitis.azureus.core.diskmanager.access.impl.DiskAccessControllerInstance$2.runSupport(Azureus2.jar.so)
   at org.gudy.azureus2.core3.util.AEThread.run(Azureus2.jar.so)

GC Warning: Out of Memory!  Returning NIL!
DEBUG::Sat Oct 13 16:38:32 GMT+10:00 2007::com.aelitis.azureus.core.diskmanager.access.impl.DiskAccessControllerInstance$2::runSupport::-1:
  java.lang.OutOfMemoryError: Cannot create additional threads
   at java.lang.Thread.start(libgcj.so.70)
   at org.gudy.azureus2.core3.disk.impl.DiskManagerImpl.setFailed(Azureus2.jar.so)
   at org.gudy.azureus2.core3.disk.impl.access.impl.DMReaderImpl$requestDispatcher.failed(Azureus2.jar.so)
   at org.gudy.azureus2.core3.disk.impl.access.impl.DMReaderImpl$requestDispatcher.requestFailed(Azureus2.jar.so)
   at com.aelitis.azureus.core.diskmanager.access.impl.DiskAccessRequestImpl.runSupport(Azureus2.jar.so)
   at com.aelitis.azureus.core.diskmanager.access.impl.DiskAccessControllerInstance$2.runSupport(Azureus2.jar.so)
   at org.gudy.azureus2.core3.util.AEThread.run(Azureus2.jar.so)

---

