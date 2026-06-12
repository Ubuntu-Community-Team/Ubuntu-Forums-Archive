---
title: "Wine Problem"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by th1bill on 2007-11-29
I have downloaded wine and then installed e-Sword only to get the frames and no text.  I was then advise to download riched20.dll and I did so and have unzipped the files to my storage directory.  The problem is that I was instructed to put the .dll in ~/.wine/drive_c/windows/system32 and I cannot find the directory to paste it there.

I know, it's a Windows user thing, but I'm learning, all be it slowly.

Thanks in advance for the help moving from windows to a great system.

---

### Post by jasay on 2007-11-29
"~" is your home directory.  ".wine" (note the period at the beginning) is a hidden directory so you will have to hit ctrl+h in nautilus or ctrl+. in konquorer to see it.

The other option is that wine has not been initialized yet.  Run winecfg in a terminal (Applications -> Accessories -> Terminal) and it should set everything up as well as let you make changes to the settings.

---

### Post by th1bill on 2007-11-29
> **jasay said:**
> "~" is your home directory.  ".wine" (note the period at the beginning) is a hidden directory so you will have to hit ctrl+h in nautilus or ctrl+. in konquorer to see it.

The other option is that wine has not been initialized yet.  Run winecfg in a terminal (Applications -> Accessories -> Terminal) and it should set everything up as well as let you make changes to the settings.

Thanks.  Now I have pasted the DLL file and three others that were recommended in an article I printed and still no sucess with e-Sword.  I hope someone running the program has an idea and btw, thank you for the help.

---

### Post by jasay on 2007-11-29
I've never run e-sword so I can't give any advice.  It might be that you are missing a font, but I have no idea which one.

Another option is to try one of the bible study programs for linux.  Have you tried gnomesword or bibletime?  They can both be found in the repos if you search for them in Synaptic (System -> Adminstartion -> Synaptic Package Manager)

---

### Post by jasay on 2007-11-29
Looking around a bit I found that creator of Ubuntu Christian Edition has made a .deb to install e-sword.  You should give that a try too.  See this thread: [http://ubuntuforums.org/showthread.php?t=372359](http://ubuntuforums.org/showthread.php?t=372359)

Edit: Sorry I just now tried downloading the file and get a 404 error.  I might have to ask mhancoc7 if he still has a working package.

Edit2:  Here we go: [http://www.christianubuntuukmirror.co.uk/ubuntuce/debs/esword-ubuntu_1.6_all.deb](http://www.christianubuntuukmirror.co.uk/ubuntuce/debs/esword-ubuntu_1.6_all.deb)  Download, double click to begin the install.  Then go to Applications -> Accessories -> e-Sword installer to finish the install.  Modules can be added with the e-Sword module manager.

---

