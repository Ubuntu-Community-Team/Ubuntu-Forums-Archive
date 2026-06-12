---
title: "Basic walkthrough on installing ndiswrapper"
date: 2006-11-24
forum: Absolute Beginner Talk
---

### Post by dmb83fan41 on 2006-11-24
(Still very new to this)

I have been installing many different programs onto my new Ubuntu running notebook, but I have no idea how to open and install ndiswrapper.  I have been trying to get my Linksys WPC11 ver. 4 to connect to the internet.  Right now I can only connect at work which is through a cable.  I am really anxious to get my wireless card working at home where I have more time to play around with Ubuntu:)   

Thanks for your help!

---

### Post by MasterOfDisaster on 2006-11-25
For a CLI solution, follow the instructions here:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper/edgy?highlight=%28ndiswrapper%29)

For a GUI, also do 

"sudo apt-get install ndisgtk"

Then look in Systen -> Administration/Preferences for a ndiswrapper related entry.  Click on that, then the 'Add Driver' button, and browse to the .inf file of the driver.

Cheers

---

### Post by dmb83fan41 on 2006-11-25
Ok, i think I was able to install the ndiswrapper, but where do I find this .inf file of my driver.  I have tried to find the file for it with no luck yet.  I am so lost with getting this wireless driver up and running....

---

