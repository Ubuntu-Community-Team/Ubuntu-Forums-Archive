---
title: "Can't run Minecraft with updated drivers?"
date: 2011-04-30
forum: Any Other OS
---

### Post by cbennett a7xftw on 2011-04-30
Alright, i was using Windows 7 and had Minecraft working. Then i switched operating systems to Ubuntu 10.10 and Minecraft worked. Now i'm back on Windows 7 and i'm getting this error


Bad video card drivers! 
----------------------- 

Minecraft was unable to start because it failed to find an accelerated OpenGL mode.
This can usually be fixed by updating the video card drivers.



--- BEGIN ERROR REPORT 7fe0271 --------
Generated 4/30/11 3:31 PM

Minecraft: Minecraft Beta 1.5_01
OS: Windows 7 (amd64) version 6.1
Java: 1.6.0_25, Sun Microsystems Inc.
VM: Java HotSpot(TM) 64-Bit Server VM (mixed mode), Sun Microsystems Inc.
LWJGL: 2.4.2
[failed to get system properties (java.lang.NullPointerException)]

org.lwjgl.LWJGLException: Pixel format not accelerated
at org.lwjgl.opengl.WindowsPeerInfo.nChoosePixelFormat(Native Method)
at org.lwjgl.opengl.WindowsPeerInfo.choosePixelFormat(WindowsPeerInfo.java:52)
at org.lwjgl.opengl.WindowsDisplay.createWindow(WindowsDisplay.java:185)
at org.lwjgl.opengl.Display.createWindow(Display.java:311)
at org.lwjgl.opengl.Display.create(Display.java:856)
at org.lwjgl.opengl.Display.create(Display.java:784)
at org.lwjgl.opengl.Display.create(Display.java:765)
at net.minecraft.client.Minecraft.a(SourceFile:272)
at net.minecraft.client.Minecraft.run(SourceFile:658)
at java.lang.Thread.run(Unknown Source)
--- END ERROR REPORT 38480e7e ----------


Everything on my computer is fully updated. My drivers are updated my java is updated. Everything is updated.

How do i fix this? My Minecraft addiction needs to be satisfied!
This is the GFX card i have been using the whole time on all of these os's 
Nvidia GeForce 1650SE nForce 430.

---

