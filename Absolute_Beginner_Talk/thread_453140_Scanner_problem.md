---
title: "Scanner problem"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by bob74 on 2007-05-24
Feisty does not recognise my Canon FB620P scanner. It is on the same parallel port
as my Epson printer which is OK. Any ideas Please.

---

### Post by Martin on 2007-05-24
Have you started xsane? - It will be xsane that searches for the scanner.

---

### Post by bob74 on 2007-05-24
Thanks for your quick response. X-sane opens up my TV card BT878 and not the scanner.
Any other ideas, please?

---

### Post by Martin on 2007-05-24
[http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon+&model=FB620P&bus=par&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=Canon+&model=FB620P&bus=par&v=&p=)
The above link shows that your scanner is supported to some extent.
I don't have any experience with TV cards. Sorry

---

### Post by klytu on 2007-05-24
> **bob74 said:**
> Feisty does not recognise my Canon FB620P scanner. It is on the same parallel port
as my Epson printer which is OK. Any ideas Please.

Disconnect the power cord on the scanner for about 5-10 seconds, then plug it back in. Now try this command in a terminal window: ```
gksudo xsane
``` If xsane now recognizes your scanner, then read this thread: [http://ubuntuforums.org/showthread.php?t=428493](http://ubuntuforums.org/showthread.php?t=428493)

Post back what happens or if you have any questions. I have the same scanner working under Feisty.

---

### Post by bob74 on 2007-05-24
Sorry about delay in coming back to you but I had some personal problems to sort out. 
I did as you suggested and a window popped up saying "you are trying to run XSane as root, THAT REALLY IS DANGEROUS. Do not send any bug reports when you have any problems while running XSane as root--You are alone" Then the choice was ro Cancel or continue at your own risk.
I tried the continue and again it found only my TV card)Hauppauge BT878 etc.)

---

### Post by klytu on 2007-05-24
> **bob74 said:**
> Sorry about delay in coming back to you but I had some personal problems to sort out. 
I did as you suggested and a window popped up saying "you are trying to run XSane as root, THAT REALLY IS DANGEROUS. Do not send any bug reports when you have any problems while running XSane as root--You are alone" Then the choice was ro Cancel or continue at your own risk.
I tried the continue and again it found only my TV card)Hauppauge BT878 etc.)

OK. The warning message is normal, don´t worry about that for now. Let´s make sure the correct sane backend configuration files are in place. First do: ```
sudo gedit /etc/sane.d/dll.conf
``` Make sure canon_pp is listed and does not have a # in front of it. If canon_pp has a # in front of it, delete the #; then save and close the file. The file should look similar to this when you are done: > # /etc/sane.d/dll.conf - Configuration file for the SANE dynamic backend loader
#
# On Debian systems, the dll backend will also look for pieces of configuration
# in the /etc/sane.d/dll.d directory -- packages providing backends should drop
# a config file similar to dll.conf in this directory.
#

# enable the next line if you want to allow access through the network:
net
abaton
agfafocus
apple
avision
artec
artec_eplus48u
as6e
bh
canon
canon630u
canon_pp
coolscan
coolscan2
#dc25
#dc210
#dc240
dell1600n_net
dmc
epson
fujitsu
#gphoto2
genesys
gt68xx
hp
hpsj5s
hp3500
hp4200
hp5400
ibm
leo
lexmark
ma1509
matsushita
microtek
microtek2
mustek
#mustek_pp
mustek_usb
mustek_usb2
nec
niash
pie
pixma
plustek
#plustek_pp
#pnm
qcam
ricoh
s9036
sceptre
sharp
sm3600
sm3840
snapscan
sp15c
#st400
#stv680
tamarack
teco1
teco2
teco3
#test
u12
umax
#umax_pp
umax1220u
v4lNext do: ```
sudo gedit /etc/sane.d/canon_pp.conf
``` This file should look like this:> # Define which port to use if one isn't specified - you should only have 
# one of these lines!
# This is the default port to be used - others will be detected
ieee1284 parport0


# Define the location of our pixel weight file, can begin with ~/ if needed.
# You can have as many of these as you like - lines with ports that don't exist # will be ignored.
#
# Parameters are:
# calibrate /path/to/calibration-file port-name
#
# The format of port-name is dependant on your OS version.
#
# If a file isn't speficied, the default name will be
# ~/.sane/canon_pp-calibration-[port-name]

