---
title: "Wireless breaks on restart!"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by Mazza558 on 2007-11-23
Man, this is an uphill battle against the combination of wireless drivers, the keyring manager, the network (the bootscreen) (is this caused by the quiet splash flag?) and the ridiculous boot time of over 2 minutes. Here is a typical run down of what I have to do in order to get on the net, and get to a usable position:

-Come home, boot my laptop. (2 minutes total)
-Close AWN due to a white bar which covers most icons at startup, and then restart it (3 minutes)
-Enter the password for the keyring manager (Why?!?) to connect to the network
-Wait a minute for the second green orb to light up when connecting (4 minutes)
-Open Opera and begin to browse some pages. Google takes 20 seconds to load. Works fine on the other PCs. Something is up here... (5 minutes)
-Watch as the connection grinds to a halt. Connection info in nm-applet tells me I'm connected at 24mbps. Fair enough. (6 minutes)
-Disable the wireless and networking and re-enable it. Doesn't even disconnect from the network, let alone restart the connection.
-Close nm-applet using "kill <process ID>", open it from the terminal (7 mins)
-Okay, hmm... nm-applet can't see my hardware anymore, telling me there's no network devices. Erm.. no. (8 mins)
-Well, let's restart, maybe that'll change things! (10 mins)
-Logging on to the network, ooh, it's quicker this time... 
-No internet connection at all now... great. (11 mins)
-Maybe it's the router playing up? I check the connection on the other PCs, including the wireless connections. It's fine here. I reset the router. (12 mins)
-Okay, let's have another go... still no luck...  seems that the router reset the encryption key when it reset... (This isn't Ubuntu's fault). I change the encryption key back to what it used to be. (13 mins)
-This time, nm-applet gets a bit cheeky, and refuses to "disconnect" from the network again. Yay, let's restart... again! (15 mins)
-Aha! Finally! wireless is working again, and I have internet access. Instead of feeling happy, I'm tempted to go back to Vista again.

This process is repeated every single time I restart the laptop. The time I showed above is my latest record for getting on the internet, it started at about an hour. Things like these shouldn't break on restart. By comparison, it takes 45 seconds from the PC being off to firefox loading the homepage on my XP PC, with its specs in my signature. 

Does anyone have any solutions to these problems? I'm using the fw-cutter driver (from restricted drivers manager) for the broadcom card which comes with this laptop, and have tried the epic ndiswrapper guide on the inspiron 1501 ubuntu blog, which doesn't work at all. I have tried the generic broadcom driver package, which doesn't work (neither allow nm-applet to show the wireless networks in the area). Finally, I've also tried Wicd, which completely smashed my wireless settings, and took nearly 3 hours to manually restore nm-applet.

Thanks in advance for any help!

---

### Post by corney91 on 2007-11-23
For the splash screen - it can be switched on in gconf-editor (/apps/gnome-session/options/show_splash_screen)

Do you have libpam-gnome-keyring installed to remember your password?

'Fraid I can't help you with your drivers

---

### Post by Mazza558 on 2007-11-23
I meant the bootscreen, not the splash screen :)

---

### Post by Mazza558 on 2007-11-23
Hmm... I tried reinstalling libpam, but it still doesn't let me choose the option to remember the password....

---

### Post by Mazza558 on 2007-11-24
Anyone else have any ideas?

---

