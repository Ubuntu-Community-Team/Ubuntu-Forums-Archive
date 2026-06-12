---
title: "Nokia Pc Suite alternative"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by armisz on 2007-06-09
Hi,plz help me-im pretty new to ubuntu.Is there any nokia pc suite alternative software to connect my nokia n80 to pc?

---

### Post by Skrynesaver on 2007-06-09
gnokii may be what you are after

---

### Post by Arwen on 2007-08-14
I installed  gnokii for my nokia N70but when I start it from applications a small window opens,showing connecting...But it never connects and moreover it crashes(not responding) when I try to close it.
I reinstalled gnokii a couple of times but it's still the same problem.Any ideas or any other alternatives of gnokii except Kmobile tools?I don't care about connecting to internet with my phone,I just want to manage my music and the pictures I have in it.
Thanx 4 any answer!

---

### Post by MrKlean on 2007-08-14
Lots of luck LOL!!   I looked too, and all I could come up with for my N75 was to dual boot xp, then switch to it JUST to use PC Suite !   I hate doiung it but there's no other way I have found.  I can transfer files back and forth...but for connecting.. dual boot seems the only way to go.  My 6102i worked with wvdial, but I can't get the N75b to work that way ; )  If you find something..lemme know ; )

---

### Post by Arwen on 2007-08-14
I don't know anything else except Kmobile tools,maybe it will work..:-k
In the end I'll not avoid installing wine(I'm sick of dual booting :-P):roll:
Or end up buying a bluetooth adaptor,so please ,if anyone knows one that works with nokia N70 and ubuntu let me know :)

---

### Post by Arjunanda on 2007-08-16
The latest Nokia phones are using OBEX protocol for communication. It is a binary protocol and requires another driver. I have N70 and have not been able to tranfer files to/from it this far. I have installed following:
cobex obexfs obexfto openobex-aoos
and these tools enable one to communicate with the phone. They are commandline tools, and not very user-friendly.
There is also nice Java based GUI called openobex-frontend that I am trying  right now, but I am stuck with the configuration, as bluetooth on my laptop is not working and  there is no documentation available howto configure this tool.

You can try these thing out - and I hope that the openobex-frontend will soon have some documentation and I would finally be able to access my files on my phone!

---

### Post by steveman2000 on 2007-08-16
I found my nokia e61 supports SyncML (Synchronization Markup Language). There has surely got to be something open source that uses it. I think i foudn one but was too lame to be able to get it installed and working (im a beginner).

---

### Post by Arjunanda on 2007-08-16
Update: Got my obexFTP frontend working. It was just permission issue. Finally I can tranfer files to and from my N70!

---

### Post by Arwen on 2007-08-28
Guys,what is that obexFTP frontend and how can I install it?
Thanx!

---

### Post by Arjunanda on 2007-08-29
Google obexFTP frontend gives you the answer you need. In the search, the first link is the project homepage, where you can download it. It is a Java application that can be used for trnsferring the files. Download the zip package, create a folder for it, extract the files there and run the app.

---

### Post by Arwen on 2007-08-29
It created a folder named "obexftp-frontend-0.6.2-bin",how can I run the app?

---

### Post by schorsch on 2007-08-29
```
cd obexftp-frontend-0.6.2-bin
chmod 755 Run.sh
./Run.sh
```
@arjunanda: Thanks for tip, it works great!

---

### Post by Arwen on 2007-08-29
Thanx but it fails when trying to access the / files of my nokia,it's connected via usb,is there sth I haven't installed?

---

### Post by Arjunanda on 2007-08-29
What is the error message?

---

### Post by schorsch on 2007-08-29
Sorry, I have tested if via Bluetooth on my Nokia N73. I just tried to get a connect via USB but I had no connect when using the "PC Suite" Mode. After that I just switched to "Data Transfer" Mode and after a few seconds a nautilus window popped up as I was recognized as a normal USB disk device.

---

### Post by Arwen on 2007-08-29
How do I get to Data Transfer mode?

@Arjunanda:Command failure.Tha following command has failed:Listing files under the / folder.
It happened when I pressed F5.

---