calibrate ~/.sane/canon_pp-calibration-pp0 parport0

# calibrate /etc/sane/my_calibration parport1


# Enable the next line if you're having trouble with ECP mode such as I/O 
# errors.  Nibble mode is slower, but more reliable.

#force_nibble

# Set a default initialisation mode for each port.  Valid modes are:
# AUTO		(attempts to automatically detect by trying both methods)
# FB620P	(10101010 style.. also works for FB320P)
# FB630P	(11001100 style.. also works for FB330P, N340P, N640P)

# init_mode AUTO parport0
init_mode FB620P parport0
# init_mode FB630P parport0 The important part is the line>  init_mode FB620P parport0 If these files are both in place and set up correctly, then xsane is seeing your TV card as its default scanning device.  You´ll need to name the Canon scanner explicitly when invoking xsane.  Unplug the power cord from the scanner for about 5-10 seconds, plug the scanner back in again and try this: ```
gksudo xsane canon_pp:parport0
``` If this works, you are open for business! The next step would be to visit the link in my first post, read that thread,  and then update the permissions on your parallel port and the configuration files in your /home/<your username>/.sane folder. Then you can try scanning without using gksudo: ```
xsane canon_pp:parport0
```If this works (it should if the previous steps were successful) you won´t need to keep scanning as a root user and that alarming warning about how dangerous it is to scan as root won´t keep appearing. A final step would be to update the command for xsane in your Applications menu. 

Once you get the scanner working, you won´t need to keep unplugging and plugging the power cord back in each time- (though sometimes you might need to!)  I posted that because if the scanner hasn´t been power cycled it might not be found even if everything is set up properly. Also, **all the preceding steps assume that your printer and scanner are connected to parport0**. They almost definitely are if you have just one parallet port. If you have more than one parallel port, let me know - some adjustments in the steps above may be needed.

Try these steps out and post back what happens. If you get stuck or need help at any point, I´ll try to help.

---

### Post by bob74 on 2007-05-25
All OK until  I do the gksudo when the warning window comes up and I hit continue.
A message "xsane 0.991 not responding appears and I have to do a force quit. I have been through the preliminary steps several times and everything appears to agree OK. I appreciate the time you have put into this and hope you can continue to give further guidance.
Regards,
Bob

---

### Post by bob74 on 2007-05-25
Further to my earlier reply I restarted the system  and went through the steps again.
 When I tried the gksudo I got the message "Failed to open device 'canon_pp:parport 0'
error during device I/O

---

### Post by klytu on 2007-05-25
> **bob74 said:**
> Further to my earlier reply I restarted the system  and went through the steps again.
 When I tried the gksudo I got the message "Failed to open device 'canon_pp:parport 0'
error during device I/O

If you got that error message, I think you may be close to getting the scanner working. Each time before trying: 
```
gksudo xsane canon_pp:parport0
``` make sure you unplug the scanner, wait, and plug it back in first (let´s call that procedure ¨power cycling¨ from now on). You don´t need to keep checking the configuration files if you have confirmed they are set up properly. Try the command above two or three more times after power cycling the scanner. If you still get the same error message  > "Failed to open device 'canon_pp:parport 0' there are a couple other things we can try. 

1. Try installing sane-utils and using them to gather more information. Make sure you have the universe repository active in your /etc/apt/sources.list first (if you don´t know what I mean by that see [**_[COLOR="RoyalBlue"]this[/COLOR]_**]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") ) Then: ```
sudo aptitude install sane-utils
``` These can always be removed later if you want to with ```
sudo aptitude remove sane-utils
``` After you have installed sane-utils, power cycle the scanner and try ```
scanimage -L
```  Hopefully, you´ll get an output that contains at least something like this:
> [canon_pp] WARNING: Don't know how to reset an FBx20P, you may have to power cycle
device `canon_pp:parport0' is a CANON FB620P flatbed scanner  Whatever the output is, please post it. (You can just copy and paste the output into your post. Before posting you might want to also disable smilies for now - there is an option to do this after the submit reply buttons that appear when you post.)

