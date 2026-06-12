---
title: "problems starting with Ubuntu"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by jaekim on 2008-01-15
I downloaded 7.10 desktop x86 version and tried to run it on my laptop (Copmaq Presario 2100).  

I tested the CD with Ubuntu and it checked out fine.

Then I tried to boot from the CD.  It got some error messages - I think it had to do with hardware drivers, but it kept going. Then it got to the point where the screen turned white and the laptop started making little clikcing noise - like the hard drive or the CD drive was being accessed constantly.

The white screen stayed like that overnight.

So, I burned the 6.06 desktop x86 version.  Again the CD checked out fine.

I can now boot from the CD, but I still get a lot of clicking noise.  Oh and I also got the same (I think) hardware driver errors.

Not only that, everything takes so long - even moving the mouse.  And I have no network access.

I had such high hopes.  I need help!

---

### Post by billgoldberg on 2008-01-15
Llive cd's don't always do that well. The reason everything is slow is because you are at cd speeds.

Install it using the text mode on a spare partitiion somewhere and everything should be fine.

---

### Post by ByteJuggler on 2008-01-15
Have you tried Safe Graphics mode?  Booting to the desktop should take no more than (say) 10mins on a slowish machine.  If you don't have a desktop by then, and you have e.g. some obvious display anomaly (like a white screen) then you might as well try something else.  The screen never turns white intentionally , and during boot you should see pretty much straight after the boot splash logo and/or some text mode blah, a graphical mouse pointer and, eventually a desktop.  

6.06 is pretty old by todays standards.  You might consider trying 7.04 (Feisty), or perhaps better, the "Alternate install CD" which uses a text mode installer.  

You appear to be having some graphics driver issues.  We may be able to help you work through them.

---