### Post by schorsch on 2007-08-29
You have to configure it on your phone .... somewhere in system configuration, data cable or something similar... at least there it is on my phone ...

---

### Post by Arwen on 2007-08-29
I can't find anything like that..

---

### Post by schorsch on 2007-08-29
What phone do you have?

---

### Post by Arwen on 2007-08-29
Nokia N70

---

### Post by schorsch on 2007-08-29
Perhaps it is hidden somewhere under "Connectivity" ....

---

### Post by Arwen on 2007-08-29
Maybe I have to create a new server profile but I have no idea how or if it's what I need.But that's the only thing I've found..

Edit:I found "Synchronisation" but there's no option for anything else but Web and Bluetooth for Nokia PC suite to synchronise....

---

### Post by Arwen on 2007-08-29
[http://news.softpedia.com/news/Transfer-Files-To-And-From-Your-Nokia-Phone-63116.shtml](http://news.softpedia.com/news/Transfer-Files-To-And-From-Your-Nokia-Phone-63116.shtml)
I followed the guide in that link but when configuration window shows up it's blank.I think sth is wrong with my java,the same problem I had when I was trying to install limewire(never solved so I used frostwire..)Any suggestions??

---

### Post by Arwen on 2007-08-29
Anyone?I found out that the obexftpfrontend/config.xml is missing that's why so many warnings and errors appear in terminal.Do you guys have that file in the obex installation folder?Thanx for any answer,I really don't know what's wrong.. :-S

---

### Post by Arjunanda on 2007-08-29
Here is what I have there
```

obexftp-frontend-0.6.1-bin$ ls
CHANGELOG.txt  LICENSE.txt          README.txt  TROUBLESHOOTING.txt
lib            OBEXFTPFrontend.jar  Run.sh

```
and in the lib subfolder
```

obexftp-frontend-0.6.1-bin/lib$ ls
jdom-1.0.jar  log4j-1.2.13.jar  OBEXFTPFrontend-Resources.jar
jhall.jar     looks-2.1.4.jar

```

Where did you get the idea you need such file?

---

### Post by Arwen on 2007-08-29
By the error I got.Sth is wrong with my java..That file is in the  .obexftpfrontend/ folder.That's all for now,I think I'll buy a bluetooth device or check it out again tomorrow,Thanx anyway!

---

### Post by schorsch on 2007-08-29
Well, do you have the right java version installed? What is the output of
```
java -version
```
And the mentioned config.xml will be created when you configure the frontend, I guess .....
@Arwen: Thanks for the last link! I can connect my N73 now also when it is in PC-Suite mode.

---

### Post by Arjunanda on 2007-08-29
Hmm, ObexFTP frontend was working for me, but when I went through the guide to do full configuration for it, it stopped working. The configuration dialog is blank and the thing wont connect to my Nokia anymore. Must be something with the device permissions.

---

### Post by schorsch on 2007-08-29
Which file have you edited in /etd/udev/rules.d and which line did you add or change there?

EDIT: There is an error in the line which is supposed to add to the udev-rules in the link Arwen gave. Instead of
```
BUS=="usb", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="043a", GROUP="plugdev", USER="marius"
```
you should add
```
BUS=="usb", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="043a", GROUP="plugdev", **OWNER**="marius"
```
Furthermore the files in the directory /etc/udev/rules.d/ are searched in order and the first rule that matches will win. So I created a file starting with a low number (e.g. 15-local.rules) to make sure that my rule matches first. I had to use this in the past to enable myself to write to CD/DVD as it was detected as a SCSI Device and got used to it.

---

### Post by Arjunanda on 2007-08-29
I edited the file /etc/udev/rules.d/040-permissions.rules. Actually that was a new file, so this is the only entry.
```
BUS=="usb", SYSFS{idVendor}=="0421", SYSFS{idProduct}=="043a", GROUP="plugdev", OWNER="MyUserName"
```

Oh now I see. When looking into the dir and reading the README file, I got it. It should be 40-permissions.rules and not 040-oersmissions.rules, as it was in the guide. I just blindly followed what was said, and not using my brains a single bit. Well, deleted the 040 file and made the change in the 40 file. Result: no difference.

This is what Ive got there
```

$ ls /etc/udev/rules.d00-init.rules          45-libgphoto2.rules                85-hdparm.rules
05-options.rules       45-libsane.rules                   85-hplj10xx.rules
20-names.rules         50-xserver-xorg-input-wacom.rules  85-hwclock.rules
25-dmsetup.rules       60-libpisock.rules                 85-ifupdown.rules
25-iftab.rules         60-symlinks.rules                  85-pcmcia.rules
30-cdrom_id.rules      65-persistent-input.rules          90-modprobe.rules
40-permissions.rules   65-persistent-storage.rules        95-hal.rules
40-permissions.rules~  80-programs.rules                  99-udevmonitor.rules
45-fuse.rules          85-alsa.rules                      README
45-hplip.rules         85-brltty.rules

```

Weird behavior. Still the settings dialog of obexFTP frontend is blank, with nothing in it, just a blank grey screen containing no text, fields neither buttons.

---

### Post by schorsch on 2007-08-29
Which java version are you using:
```
java -version
```

Edit: And there are two files starting with 40..... The one with the "~" at the end is a temporary file created by some editor so are you sure you closed any editor that was editing this file?

---

### Post by Arjunanda on 2007-08-29
Removed the double file and cheked that the right file is as it should. Still no change.

java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

---

### Post by schorsch on 2007-08-29
Hmm .. i am running the same java version .... right at the moment I have no idea ... stay tuned :-)

