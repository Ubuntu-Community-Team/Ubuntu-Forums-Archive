---
title: "Java"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by bgast1 on 2008-04-20
Can somebody tell me how to install Java? I need it for a download manager for e-music. If I can't get this solved, I will have to go back to Windows, and the only thing I have installed right now is Hardy Heron.

---

### Post by OldTimeTech on 2008-04-20
Have you checked in the add/remove in the applications ....it has 3 different versions of java..this should work.

---

### Post by TJCIB on 2008-04-20
this thread gives some great tips for all sorts of media, java, flash, etc.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

helped me alot.

---

### Post by Fixman on 2008-04-20
Do you have the 64 bit version of Ubuntu or the 32 bit version?

---

### Post by bgast1 on 2008-04-20
I installed Java 6, now I just need to figure out the e-music thing.

---

### Post by bgast1 on 2008-04-20
Fixman -- I have the 32 bit version.

---

### Post by SOULRiDER on 2008-04-20
> **bgast1 said:**
> I installed Java 6, now I just need to figure out the e-music thing.

Could you elaborate?

---

### Post by bgast1 on 2008-04-20
SoulRider-- I am happy to elaborate, E-music is a subscription music service similar to iTunes, but it has a linux download manager available, but being the inexperienced and perhaps sometimes dense user that I am, I don't know what to look for when installing this download manager. There was a how to thread somewhere here in the Ubuntu forums, but for some reason I don't think that I am understanding what to do. 

I downloaded the file. /home/bob/Desktop/emusicj-linux-i686-0.24.tar.gz. Then I clicked on it and extracted it to my desktop. It happend so fast that I wasn't sure that it even extracted. 

Then the instructions said to click on the file 'emusicj' which I did, a box came up asking me to run in a terminal, cancel, or run. I chose run, but I don't think anything happened, and if it did it was so fast that I didn't notice it. 

Perhaps if I knew what to expect, I might understand better.

---

### Post by Fixman on 2008-04-20
You can use iTunes under Linux, just download Amarok.

---

### Post by bgast1 on 2008-04-20
But I am already subscribed to emusic and it costs me money every month, quite a bit less than itunes as well. Of course one option is canceling the service, but I happen to like it,

---

### Post by cardinals_fan on 2008-04-20
Open a terminal (Accessories -> Terminal) and type the following:
```
cd /home/yourusername/Desktop/emusicj-linux-i686-0.24/
./emusicj
```
Did that work?  If not, what happened?

---

### Post by bgast1 on 2008-04-20
Here's what happened.

```
bob@bob-desktop:~$ cd /home/bob/Desktop/emusicj-linux-i686-0.24/./emusicj
bash: cd: /home/bob/Desktop/emusicj-linux-i686-0.24/./emusicj: No such file or directory
bob@bob-desktop:~$ 

```

---

### Post by cardinals_fan on 2008-04-20
> **bgast1 said:**
> Here's what happened.

```
bob@bob-desktop:~$ cd /home/bob/Desktop/emusicj-linux-i686-0.24/./emusicj
bash: cd: /home/bob/Desktop/emusicj-linux-i686-0.24/./emusicj: No such file or directory
bob@bob-desktop:~$ 

```
Those were two seperate commands.  I should have been more clear ;)  Enter the 1st line, then enter the 2nd.

---

### Post by bgast1 on 2008-04-20
Finally after playing around with it I got this:

```
bob@bob-desktop:~$ cd /home/bob/Desktop/emusicj-linux
bob@bob-desktop:~/Desktop/emusicj-linux$ ./emusicj
Exception in thread "main" java.lang.UnsatisfiedLinkError: /home/bob/Desktop/emusicj-linux/lib/libswt-pi-gtk-3235.so: /home/bob/Desktop/emusicj-linux/lib/libswt-pi-gtk-3235.so: wrong ELF class: ELFCLASS64 (Possible cause: architecture word width mismatch)
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1676)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at nz.net.kallisti.emusicj.view.SWTView.setState(SWTView.java:144)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.google.inject.ConstructionContext$DelegatingInvocationHandler.invoke(ConstructionContext.java:111)
	at $Proxy12.setState(Unknown Source)
	at nz.net.kallisti.emusicj.controller.EMusicController.run(EMusicController.java:163)
	at nz.net.kallisti.emusicj.EMusicJ.<init>(EMusicJ.java:61)
	at nz.net.kallisti.emusicj.EMusicJ.main(EMusicJ.java:77)
/home/bob/Desktop/emusicj-linux


```

---

### Post by cardinals_fan on 2008-04-20
Do you have a version of jre installed?  Search Synaptic for 'jre' and see.

---

### Post by bgast1 on 2008-04-20
Yes. It says sun-java6-jre, The box is green. Maybe I should go to sun-java5-jre?

---

### Post by cardinals_fan on 2008-04-20
It runs fine on my Zenwalk system with JRE 6u5 installed.  So don't give up, it's definitely possible to run eMusic on your box.  Did you try the developers [tips on installing Java in Ubuntu]("http://www.kallisti.net.nz/EMusicJ/InstallingJava")?  Alternatively, you could try the eMusic remote beta at [http://www.emusic.com/dlm/download.html](http://www.emusic.com/dlm/download.html).

---

### Post by bgast1 on 2008-04-20
Still not getting anywhere. I would like to go to Sun's site to try, but I don't understand how to download and install from there. If not my downloads renew tomorrow night at 8:00 PM and I've already wasted a 10 download booster pack trying to get this to work. I may just have to reinstall windows, get my downloads, reinstall ubuntu and cancel my subscription if I can't get it to work. I've been trying so hard to be done with Windows.

---

### Post by cardinals_fan on 2008-04-20
Here are some instructions to try: download the [official eMusic installer]("http://www.emusic.com/remote/1.0/emusicremote-linux-installer.bin") to your desktop.  Open a terminal and enter the following (each line is a seperate command):
```
cd Desktop/
sudo chmod a+x emusicremote-linux-installer.bin
./emusicremote-linux-installer.bin
```
Another tip: hitting tab in the terminal will autocomplete either a command or a file name.  For example, on the last step, just start typing the name (after ./) and hit tab.  If nothing happens, hit it twice for a list of all options.

---

### Post by bgast1 on 2008-04-21
Thank you! Thank you! Thank you! You saved me from having to put windows back on my machine. I bought a Playstation 3 just last weekend so that I could play games and not have to use windows. Although I hope that I will still be able to play a few games through linux. Who ever heard of 56 year old Playstation 3 gamer?

By the way, I am a 56 year old Cubs fan. But for football I am a Greenbay Packer fan. Enough of this so that when and if you read this I will mark it solved. 

On emusic, I download metal, and I believe I go by bgast1 there too.

---

### Post by cardinals_fan on 2008-04-21
> **bgast1 said:**
> 
By the way, I am a 56 year old Cubs fan. But for football I am a Greenbay Packer fan. Enough of this so that when and if you read this I will mark it solved. 

Mark it solved, you Cubs-loving infidel :razz:

---

