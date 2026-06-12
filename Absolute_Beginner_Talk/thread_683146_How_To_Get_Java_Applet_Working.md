---
title: "How To Get Java Applet Working"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-01-30
My problem is: 

I want to be able to upload many photo's at a time onto facebook, and a prompt pops up that says "Trust Applet, Trust Applet and add to Whitelist" and I click "yes" everytime, but then nothing loads and I cannot upload many pictures at once. 

How do I get this to work?
Is it a Java problem? If so, how do I fix it?

---

### Post by taurus on 2008-01-30
Do you think it is a java problem?  Let's see which version of java you're using right now.

```
java -version
```

---

### Post by jordank on 2008-01-30
This is what it says!

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)

---

### Post by jan quark on 2008-01-30
do you have java installed?
if not type this into the terminal

```
sudo apt-get install sun-java6-bin sun-java6-jre
```

I dont really know if this is a java issue but hey its worth a try

---

### Post by jordank on 2008-01-30
It doesn't look like anything installed...

kristie@Sparktop:~$ sudo apt-get install sun-java6-bin sun-java6-jre
[sudo] password for kristie:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manual installed.
sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by jan quark on 2008-01-30
no java is already installed and up-to-date

hmm let me think it over

---

### Post by taurus on 2008-01-30
You also have installed java plugin, right?

```
sudo apt-get install sun-java6-plugin
```

---

### Post by Auslegung on 2008-02-23
I'm having an identical problem, I have the most up-to-date java everything, I pass the test on the java website, and yes I can use the alternate method of uploading pictures but I'd rather not for two reasons 1) takes long as hell 2) it logs me out after I upload photos for the first time of any Facebook session.  Any other ideas?  Is it possible that the Ubuntu Firefox version just doesn't play nice with Facebook (I know nothing about programming and don't know if that suggestion is asinine or not).

---

### Post by Drakkenfyre on 2008-02-29
I'm having exactly the same problem, and it's pretty much making me the big bad wolf in this household for suggesting Linux in the first place, so if anyone could help me, I'd greatly appreciate it.

I try to upload photos using the Facebook photo upload applet as installed to Firefox 2.0.0.12.

Java version 1.6.0_03.

Yes I have the latest Java plugin.

I can view the applet and it did work for a time when using Internet Explorer 6.0 by IEs4Linux, but now it will work and then fail part-way through an upload. Sadly, I don't even know how to uninstall and reinstall an applet in either Firefox or MSIE for Linux, but given that the applet works fine for me in Seamonkey on Windows and IE on Windows, I suspect this is be an OS-related issue.

Another piece of information: When we happily unpacked our laptop with Linux pre-installed and went to Facebook photo upload, it asked two things: Would you like to install this applet and what would you like to run this applet with? I remember installing and adding this to the whitelist, and I later did it again after updating the browser, but I don't remember what the options were offered about what we should run it with or what we chose, other than that there were two kinds of Java offered.

I'm only confused because I thought that Java applets were supposed to be cross-platform.

Also, I have confirmation that it has worked for another Ubuntu Gutsy Gibbon user, but I don't know if any ritual sacrifice was involved. ;) In other words, I don't know how they got theirs to work or if it just did.

I'm going to keep hunting for the solution, so if I find anything, I'll report back.

---

### Post by Drakkenfyre on 2008-02-29
Hmmmm, I found this possible solution to your problem, which Dwarf007 posted on these forums:

> sudo apt-get remove gcj libgcj-common libgcj7-0

Sadly, I don't really know what it does. I mean, I get that you're getting root privileges in order to use apt-get to remove some libraries. However, I don't have any information on why that would be useful.

For me it had the effect of making the applet finally appear in Firefox. It failed a number of times when trying to upload photos. A message box would pop up in the photo uploading applet saying "Upload failed." I managed to get one photo uploaded. Of sixty.

Then I thought I should try a wired rather than a wireless connection. It worked!--sort of. They all uploaded, but then Firefox crashed.

So, I don't really have any answers as to how to get it to work properly, but there you go.

---

### Post by TheZergcorp on 2008-03-01
I am having the exact same issue. What doesn't make sense to me is that the applet was working fine up until January Twenty-something, and then simply ceased to function.