---

### Post by Arwen on 2007-08-30
I have the same version of java Arjunanda has.I changed user to owner in udev/rules.d.
In someone else's ubuntu obex works but he has in his config.xml [this]("http://rafb.net/p/9fC7HW63.html") instead of :

<?xml version="1.0" encoding="UTF-8"?> 
<java version="1.6.0" class="java.beans.XMLDecoder"> 
 <object class="net.sourceforge.obexftpfrontend.model.Configuration"> 
  <void property="documentExtensions"> 
   <string>.doc .xls .ppt .odf .pdf</string> 
  </void> 
  <void property="musicExtensions"> 
   <string>.mp3 .mid .amr .wav</string> 
  </void> 
  <void property="obexftpLocation"> 
   <string>/usr/bin/obexftp</string> 
  </void> 
  <void property="photoExtensions"> 
   <string>.jpg .jpeg .png .gif .bmp</string> 
  </void> 
  <void property="videoExtensions"> 
   <string>.avi .divx .3gp .mpg .mpeg</string> 
  </void> 
 </object> 
</java> 
-----
content of my config.xml.I copied and pasted the other config.xml on mine but I still have blank configuration window.If you are not too bored try it out and see if it works.
I hope there's no need to install any other java stuff(sdk or sth)
Good luck!

---

### Post by schorsch on 2007-08-30
I tested it with the config.xml you posted and it worked. I removed the directory ".obexftpfrontend" and on the next run it was recreated and the app was running.
Do you start it via a desktop launcher or by executing the "Run.sh" script in the directory you extracted it to? If using the first one there is a ".obexftpfrontend"-directory in your $HOME. If starting it the second way via "./Run.sh" you have the same directory in the actual directory.
There you will find a directory "log". Change there, remove all the files, try to start the program again and post the file "messages.log"

---

### Post by Arwen on 2007-08-30
By terminal,I get into obex dir and type that java -jar command.But it's the same thing as ./Run.sh..

messages.log:

