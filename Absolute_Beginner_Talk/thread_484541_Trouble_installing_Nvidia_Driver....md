---
title: "Trouble installing Nvidia Driver..."
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by choppra on 2007-06-25
I have the 7 series Video card..

I'm assuming this is the driver I need...

When I try to run 'sh' on the .run file it gives me a error saying that I need to run it as root?

---

### Post by bodhi.zazen on 2007-06-25
> **choppra said:**
> I have the 7 series Video card..

I'm assuming this is the driver I need...

When I try to run 'sh' on the .run file it gives me a error saying that I need to run it as root?

Well, you need to run it as root then :```
sudo sh ./xXx.run
```

---

### Post by choppra on 2007-06-26
I'm confused..can you explain the command? I'm a total noob when it comes to Linux...still learning...

---

### Post by choppra on 2007-06-26
Also, I was never asked to setup the root password??

---

### Post by MorphingJar on 2007-06-26
Okay.  I'm in the same boat as choppra.  Though I've manage to get slightly further.

To make this entire process so much easier, I would copy the drivers you downloaded to yoru "home" folder.  This will give you easy access to them later.  Assuming your on a fresh install of Ubuntu like me, you need to first go to System -> Administration -> Synaptic Package Manager.  Then click the search button and search for libc6-dev.  Rightclick and mark that for installation.  Then hit apply.  The NVIDIA drivers will need this to compile itself.

Then you will need to shut down the "X server" which is apparently the GUI for Ubuntu.  In order to start and stop the X server,  you need to type the following

```
sudo /etc/init.d/gdm start
and
sudo /etc/init.d/gdm stop
```

Once you have the X server stopped, it will turn off the GUI and knock you to a command prompt.  Once there you will probably need to log into yourself again.  After that.  Type the following to start the install of the drivers

```
sudo sh "Driver.run" 
```

(Linux is extremely case-sensitive for just about eveything.  So type the file name for the driver exactly as it appears.)

You can type "dir" to see all the files and folders.  You should be located in your "home" directory just after logging in.  So if you coppied the driver there earlier you wont have to search for it.  Just follow the options and let it do its thing.  It should start compiling its own kernel or something.  make sure to back up your X config file.  You might need to revert back to it if something screws up.

Once thats done, start up the X server again using the earlier command and there you have it.  Your Nvidia drivers are now installed.

The only problem is.  I must be missing a step somewhere.  Because once I reboot my computer.  I get some sort of error saying that the X server is configured improperly and wont load.  It seems to work fine if you just start up the X server after installing the drivers.  But after a reboot.  Its hosed.  Anyone care to chime in and tell me what I didnt do?

---

### Post by bodhi.zazen on 2007-06-26
> **MorphingJar said:**
> Okay.  I'm in the same boat as choppra.  Though I've manage to get slightly further.

To make this entire process so much easier, I would copy the drivers you downloaded to yoru "home" folder.

You have the right idea. I save things like this in $HOME/src

In the src directory I would keep each app separate (ie nvidia, etc).

As far as your issue, I do not know. I have not installed the nvida driver that way.

Error message ?

I would re-install the nvidia driver you way and if it does not survive a re-boot, try the other way as outlined above.

---

### Post by PinkBullets9 on 2007-06-26
I think it is easiest just to use Envy to install the drivers. It does it correctly and is easiest for noobs like me.

---

### Post by MorphingJar on 2007-06-26
Apprarently theres some more insight to my specific problem here.

[http://ubuntuforums.org/showthread.php?t=481650](http://ubuntuforums.org/showthread.php?t=481650)

---

### Post by MorphingJar on 2007-06-26
okay very nice.  I followed Cappy's instructions on how to compile the drivers and everything is working fine now! type the following to check and change nvidia driver settings

```
nvidia-settings
```

---

### Post by bodhi.zazen on 2007-06-26
Run that as root :

```
gskudo nvidia-settings
```

Then use the "save changes" button (you can not save the changes as a normal user).

This will save your configuration settings (dual monitors/resolution/etc) WITHOUT having to manually editing /etc/X11/xorg.conf :twisted:

---

### Post by gimfred on 2007-07-17
```
You can type "dir" to see all the files and folders. 
```
Just a note, the equivilent command in all linux/unix systems is "ls" (maybe it stands for looksee). "dir" will work, but "ls" is the 'official' command.

---