### Post by Fnubey on 2008-01-15
Don't be that desperate: Start your liveCD with the option ```
acpi=off 
```(simply put that to the boot-options in the bootscreen of your liveCD). Especially notebooks sometimes need that option to be turned off...

Hope that helps!

---

### Post by ByteJuggler on 2008-01-15
Can you confirm whether your specs is as follows:
[http://lisonbee.freeshell.org/linux/laptop/presario_2100.html](http://lisonbee.freeshell.org/linux/laptop/presario_2100.html)

Particularly, can you confirm whether this is the graphics chipset your machine uses?

---

### Post by dstew on 2008-01-15
I agree with ByteJuggler that you should try the Alternate Install CD. It installs the same Ubuntu system as the LiveCD, but uses a text-based interface that is easier on your hardware. I think the LiveCD is having trouble dealing with your hardware. The real problem is the LiveCD. It only has so much room on it, and sometimes its software just can't handle your hardware.

By the way, the clicking is probably your disk drive loading and unloading (parking the head makes the click). This is due to the software on the LiveCD having trouble with your disk's power management. This is harmless, at least in the short run.

---

### Post by jaekim on 2008-01-16
Thanks for all the help folks.

I booted with acpi=off and that helped quite a bit.  But once I got to the desktop, neither 6.06 nor 7.10 would open any thing I clicked on.

So, I'm downloading the alternate install cd.  Stay tuned - more later :)

Oh, how do I go about determining what graphics chip set I have?  I thought the setup menu might have this info, so I tried going into that.  while powering up, it says to press F2 key for setup.  Well, the laptop ignored this and kept booting to XP (and for all the other F keys, as well).  So, if I have to go into the setup menu to find out, I need to figure out how to get there.

---

### Post by ByteJuggler on 2008-01-16
> **jaekim said:**
> Thanks for all the help folks.
I booted with acpi=off and that helped quite a bit.  But once I got to the desktop, neither 6.06 nor 7.10 would open any thing I clicked on.


Did the menu's display?  Did the mouse pointer move as you would expect?  What specifically did you try to open that did not work?  Did you try to double-click the "install" icon to start the installation?  What happened?

---

### Post by jaekim on 2008-01-17
> **ByteJuggler said:**
> Did the menu's display?  Did the mouse pointer move as you would expect?  What specifically did you try to open that did not work?  Did you try to double-click the "install" icon to start the installation?  What happened?

The mouse pointer did move.  The menu didn't display.  I tried to open the "examples" and "install" icons.  I double-clicked and nothing happened.

I downloaded alternate image 7.04 (7.10 downloaded the normal image even though I had checked the box for the alternate image).  At any rate, I installed Ubuntu (no XP any more), and I played around a bit.  It looks like it's working.

Except I have problems accessing wireless.  What does it mean to enable "roaming"?  I'll have to play around with it more this weekend.

My present network: security type is WPA-PSK, data encryption type is TKIP, connection type is DHCP, key provided is "0", and I have a wireless pass phrase.

I've played around with settings, but I can't seem to connect.

Any help will be greatly appreciated :)

Oh, the system also has problems going into hibernation.  Any ideas?

---

### Post by ByteJuggler on 2008-01-17
> **jaekim said:**
> The mouse pointer did move.  The menu didn't display.  I tried to open the "examples" and "install" icons.  I double-clicked and nothing happened.

I downloaded alternate image 7.04 (7.10 downloaded the normal image even though I had checked the box for the alternate image).  At any rate, I installed Ubuntu (no XP any more), and I played around a bit.  It looks like it's working.

Except I have problems accessing wireless.  What does it mean to enable "roaming"?  I'll have to play around with it more this weekend.

My present network: security type is WPA-PSK, data encryption type is TKIP, connection type is DHCP, key provided is "0", and I have a wireless pass phrase.

I've played around with settings, but I can't seem to connect.

Any help will be greatly appreciated :)

Oh, the system also has problems going into hibernation.  Any ideas?

Roaming = DHCP

Wireless can be problematic, depending on the wireless chipset in use.  The drivers for some aren't finished and some chipsets don't have drivers at all.  There is however a way of using Windows drivers under Linux which works well enough for the most part -- it's called "ndiswrapper" and basically is a translation layer allowing the Linux kernel to use the Windows driver.  We'll have to try and identify your wireless chipset in order to give you specific instructions.  Perhaps the best thing to do is to post the output of the "lspci" command.  To do that, press alt-f2, and paste/type the following command into the resultant "Run" dialog, exactly as shown:

```
lspci >/tmp/lspci.txt; gedit /tmp/lspci.txt 
```

This will open up the output in a text editor.  Then copy and paste it into a browser and paste it here.  (I'm assuming while your wireless is broken, you're using a wired internet connection?)

---

### Post by jaekim on 2008-01-19
> **ByteJuggler said:**
> Roaming = DHCP

Wireless can be problematic, depending on the wireless chipset in use.  The drivers for some aren't finished and some chipsets don't have drivers at all.  There is however a way of using Windows drivers under Linux which works well enough for the most part -- it's called "ndiswrapper" and basically is a translation layer allowing the Linux kernel to use the Windows driver.  We'll have to try and identify your wireless chipset in order to give you specific instructions.  Perhaps the best thing to do is to post the output of the "lspci" command.  To do that, press alt-f2, and paste/type the following command into the resultant "Run" dialog, exactly as shown:

```
lspci >/tmp/lspci.txt; gedit /tmp/lspci.txt 
```

This will open up the output in a text editor.  Then copy and paste it into a browser and paste it here.  (I'm assuming while your wireless is broken, you're using a wired internet connection?)


Thanks for all your help, ByteJuggler.  

I put Ubuntu on to my daughter's laptop - she's complained that it's been slowing down.  I've wanted to try Linux, and here was my chance :)

Yes, I can access the internet via wired LAN.  I am typing this on my desktop, though.

Here is the output of lspci:

00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1

---

### Post by ByteJuggler on 2008-01-19
Ok that's the line that identifies your wireless adapter:

```
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

OK, that's a fairly common chipset, it happens to be the same one I have, or a close variant.  Anyway, here's one howto: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