2007-08-30 16:15:11,187 DEBUG 	 [main                ] Look and feel changed (at Main:51)
2007-08-30 16:15:11,191 INFO 	 [AWT-EventQueue-0    ] Displaying the application's main frame (at Main$1:38)
2007-08-30 16:15:11,226 DEBUG 	 [AWT-EventQueue-0    ] OBEXResponseParser object created (at MainFrameHelper:174)
2007-08-30 16:15:11,228 DEBUG 	 [AWT-EventQueue-0    ] Adding a CommandExecutionListener (at DefaultCommandQueue:75)
2007-08-30 16:15:11,229 DEBUG 	 [AWT-EventQueue-0    ] Queue object created (at MainFrameHelper:178)
2007-08-30 16:15:11,235 DEBUG 	 [AWT-EventQueue-0    ] CommandConsumer object created (at MainFrameHelper:183)
2007-08-30 16:15:11,235 DEBUG 	 [Command-Consumer    ] Trying to get the next command from the queue (at DefaultCommandConsumer:51)
2007-08-30 16:15:11,236 DEBUG 	 [Command-Consumer    ] Trying to take a command from the queue (at DefaultCommandQueue:49)
2007-08-30 16:15:11,939 DEBUG 	 [AWT-EventQueue-0    ] Created the ConfigurationListener list object (at ConfigurationDialogHelper:204)
2007-08-30 16:15:11,941 DEBUG 	 [AWT-EventQueue-0    ] Created the configuration persistence manager (at ConfigurationDialogHelper:207)
2007-08-30 16:15:11,941 DEBUG 	 [AWT-EventQueue-0    ] Created the OBEXResponseParser object (at ConfigurationDialogHelper:216)
2007-08-30 16:15:11,942 DEBUG 	 [AWT-EventQueue-0    ] Adding a CommandExecutionListener (at DefaultCommandQueue:75)
2007-08-30 16:15:11,947 DEBUG 	 [AWT-EventQueue-0    ] Created the CommandQueue object (at ConfigurationDialogHelper:220)
2007-08-30 16:15:11,947 DEBUG 	 [AWT-EventQueue-0    ] Started the CommandConsumer object (at ConfigurationDialogHelper:223)
2007-08-30 16:15:11,948 DEBUG 	 [Command-Consumer    ] Trying to get the next command from the queue (at DefaultCommandConsumer:51)
2007-08-30 16:15:11,948 DEBUG 	 [Command-Consumer    ] Trying to take a command from the queue (at DefaultCommandQueue:49)
2007-08-30 16:15:11,956 DEBUG 	 [AWT-EventQueue-0    ] Returning the current configuration (at ConfigurationDialogHelper:154)
2007-08-30 16:15:11,958 DEBUG 	 [AWT-EventQueue-0    ] ConnectionTest command created (at ConfigurationDialogHelper:226)
2007-08-30 16:15:11,964 DEBUG 	 [AWT-EventQueue-0    ] ObexFTP file chooser configured (at ConfigurationDialogHelper:262)
2007-08-30 16:15:11,965 DEBUG 	 [AWT-EventQueue-0    ] Trying to load the configuration (at XMLConfigurationPersistence:51)
2007-08-30 16:15:12,002 INFO 	 [AWT-EventQueue-0    ] Loaded the configuration from the disk (at ConfigurationDialogHelper:193)
2007-08-30 16:15:12,009 DEBUG 	 [AWT-EventQueue-0    ] Help info added successfully (at ConfigurationDialogHelper:325)
2007-08-30 16:15:12,015 INFO 	 [AWT-EventQueue-0    ] Configuration dialog ready (at ConfigurationDialog:44)
2007-08-30 16:15:12,020 DEBUG 	 [AWT-EventQueue-0    ] ConfigurationListener added (at ConfigurationDialogHelper:81)
2007-08-30 16:15:12,021 DEBUG 	 [AWT-EventQueue-0    ] Returning the current configuration (at ConfigurationDialogHelper:154)
2007-08-30 16:15:12,021 DEBUG 	 [AWT-EventQueue-0    ] Using the default XML entity resolver (at JDOMOBEXResponseParser:147)
2007-08-30 16:15:12,121 DEBUG 	 [AWT-EventQueue-0    ] FilePropertiesDialog is ready (at FilePropertiesDialog:38)
2007-08-30 16:15:12,126 DEBUG 	 [AWT-EventQueue-0    ] Application's actions created (at MainFrameHelper:165)
2007-08-30 16:15:12,182 DEBUG 	 [AWT-EventQueue-0    ] Done custom look and feel configuration (at MainFrameHelper:111)
2007-08-30 16:15:12,192 DEBUG 	 [AWT-EventQueue-0    ] Returning the current configuration (at ConfigurationDialogHelper:154)
2007-08-30 16:15:12,193 DEBUG 	 [AWT-EventQueue-0    ] ConfigurationListener added (at ConfigurationDialogHelper:81)
2007-08-30 16:15:12,194 DEBUG 	 [AWT-EventQueue-0    ] Adding a CommandExecutionListener (at DefaultCommandQueue:75)
2007-08-30 16:15:12,196 DEBUG 	 [AWT-EventQueue-0    ] File system tree configured (at MainFrameHelper:138)
2007-08-30 16:15:12,196 DEBUG 	 [AWT-EventQueue-0    ] Progress label configured (at MainFrameHelper:119)
2007-08-30 16:15:12,197 DEBUG 	 [AWT-EventQueue-0    ] Disabling showFilesProperties (at MainFrameHelper:287)
2007-08-30 16:15:12,197 DEBUG 	 [AWT-EventQueue-0    ] Disabling getSelectedFilesAction (at MainFrameHelper:244)
2007-08-30 16:15:12,198 DEBUG 	 [AWT-EventQueue-0    ] Disabling getAndRemoveSelectedFilesAction (at MainFrameHelper:247)
2007-08-30 16:15:12,198 DEBUG 	 [AWT-EventQueue-0    ] Disabling removeSelectedFilesAction (at MainFrameHelper:255)
2007-08-30 16:15:12,199 DEBUG 	 [AWT-EventQueue-0    ] Disabling refreshSelectedFoldersAction (at MainFrameHelper:263)
2007-08-30 16:15:12,199 DEBUG 	 [AWT-EventQueue-0    ] Enabling createFolderAction (at MainFrameHelper:271)
2007-08-30 16:15:12,199 DEBUG 	 [AWT-EventQueue-0    ] Enabling sendFilesAction (at MainFrameHelper:279)
2007-08-30 16:15:12,200 DEBUG 	 [AWT-EventQueue-0    ] Updating the initial enablement state of context menus (at MainFrameHelper:103)
2007-08-30 16:15:12,201 INFO 	 [AWT-EventQueue-0    ] Main frame ready (at MainFrame:34)
2007-08-30 16:15:18,280 DEBUG 	 [AWT-EventQueue-0    ] Restoring the initial dialog state before show the dialog to the user (at ConfigurationDialog:51)
2007-08-30 16:15:18,285 DEBUG 	 [AWT-EventQueue-0    ] Trying to load the configuration (at XMLConfigurationPersistence:51)
2007-08-30 16:15:18,291 INFO 	 [AWT-EventQueue-0    ] Loaded the configuration from the disk (at ConfigurationDialogHelper:193)
2007-08-30 16:15:18,292 DEBUG 	 [AWT-EventQueue-0    ] Enabling the connection components (at ConfigurationDialogHelper:272)
2007-08-30 16:15:21,199 DEBUG 	 [AWT-EventQueue-0    ] Closing the configuration dialog (at ConfigurationDialog:682)
-----------------
Configuration window has to pop up when obex starts?Cause I have to press F12 and enjoy the blank window :-P

