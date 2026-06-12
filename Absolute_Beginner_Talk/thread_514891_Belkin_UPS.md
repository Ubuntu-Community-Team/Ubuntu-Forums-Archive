---
title: "Belkin UPS"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by mrkedvz on 2007-08-01
I am sooo new to Linux - How do I install the Belkin Bulldog Monitor for my UPS. I have the tar file but nothing seems to work.

---

### Post by Fraoch on 2007-08-01
I'm tacking on to this thread too - I just got a Belkin F6C1200-UNV and I can't get Bulldog installed.

mrkedvz - you should have been provided with a CD that comes with Linux install packages.  Amazingly mine comes with several Linux install packages - Linux, LinuxAMD64, GenericUnix, etc.  These programs are also available at the Belkin website.

I made a little progress but encountered a fatal error which I can't overcome.  You have to extract the files and change their permissions.  What I did was extracted them to a "temp" folder on my desktop and then executed:

```
cd Desktop/temp
sudo chmod 777 -R *
```

Then:

```
./setup.bin
```

which unfortunately returns:

```
Exception in thread "main" java.lang.NoClassDefFoundError: com/zerog/lax/LAX
```

which is where I'm stuck.  Some sort of Java problem.  There's also a setup_console.bin, which I gather has a GUI, but it returns the same error.

There are generic Linux packages to handle UPSes but they seem to be extremely complicated.  I've installed them all but configuring them is very difficult at my skill level.:(

I'll try Belkin support but I'm expecting either "Linux?  What's that?" or "Please make sure your computer is turned on.  Then turn on your UPS.  Now install the software."

---

### Post by Fraoch on 2007-08-01
More investigation:

There are several points in the Belkin documentation that indicate JRE (Java) 1.3.1 is required.

That's a very old version and it's no longer even available for install.  I have JRE 1.5.0 installed.  I'm thinking this software is incompatible with JRE 1.5.0, so that's the end of the road.

I've been banging my head against nut (one of the Linux USB apps) for several hours now without success.  My UPS is even listed as supported but I don't know how to define a USB port in "/dev/" terms, and when I say port = auto it has no idea.

---

### Post by Fraoch on 2007-08-03
Well mrkedvz - I'm thinking we have two different versions here, because I clearly don't have the source file.  I'm trying to install "Bulldog v2", are you trying to install "Bulldog Plus"?  What UPS do you have?

Anyway, I gave up on Bulldog.  Belkin's only suggestion was "reinstall Java".  Sorry, no.  Java's working just fine for everything else.  I tried it on my other machine that has JRE 1.6, same error.

It's no big deal because I managed to install [nut]("http://www.networkupstools.org/") and get it working.  It's the new version 2.2.0, and I installed from source - the version in the Ubuntu repositories is 2.0.5 and doesn't support my UPS.  All I need is to configure my startup/shutdown scripts and I have no idea how...

But to install from source there should be a README or INSTALL file in the archive.  You can also follow these instructions:

[http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing/#installing_a_package_manually)

---

### Post by Themicles on 2007-10-19
I have a Belkin 1500VA UPS that I'd like to install Bulldog Plus on my Ubuntu server for...

I have a Windows computer that is directly connected, and would like to get Bulldog Plus installed as a network slave.

Anyone made any progress with this or have any other suggestions on how I can remotely shut down my Ubuntu server from the Windows computer automatically on a low battery event?

---

### Post by Themicles on 2007-10-19
Alright, I have Bulldog Plus v1 installed. It appears to work properly, though I have yet to test any specific events. Have to wait for users to not be logged in for that...

Place the TAR file in YourTempDir (replace YourTempDir with a directory of your choosing)
To install:
```
cd /YourTempDir
tar -xvf LINUX.TAR
```
I had to do
```
 sudo chmod 777 -R *
```
 to get the next step to work:
```
sudo ./install
```
Follow the steps on screen...

Since I only needed this to be a network slave, I didn't mess with setting it up on USB or Serial.

If anyone wants to refine my instructions feel free. I am very much a Linux newbie. Running ./install requires sudo or it will give you an error saying you must be logged in as root.

---

### Post by Lord C on 2007-11-24
> **Fraoch said:**
> 
```
cd Desktop/temp
sudo chmod 777 -R *
```

Then:

```
./setup.bin
```

which unfortunately returns:

```
Exception in thread "main" java.lang.NoClassDefFoundError: com/zerog/lax/LAX
```
"

I had this error when I try to run it from the desktop, if you run it straight from the CD you should be fine.

---

### Post by Fraoch on 2007-11-24
> **Lord C said:**
> I had this error when I try to run it from the desktop, if you run it straight from the CD you should be fine.

Did it work for you off the CD?

It didn't work off the CD for me either.

I'll try again though.

---

### Post by Fraoch on 2007-11-24
Anything I try off the CD, either setup.bin or setup_console.bin, results in "permission denied" even with sudo.

```
mark@Sauron:/media/cdrom/LinuxAMD64$ sudo ./setup.bin
sudo: unable to execute ./setup.bin: Permission denied
mark@Sauron:/media/cdrom/LinuxAMD64$ sudo ./setup_console.bin
sudo: unable to execute ./setup_console.bin: Permission denied
```

How did you get it to work, Lord C?

---

### Post by Lord C on 2007-11-24
I used the Linux dir, not the LinuxAMD, and I just double clicked the setup bin. This launched a nice Java installation.

After installing, to run the program you need:

cd /opt/upspilot
sudo ./agent start
sudo ./monitor

It launches a nice java app.
And this is the point where it should detect your USB UPS.
If it doesn't click "System > Administrator" (default pass is Administrator), then "System > Auto Search UPS".

My PC fails to find the UPS at all.
I don't know if I'm supposed to add some /dev/usb device to System > Com Port Settings.

> lordc@umbongo:~$ lsusb
Bus 008 Device 001: ID 0000:0000  
Bus 009 Device 001: ID 0000:0000  
Bus 007 Device 004: ID 0665:5161  
Bus 007 Device 003: ID 0a5c:200a Broadcom Corp. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 046d:c50e Logitech, Inc. MX-1000 Cordless Mouse Receiver
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 038: ID 04a9:170a Canon, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 047f:0ca1 Plantronics, Inc. 
Bus 002 Device 001: ID 0000:0000
Logitech mouse, Canon printer, Plantronics headset, Broadcam bluetooth device, and there's one more without a name :o maybe that's it.
...yes. After testing, it seems "0665:5161 " is my UPS.

Now how to I let Winpower find Bus 007 Device 004: ID 0665:5161  ?

---

### Post by Fraoch on 2007-11-24
> **Lord C said:**
> I used the Linux dir, not the LinuxAMD, and I just double clicked the setup bin. This launched a nice Java installation.

The problem is, when I double-click it just opens the script in a text editor!  Right-clicking brings up the option to open in other editors, but nowhere can I actually *execute* the script.

I'm using AMD64 because that's the architecture I'm using, but I also tried Linux and GenericUnix with the same result.

---

### Post by Fraoch on 2007-11-24
> **Lord C said:**
> Have any of you guys actually identified the device connected to your PC in anyway? If so let me know how I can check please

In the hopes that you can help me out :-) here's my lsusb:

```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0665:5161  
Bus 001 Device 005: ID 04b8:0002 Seiko Epson Corp. ISD Smart Cable for Mac
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 062a:0000 Creative Labs Optical Mouse
Bus 002 Device 003: ID 04a9:2204 Canon, Inc. CanoScan FB630U
Bus 002 Device 001: ID 0000:0000 
```

This is the one, you have it as well:

Bus 001 Device 004: ID 0665:5161

I believe in my research to get NUT working, 0665:5161 is a generic USB-to-serial adapter, it's not specifically Belkin.

BTW I never did get NUT fully working, I can get it to report data on the UPS but I never got it to execute a shutdown command when the UPS battery runs low, or even restart when the PC restarts.  This is despite help from the developer, I just don't have the skill.:(

---

### Post by Lord C on 2007-11-24
Wow this gives me a headache. Been playing with nuts for ages. What driver did you use?

I tried > [belkin]
driver = megatec
port = auto But it didn't like the "auto". Wanted an actual device.

As for your problem...

> mark@Sauron:/media/cdrom/LinuxAMD64$ sudo ./setup.bin
sudo: unable to execute ./setup.bin: Permission denied
I don't understand why you get permission denied even with sudo.

This is what my /etc/fstab looks like as far as the cd rom is concerned.
> /dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by Fraoch on 2007-11-24
> **Lord C said:**
> Wow this gives me a headache. Been playing with nuts for ages. What driver did you use?

