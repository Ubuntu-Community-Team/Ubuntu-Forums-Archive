---
title: "Linux DC++"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by TwistableLime on 2008-04-20
I'm having a bit of trouble with linuxdcpp v1.0.0. The program and everything work fine however I'm trying to connect to an on-campus hub at college. I've been told that I can use other programs however I'm not much of a fan of their interfaces. There is a "patch" that someone made that will allow linuxdcpp to properly connect to the hub however he has yet to get back to me as to how to install it.

Also, since I'm a bit new to Linux I'm not too familar with certain file types and extensions. Now I have the patch file (which ends in .patch) and when I open it, it looks like a some sort of script. I guess it would be because what I'm utimately trying to do is fool my school's hub into thinking i have a different version. I'm just not sure where I should drop the file or how to actually use it.

Any help would be greatly appreciated.

Thanks

---

### Post by finer recliner on 2008-04-20
change to the directory that has linuxdcpp executable and do:

```
patch -p0 < patch-file-name-here
```

---

### Post by TwistableLime on 2008-04-20
OK, I can navigate to the directory but when I enter the code I receive this:

"joe@joe-laptop:/usr/bin$ patch -p0 < ruxan_patch_for_linuxdcpp-1.0.0.patch
bash: ruxan_patch_for_linuxdcpp-1.0.0.patch: No such file or directory"

I take this to mean that the patch must be in the same directory, however I don't have the permission to put the patch in there. Do I have to change permissions around?

---

### Post by finer recliner on 2008-04-20
try providing the entire path to the patch:

```
 patch -p0 < /home/user/myPatch.patch 
```

---

### Post by TwistableLime on 2008-04-20
This is what I receive now:
________________________________________________________
joe@joe-laptop:/usr/bin$ patch -p0 < /home/joe/Desktop/ruxan.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ur linuxdcpp-1.0.0/client/NmdcHub.cpp linuxdcpp-1.0.0_dave/client/NmdcHub.cpp
|--- linuxdcpp-1.0.0/client/NmdcHub.cpp	2007-08-04 17:21:46.000000000 -0400
|+++ linuxdcpp-1.0.0_dave/client/NmdcHub.cpp	2007-12-03 14:39:59.000000000 -0500
--------------------------
File to patch: /usr/bin/linuxdcpp
patching file /usr/bin/linuxdcpp
Hunk #1 FAILED at 796.
patch: **** Can't rename file /usr/bin/linuxdcpp to /usr/bin/linuxdcpp.orig : Permission denied
_________________________________________________________

Is the permission causing the problem?

---

### Post by finer recliner on 2008-04-20
yeah looks like a permissions problem. run the same command again with 'sudo' preceeding it. this will give you temporary root priveledges. 

```
sudo patch -p0 < /home/joe/Desktop/ruxan.patch
```

---

### Post by TwistableLime on 2008-04-20
I'm not sure whats wrong here. Perhaps there is something wrong with the actual file?


_________________________________________________________________
joe@joe-laptop:/usr/bin$ sudo patch -p0 < /home/joe/Desktop/ruxan.patch
can't find file to patch at input line 4
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ur linuxdcpp-1.0.0/client/NmdcHub.cpp linuxdcpp-1.0.0_dave/client/NmdcHub.cpp
|--- linuxdcpp-1.0.0/client/NmdcHub.cpp	2007-08-04 17:21:46.000000000 -0400
|+++ linuxdcpp-1.0.0_dave/client/NmdcHub.cpp	2007-12-03 14:39:59.000000000 -0500
--------------------------
File to patch: /usr/bin/linuxdcpp
patching file /usr/bin/linuxdcpp
Hunk #1 FAILED at 796.
1 out of 1 hunk FAILED -- saving rejects to file /usr/bin/linuxdcpp.rej
can't find file to patch at input line 16
Perhaps you used the wrong -p or --strip option?
The text leading up to this was:
--------------------------
|diff -ur linuxdcpp-1.0.0/client/version.h linuxdcpp-1.0.0_dave/client/version.h
|--- linuxdcpp-1.0.0/client/version.h	2006-12-04 14:11:41.000000000 -0500
|+++ linuxdcpp-1.0.0_dave/client/version.h	2007-12-03 14:40:32.000000000 -0500
--------------------------
File to patch: /usr/bin/linuxdcpp
patching file /usr/bin/linuxdcpp
Hunk #1 FAILED at 17.
1 out of 1 hunk FAILED -- saving rejects to file /usr/bin/linuxdcpp.rej

---

### Post by finer recliner on 2008-04-20
post the contents of the patch file you have (and please wrap it it with code tags for easy reading!)

---

### Post by TwistableLime on 2008-04-20
Heres the contents:

```
diff -ur linuxdcpp-1.0.0/client/NmdcHub.cpp linuxdcpp-1.0.0_dave/client/NmdcHub.cpp
--- linuxdcpp-1.0.0/client/NmdcHub.cpp	2007-08-04 17:21:46.000000000 -0400
+++ linuxdcpp-1.0.0_dave/client/NmdcHub.cpp	2007-12-03 14:39:59.000000000 -0500
@@ -796,7 +796,7 @@
 	string myInfoA =
 		"$MyINFO $ALL " + fromUtf8(getMyNick()) + " " + fromUtf8(escape(getCurrentDescription())) +
 		tmp1 + VERSIONSTRING + tmp2 + modeChar + tmp3 + getCounts() + tmp4 + Util::toString(SETTING(SLOTS)) + uMin +
-		">$ $" + SETTING(UPLOAD_SPEED) + "\x01$" + fromUtf8(escape(SETTING(EMAIL))) + '$';
+		">$ $LAN(T3)\x01$" + fromUtf8(escape(SETTING(EMAIL))) + '$';
 	string myInfoB = ShareManager::getInstance()->getShareSizeString() + "$|";
  
  	if(lastMyInfoA != myInfoA || alwaysSend || (lastMyInfoB != myInfoB && lastUpdate + 15*60*1000 < GET_TICK()) ){
diff -ur linuxdcpp-1.0.0/client/version.h linuxdcpp-1.0.0_dave/client/version.h
--- linuxdcpp-1.0.0/client/version.h	2006-12-04 14:11:41.000000000 -0500
+++ linuxdcpp-1.0.0_dave/client/version.h	2007-12-03 14:40:32.000000000 -0500
@@ -17,7 +17,7 @@
  */
 
 #define APPNAME "DC++"
-#define VERSIONSTRING "0.698"
-#define VERSIONFLOAT 0.698
+#define VERSIONSTRING "0.674"
+#define VERSIONFLOAT 0.674
 
 /* Update the .rc file as well... */
```

---

### Post by diablo75 on 2008-04-20
Half-way off topic:

Can someone direct me to a simple explanation of what DC++ is and how to use it?  The last time I tried, the client I installed was just utterly confusing as well as very buggy...

---

### Post by finer recliner on 2008-04-20
ugh, im sorry. i told you to apply the patch to the executable. that is wrong. you should be applying the patch to the SOURCE CODE. you'll need to reinstall linuxdcpp after applying the patch.

---

### Post by TwistableLime on 2008-04-20
OK, thanks. Now how would I go about applying it to the source code? Is there a directory where most source codes are stored? Would this be as simple as copy-&-pasting the text?

---

### Post by finer recliner on 2008-04-20
you probably installed it from the repositories. uninstall it from the repositories, then download the latest source code from the official linuxdcpp website. change to the directory that you downloaded the source code too, apply the patch as you tried doing before. then compile and install.

---