2.  If sane-utils don´t give any promising feedback, you can try more radical troubleshooting by disconnecting or removing your TV-card and/or printer, then power cycling your scanner and seeing if xsane or scanimage recognizes it. If you decide to try this route, I would first try taking the printer out of the equation by directly connecting the scanner to your parallel port. You will need to be patient and methodical to figure out exactly which device or combination of devices is preventing the scanner from being recognized. Let me know what you find out if you go this route and maybe we can either figure out a workaround or post a bug report.

---

### Post by bob74 on 2007-05-25
Please see following response:
bob@bob-desktop:~$ scanimage -L
device `v4l:/dev/video0' is a Noname BT878 video (Hauppauge (bt878)) virtual device
bob@bob-desktop:~$

---

### Post by klytu on 2007-05-25
> **bob74 said:**
> Please see following response:
bob@bob-desktop:~$ scanimage -L
device `v4l:/dev/video0' is a Noname BT878 video (Hauppauge (bt878)) virtual device
bob@bob-desktop:~$

I was just looking through the man pages for both xsane and scanimage and it appears that only the first device detected is listed by default. I had mistakenly thought scanimage would list all available devices. It appears that to force scanimage and xsane to use anything other than the first detected device as the default, an environment variable has to be set. I think this is done with the export command, but I am not 100% sure of the syntax for this situation. Try: ```
export SANE_DEFAULT_DEVICE=canon_pp:parport0
``` then power cycle your scanner and again try ```
gksudo xsane
```.

---

### Post by bob74 on 2007-05-25
bob@bob-desktop:~$ scanimage -L
device `v4l:/dev/video0' is a Noname BT878 video (Hauppauge (bt878)) virtual device
bob@bob-desktop:~$ 

Hope you find above self explanatory

---

### Post by bob74 on 2007-05-25
Sorry I seem to have duplicated the last message. I removed the printer did the export and then 
gdk etc but it freezes attempting to find the scanner. I will remove the TV card but this will take a while because my PC is in  an awkward position not favorable to immediate access.
Will be in touch ASAP. Thanks for your patience.
Bob

---

### Post by bob74 on 2007-05-29
Hello Klytu, hope you are still monitoring. Cutting straight to the point I now have a situation where I get the Xsane window giving available devices i.e. BT878 TV or Canon FB620P etc.
When I select  scanner and click OK the scanner runs for 2-3 seconds then the program freezes
and I have to do a force quit. At least I have progessed but am stuck now as to what is causing the freeze. My printer is working OK. Your further help would be appreciated. By the way my 9-year
PSU decided to give up the ghost but my old box is now a lot quieter.

---

### Post by klytu on 2007-05-29
> **bob74 said:**
> Hello Klytu, hope you are still monitoring. Cutting straight to the point I now have a situation where I get the Xsane window giving available devices i.e. BT878 TV or Canon FB620P etc.
When I select  scanner and click OK the scanner runs for 2-3 seconds then the program freezes
and I have to do a force quit. At least I have progessed but am stuck now as to what is causing the freeze. My printer is working OK. Your further help would be appreciated. By the way my 9-year
PSU decided to give up the ghost but my old box is now a lot quieter.

Glad to hear that at least the scanner is now showing as an available device. What did you do to get to that point? And does the scanner freeze when you remove the TV card?

I haven't experienced xsane or scanimage freezing before. There might be clues in /var/log/messages. You can try this command before the program locks up: ```
tail -f /var/log/messages
``` and examine the output to see if there is a reference to your parport, scanner, or xsane.  You can stop the output of the command with <ctrl> + c.

You can also try setting debugging output with ```
export SANE_DEBUG_CANON_PP=100
``` and then running ```
gksudo xsane
``` from the terminal and watching the output before the lock up.

Also take a look at the man page for canon_pp for background info: ```
man sane-canon_pp
```

---

### Post by bob74 on 2007-05-30
I posted a message yesterday but it doesn't appear. At the risk of repeating myself
I have reached the stage where I get the Xsane window giving the choice of BT878(TV) or
Canon scanner. Having selected "Scanner" I get the scanner window with preview etc.
However when I click scan the scanner runs for  2-3 seconds then stops and the program freezes,
needing a force quit to return to desktop. Any ideas please?

---

### Post by klytu on 2007-05-30
> **bob74 said:**
> I posted a message yesterday but it doesn't appear. At the risk of repeating myself
I have reached the stage where I get the Xsane window giving the choice of BT878(TV) or
Canon scanner. Having selected "Scanner" I get the scanner window with preview etc.
However when I click scan the scanner runs for  2-3 seconds then stops and the program freezes,
needing a force quit to return to desktop. Any ideas please?

I saw your post yesterday and responded.  If you don't see your post or my response, try clearing your browser's cache and reloading this page. Then try the suggestions I posted.  The suggestions may help you get additional information on why xsane is freezing. Also, how did you get to the stage where you are now? What changes did you make that allowed you to get the choice in xsane?

---

### Post by ashdezign on 2007-05-30
Hi, I am having a similar problem with my Brother DCP 130C printer/scanner.

Sorry if I am cluttering up this thread, wasn't sure if I should post here or start a new one.

Note: I am a complete Linux newbie recently swapped over from Windows.

The printer works fine it is just the scanner that is giving me trouble.

My .sane directory has already read/write access for me as a user.

When I start Xsane it gives me the following error message:

> failed to open device 'brother2:bus5;dev': Error during device I/O

When I start Xsane with gksudo it works fine (with the warning message about it being dangerous and I am on my own)
 I did the install of Sane utilities and ran scanimage -L

the output is as follows:

> 
device `brother2:bus5;dev1' is a Brother DCP-130C USB scanner