There's also this thread related to the howto: [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

Please post back if you get stuck or something, we'll try to be of assistance.  (Aside:  The native Gutsy driver also didn't work for me, it doesn't support certain features yet required for my laptop to work in its current location, apparently.  It does work with the native if I move it to right next to the access point, but not when its in its normal location.  The NDISWrapper driver however works fine.  So until the native driver is fixed, my machine is happy with the NDISWrapper setup.  :-) )

---

### Post by jaekim on 2008-01-20
> **ByteJuggler said:**
> Ok that's the line that identifies your wireless adapter:

```
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
```

OK, that's a fairly common chipset, it happens to be the same one I have, or a close variant.  Anyway, here's one howto: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

There's also this thread related to the howto: [http://ubuntuforums.org/showthread.php?t=475963](http://ubuntuforums.org/showthread.php?t=475963)

Please post back if you get stuck or something, we'll try to be of assistance.  (Aside:  The native Gutsy driver also didn't work for me, it doesn't support certain features yet required for my laptop to work in its current location, apparently.  It does work with the native if I move it to right next to the access point, but not when its in its normal location.  The NDISWrapper driver however works fine.  So until the native driver is fixed, my machine is happy with the NDISWrapper setup.  :-) )


Well, I did step 2b, and now it looks like I'm stuck.

I'm logged in to ftp.compaq.com, then it comes back with "[number.number] bcm43xx: Error: Microcode 'bcm43xx_microcode4.fw' not available or load failed."

The number.number changes to different numbers - maybe for different files?

Some examples: 
  82453.248000
  82576.708000
  82700.192000
  82823.680000
  82947.164000
  83070.676000
  83194.168000
  83317.672000

At this point, I got the message "Error in server response, closing control connection.  Retrying."

It's now trying to reconnect for the 3rd time.

I'll reboot, and try it again.  If that doesn't work, I'll then try compiling.

My daughter stopped by and asked if we could go back to Windows :)

OK - I did the compile, and I'm stuck.

When I execute "sudo ndiswrapper -i bcmw15.inf" I get the error message: "couldn't open bcmw15.inf: No such file or directory at /usr/sbin/ndiswrapper line 219."

I also tried the same command with "bcmwl5.inf" - I think it is the number "15" after the letters "bcmw" but it might be the number "5" after the letters "bcmwl."  Same error message.

Can you tell me whether it is supposed to be the letter "l" or the number "1"?

Anyhow, I'm turning in for the night.  Boy this is frustrating.

---

### Post by dstew on 2008-01-21
Are you following this How-To?: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

If so, try to get the driver from the hp site instead. It worked fine today, but the compaq site did not. Here is my terminal output from the wget command:
```
dad@ubuntu:~$ wget ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
--10:38:26--  ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
           => `sp33008.exe'
Resolving ftp.hp.com... 15.193.112.22, 15.192.45.22
Connecting to ftp.hp.com|15.193.112.22|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.
Length: 4,318,656 (4.1M) (unauthoritative)

100%[====================================>] 4,318,656     76.12K/s    ETA 00:00

10:39:22 (75.85 KB/s) - `sp33008.exe' saved [4318656]
```You should get the exact same output.

Then, when you extract the driver archive, you should see:```
dad@ubuntu:~$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
```Did you get this far? If so, when you execute the sudo ndiswrapper command, you have to be in the same directory where you extracted the cabinet file. It looks like you changed your directory, and executed the ndiswrapper command from /usr/sbin/ndiswrapper instead. And, the driver file is bcmwl5, with a small 'L'.

---

### Post by nikoPSK on 2008-01-21
> **billgoldberg said:**
> Llive cd's don't always do that well. The reason everything is slow is because you are at cd speeds.

Install it using the text mode on a spare partitiion somewhere and everything should be fine.

live cd's don't even work on my mid to high rig. I just use alternate. :)

---

### Post by jaekim on 2008-01-21
> **dstew said:**
> Are you following this How-To?: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

