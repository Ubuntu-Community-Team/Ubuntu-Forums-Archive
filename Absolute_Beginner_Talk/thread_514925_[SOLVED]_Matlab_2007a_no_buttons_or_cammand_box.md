---
title: "[SOLVED] Matlab 2007a no buttons or cammand box"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-08-01
Hi there,

I just bought Matlab 2007a for Linux but the there are no buttons in the top menu! when I click I get option but I have no idea what I am clicking - any ideas?

Thanks,

Rudolf

PS - please see attachment
PPS: I removed windows from my drive - because i saw the Linux version of matlab, it would really suck if I had to reinstall windows! ](*,)

---

### Post by Inxsible on 2007-08-01
Sometimes just a re-start of the application would help you. At other times a reboot might.

Else, it would be best if you contacted the Customer Service for Matlab. They should know whats going on

---

### Post by zgornel on 2007-08-01
Are you using beryl/compiz ?

---

### Post by david_e on 2007-08-01
If you are using Beryl - Compiz you could try starting Matlab with:

```

export AWT_TOOLKIT="MToolkit"
matlab

```

from a terminal window: it's an old trick to fix java graphics applications (like the Matlab GUI).

---

### Post by RudolfMDLT on 2007-08-01
Thanks guys - did restart a couple of times! did nothing, then I installed KDE, works perfectly! Anyway - as soon as I'm finished with my project I'll give your command a try david_e!

PS: In Ubuntu - when I deselect the desktop effects, am I still running Compiz with now effects or bog standard MetaCity?

Thanks Rudolf

---

### Post by david_e on 2007-08-01
> **RudolfMDLT said:**
> Thanks guys - did restart a couple of times! did nothing, then I installed KDE, works perfectly! Anyway - as soon as I'm finished with my project I'll give your command a try david_e!
If it's working you don't need it. :D

---

### Post by AegisTalons on 2007-08-04
> **david_e said:**
> If you are using Beryl - Compiz you could try starting Matlab with:

```

export AWT_TOOLKIT="MToolkit"
matlab

```

from a terminal window: it's an old trick to fix java graphics applications (like the Matlab GUI).

Hey, so I just installed matlab. I got it working but I was also having problems displaying the menu. I am running Compiz Fusion. I tried your code that you mentioned and now, all i got when I try to run MatLab is: 

> Failed to start the Desktop: Failure loading desktop class

Any ideas to at least get it back to the point where matlab would start correctly even if I don't get a menu. Also does anyone know how to get the menu working? I'm currently running Ubuntu, so I don't really want to install KDE.

---

### Post by jARLAXL on 2007-10-23
> **david_e said:**
> If you are using Beryl - Compiz you could try starting Matlab with:

```

export AWT_TOOLKIT="MToolkit"
matlab

```

from a terminal window: it's an old trick to fix java graphics applications (like the Matlab GUI).

MAN MAN MAN. i dont really know how to thank you...
i had exactly the same problem. i reinstalled it about 6-7 times troubling with it for the last 12 hours contnously. i was just ready to go to the KDE solution or even to a dual boot ubuntu/kubuntu solution. just to finish a few projects and then i will get rid of these proprietary shits. there are really many numerous open source math packets that can do the job the same way without having to contact the proprietary well paid support.

thanks again for saving me the day. or maybe the other day cause this day is gone.

---

### Post by h2g2 on 2007-11-21
I have the exact same problem as AegisTalons. I am running ubuntu 7.10 on amd64. can anyone help? this is what i get:

[FONT="Courier New"][INDENT]$ export AWT_TOOLKIT=MToolkit ; /usr/local/matlab75/bin/matlab
Unable to initialize com.mathworks.mwswing.MJStartup
java.lang.UnsatisfiedLinkError: Can't load library: /usr/local/matlab75/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/motif12/libmawt.so
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.load0(Unknown Source)
        at java.lang.System.load(Unknown Source)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)
        at javax.swing.ImageIcon.<clinit>(Unknown Source)
        at com.mathworks.mwswing.desk.Desktop.<clinit>(Desktop.java:103)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at com.mathworks.jmi.OpaqueJavaInterface.findClass(OpaqueJavaInterface.java:470)
 Failed to start the Desktop: Failure loading desktop class[/INDENT]
[/FONT]

---

### Post by retrow on 2007-12-01
> **david_e said:**
> If you are using Beryl - Compiz you could try starting Matlab with:

```

export AWT_TOOLKIT="MToolkit"
matlab

```

from a terminal window: it's an old trick to fix java graphics applications (like the Matlab GUI).

Worked for me :)

Since I am too lazy to type another line in command prompt, I went in and edited the **/usr/bin/matlab** file.

Add ```
export AWT_TOOLKIT="MToolkit"
```
at the very top of that script.

---

### Post by newpants2003 on 2008-01-09
works  partially, i cant resize the windows... works fine if i turn the compiz off.

---

### Post by fuzzygenius on 2008-01-11
Worked for me wonderfully.  I can resize things at will, too.  I especially liked the suggestion to modify the matlab script itself, as now the fix works for menu launchers too.

Thanks!

---