---

### Post by philinux on 2007-08-30
If you just want to access all the files on your phone then goto applications graphics and fire up Gthumb. when phone is connected by usb it appears as a device, the internal card and any removable storage show up as folders.

anyway this is how I xfer files from my SE K810i

---

### Post by Arwen on 2007-08-30
I would be over the moon if it appeared as a usb device but it doesn't.Did you do anything to make it recognise as a usb device?

---

### Post by philinux on 2007-08-30
Nope just fired up Gthumb by accident when phone was connected, I was over the moon! :lolflag:
cos It didnt need any software installing.

---

### Post by nicolasdiogo on 2007-08-30
has anyone tried to install iSync from apple for this job.
i do not know how to install it but it could be an option.

---

### Post by schorsch on 2007-08-30
I have still no idea what is getting wrong on your side. As I do not know which version you use I installed v0.6.1 and v0.6.2 and in both versions I am able to open the configuration dialog properly. I checked the log files and could not detect any significant messages.
You mentioned in post #34 another config.xml that is working for another person. That one is preconfigured to use USB. Have you tried after installing it to query the root file system via "F5" and just forget about the configuration dialog?
I even get the configuration dialog properly when nothing is connected so the connection cannot be the cause for this behaviour......
@philinux: The Gthumb trick is not working on my Nokia N73 as these phones do not show up as regular USB devices when the phone is in "PC Suite" mode .. :-(

---

### Post by Arwen on 2007-08-30
Once again it was permissions issue,I was trying to save the correct version of config.xml with sudo gedit,it was saved and everything seemed ok but everytime I ran the app it changed to the old version.Finally I gave the whole folder "775" and saved my peace of mind.So the config.xml preconfigured to use usb is needed.
Finally F5 works! :-D 
Can you delete stuff from your mobile?Cause when I try to do it it says it may lead to corruption of the filesystem of device..

---

### Post by philinux on 2007-08-30
Can you put the phone in data transfer mode instead of pc suite that way gthumb might work.

Worth a try. Thats how my phone connects data transfer mode.

---

### Post by schorsch on 2007-08-30
@Arwen: I get same error message but I did not want to try it as there is ~ 1GB on the phone ;-)
@Philinux: On my N73 I can set the "data transfer mode" but we were not able to do this on Arwen's N70.

