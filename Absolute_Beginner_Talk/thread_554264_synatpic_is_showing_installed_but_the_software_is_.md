---
title: "synatpic is showing installed but the software is missing"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by Faris on 2007-09-18
I installed some programs using synaptic, i can find them here in the S.P.M
BUT they aren't showing up in apps menu 
-----------
plz don't tell me "alacarte" because i can't find them there 
----------
here is what i do usually:
open S.P.M 
search for x 
mark x for install
and then after successfully completing the download and everything seems to be fine
oh ... where did that x go ?
well ... S.P.M  is telling me its there somewhere ... but where i don't know you tell me 
-----------------
when i was using windows i always  found   my programs in C:/programfiles/x
when i was using ubuntu    i never     found them ( except  in /usr/bin but i can't run them !?)

---

### Post by kelnage on 2007-09-18
Right, what's probably happening here is you're installing programs that don't have a graphical user interface. Could you give an example of a program that doesn't appear? Or do all programs you try to install not appear?

To run the programs found in /usr/bin, you'll have to open a "Terminal" and type the program name in - however, most programs require different options to be entered and honestly, I'll be able to help you more if you give examples to the programs that don't appear.

---

### Post by Faris on 2007-09-18
thanks
well some of them work and some don't 
"anon-proxy" 
does not work unless i use the terminal 
may  it has no gui work just in the terminal 
avidemux also but this one has a gui

---

### Post by kelnage on 2007-09-18
Right - for those command line programs there isn't much you can do about it except use them through the command line. You could try searching synaptic to see if there are any GUIs available for it - or try an alternative.

As for avidemux, I've just tried installing it on my machine and a icon appeared under "Sound and Video". If it hasn't for you, you could manually edit your menu (Right click on Applications, "Edit Menu") by adding a new item in which ever folder you wish for the program to be and entering "avidemux" as the command.

---

### Post by Faris on 2007-09-18
thanks again 
i manage to squeeze them in the apps menu
"avidemux" is appearing now and working  just fine  
as for "anon-proxy" no i couldn't  find others with gui or any alternative 
---------
i still want "anon-proxy" to work 
entering  "anon-proxy"  in the terminal works 
but there is nothing much to do with command lines
thanks anyway

---

### Post by kelnage on 2007-09-18
I've had a look into anon-proxy and it seems to do a similar job as [Tor]("http://tor.eff.org/"). If you are already using Firefox, you can get an extension for Firefox to work through Tor, which might be useful for you.

---

### Post by Faris on 2007-09-18
tor is also is installed but what is the firefox extension  ?

---

### Post by Faris on 2007-09-18
is it FoxyTor ?

---

### Post by kelnage on 2007-09-18
I believe FoxyTor is one. The add-on that Tor recommend is [TorButton]("https://addons.mozilla.org/en-US/firefox/addon/2275"). Hope that helps.

---

### Post by Faris on 2007-09-18
unfortunately neither  FoxyTor  nor TorButton is working 4 me :(
i guess ill  go back 2 windows to do this task 
----
jap is the windows equivalent to what i am using for ubuntu "anon-proxy"

---

### Post by Faris on 2007-09-18
i think i found something 
jap (which is the Linux equivalent )
[jap click here]("http://linux.softpedia.com/get/Internet/HTTP-WWW-/JAP-3220.shtml")
i downloaded the package called "JAP_00.05.056.src.tgz" and extracted it
and yes i stuck here i don't know how to proceed 
any help

---

### Post by Faris on 2007-09-19
i discovered that this file "jap.jar" is missing so i download it
and after runing the m file in the terminal and entering s to start
this is the output (expcetion):
Exception in thread "main" java.lang.NoClassDefFoundError: JAP
   at gnu.java.lang.MainThread.run(libgcj.so.70)
Caused by: java.lang.ClassNotFoundException: JAP not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.70)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at java.lang.ClassLoader.loadClass(libgcj.so.70)
   at gnu.java.lang.MainThread.run(libgcj.so.70)
------------
i know for sure i got java 
any help

---

### Post by Maestro23 on 2007-09-19
Have you tried these instructions:[http://anon.inf.tu-dresden.de/others/download_en.html](http://anon.inf.tu-dresden.de/others/download_en.html)

---

### Post by Faris on 2007-09-19
u see this is one of the  reasons i want to use jap
this site is blocked i can't get the instructions
[http://anon.inf.tu-dresden.de/others/download_en.html](http://anon.inf.tu-dresden.de/others/download_en.html)

---