I read the other thread you linked to "http://ubuntuforums.org/showthread.php?t=428493", but I can not seem to find a parport0 file in the dev folder. I do find a port file however but am hesitant to change permissions or try editing it until I am sure it is the right one to be playing with.

Any suggestions or help would be appreciated!

Edit: I am using Ubuntu Fiesty Fawn with Gnome desktop.

---

### Post by bob74 on 2007-05-31
Hello Klytu, Bob back here- it took me a while to realise that a second page had been created, hence the confusion. The position is that I removed my TV card and after the gksudo xsane command got the scanner. But upon clicking scan the scanner again ran for 2-3 seconds then  the program froze needing a force quit. After  dozens of attempts I have found a pattern:-
The scanner cannot be detected no matter how long I power down the unit after the initial run, but if I restart the computer I can go through the process again only to have it lock up as previously. The output was:bob@bob-desktop:~$ tail -f /var/log/messages 
May 31 06:00:46 bob-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name 
May 31 06:00:46 bob-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain 
May 31 06:00:46 bob-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers 
May 31 06:01:07 bob-desktop gconfd (bob-5304): starting (version 2.18.0.1), pid 5304 user 'bob' 
May 31 06:01:07 bob-desktop gconfd (bob-5304): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 31 06:01:07 bob-desktop gconfd (bob-5304): Resolved address "xml:readwrite:/home/bob/.gconf" to a writable configuration source at position 1 
May 31 06:01:07 bob-desktop gconfd (bob-5304): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 31 06:01:07 bob-desktop gconfd (bob-5304): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 31 06:01:07 bob-desktop gconfd (bob-5304): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 31 06:01:12 bob-desktop gconfd (bob-5304): Resolved address "xml:readwrite:/home/bob/.gconf" to a writable configuration source at position 0 
Don't know if that helps but if yoy have any further thought I'd appreciate it.
Thanks once again from an elderly Ubuntu user

---

### Post by klytu on 2007-05-31
> **ashdezign said:**
> Hi, I am having a similar problem with my Brother DCP 130C printer/scanner.

Sorry if I am cluttering up this thread, wasn't sure if I should post here or start a new one.

Note: I am a complete Linux newbie recently swapped over from Windows.

The printer works fine it is just the scanner that is giving me trouble.

My .sane directory has already read/write access for me as a user.

When I start Xsane it gives me the following error message:



When I start Xsane with gksudo it works fine (with the warning message about it being dangerous and I am on my own)
 I did the install of Sane utilities and ran scanimage -L

the output is as follows:



I read the other thread you linked to "http://ubuntuforums.org/showthread.php?t=428493", but I can not seem to find a parport0 file in the dev folder. I do find a port file however but am hesitant to change permissions or try editing it until I am sure it is the right one to be playing with.

Any suggestions or help would be appreciated!