---

### Post by Arwen on 2007-08-30
@Philinux: Because there was no such option,neither with synchronisation.
@schorsch: I won't try it either,my MMC is 1GB too!
Thanx you all guys :-)

---

### Post by LordMau on 2007-09-02
Could someone please attach to this thread a copy of their usb enabled confg.xml? I also have the same issue of a blank configuraton dialog, and the posted link is dead. TIA.

---

### Post by schorsch on 2007-09-03
Here it is:
```

<?xml version="1.0" encoding="UTF-8"?> 
<java version="1.6.0" class="java.beans.XMLDecoder"> 
 <object class="net.sourceforge.obexftpfrontend.model.Configuration"> 
  <void property="documentExtensions"> 
   <string>.doc .xls .ppt .odf .pdf</string> 
  </void> 
  <void property="musicExtensions"> 
   <string>.mp3 .mid .amr .wav</string> 
  </void> 
  <void property="obexftpLocation"> 
   <string>/usr/bin/obexftp</string> 
  </void> 
  <void property="photoExtensions"> 
   <string>.jpg .jpeg .png .gif .bmp</string> 
  </void> 
  <void property="transport"> 
   <object class="net.sourceforge.obexftpfrontend.model.TransportType" method="valueOf"> 
    <string>USB</string> 
   </object> 
  </void> 
  <void property="value"> 
   <string>1</string> 
  </void> 
  <void property="videoExtensions"> 
   <string>.avi .divx .3gp .mpg .mpeg</string> 
  </void> 
 </object> 
</java> 
```

---

### Post by SOULRiDER on 2007-09-03
I couldnt make my Nokia 3100b work in Linux but i was using VMWare at the time so I installed the Nokia suite there and it worked correctly.

---

### Post by schorsch on 2007-09-03
Well, I was not able to connect to my N73 with PC-Suite running XP in a Virtual Box VM ... Some parts are detected .... but the most important parts not .. :-(

---

### Post by LordMau on 2007-09-05
much obliged schorsch.

I had to adjust the value for the usb transport here ```
  <void property="value"> 
   <string>1</string> 
  </void> 
```
to 0 and I was able to browse my SE k608.

---

### Post by Arjunanda on 2007-10-13
> **Arjunanda said:**
> Removed the double file and cheked that the right file is as it should. Still no change.


Sorry guys, I have got mine working with no problems. I just forgot to report back to the thread. I have been overly busy lately. Regarding the udev rules, I think udev got confused after I had changed the file several times. So after reboot it started working perfectly. Normally I never reboot, as there is no need, but that time my battery went flat and I eneded up restarting the system. After that obex-FTP frontend was working nicely :)

---

