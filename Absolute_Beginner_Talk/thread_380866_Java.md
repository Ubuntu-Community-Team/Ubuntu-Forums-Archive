---
title: "Java?"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by adza on 2007-03-10
Hi there, i'm not sure to be happy or sad right now... i've downloaded the i586 jre file from java and (i think) installed it using sudo sh <filename>. It appeared to have worked and now i have a dir in my home directory called jre1.5.0_11. However that's all that's happened, when i try to verify the installation in the java website this fails, mozilla still can't figure out the plugin to install... ? I'm lost now.. i thought i just installed java?

p.s. i've installed the i586 version on my AMD64 following the advice on the java website, i'm running 32 bit firefox to overcome the flash issue....

---

### Post by overdrank on 2007-03-10
> **adza said:**
> Hi there, i'm not sure to be happy or sad right now... i've downloaded the i586 jre file from java and (i think) installed it using sudo sh <filename>. It appeared to have worked and now i have a dir in my home directory called jre1.5.0_11. However that's all that's happened, when i try to verify the installation in the java website this fails, mozilla still can't figure out the plugin to install... ? I'm lost now.. i thought i just installed java?

p.s. i've installed the i586 version on my AMD64 following the advice on the java website, i'm running 32 bit firefox to overcome the flash issue....

Hi I had a similar prob and it was lacking the flash. You may try automatix and get the flash through it. Worked for me  hope this helps. Good luck!

---

### Post by adza on 2007-03-10
i'm not having a problem with flash.. the jre and the java plugin for firefox is bumming me out though

---

### Post by overdrank on 2007-03-10
> **adza said:**
> i'm not having a problem with flash.. the jre and the java plugin for firefox is bumming me out though

Ok wel the automatix has sun java as well. Its what helped me. Maybe someone else will pop in and help. Good luck!

---

### Post by adza on 2007-03-10
paul, thanks but i don't have automatix installed.. i was going to not try and install it as i want to try to figure out how to manage this stuff without auto packages etc...

---

