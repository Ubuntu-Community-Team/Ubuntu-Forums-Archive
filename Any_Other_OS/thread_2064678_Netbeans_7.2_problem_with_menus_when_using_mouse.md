---
title: "Netbeans 7.2 problem with menus when using mouse"
date: 2012-09-30
forum: Any Other OS
---

### Post by cyb3r_sn4k3 on 2012-09-30
I'm using Mint 13 (cinnamon)and when netbeans 7.2  (Installed from source from website) is maximized or enlarged by dragging. The top menus (file,  edit etc) do not work properly with mouse as in they do not stay open on  mouse click. But works fine with keyboard. Its also works if the windows is not enlarged or not maximized.

I found a bug report but don't know how to apply the patch. 
[http://netbeans.org/bugzilla/show_bug.cgi?id=198639](http://netbeans.org/bugzilla/show_bug.cgi?id=198639)

Please help.

---

### Post by T.J. on 2012-09-30
This is a "diff" patch, so you need to use the "patch" utility.

You should always backup the source before you attempt to apply a patch file.  There are no guarantees that it will apply properly the first time.  You may have to adjust the patch level ("-p" parameter  in order to get the files in the right folders), depending on where you are in the source tree when you attempt to apply the patch.


Assuming you have the source code for NetBeans to apply the patch to, try:

patch  -p0 < *patch filename* 

when in the top of the source directory.   

If you get stuck, let me know, and I'll try to help you get the patch applied properly.

T.J.

---

### Post by cyb3r_sn4k3 on 2012-09-30
> **T.J. said:**
> This is a "diff" patch, so you need to use the "patch" utility.

You should always backup the source before you attempt to apply a patch file.  There are no guarantees that it will apply properly the first time.  You may have to adjust the patch level ("-p" parameter  in order to get the files in the right folders), depending on where you are in the source tree when you attempt to apply the patch.


Assuming you have the source code for NetBeans to apply the patch to, try:

patch  -p0 < *patch filename* 

when in the top of the source directory.   

If you get stuck, let me know, and I'll try to help you get the patch applied properly.

T.J.

Thanks. But heres the problem.
the .diff file contains 
```
diff --git a/core.windows/src/org/netbeans/core/windows/view/ui/MainWindow.java b/core.windows/src/org/netbeans/core/windows/view/ui/MainWindow.java --- a/core.windows/src/org/netbeans/core/windows/view/ui/MainWindow.java +++ b/core.windows/src/org/netbeans/core/windows/view/ui/MainWindow.java @@ -58,6 +58,7 @@  import java.awt.Rectangle;  import java.awt.event.*;  import java.io.File; +import java.lang.reflect.Field;  import java.util.*;  import java.util.logging.Level;  import java.util.logging.Logger; @@ -139,6 +140,23 @@         if (mainMenuBar == null) {             mainMenuBar = createMenuBar();             ToolbarPool.getDefault().waitFinished(); +           if ("gnome-shell".equals(System.getenv("DESKTOP_SESSION"))) { +               try { +                   Class<?> xwm = Class.forName("sun.awt.X11.XWM"); +                   Field awt_wmgr = xwm.getDeclaredField("awt_wmgr"); +                   awt_wmgr.setAccessible(true); +                   Field other_wm = xwm.getDeclaredField("OTHER_WM"); +                   other_wm.setAccessible(true); +                   if (awt_wmgr.get(null).equals(other_wm.get(null))) { +                       Field metacity_wm = xwm.getDeclaredField("METACITY_WM"); +                       metacity_wm.setAccessible(true); +                       awt_wmgr.set(null, metacity_wm.get(null)); +                       LOGGER.info("installed #198639 workaround"); +                   } +               } catch (Exception x) { +                   LOGGER.log(Level.FINE, null, x); +               } +           }         }     }   
```

From the file i figured that i should patch 
/core.windows/src/org/netbeans/core/windows/view/ui/MainWindow.java  But no file exists like that. The closest directory i found was 
/home/athul/.netbeans/7.2/config/Preferences/org/netbeans/core/windows

---

### Post by T.J. on 2012-09-30
If you can point me in the right direction to get the source tree for the exact version of NetBeans that you want to use, and the patch - I'll try to patch it for you, then modify the patch if needs be and post it here for you.  It might take me a day or two with my schedule.

---

### Post by cyb3r_sn4k3 on 2012-09-30
> **T.J. said:**
> If you can point me in the right direction to get the source tree for the exact version of NetBeans that you want to use, and the patch - I'll try to patch it for you, then modify the patch if needs be and post it here for you.  It might take me a day or two with my schedule.

Here's the link to Netbeans 7.2 
[http://netbeans.org/downloads/start.html?platform=linux&lang=en&option=php](http://netbeans.org/downloads/start.html?platform=linux&lang=en&option=php)

And heres the fix
[http://netbeans.org/bugzilla/show_bug.cgi?id=198639](http://netbeans.org/bugzilla/show_bug.cgi?id=198639)


Thank You so much and take your time.

---

### Post by Perfect Storm on 2012-09-30
Moved to Other OS/Distro Talk.

---

### Post by T.J. on 2012-10-01
Hello again! =)

Just an update while I try to get the NetBeans code from their archive so I can be sure of what I'm saying.  Please do not take anything I might say to sound condescending or annoyed. My thoughts not always in order, especially on Mondays. =P

The NetBeans link that you provided is for the binary rather than the source.  That is why you could not find the file mentioned in the patch.  I looked over your patch link, and it appears to be intended for NetBeans 7.0, which means that NetBeans 7.2 probably already has been patched.  It is marked as resolved.

 Sorry to make matters more difficult for you, but the binary installs and works flawlessly as far as I can tell (on Debian 7.0 Testing, anyway).  All the menus worked fine (with OpenJDK 6 in Gnome 3.2/KDE 4.8.4). I strongly suspect that your troubles originate in either the JRE (Java Runtime) installed on your system, or the Cinnamon Desktop itself.  I'm not trying to discourage you from your favorite interface, but Cinnamon is very new, and they don't have all the kinks out yet. 

Is there any chance you can try running NetBeans in another desktop session other than Cinnamon, just to be sure that Cinnamon is not the culprit?  You don't have to reinstall, just add one from the package manager.  If it is not Cinnamon, we will need to look at your JRE.  

I'll get back to you as time permits, if I find out something in the code.

---

### Post by cyb3r_sn4k3 on 2012-10-01
> **T.J. said:**
> Hello again! =)

Just an update while I try to get the NetBeans code from their archive so I can be sure of what I'm saying.  Please do not take anything I might say to sound condescending or annoyed. My thoughts not always in order, especially on Mondays. =P

The NetBeans link that you provided is for the binary rather than the source.  That is why you could not find the file mentioned in the patch.  I looked over your patch link, and it appears to be intended for NetBeans 7.0, which means that NetBeans 7.2 probably already has been patched.  It is marked as resolved.

 Sorry to make matters more difficult for you, but the binary installs and works flawlessly as far as I can tell (on Debian 7.0 Testing, anyway).  All the menus worked fine (with OpenJDK 6 in Gnome 3.2/KDE 4.8.4). I strongly suspect that your troubles originate in either the JRE (Java Runtime) installed on your system, or the Cinnamon Desktop itself.  I'm not trying to discourage you from your favorite interface, but Cinnamon is very new, and they don't have all the kinks out yet. 

Is there any chance you can try running NetBeans in another desktop session other than Cinnamon, just to be sure that Cinnamon is not the culprit?  You don't have to reinstall, just add one from the package manager.  If it is not Cinnamon, we will need to look at your JRE.  

I'll get back to you as time permits, if I find out something in the code.

Hey, I tried another session like you suggested(gnome classic) and it worked fine no menu issues!. So I'm guessing its something with Cinnamon or JRE. Thanks!

---

### Post by T.J. on 2012-10-01
> **cyb3r_sn4k3 said:**
> Hey, I tried another session like you suggested(gnome classic) and it worked fine no menu issues!. So I'm guessing its something with Cinnamon or JRE. Thanks!


I'm fairly sure that you are using the same JRE in both sessions,  so I'm 95% certain that the JRE is not the cause of the problem.  Debian, Ubuntu, and Mint all use the same package as far as I know. It is probably Cinnamon, I'm sorry to say.   I'm not surprised.  Cinnamon has some unresolved bugs, at least - it did with the last version I tried a few months ago.

The problem will have to be fixed by the Cinnamon Project, since that's rather outside my knowledge presently.  

I'm sorry I can't provide you with a better solution, but I'm glad I could help you pin it down.  Do take care, and best of luck.  If there is anything else I can do, please message me, or post here. =)

---

### Post by cyb3r_sn4k3 on 2012-10-02
> **T.J. said:**
> I'm fairly sure that you are using the same JRE in both sessions,  so I'm 95% certain that the JRE is not the cause of the problem.  Debian, Ubuntu, and Mint all use the same package as far as I know. It is probably Cinnamon, I'm sorry to say.   I'm not surprised.  Cinnamon has some unresolved bugs, at least - it did with the last version I tried a few months ago.

The problem will have to be fixed by the Cinnamon Project, since that's rather outside my knowledge presently.  

I'm sorry I can't provide you with a better solution, but I'm glad I could help you pin it down.  Do take care, and best of luck.  If there is anything else I can do, please message me, or post here. =)

Thanks T.J you been alot of help. I'll report a bug something :P Thanks!

---

### Post by WolfRage on 2012-10-07
I found a simple workaround for the time being from a Cinnamon bug report. Just do this: 
"A hacky fix for this is to go to Full screen mode, which makes the menu work correctly, even after changing back to normal view."

So just transition the IDE to full-screen with Alt+Shift+Enter, and then back again with the same keyboard shortcut and your problem is fixed until you open Netbeans again.  The next version of Cinnamon should fix this by reporting it's self as Mutter to the Java virtual machines until proper support is added for Muffin.

---

### Post by cyb3r_sn4k3 on 2012-10-07
> **WolfRage said:**
> I found a simple workaround for the time being from a Cinnamon bug report. Just do this: 
"A hacky fix for this is to go to Full screen mode, which makes the menu work correctly, even after changing back to normal view."

So just transition the IDE to full-screen with Alt+Shift+Enter, and then back again with the same keyboard shortcut and your problem is fixed until you open Netbeans again.  The next version of Cinnamon should fix this by reporting it's self as Mutter to the Java virtual machines until proper support is added for Muffin.


OMG it worked. Awesome. Thanks!

---

