---
title: "[SOLVED] looking for a program similar to Limewire."
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by phread59 on 2008-04-12
Is there any Ubuntu supported programs like Limewire?  It would be nice to search for music on the web like Limewire does.  I enjoy working on my computer with some tunes going in the background.  Any suggestions?

Mark Shuman

---

### Post by Fixman on 2008-04-12
I recommend you gtk-gnutella, its in the repos.

*Hey, that is illegal!*

---

### Post by tamoneya on 2008-04-12
you could also look into amule.  I havent used it myself but it is in the repositories and should be rather straight forward.

---

### Post by joshrobinson on 2008-04-12
frostwire is an exact clone of limewire, just a different color and name
you need java to run it though

im not sure if it will be in the repo's for you, it used to be

but if not you can check out [www.frostwire.com](www.frostwire.com)

gtk-gnutella as suggested is good
and so is nicotine (a soulseek clone)

---

### Post by Tyke91 on 2008-04-12
limewire is also java based... 
from the wiki
>  


 As with LimeWire, FrostWire is written in [Java]("http://en.wikipedia.org/wiki/Java_%28programming_language%29"), and so is capable of supporting multiple platforms. LimeWire is available in both free and paid versions, while FrostWire is released only as a free version. The FrostWire program includes all of the free LimeWire version's functionality, plus a few features of LimeWire Pro's fee based upgrades. FrostWire also provides a chatroom which is absent in LimeWire. FrostWire's interface is nearly identical to that of LimeWire's since it's based on the same code base, however, the color scheme is slightly different. As in LimeWire, the FrostWire skin may also be changed to a variety of different colors.

---

### Post by joshrobinson on 2008-04-12
> **Tyke91 said:**
> limewire is also java based... 
from the wiki

yeah i said that :-P
not directly, but when i said its a clone i thought someone would pick up on that they both used java, but oh well

---

### Post by Mark20 on 2008-04-12
Ok...

Or you can just download Limewire for linux.  It's written for Windows, Linux, and Mac eh?

```

wget http://www.limewire.com/LimeWireSoftLinuxDeb
sudo dpkg --install LimeWireLinux.deb

```

Then run it by typing```
limewire &
``` in a console.

Hope that helps.

Mark

---

### Post by Mark20 on 2008-04-12
@Fixman

It's not illegal in Canada :)

---

### Post by Tyke91 on 2008-04-12
true, in canada it's only illegal to upload, not download.

anyway, limewire itself is not illegal, it's only illegal to download music that you should be paying for... and we know *nobody* here does that

---

### Post by phread59 on 2008-04-13
Thank you fellows.  Mark20 thank you ever so much.  Your instructions were right on the button.  I now have Limewire loaded up.  I haven't used it yet but it's there.  Josh I haven't tried Frostwire.  I have had plenty of luck with Limewire.  So I have stuck with it.  Thank you all again for the help.

Mark Shuman

---

### Post by Sanoski on 2008-04-13
I personally like frostwire better than limewire.... ya know.. if I used that kind of thing.

---

### Post by hshaw on 2008-05-20
Hi Mark20... I tried to download this thru a terminal and the download worked but I still can not load LimeWire it keeps showing up blank. 

heather@box1:~$ wget [http://www.limewire.com/LimeWireSoftLinuxDeb](http://www.limewire.com/LimeWireSoftLinuxDeb)
--14:24:43--  [http://www.limewire.com/LimeWireSoftLinuxDeb](http://www.limewire.com/LimeWireSoftLinuxDeb)
           => `LimeWireSoftLinuxDeb'
Resolving [www.limewire.com](www.limewire.com)... 64.156.82.107, 64.156.82.108, 64.156.82.109
Connecting to [www.limewire.com|64.156.82.107|:80](www.limewire.com|64.156.82.107|:80)... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://www9.limewire.com/download/LimeWireLinux.deb](http://www9.limewire.com/download/LimeWireLinux.deb) [following]
--14:24:43--  [http://www9.limewire.com/download/LimeWireLinux.deb](http://www9.limewire.com/download/LimeWireLinux.deb)
           => `LimeWireLinux.deb'
Resolving www9.limewire.com... 64.156.82.101
Connecting to www9.limewire.com|64.156.82.101|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 8,553,092 (8.2M) [application/x-debian-package]

100%[====================================>] 8,553,092    311.99K/s    ETA 00:00

14:25:11 (303.22 KB/s) - `LimeWireLinux.deb' saved [8553092/8553092]

heather@box1:~$ sudo dpkg --install LimeWireLinux.deb
[sudo] password for heather: 
Selecting previously deselected package limewire-basic.
(Reading database ... 115325 files and directories currently installed.)
Unpacking limewire-basic (from LimeWireLinux.deb) ...
Setting up limewire-basic (4.16.7-1) ...

heather@box1:~$ limewire &
[1] 8830
heather@box1:~$ Starting LimeWire...
Java exec found in PATH. Verifying...
Suitable java version found [java = 1.5.0_15]
Configuring environment...
Loading LimeWire:
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb003f767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb003f8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb00841bd]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb0173dce]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb015dd77]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb015def3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb015e136]
#7 [0xb264fbfa]
#8 [0xb2649b3b]
#9 [0xb2649b3b]
#10 [0xb2647219]
#11 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78062bc]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb791aed8]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78060ef]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7863b9d]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75fb30d]
#16 [0xb264f4ab]
#17 [0xb2649a64]
#18 [0xb2647219]
#19 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78062bc]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb003f767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb003f81e]
#2 /usr/lib/libX11.so.6 [0xb0083518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb007a0a6]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb015d0b9]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb015d303]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so [0xb015dfa1]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb015e136]
#8 [0xb264fbfa]
#9 [0xb2649b3b]
#10 [0xb2649b3b]
#11 [0xb2647219]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78062bc]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb791aed8]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so [0xb78060ef]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb7863b9d]
#16 /usr/lib/jvm/java-1.5.0-sun-1.5.0.15/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb75fb30d]
#17 [0xb264f4ab]
#18 [0xb2649a64]
#19 [0xb2647219]
/usr/share/themes/Crux/gtk-2.0/gtkrc:37: error: lexical error or unexpected token, expected valid token

---