### Post by Perfect Storm on 2007-03-10
Tried this? 
[http://ubuntuforums.org/showthread.php?t=202537&highlight=java+64+bit](http://ubuntuforums.org/showthread.php?t=202537&highlight=java+64+bit)

---

### Post by phossal on 2007-03-10
A few thousand people have solved similar issues: [http://phossal.com/thread?view=702216931](http://phossal.com/thread?view=702216931).  You've already installed Java, though, so the instruction you're most concerned with is creating the symbolic link from the plugin in the Java folder (the one on your desktop) to /usr/lib/firefox/plugins (or wherever firefox is). 

The command will look something like this:
> sudo ln -s /home/**YOU**/jre1.5.0_11/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins

---

### Post by azteech on 2007-03-10
I have tried both the java 5 and java 6 downloads, both with jre. I find java is loaded, but when I go to firefox and enter in about:plugins, I find that the plugin has not been loaded. To so ensure I have the symbolic link loaded in properly, I did the following:

From a terminal window, I enter in the command

sudo ln -s /home/stevan/jre1.5.0_11/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins

I get the following response:

ln: creating symbolic link `/usr/lib/firefox/plugins/libjavaplugin_oji.so' to `/home/stevan/jre1.5.0_11/jre/plugin/i386/ns7/libjavaplugin_oji.so': File exists

when I go look at my home directory, select "view hidden files", I am not able to locate the directory 

jre1.5.0_11

Here is a copy of my directory listing for my home directory:

total 180
drwxr-xr-x 26 stevan stevan  4096 2007-03-10 13:00 .
drwxr-xr-x  7 root   root    4096 2007-02-21 02:09 ..
-rw-------  1 stevan stevan   648 2007-03-10 11:46 .bash_history
-rw-r--r--  1 stevan stevan   220 2007-02-20 18:31 .bash_logout
-rw-r--r--  1 stevan stevan   414 2007-02-20 18:31 .bash_profile
-rw-r--r--  1 stevan stevan  2227 2007-02-20 18:31 .bashrc
drwx------  3 stevan stevan  4096 2007-02-23 20:54 .config
drwxr-xr-x  2 stevan stevan  4096 2007-03-10 10:27 Desktop
-rw-------  1 stevan stevan    26 2007-02-21 01:47 .dmrc
drwxr-xr-x  6 stevan stevan  4096 2007-03-10 10:27 Documents
-rw-------  1 stevan stevan    16 2007-02-21 01:47 .esd_auth
lrwxrwxrwx  1 stevan stevan    26 2007-02-20 18:31 Examples -> /usr/share/example-content
-rw-r--r--  1 stevan stevan 13920 2007-03-06 04:00 .fonts.cache-1
drwx------  4 stevan stevan  4096 2007-03-10 11:46 .gaim
drwx------  6 stevan stevan  4096 2007-03-10 10:25 .gconf
drwx------  2 stevan stevan  4096 2007-03-10 13:22 .gconfd
drwxr-xr-x 21 stevan stevan  4096 2007-02-21 01:53 .gimp-2.2
-rw-r-----  1 stevan stevan     0 2007-03-10 11:49 .gksu.lock
drwxr-xr-x  3 stevan stevan  4096 2007-02-21 01:47 .gnome
drwx------ 12 stevan stevan  4096 2007-03-06 23:56 .gnome2
drwx------  2 stevan stevan  4096 2007-02-21 01:47 .gnome2_private
drwxr-xr-x  2 stevan stevan  4096 2007-02-21 01:47 .gstreamer-0.10
-rw-r--r--  1 stevan stevan    88 2007-02-21 01:47 .gtkrc-1.2-gnome2
-rw-------  1 stevan stevan   175 2007-03-10 10:25 .ICEauthority
drwxr-xr-x  2 stevan stevan  4096 2007-02-23 20:53 .icons
drwxr-xr-x  3 stevan stevan  4096 2007-03-10 11:22 .java
drwx------  3 stevan stevan  4096 2007-02-23 18:41 .macromedia
drwx------  3 stevan stevan  4096 2007-02-21 01:47 .metacity
drwx------  4 stevan stevan  4096 2007-02-23 18:40 .mozilla
drwxr-xr-x  3 stevan stevan  4096 2007-03-06 23:56 .nautilus
drwx------  3 stevan stevan  4096 2007-03-05 23:29 .openoffice.org2
-rw-------  1 stevan stevan  3714 2007-02-27 00:51 .recently-used
-rw-r--r--  1 stevan stevan  9565 2007-03-10 13:00 .recently-used.xbel
-rw-r--r--  1 stevan stevan     0 2007-02-23 01:09 .sudo_as_admin_successful
drwxr-xr-x  2 stevan stevan  4096 2007-02-23 20:53 .themes
drwx------  5 stevan stevan  4096 2007-02-24 11:26 .thumbnails
drwx------  2 stevan stevan  4096 2007-03-10 12:58 .Trash
drwxr-xr-x  2 stevan stevan  4096 2007-02-23 02:02 .update-manager
drwx------  2 stevan stevan  4096 2007-02-21 01:47 .update-notifier
drwxr-xr-x  2 stevan stevan  4096 2007-02-24 11:26 .wapi
-rw-------  1 stevan stevan   125 2007-03-10 10:25 .Xauthority
-rw-r--r--  1 stevan stevan  4939 2007-03-10 12:57 .xsession-errors

when I do this for java 6 version (which is the latest version I have loaded, I still get the same response - already exists - but alas, again no jre directory can be located.

When I look at the deployment file for java6 it shows

/usr/lib/jvm/java-6-sun-1.6.0.00/jre/bin/java

What am I missing, and how can I correct the problem so that java plug-in is properly installed in firefox.  Any help is greatly appreciated.

---

### Post by phossal on 2007-03-10
You said earlier that you had a Java directory on your desktop. Now you don't? The point is that wherever your JRE folder is, you want to make a link from the plugins folder inside to the /usr/lib/firefox/plugins folder. That's all. If you *do not* have a JRE with a plugins folder, you should download it from SUN.

Get version 6.

---

### Post by dstew on 2007-03-10
I used Synaptic to get the Sun Java jre version 5, with the plug-in. All I had to do was enable the Multiverse Synaptic repository, then get and install Sun Java jre. The plugin went to the correct place without any intervention on my part. I also have Dapper 6.06.

---

### Post by phossal on 2007-03-10
> **dstew said:**
> I used Synaptic to get the Sun Java jre version 5, with the plug-in. All I had to do was enable the Multiverse Synaptic repository, then get and install Sun Java jre. The plugin went to the correct place without any intervention on my part. I also have Dapper 6.06.

Usually works. Of course, you're a version behind. If the package manager fails, or you've tried to configure your system another way, the packages *don't* always work the way they're supposed to. Then it's as simple as making the link yourself. But, again, the issue doesn't seem to be that he *needs* Java.

---

### Post by adza on 2007-03-10
Success!! i've installed the jre v 5 from the instructions found in the post by AI... i should've tried there first as that's the post i found the instructions to get flash working properly doh! .. Nevermind, sorry for wasting ppls time on this post... however, like all good answers this leads me to another question, if i wanted to uninstall this software now (for example, if i wanted to go to version 6 or whatever) is it as simple as removing the directory i created the jre in (/usr/local/java32), then deleting the symbolic link in /usr/lib32/firefox32/plugins? Is this then uninstalled? Or is there a regedit or similar that i need to do?

---

