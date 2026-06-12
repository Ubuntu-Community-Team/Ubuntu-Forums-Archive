---
title: "Xbox 360 media streaming with x360mediaserve"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by capt scroggins on 2007-08-10
Hi. I know there is another recent post on this but it deals with Twonky and I would like to try x360mediaserve from here: [http://sourceforge.net/projects/x360mediaserve](http://sourceforge.net/projects/x360mediaserve). 

I recently made the switch to Ubuntu and the one thing that I have left to move from Windows is streaming media to my Xbox 360. I do not care about video but I would like to listen to my music. I have the files I need, I just can not figure out how to install them. I've tried using the website "How to install everything in Ubuntu" but I cannot get this "x360mediaserve" installed. I know this stems from my inability to install programs with anything but the repository. Here is the list of files in the archive if someone can just give me pointers on how to get this installed I would be greatly indebted:

Thanks for any help.

---

### Post by SOULRiDER on 2007-08-10
Thats java, first make sure that you have java installed or install it by doing:
```
sudo aptitude install sun-java6-jre
```

To start the program, move to the directory where it is located and type:
```
./start
``` If it complains about permissions type: ```
sudo chmox +x start
```

Good luck!

EDIT: Check the README file, theres some packages you might need to install for it to work well.

---

### Post by capt scroggins on 2007-08-10
Awesome. Thanks for your reply. I will try it when I get home and reply back.

---

### Post by capt scroggins on 2007-08-10
When I type "sudo chmox +x start" I get a command not found. I am running Ubuntu Feisty Fawn by the way.  What does this command do?

---

### Post by SOULRiDER on 2007-08-10
Doh, damn typ0s. Its chmod, with a D, not at x. The command should be:
```
sudo chmod +x start
```

Sorry about that :P

---

### Post by capt scroggins on 2007-08-10
That's cool. I figured it out by checking the file permissions in Nautilus (they were set to read-only instead of read and write). It actually helps that it didn't work because I learned many things along the way. Now when I run "./start" it gives me this message. I have Java 5 RE installed. Should that matter? Do I need 6?

ubuntu@ubuntu-desktop:~/Desktop/x360mediaserve-0.0.1$ ./start
Exception in thread "main" java.lang.UnsupportedClassVersionError: Run (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
ubuntu@ubuntu-desktop:~/Desktop/x360mediaserve-0.0.1$ 

I didn't know if this message was bad so I checked System Monitor and could not find the "x360mediaserv" process so I don't think it worked.

Thanks again for your patience.

---

### Post by capt scroggins on 2007-08-10
Thanks for your help Soulrider. I got it going. I had to uninstall JRE 1.4 and J5SE and then installed J6SE and now I didn't get any errrors and I can stream music to my 360. Unbelievable. It takes up less resources and loads faster than it did when I ran it from XP. I owe you a virtual beer.

---

### Post by esc1 on 2007-08-10
Hey I'm trying this after seeing your thread except I get this error:

Exception in thread "main" java.lang.NoClassDefFoundError: org/mortbay/jetty/Handler
        at net.sourceforge.x360mediaserve.newServlet.MediaServer.setUpWebServer(MediaServer.java:109)
        at net.sourceforge.x360mediaserve.newServlet.MediaServer.setup(MediaServer.java:100)
        at net.sourceforge.x360mediaserve.newServlet.MediaServer.<init>(MediaServer.java:70)
        at Run.main(Run.java:57)

---

### Post by capt scroggins on 2007-08-12
I am sorry. I can't help you there. I am an Ubuntu newbie. I just googled my error and found out I probably had conflicting versions of JAva. I would uninstall all Java references and then reinstall Java 6SE from Synaptic and see if that clears the error. I can assure you that when you get it working, it works like a dream. I can now stream all my music to my 360. I guess there is a way to also stream Internet radio after reading some helpfiles from [http://sourceforge.net/projects/x360mediaserve](http://sourceforge.net/projects/x360mediaserve).

Good Luck.

---

### Post by Colonel_Anya on 2007-08-13
Could someone please help me out with this? I think the problem stems from my lack of experience. I downloaded the file, opened the readme, downloaded the extra requirements, and opened the start. It opens in text editor, which is no god. I tried to open it in Nautilus but it won't show me the file. I'm confused as to what to do, and how to properly open the file. I'm relatively new to Ubuntu (I have Feisty Fawn). Any and all help is greatly appreciated!

---

### Post by capt scroggins on 2007-08-13
You need to open a terminal, change the directory (cd) to the directory where "start" is located and then type "./start xxx.xxx.xxx.xxx" where the x'es are the IP of your machine. Once this is running you go to the website and put in the path to your music. What got it working for me (besides Soulrider's help) was to go to the page for this on sourceforge.net and there is a forum. The developer posted exactly how to configure this on the x360mediaserve forum. Once I got my Java issue sorted out (had conflicting versions installed apparently) the developer's post on the forum was exactly what I needed. Here is the link. The paragraph that starts with "Now" is what you need I believe. Remember to post back whether it works or not. This will help other people.

[http://sourceforge.net/forum/forum.php?thread_id=1600567&forum_id=539937](http://sourceforge.net/forum/forum.php?thread_id=1600567&forum_id=539937)

Also if you get a permissions error (when trying to run "start") type this to allow you to execute start.  I think the default permissions are read-only and no execute.

sudo chmod +x start

---

### Post by esc1 on 2007-08-20
Which version of Java should I use?  I have 6 and I'm still getting errors:

Exception in thread "main" java.lang.UnsupportedClassVersionError: Run (Unsupported major.minor version 49.0)
        at java.lang.ClassLoader.defineClass0(Native Method)
        at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
        at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:123)
        at java.net.URLClassLoader.defineClass(URLClassLoader.java:251)
        at java.net.URLClassLoader.access$100(URLClassLoader.java:55)
        at java.net.URLClassLoader$1.run(URLClassLoader.java:194)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.net.URLClassLoader.findClass(URLClassLoader.java:187)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:289)
        at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:274)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
        at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)

---

### Post by capt scroggins on 2007-08-20
I can't tell you man. I am not a Java programmer but I would start by uninstalling all types of Java on your PC. Reboot your PC and then install Java 6SE and reboot again. Then try the steps I explained above to see if your 360 media server will start. Your error message is similar to mine but not the same so I would try to reinstall.

---

### Post by Sonic Reducer on 2008-05-14
i got this downloaded and had it running from the extracted folder on my desktop. i moved it to a hidden file in my /home directory and want to make it start when i start my computer.

the folder containing ./start is: /home/ryan/.x360MediaServe

my music directory is: /home/ryan/Music

and the address that i originally set everything up with (and i'm assuming didn't change) is: [http://127.0.0.1:7000/configure](http://127.0.0.1:7000/configure)

how can i make x360MediaServe load my music folder on boot?

---

### Post by Sonic Reducer on 2008-05-14
i posted a complete how-to just now covering downloading, hiding, setting up x360MediaServe, and setting it to start at boot.

once it's approved by a moderator i'll post a link here

---

### Post by cwill747 on 2008-06-06
If you install Java 6 and still have problems, do the following:

Run this command from the terminal

```
sudo update-alternatives --config java
```

Then select Java6 as the version that you wish to use. This was my problem. If this doesn't work, I don't know what else to do.

---

### Post by Sonic Reducer on 2008-06-06
> **cwill747 said:**
> Run this command from the terminal

```
sudo update-alternatives --config java
```

i've never seen that command before, what's it do?

---