megatec_usb, it's in NUT 2.2.0.

> I tried  But it didn't like the "auto". Wanted an actual device.

I believe this is solved if you use megatec_usb in 2.2.0.  But I'll look into it.

> As for your problem...


I don't understand why you get permission denied even with sudo.

This is what my /etc/fstab looks like as far as the cd rom is concerned.

My fstab is exactly the same.:(

---

### Post by Lord C on 2007-11-24
I used megatec, didn't see a megatec_usb, and I am using the latest nut I believe :/

[Edit]
Was using old nut, it works now - well, to some extent. It detects my UPS anyway. Now to play with the damn configs etc.

---

### Post by Lord C on 2007-11-25
If you can't get winpower to install, try bulldog plus...
[http://www.belkin.com/uk/support/article/?lid=enu&pid=F6C1000eiTW-RK&aid=6153&scid=0](http://www.belkin.com/uk/support/article/?lid=enu&pid=F6C1000eiTW-RK&aid=6153&scid=0)

Extract it somewhere, then just do sudo ./install
It is a quick command based install (I installed with options *Enter, 1, /dev/usb, y*)

The daemon is /usr/local/bulldog/upsd
And the GUI is /usr/local/bulldog/monitor

When I open my monitor, it doesn't detect my damn USB connection to the UPS - just the same as with Winpower.

I have finally got NUT to detect it, but NUT is a pain in the **** - I have no idea how to set it up, it's such a long winded headache process.

---

### Post by Catweasle on 2007-11-28
I had the java LAX error and the Permission denied errors also.

Finally I got it to work by running 
 sudo update-alternatives --config java
then selecting the correct java version from the options presented.  You can find this by typing 
  java -version

Then I copied the entire CD from Belkin into a directory on the harddrive and did a chmod -R 777 * on that directory.

Then 
 cd /mydirectory/Linux
 sudo ./setup_console.bin

This time it all installed fine.  I suspect the actual cure was copying the entire CD to harddrive, not just the Linux directory.

Hope this helps.

---

### Post by Lord C on 2007-11-28
Catweasle, after installing, are you actually able to use the program?

---

### Post by Fraoch on 2007-11-28
> **Lord C said:**
> Was using old nut, it works now - well, to some extent. It detects my UPS anyway. Now to play with the damn configs etc.

That's where I'm stuck.  You need to create and edit startup scripts.  Well outside my expertise.

Copying the entire Bulldog Plus CD sounds like a good idea though, I suspected the errors I'm getting were the installer not finding certain files.

Catweasle - which java version is the "correct" version?

---

### Post by Lord C on 2007-11-28
For me it was java version "1.6.0_03"

---

### Post by Fraoch on 2007-11-28
> **Lord C said:**
> For me it was java version "1.6.0_03"

That's the one I have...

---

### Post by Fraoch on 2007-11-28
I finally did get it to install by copying the entire CD, but it doesn't run:

```
mark@Sauron:/opt/upspilot$ ./agent start
 Starting Agent: 
./Agent: line 1515:  6599 Segmentation fault      (core dumped) "/opt/upspilot/jre/bin/java" com.zerog.lax.LAX "/opt/upspilot/./Agent.lax" "/tmp/env.properties.6557"
 Done
mark@Sauron:/opt/upspilot$ ./monitor
 Starting Belkin Automatic Power Management Software Manager: 
./Manager2: line 1515:  6657 Segmentation fault      (core dumped) "/opt/upspilot/jre/bin/java" com.zerog.lax.LAX "/opt/upspilot/./Manager2.lax" "/tmp/env.properties.6615"
 Done
```

Segmentation fault = baaaaaad!!:(

---

### Post by Lord C on 2007-11-28
Install the latest Java through synaptic. Looks like it's definitely Java problems Mark.

---

### Post by Fraoch on 2007-11-29
But Java is the latest, Synaptic doesn't have anything newer.

I've always found the various Java packages and names confusing, there's the app itself, the runtime environment, another thing - they're named JDK, JRE, JEE, jeez.

Anyway I have:

sun-java5-bin 1.5.0-13-0ubuntu1
sun-java5-jre 1.5.0-13-0ubuntu1
sun-java6-bin 6-03-0ubuntu2
sun-java6-jre 6-03-0ubuntu2

and when I type java -version I get:

```
mark@Sauron:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)
mark@Sauron:~$
```

I'm thinking I may have two versions installed though?  Should I remove the "java5" components?  Don't see how that will help based on what the CLI is returning, it seems to be using java6 (i.e. 1.6).

Java was a PITA on Windows and it continues to be so in Linux.:mad:

---

### Post by Lord C on 2007-11-29
Yeah i'd install java5 if I were you. Worth a shot, I can't see you needing two versions.

Java is never simple :/.

It's definitely JRE you need, the Runtime environment.

---

### Post by alizard on 2008-01-08
From the Belkin UPS help menu - UPS Communications Interface:
quote--------------------------------------------------------------------
UPS Communication Interface
Belkin Automatic Power Management Software communicates with UPS through RS232 . . .
Note: Only in Windows 98/2000/2003/XP/Vista and Mac OS X can use the USB port.
end quote ---------------------------------------------------------------

BTW, thanks for the person who posted about update-alternatives. I'd spent the last several hours trying to set PATH in some manner that the Belkin UPS software can actually read.

IOW, Belkiin screwed up, and since it's proprietary, solutions have to come from them. I'd waited quite some time for Belkin to update it's originally adequate Belkin Sentry Bulldog software to compatibility with modern Linux versions. It figures that they'd finally release a Linux version that can't read the USB port.

So our options are to complaint to belkin or figure out nut.

---

### Post by idomagic on 2008-01-22
Hmm, anyone tested this?
[http://www.hostingforum.ca/134714-get-belkin-bulldog-usb-working-under-newer-linux-distros.html](http://www.hostingforum.ca/134714-get-belkin-bulldog-usb-working-under-newer-linux-distros.html)

"To get Belkin Bulldog USB working under SuSE 10.x or SLE 10 you will
need to create the following device:

mkdir /dev/usb
mknod /dev/usb/hiddev0 c 180 96"

Seems to work for me, using bulldog 3.01.18 on feisty.


edit: nvm, scratch that, was just referring to the following upsd told me:
"Broadcast Message from root@UltiServer                                         
        (somewhere) at 2:36 ...                                                
                                                                               
UPS Connection Established!  "

Monitor gives segmentation fault though

(edit2: and "Exception in thread "main" java.lang.NoClassDefFoundError: /usr/local/bulldog/monitor" when trying with java 1.5 or 1.6)

---

### Post by idomagic on 2008-01-23
Well, the connection does work to my ups, I've connected a slave bulldog (running on windows) via the network and everything is reading out fine, all settings are available as well so I won't dwelve deeper into getting the gui/monitor running on my server.

---

### Post by Fraoch on 2008-01-25
> **idomagic said:**
> mkdir /dev/usb
mknod /dev/usb/hiddev0 c 180 96"

I had high hopes for this one but:

```
mark@Sauron:~$ sudo mkdir /dev/usb
mkdir: cannot create directory `/dev/usb': File exists
mark@Sauron:~$ sudo mknod /dev/usb/hiddev0 c 180 96
mknod: `/dev/usb/hiddev0': File exists"
```

---

### Post by idomagic on 2008-01-25
So "/usr/local/bulldog/upsd" is still failing for you?

Do you have "/usr/local/bulldog/PRO_UPS.LOG"?
If so, what does it say?

The java issues should really only apply to getting the monitor itself running, afaik the daemon should be able to run (and execute commands) without the monitor.

---

### Post by qgfreire on 2008-06-09
Hello,
I solved the problem of USB port not found on Hardy  2.6.24-18-386, Winpower 2.2.0.0 on :
lsusb
Bus 003 Device 002: ID 06da:0003 Phoenixtec Power Co., Ltd 


Mustek 1kVA by selecting with
sudo update-alternatives --config java:

java version "1.6.0_06"
Java(TM) SE Runtime Environment (build 1.6.0_06-b02)
Java HotSpot(TM) Client VM (build 10.0-b22, mixed mode, sharing)




And sudo ./agent stop
sudo ./agent start
sudo ./monitor
and marvelous, 1st time it works after ubuntu 7.04!
FGF
----------------------------------------------

PS.
After some days, 1 week, with some last actualizations of Ubuntu Hardy, all went wrong again. The ups respond for one minute and in the next minute it disappears from the winpower monitor panel.
Uninstall
Install  winpower 2.2.0 (from Belkin, mine is Mustek "label believing") and all working fine again!

---

