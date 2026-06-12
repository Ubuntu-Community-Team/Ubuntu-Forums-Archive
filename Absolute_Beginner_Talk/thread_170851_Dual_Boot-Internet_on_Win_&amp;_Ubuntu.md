---
title: "Dual Boot-Internet on Win &amp; Ubuntu"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by WaterWalker on 2006-05-05
I have a Dual Boot with WinXP en Ubuntu.
When I log out of Ubuntu and reboot in WinXP everything is fine.
When I log out of Windows and reboot in Ubuntu, I can't access the Internet.
I've already tried to find the answer with Google. And I found a tip about "ipconfig /release"(typing it in the Windows-terminal).When I do this before I log out of Windows, I have no problem accessing to the internet when I reboot in Ubuntu.

But I would like to know if there isn't an easier way of doing this(changing configuration in Windows,changing it in Ubuntu, something else,...).
Many thanks.

---

### Post by Geoneil on 2006-05-05
What are you usinbg to get online?  Router or modem?

If it's a USB modem, try searching for the model of modem that you're using.

I had to take time out from (read: give up on) Kubuntu when I couldn't get my Sagem USB modem to work (not even with the Linux driver from the manufacturer) in the end I had to dig out the Speedtouch that another ISP sent me when I switched from the one that sent me the Sagem.  I'm online, Kubuntu is usable and it was all sorted with a quick search and a couple of links!

If you're using a router, I'm led to believe that they just work when connecting your network card to it through the Ethernet port (unsure about WiFi)

Please note, nothing that you do in Windows (short of formatting the partition that Linux is on of course!) affects what happens in Ubuntu, you have to reboot to get between the two.

---

### Post by mostwanted on 2006-05-05
You need to be more specific. How are you trying to connect? Are you using wifi (if so, what's the card called?), DSL/cable or a modem (you might have a so called *winmodem* which can cause problems)?

---

### Post by WaterWalker on 2006-05-05
I have Cable internet with a modem from my provider that is connected via USB with my Computer.

---

### Post by Al3xanR0 on 2006-05-05
Must.. Have... More.. more --information.

---

### Post by Al3xanR0 on 2006-05-05
[QUOTE=WaterWalker]I have Cable internet with a modem from my provider that is connected via USB with my Computer.[/QUOTE]

Unless it is a USB 2.0 connection, wouldn't it be faster to use Fast Ethernet?

---

### Post by WaterWalker on 2006-05-05
It's a USB 2.0 and my internet is fast enough.
I'm not really an expert, so I don't know any details(the modem is a motorola directally connected from the incoming cable with my computer).
But logically I would think the problem lies with the Windows Software and not with the Hardware. Because Ubuntu->Windows=everything works, but 
Windows->Ubuntu=no internet.
It's not really a problem if nobody finds the solution, because I can easily solve it with "ipconfig /release" everytime I log out of Windows(unless I forget it which resluts in logging out Ubuntu->rebooting in Win->releasing IP in Win->rebooting in Ubuntu).

---

### Post by tonyr on 2006-05-05
**ipconfig /release** in Windows is a command that releases the DHCP lease
on your IP adress.  Therefore, your WIndows network is configured to get an IP
address via DHCP automatically.  You can have Windows do the **ipconfig /release**
for you at shutdown.  If you're using **XP Home**, you have to edit
the registry (Regedit) directly. See
[URL="http://www.windowsitpro.com/Article/ArticleID/47131/47131.html"]
http://www.windowsitpro.com/Article/ArticleID/47131/47131.html[/URL]
for some instruction.

If you are using **XP Pro**, there is a utility, **gpedit.msc,** that will let you create a shudown script that you can put ipconfig ./release into.  There are instructions
out there somewhere about how to use it, I just can't find my last known
reference.

There is probably a way to have Ubuntu do the release/renew cycle at startup,
maybe via rc.local.

EDIT: GACCKKKKPHPHPHPPPTTT!!!  wrong url.  I replaced it with the right one.

---

### Post by tonyr on 2006-05-05
[QUOTE=tonyr]If you are using **XP Pro**, there is a utility, **gpedit.msc,** that will let you create a shudown script that you can out ipconfig ./release into.  There are instructions
out there somewhere about how to use it, I've just can't find my last known
reference.
[/QUOTE]

I found this ( for **gpedit.msc** in **XP Pro** ) at
[URL="http://www.experts-exchange.com/Networking/Q_21300954.html"]
http://www.experts-exchange.com/Networking/Q_21300954.html[/URL]
> 
 Here's exactly what you'd do to use ipconfig in a shutdown script as others have mentioned...

Make a file called dhcprelease.bat and edit it with Notepad.  Enter the following lines and save the file somewhere, it'd be easiest to just save it to C:\

@echo off
ipconfig /release

Now go to Start, Run, and type in gpedit.msc and click OK

1. Click the + in front of Windows Settings under Computer Configuration.
2. Click Scripts (Startup/Shutdown)
3. Double-click Shutdown in the right hand pane of this window
4. Click the Add button
5. Click the Browse button and find the script you just saved, click it and click Open
6. Click OK
7. Close the Group Policy window

That's it!

-Bernie


---