### Post by Arwen on 2007-11-02
Hello boys and girls!
I have a problem with obextfp: I can transfer files from my ubuntu to  my nokiaN70 but not from the phone to ubuntu.Till a couple of weeks ago everything was fine and I haven't done anything strange to nokia or ubuntu..I can also see errors in terminal when running ./Run.sh:
> 2007-11-02 15:07:10,785 INFO     [Command-Consumer    ] Trying to download a file from the device (at GetFilesCommand:74)
2007-11-02 15:07:30,411 WARN     [AWT-EventQueue-0    ] The action cannot be executed successfully due to some error in it's underlying commands (at GetSelectedFilesAction:175)
java.lang.IllegalArgumentException: The localFolder argument should point to a directory
        at net.sourceforge.obexftpfrontend.command.GetFilesCommand.<init>(GetFilesCommand.java:49)
        at net.sourceforge.obexftpfrontend.gui.action.GetSelectedFilesAction.addGetCommandsToQueue(GetSelectedFilesAction.java:169)
        at net.sourceforge.obexftpfrontend.gui.action.GetSelectedFilesAction.actionPerformed(GetSelectedFilesAction.java:95)
        at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
        at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
        at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
        at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
        at javax.swing.plaf.basic.BasicButtonListener.mouseReleased(BasicButtonListener.java:236)
        at java.awt.AWTEventMulticaster.mouseReleased(AWTEventMulticaster.java:273)
        at java.awt.Component.processMouseEvent(Component.java:6038)
        at javax.swing.JComponent.processMouseEvent(JComponent.java:3260)
        at java.awt.Component.processEvent(Component.java:5803)
        at java.awt.Container.processEvent(Container.java:2058)
        at java.awt.Component.dispatchEventImpl(Component.java:4410)
        at java.awt.Container.dispatchEventImpl(Container.java:2116)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4322)
        at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3986)
        at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3916)
        at java.awt.Container.dispatchEventImpl(Container.java:2102)
        at java.awt.Window.dispatchEventImpl(Window.java:2429)
        at java.awt.Component.dispatchEvent(Component.java:4240)
        at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
        at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
        at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
        at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
        at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
        at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)
2007-11-02 15:08:21,718 INFO     [Command-Consumer    ] Trying to download a file from the device (at GetFilesCommand:74)
2007-11-02 15:08:25,345 INFO     [Command-Consumer    ] Trying to download a file from the device (at GetFilesCommand:74)
2007-11-02 15:08:31,741 INFO     [Command-Consumer    ] Trying to download a file from the device (at GetFilesCommand:74)
2007-11-02 15:14:34,647 INFO     [Command-Consumer    ] Trying to download a file from the device (at GetFilesCommand:74)
2007-11-02 15:14:49,779 INFO     [AWT-EventQueue-0    ] Closing the application (at MainFrameHelper:413)


Does anyone know what caused this?

Thanx for any help!

---

### Post by mssg131187 on 2008-04-20
Is it possible to run Nokia PC Suite with Wine?  Also, can we update the firmware and everything using Wine?

---

### Post by dross_kuh on 2008-06-14
Nokia PC Suite runs fine on a virtualbox winxp install.
or i should say it runs fine on mine :)  Ubuntu hardy 8.04

---

### Post by twoseids on 2008-06-20
> **dross_kuh said:**
> Nokia PC Suite runs fine on a virtualbox winxp install.
or i should say it runs fine on mine :)  Ubuntu hardy 8.04
I'm sure Nokia PC Suite would work just fine on my VirtualBox XP install, except I can't get it to recognize the phone via bluetooth, and I can't get VirtualBox to recognize my USB for anything (phone included). But the program looks pretty.

Frustrated...

---

### Post by timjohn7 on 2008-06-26
> **twoseids said:**
> I'm sure Nokia PC Suite would work just fine on my VirtualBox XP install, except I can't get it to recognize the phone via bluetooth, and I can't get VirtualBox to recognize my USB for anything (phone included). But the program looks pretty.

Frustrated...

Have you got the latest Non-free Open source version of VirtualBox from the Sun site?
The Opensource version doesn't support USB at all.

Search VirtualBox on this forum for plenty of entries to install the latest version.

---

### Post by twoseids on 2008-06-28
Appreciate the tip. Will try it out!

---

