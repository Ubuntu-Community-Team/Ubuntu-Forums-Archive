---
title: "Trouble accessing the internet (ISP requires password)"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by Noir on 2006-05-12
Hi there, I am a total newbie to Linux and Ubuntu, though I have previous experience in Windows and various flavors of Unix many years before so I know some basic concepts and commands.

I just installed Ubuntu on a clean machine (i.e. no other OS) on my old ThinkPad to experiment a bit, and boy, was the setup intuitive and effortless!

The system recognized my D-Link wireless adapter card during setup, detected my wireless access point, and everything was cool.  However, once the whole system is set up, I am having trouble getting connected to my ISP.

My ISP requires a username and password (which I have) and I have a cheap network switch that is not smart enough to automatically authenticate against the ISP.  In Windows, I have to set up a specific connection with the username and password and do a manual ISP login every time I boot my machine.  This is cumbersome, but worked well.

Is there any way to do this in Ubuntu?  I looked at every menu option and network settings panel, but I could not locate a place where I can set up a 'network connection' (using Windows terminology) and specify an ISP username and password to get on my ISP.  Am I missing something here, or do I have to do it at script level somewhere?

Any help on this will be greatly appreciated.  The system is up and running but I just can't get through this last hurdle!!!

Other than that, Ubuntu ROCKS!

Thanks,
- K. aka Noir

---

### Post by tenn on 2006-05-12
I dont know for sure I have never done it but have you tried, 
System/Administration/Networking/Modem Conection

---

### Post by Noir on 2006-05-14
Thanks tenn.  Someone else told me that I can access the configuration using

sudo pppoeconf

Seems to work but I have some other new issues with the PPPOE connection.

Cheers,
- K.

---

### Post by Noir on 2006-05-17
Just to the not-so-casual reader who is interested in finding out how this was resolved, you can follow [this link]("http://www.ubuntuforums.org/showthread.php?t=177598").

Cheers,
- Noir / K.

---