I downloaded Opera web Browser as an alternative, and even though pages are choppy as hell on there, the applet still functioned. Now, however (in the last few days) even that's been being difficult. I'll select all the files I want to upload and it gives the go-ahead, but suddenly about half the way through the browser window just up and leaves. Gone.

Extremely frustrating. I'd rather not have to load all my pictures onto a flash drive and go to a computer lab any time I want to upload my photos.


Anyone have a positive fix for this?

---

### Post by pickarooney on 2008-03-01
Struggling with this same problem fo a couple of weeks now. Fireuploader seems to be incompatible with facebook too.

---

### Post by Jetjoint on 2008-03-02
[SIZE="3"]Same problem here ............. just stopped working oneday![/SIZE]

---

### Post by okey666 on 2008-03-02
The gcj is the open source Java compiler/jvm, I used to have this trouble. I will try and remember how I solved it. I think it involved removing the gcj and then reconfiguring  what the command 'java' did.

---

### Post by okey666 on 2008-03-02
I remember editing symbolic links somewhere in firefox, anyone have any ideas what I could have done?

---

### Post by Auslegung on 2008-03-08
I've found that by using ie4linux or Opera you can upload photos to Facebook using the real applet.  ie4linux is so slow as to almost be useless, but Opera's not bad.  This had better be a temporary fix, however, as I'm really looking forward to being able to do this in Firefox3.

---

### Post by TylerRick on 2008-03-13
I'm having the same problem. 

Ubuntu 7.10 Gutsy
Architecture: amd64 (64-bit)
Firefox 2.0.0.12
icedtea-java7-plugin (7~b22-1.5~20071018-0ubuntu1)

I'm able to load other applets just fine, but not the Facebook photo uploader.

This is the backtrace I see when I start Firefox from the command line and go to the Facebook uploader page:

```

...
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback: setting status starting applet...
  PIPE: plugin read: status starting applet...
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status starting applet...
  PIPE: appletviewer read: instance-28210-2
  PIPE: appletviewer read: width 580
  PIPE: appletviewer read: instance-28210-2
  PIPE: appletviewer read: height 320
  PIPE: appletviewer wrote: status error: netscape/javascript/JSObject.
java.lang.NoClassDefFoundError: netscape/javascript/JSObject
        at java.lang.Class.getDeclaredMethods0(Native Method)
        at java.lang.Class.privateGetDeclaredMethods(Class.java:2445)
        at java.lang.Class.getDeclaredMethod(Class.java:1953)
        at java.awt.Component.isCoalesceEventsOverriden(Component.java:5785)
        at java.awt.Component.isCoalesceEventsOverriden(Component.java:5774)
        at java.awt.Component.access$100(Component.java:168)
        at java.awt.Component$3.run(Component.java:5739)
        at java.awt.Component$3.run(Component.java:5737)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Component.checkCoalescing(Component.java:5736)
        at java.awt.Component.<init>(Component.java:5705)
        at java.awt.Container.<init>(Container.java:271)
        at java.awt.Panel.<init>(Panel.java:65)
        at java.awt.Panel.<init>(Panel.java:57)
        at java.applet.Applet.<init>(Applet.java:66)
        at javax.swing.JApplet.<init>(JApplet.java:131)
        at com.aurigma.imageuploader.ImageUploader.<init>(Unknown Source)
        at com.facebook.facebookphotouploader.FacebookPhotoUploader.<init>(Unknown Source)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
        at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
        at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
        at java.lang.reflect.Constructor.newInstance(Constructor.java:539)
        at java.lang.Class.newInstance0(Class.java:373)
        at java.lang.Class.newInstance(Class.java:326)
        at sun.applet.AppletPanel.createApplet(AppletPanel.java:797)
        at sun.applet.AppletPanel.runLoader(AppletPanel.java:726)
        at sun.applet.AppletPanel.run(AppletPanel.java:380)
        at java.lang.Thread.run(Thread.java:675)
Caused by: java.lang.ClassNotFoundException: netscape.javascript.JSObject
        at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:201)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:324)
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback: setting status error: netscape/javascript/JSObject.
  PIPE: plugin read: status error: netscape/javascript/JSObject.
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback return
        at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:145)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:269)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:337)
        ... 28 more
Caused by: java.io.IOException: open HTTP connection failed.
        at sun.applet.AppletClassLoader.getBytes(AppletClassLoader.java:304)
        at sun.applet.AppletClassLoader.access$100(AppletClassLoader.java:62)
        at sun.applet.AppletClassLoader$1.run(AppletClassLoader.java:191)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:188)
        ... 32 more
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback: setting status Init: applet not loaded.
  PIPE: plugin read: status Init: applet not loaded.
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Init: applet not loaded.
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback: setting status Start: applet not initialized.
  PIPE: plugin read: status Start: applet not initialized.
GCJ PLUGIN: thread 0x619400: plugin_in_pipe_callback return
  PIPE: appletviewer wrote: status Start: applet not initialized.

```