If so, try to get the driver from the hp site instead. It worked fine today, but the compaq site did not. Here is my terminal output from the wget command:
```
dad@ubuntu:~$ wget ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
--10:38:26--  ftp://ftp.hp.com/pub/softpaq/sp33001-33500/sp33008.exe
           => `sp33008.exe'
Resolving ftp.hp.com... 15.193.112.22, 15.192.45.22
Connecting to ftp.hp.com|15.193.112.22|:21... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /pub/softpaq/sp33001-33500 ... done.
==> PASV ... done.    ==> RETR sp33008.exe ... done.
Length: 4,318,656 (4.1M) (unauthoritative)

100%[====================================>] 4,318,656     76.12K/s    ETA 00:00

10:39:22 (75.85 KB/s) - `sp33008.exe' saved [4318656]
```You should get the exact same output.

Then, when you extract the driver archive, you should see:```
dad@ubuntu:~$ cabextract sp33008.exe
Extracting cabinet: sp33008.exe
  extracting bcm1xsup.dll
  extracting bcm43xx.cat
  extracting bcm43xx64.cat
  extracting Bcmnpf64.sys
  extracting bcmwl5.inf
  extracting bcmwl5.sys
  extracting bcmwl564.sys
  extracting bcmwliss.dll
  extracting bcmwlnpf.sys
  extracting bcmwlpkt.dll
  extracting bcmwls.ini
  extracting bcmwls32.exe
  extracting bcmwls64.exe
  extracting bcmwlu00.exe
  extracting data1.cab
  extracting data1.hdr
  extracting data2.cab
  extracting ikernel.ex_
  extracting is.exe
  extracting launcher.ini
  extracting layout.bin
  extracting setup.exe
  extracting Setup.ini
  extracting setup.inx
  extracting setup.iss
  extracting sp33008.cva

All done, no errors.
```Did you get this far? If so, when you execute the sudo ndiswrapper command, you have to be in the same directory where you extracted the cabinet file. It looks like you changed your directory, and executed the ndiswrapper command from /usr/sbin/ndiswrapper instead. And, the driver file is bcmwl5, with a small 'L'.

Yes- that file is what I'm following to try to get wireless connection.

I had downloaded from the HP directory and tried compiling.  I guess I was in the wrong directory.

I followed your directions and got everything you got.  Then followed step 3 and everything executed with no error messages.

I rebooted.  Things looked promising - I saw 3 wireless networks that I could join.  But then reality - I could not join the one that I wanted.

I click on the network I want, put in my 10 character password, and select TKIP for type.  But it doesn't connect.  I also tried the default type, but that doesn't work either.

I'm pretty sure the password is correct.  I'll verify this tomorrow.

---

### Post by ByteJuggler on 2008-01-22
> **jaekim said:**
> I click on the network I want, put in my 10 character password, and select TKIP for type.  But it doesn't connect.  I also tried the default type, but that doesn't work either.

I'm pretty sure the password is correct.  I'll verify this tomorrow.

Hmm, make sure you use WPA-PSK or WEP as appropriate to your router.  I don't think TKIP is right.  Nearly there!!! :-)

---

### Post by jaekim on 2008-01-22
> **ByteJuggler said:**
> Hmm, make sure you use WPA-PSK or WEP as appropriate to your router.  I don't think TKIP is right.  Nearly there!!! :-)

Could be a case of so close and yet so far :)

When I click on the network icon, I get a box with 3 fields.  The first field is for Wireless Security, and has the words "WPA Personal" already populated.  I don't get any other choices.  There are arrows pointing up and down on the right hand side as if I have choices, but when I click on the field or on the arrows, the only choice I have is "WPA Personal," and the arrows go away.  When I go to another field, the arrows come back.  I can't type in anything in to this field.

The next field is for the password.

The last field is for "Type."  Here I have 2 choices - "Automatic (Default)" and "TKIP."  Neither choice works.

I've verified that my password is correct - well according to a note I have.

---

