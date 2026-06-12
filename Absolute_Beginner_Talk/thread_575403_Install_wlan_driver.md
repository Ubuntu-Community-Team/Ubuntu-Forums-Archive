---
title: "Install wlan driver"
date: 2007-10-14
forum: Absolute Beginner Talk
---

### Post by garyjohnsmith on 2007-10-14
Hi all

I am an absolute newcomer to ubuntu and Linux so please excuse my naivety, I have been brought up on Microsoft's plug and play approach but love the whole Linux concept.  I have been trying to install a driver for my D Link DWL-G122 USB wireless adapter and am completely lost.  I followed instructions for downloading from serialmonkey, downloaded the file to my home folder.  The next step is extract and install - execute in the console!  At risk of sounding a fool, I can't for the life of me find a console or any place that I can enter the code!  Can anyone point me in the right direction?  I even had the good folk at D Link tell me they don't officially support Linux and then sent me through a driver, but again I can't install.

Overall everything else is a walk in the park with Ubutu, I even just plugged in my HP Color Laserjet MFP and it worked straight away.

Thanks for not laughing too loud.

---

### Post by anewguy on 2007-10-14
When you see someone mention the console, they are normally talking about the command line, and you access that via a terminal session.  To get to a terminal session, click "Applications", scroll down to "Accessories" then over to and click on "Terminal".

Some commands may say they require you to be root or have super user rights.  Just prevace the command with "sudo ", and when it prompts for a password just enter your normal password.  As an example:

"sudo ndiswrapper -i  somefile"

Hope it helps!:)

---

### Post by garyjohnsmith on 2007-10-14
Thanks anewguy, I followed your advice and installed the wlan which works perfectly and I have now learned a bit about Linux/Unix.  Who knows where it will lead.

---