Looks like it's a problem with this Java plugin implementation lacking Javascript support (netscape/javascript/JSObject)...

See [http://icedtea.classpath.org/bugzilla/show_bug.cgi?id=85](http://icedtea.classpath.org/bugzilla/show_bug.cgi?id=85)

---

### Post by SuperGiraffe on 2008-03-19
I had the same kind of problems using Ubuntu feisty fawn. facebook suddenly stopped uploading photos in firefox.

I updated firefox and java to the latest version and that appears to be the problem.
By linking to an earlier java plugin I got facebook working again.

of course, there is a post that says removing gcj works and another one saying if you download and install java 6 update 5 it works
[http://icedtea.classpath.org/bugzilla/show_bug.cgi?id=85](http://icedtea.classpath.org/bugzilla/show_bug.cgi?id=85)
If those don't work, then you should try what i did.

First thing to do is check the versions of java you have available, the command also gives you the option of choosing the java version you want to use but don't change it yet.

```
sudo update-alternatives --config java
```

install java 5 (an older version)

```
sudo apt-get install sun-java5-jre sun-java5-plugin
```

use the update alternative command again and select java5 

```
muz@HAL:~/.mozilla/plugins$ sudo update-alternatives --config java
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-sun/jre/bin/java
Press enter to keep the default[*], or type selection number:  

```
finally, you're going to link to the java plugin file from the older java version from the plugin directory in your profile folder. 

```
muz@HAL:~$ cd .mozilla/plugins/
muz@HAL:~/.mozilla/plugins$ ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
```

cd .mozilla/plugins/ (GO FROM YOUR HOME DIRECTORY TO YOUR FIREFOX PLUGINS DIRECTORY)
ln (LINK) -s (SYMBOLIC) /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/plugin/i386/ns7/libjavaplugin_oji.so (LOCATION OF PLUGIN FROM OLD JAVA VERSION)
libjavaplugin_oji.so (NAME OF LINK CREATED)

So this stuff got my photo uploader for facebook working in firefox so i don't need to individually upload dozens of photos or switch to windows. unfortunately it works only for individual users as far as i know but it's easy to switch back to java 6 by using the config commands and changing the link target.
tell me what you think of this information, it's my first post.
```

sudo apt-get install sun-java5-jre sun-java5-plugin
sudo update-alternatives --config java
```
(following command from home folder)
```
ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/plugin/i386/ns7/libjavaplugin_oji.so .mozilla/plugins/libjavaplugin_oji.so
```

---

### Post by kiisu on 2008-03-21
Drakkenfyre's suggestion at the bottom of the first page worked for me:

> sudo apt-get remove gcj libgcj-common libgcj7-0

It had the effect of crashing on me the first try but I think thats cause I was logged into the same site in 2 windows.
Second time it worked, I'll see if it holds up. This is in Epiphany though, haven't tried in FF.

---

### Post by Auslegung on 2008-03-21
I just did a fresh install of Gutsy and now it works.  I wouldn't suggest a fresh install just to upload pictures to Facespace, but it seems that having the latest version of stuff is the culprit and apparently I didn't.

---

### Post by ediblestarling on 2008-03-22
I don't know if this issue has been resolved elsewhere, but I got in working doing the following:

A)install java 6

B)remove gcj

C)reboot computer (probably not necessary) and then restart firefox

D)when the window popped up notifying me I needed a plug-in, I chose Java 6!! The first time I chose gcj and it didn't work! 

Since then everything has worked perfectly.

---