Edit: I am using Ubuntu Fiesty Fawn with Gnome desktop.

Hi, Ashdezign.

From the output of scanimage -L it looks like you have a USB scanner, so the thread about changing the parport permissions is not relevant for you. Check out this thread: [http://ubuntuforums.org/showthread.php?t=71104&highlight=Brother+DCP+130C](http://ubuntuforums.org/showthread.php?t=71104&highlight=Brother+DCP+130C)
I think if you read that thread (read all of it, you probably won't need to go through all the steps - just the ones that workaround using sudo .... ) and post there with your questions, you'll probably be able to solve your problem.

---

### Post by klytu on 2007-05-31
> **bob74 said:**
> Hello Klytu, Bob back here- it took me a while to realise that a second page had been created, hence the confusion. The position is that I removed my TV card and after the gksudo xsane command got the scanner. But upon clicking scan the scanner again ran for 2-3 seconds then  the program froze needing a force quit. After  dozens of attempts I have found a pattern:-
The scanner cannot be detected no matter how long I power down the unit after the initial run, but if I restart the computer I can go through the process again only to have it lock up as previously. The output was:bob@bob-desktop:~$ tail -f /var/log/messages 
May 31 06:00:46 bob-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name 
May 31 06:00:46 bob-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain 
May 31 06:00:46 bob-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers 
May 31 06:01:07 bob-desktop gconfd (bob-5304): starting (version 2.18.0.1), pid 5304 user 'bob' 
May 31 06:01:07 bob-desktop gconfd (bob-5304): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0 
May 31 06:01:07 bob-desktop gconfd (bob-5304): Resolved address "xml:readwrite:/home/bob/.gconf" to a writable configuration source at position 1 
May 31 06:01:07 bob-desktop gconfd (bob-5304): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2 
May 31 06:01:07 bob-desktop gconfd (bob-5304): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3 
May 31 06:01:07 bob-desktop gconfd (bob-5304): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4 
May 31 06:01:12 bob-desktop gconfd (bob-5304): Resolved address "xml:readwrite:/home/bob/.gconf" to a writable configuration source at position 0 
Don't know if that helps but if yoy have any further thought I'd appreciate it.
Thanks once again from an elderly Ubuntu user

Bob,

Unfortunately, there is nothing in the logs you posted relating to your scanner issue. Try this:```
export SANE_DEBUG_CANON_PP=100
``` and then ```
gksudo xsane
``` Does the debugging output give any clues as to why things are locking up?

---

### Post by bob74 on 2007-05-31
Thanks for your  response. I get nothing with the export command, either before or after
gksudo xsane. I have the same problem when trying to repeat the cycle i.e. it cannot find any device even after the power down. It looks as though the program is corrupted after the first attempt to scan and only reloading by a restart will correct it. By the way all this with the printer disconnected.Thanks for the time you are putting into this and I will understand if you want to 
drop out at this stage. Incidentally I did try removing and re-installing Xsane and sane etc. with no improvement. It's a shame because everything else I need works.
Regards, Bob Hendry

---

### Post by klytu on 2007-05-31
> **bob74 said:**
> Thanks for your  response. I get nothing with the export command, either before or after
gksudo xsane. I have the same problem when trying to repeat the cycle i.e. it cannot find any device even after the power down. It looks as though the program is corrupted after the first attempt to scan and only reloading by a restart will correct it. By the way all this with the printer disconnected.Thanks for the time you are putting into this and I will understand if you want to 
drop out at this stage. Incidentally I did try removing and re-installing Xsane and sane etc. with no improvement. It's a shame because everything else I need works.
Regards, Bob Hendry

The only other thing I can think of that might be causing this situation is an interrupt conflict. I don't really think this is your problem because your printer normally works OK. If there were an interrupt conflict where the parallel port is conflicting with another device, neither the scanner nor the printer would work.  But anyway, If you want check out this possibility try: ```
cat /proc/interrupts
``` and ```
dmesg | grep irq
``` What you are checking for is the parport using the same interrupt as another device. I don't expect you'll find any problems and that this will be a dead end, but it doesn't hurt to check. 

Really wish I could have helped, but this has me stumped. If you ever find a solution, please do post back with it.

---

### Post by bob74 on 2007-06-01
Hello Klytu, as you anticipated nothing showed up. One final question can you help me to cope
with changing the permissions as [http://ubuntuforums.org/showthread.php?t=428493](http://ubuntuforums.org/showthread.php?t=428493) describes.
I get something like not owner and cannot change etc. and I  cannot see where I'm going wrong.
Could you in simple terms describe the procedure. Hopefully I won't hit a dead end and it's one
desperate shot in the scanner saga.
Thanks once again for your patience,
Bob 74

---

### Post by klytu on 2007-06-01
> **bob74 said:**
> Hello Klytu, as you anticipated nothing showed up. One final question can you help me to cope
with changing the permissions as [http://ubuntuforums.org/showthread.php?t=428493](http://ubuntuforums.org/showthread.php?t=428493) describes.
I get something like not owner and cannot change etc. and I  cannot see where I'm going wrong.
Could you in simple terms describe the procedure. Hopefully I won't hit a dead end and it's one
desperate shot in the scanner saga.
Thanks once again for your patience,
Bob 74

There is an excellent introduction to file permissions and changing them from the command line here: 

[http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions](http://www.linuxquestions.org/linux/answers/Security/Quick_and_Dirty_Guide_to_Linux_File_Permissions)

You can also change file permissions from your GUI. First: ```
gksudo nautilus
``` then navigate to the desired file, right-click it, and change the permissions as you like. **Be careful when using the GUI method. When you are browsing in Nautilus as a root user, you don't want to accidentally delete any critical system files.**

---

### Post by bob74 on 2007-06-01
Hello, me again. Having changed the permissions  and get to sane, clicking on the preview 
the scanner runs and starts to show the preview up to point at scale 8 on the left hand rule. In other words I can see part of the scanned picture then everything freezes needing a force quit. But after that I have to restart the PC because no amount of powering down etc will  allow the scanner to be detected and then the whole cycle repeats. At least I'm a bit further advanced but there is obviously something wrong with the program. I don't know if it is due to my fiddling around but the last time I restarted a message saying that Nautilis wasn't available and I had a screen without background. A further restart and everything was back to normal. I'm beginning to feel that perhaps a new scanner known to work with Feisty may be the only choice. 
Regards-- Bob the pest.

---

### Post by klytu on 2007-06-02
> **bob74 said:**
> Hello, me again. Having changed the permissions  and get to sane, clicking on the preview 
the scanner runs and starts to show the preview up to point at scale 8 on the left hand rule. In other words I can see part of the scanned picture then everything freezes needing a force quit. But after that I have to restart the PC because no amount of powering down etc will  allow the scanner to be detected and then the whole cycle repeats. At least I'm a bit further advanced but there is obviously something wrong with the program. I don't know if it is due to my fiddling around but the last time I restarted a message saying that Nautilis wasn't available and I had a screen without background. A further restart and everything was back to normal. I'm beginning to feel that perhaps a new scanner known to work with Feisty may be the only choice. 
Regards-- Bob the pest.

Bob, 

It's encouraging that you got part of a preview, but this behaviour now also brings up another question. Have you ruled out the possibility that there is a mechanical problem with the scanner? When was the last time you used it and knew that it worked properly?

---

### Post by bob74 on 2007-06-02
Hello Klytu, I tried the scanner on my dual/boot(Me) and it is fine. Wish I could have said otherwise.
Bob

---

### Post by bob74 on 2007-06-02
I tried the calibration process in case that had any significance and the prog froze This was displayed on the terminal :  bob@bob-desktop:~$ gksudo xsane
[canon_pp] WARNING: Don't know how to reset an FBx20P, you may have to power cycle
The application 'xsane' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
bob@bob-desktop:~$ 

Can you make anything out of that?
Bob

---

### Post by klytu on 2007-06-02
> **bob74 said:**
> I tried the calibration process in case that had any significance and the prog froze This was displayed on the terminal :  bob@bob-desktop:~$ gksudo xsane
[canon_pp] WARNING: Don't know how to reset an FBx20P, you may have to power cycle
The application 'xsane' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.
bob@bob-desktop:~$ 

Can you make anything out of that?
Bob

This warning is normal:>  [canon_pp] WARNING: Don't know how to reset an FBx20P, you may have to power cycle

But I have no idea what is causing this:> The application 'xsane' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed the application. 
... unless this appeared after you did a force quit of xsane - in which case it's just confirming that you stopped the application xsane.  

If this last message appeared as xsane froze but before you did a force quit, maybe this is a  clue as to why you keep locking up. Have you been having any display problems apart from your scanner issue? You mentioned in passing that you had a problem with Nautilus and a screen without a background - has that happened before?

---

### Post by bob74 on 2007-06-03
I have not had a repeat of the Nautilis thing  having restarted at least 18 times. I cannot remember exactly but I believe the message came up after the force quit. The strange thing is that this morning when I did the gksudo I had the xsane window asking to select the device, i.e. either the TV card or the FB629P , choosing the latter. Upon starting scan I had nearly half the photo appear beforethe program froze, which is the most to date. Unfortunately I cannot get it to repeat.It's almost as if there is a timeout, and not a regular one at that. Are there any other sources that might be able to help. I find it very hard to believe that in the whole world there are only two FB620
in use. The fact that sane didn't come up with a solution to this Canon model until comparatively
recently must indicate there was a need for it otherwise why spend time on developing it.
Will persevere and thanks for your continuing involvement.

---

### Post by bob74 on 2007-06-03
This evening I had the following which hopefully might throw some light on things:-
bob@bob-desktop:~$ xsane canon_pp:parport0
[gphoto2] init_gphoto2: error: serial:/dev/ttyd1 is not a valid gphoto2 port.  Use "gphoto2 --list-ports" for list.
bob@bob-desktop:~$ *gphoto2 --list-ports
bash: *gphoto2: command not found
bob@bob-desktop:~$ gphoto2 --list-ports
Devices found: 7                                                               
Path                             Description
--------------------------------------------------------------
disk:/                           Media 'Volume (ext3)'           
ptpip:                           PTP/IP Connection               
serial:/dev/ttyS0                Serial Port 0                   
serial:/dev/ttyS1                Serial Port 1                   
serial:/dev/ttyS2                Serial Port 2                   
serial:/dev/ttyS3                Serial Port 3                   
usb:                             Universal Serial Bus            
bob@bob-desktop:~$

---

### Post by klytu on 2007-06-03
> **bob74 said:**
>  I find it very hard to believe that in the whole world there are only two FB620
in use. 

But we might be the only two people who use Ubuntu and read this forum that use the FB620P. :-)

>  The fact that sane didn't come up with a solution to this Canon model until comparatively
recently must indicate there was a need for it otherwise why spend time on developing it.
Will persevere and thanks for your continuing involvement.


About four years ago I had Red Hat 7.2 Linux installed - back then I had to compile the driver for the scanner from source and run it from the command line - couldn't get it to work in a GUI at all back then. I was actually floored  to find out - after I started using Ubuntu - that the driver had been incorporated into xsane at all!

Meanwhile, I came across [**_[COLOR="Red"][U]an old post about a different Canon parallel port scanner_[/COLOR][/U]**]("http://ubuntuforums.org/showthread.php?t=6419") where a person having trouble went into his BIOS and changed the parallel port setting to EPP. For him that ended all of his difficulties. May be worthwhile for you to check out this possibility if you haven't already. 

I have no experience using gphoto2. Did you install that package recently since starting this thread? If so, then likely it's not the cause of your difficulties.

---

### Post by FoolishGhoul on 2007-06-04
If it helps i'm having pretty much the exact same problem!

My scanner is the Canon N640P and the only time I have managed to get anywhere close to it working is the first time after booting the computer.  If I load xsane and try to do a preview the scanner starts up, moves its imaging arm a couple of centimetres and then stops while xsane crashes. (also while the scanner is in this state it prevents anything from reaching the printer until I do a power cycle)

After the first time xsane wont even get past the "scanning for devices" stage until I reboot the computer.

I have followed this post and tried setting the parallel port to EPP but nothing has changed.

---

### Post by FoolishGhoul on 2007-06-04
update:

After posting that I just tried xsane again and it worked fine!

Worryingly I haven't a clue why...?

---

### Post by bob74 on 2007-06-04
Whilst I am sorry about your predicament, I am relieved that  I am not the oddball here. You are 
having exactly the same symptoms as me and there doesn't seem to be a solution to it. As you see from the posts Klytu has come up with many suggestions but it would appear that their is a basic program error here in Xsane. I have spent countless hours exploring as many sources of
information as possible and they all lead to the same result. Hopefully someone might come up with a solution but I'm feeling somewhat frayed around the edges.
Bob 74

---

### Post by klytu on 2007-06-04
> **bob74 said:**
> Whilst I am sorry about your predicament, I am relieved that  I am not the oddball here. You are 
having exactly the same symptoms as me and there doesn't seem to be a solution to it. As you see from the posts Klytu has come up with many suggestions but it would appear that their is a basic program error here in Xsane. I have spent countless hours exploring as many sources of
information as possible and they all lead to the same result. Hopefully someone might come up with a solution but I'm feeling somewhat frayed around the edges.
Bob 74

Bob, I can understand that you are frustrated about not getting your scanner working properly. I have had frustrating problems with peripherals and hardware before as well, so believe me I understand.  However, from what you have posted so far I am not convinced the problem is with xsane. A strong indication that it´s not xsane that is the root cause of your problem is that I have the same model scanner running well using the same Linux distribution you are using; I´ve also found posts from people using xsane with this scanner in other Linux distributions.  This leads me to think that likely your problem is being caused by a factor outside of xsane.  Have you been able to get your scanner working before at all outside of Windows? Also, did you try the suggestion in my last post - the one about setting your parallel port to EPP mode in your BIOS?  A person in the linked thread in my last post stated they uncommented ¨force nibble¨ in canon_pp.conf and got results.  The canon_pp.conf file contains a comment that indicates this last suggestion could help if your parallel port is in ECP mode.

A method that often works for me in solving frustrating problems like this is to jot down or make a note file listing the steps I have taken to solve the issue, what I have learned, mistakes I made, steps that lead to improvement, and research that appeared to lead to a dead end.  Then I leave the situation for a couple of days or weeks and come back to it later, reviewing my notes. Sometimes I realize something simple I overlooked or come across an idea based on something I learned in the interim. Most often I end up eventually solving the problem.

It might also be useful if you post your complete hardware and software environment. If you are up to doing this you should include: 
1. Your motherboard manufacturer and model, your BIOS version and vendor. 
2. Any attached external peripherals (include manufacturer, make, and model and where the peripherals are attached). 
3. A text file containing the output of dmesg. You can create this by doing, for example:```
dmesg > bootlog
``` and then attaching the file bootlog to your post. 
4. A file containing the packages installed after you installed Feisty. An Ubuntu forum member wrote a nice script to generate this information. [[COLOR="Red"]**_See this thread._**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=393615") (also, did you upgrade to Feisty from a previous Ubuntu version or was this a fresh install)
5. The output of ```
lspci -v
```
I am not sure I´ll be able to help you even with all that information, but it´s possible that someone else who stumbles across this thread might find something subtle in there that we have overlooked. Anyway, at least I can look over your configuration and rule out things I am aware of that might be causing difficulty.

---

### Post by bob74 on 2007-06-05
Hello Klytu, sorry about the delay in replying. I forgot to mention that I had tried the ECP mode with no change. I will let you have the other information ASAP. In the meantime , bearing in mind your comments, I am going to put everything back to original and start over with a clean sheet because I fell into the trap of trying things without logging them consequently not knowing now just what I have changed. Thanks again for your continuing help.
bob74

---

### Post by ashdezign on 2007-06-08
Thanks klytu!

Sorry it took me so long to get back. Have had some priority issues come up that kept me from even looking at the scanner.

Will be reading through the link you referred me to. I am sure I will find the answers there.

Much Appreciated.

---

### Post by BitJam on 2007-06-11
I was having the exact same problem with this scanner.  Uncommenting the "force nibble" line in /etc/sane.d/canon_pp.conf fixed the problem for me.   

Thanks all.

---

### Post by bob74 on 2007-06-12
Hello Klytu, I have taken the easy way out. Picked up a lide30 from ebay, entered two lines
in the terminal and straightaway it worked OK. So my old FB620 is no longer being used.
Now I have everything I need in Ubuntu. Thanks any way for your  guidance: I certainly
learnt a lot more about the terminal and commands so it was not time wasted. All the best,
Bob74

---

