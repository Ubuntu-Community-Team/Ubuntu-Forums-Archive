---
title: "Wireless adapter problems on ubuntu."
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by Saulie on 2007-08-18
Hello everyone.
I installed ubuntu this morning however I cannot find a way to use my belkin wireless adapter gplus mimo on it. I click the two computers at the top right, select my modem and type in the password. It just loads and loads and then eventualy a cross appears next to the two computers.

I am sure the password is correct btw.

Cant anyone tell me if there is any way i can use this? Thanks.

---

### Post by mikeyphi on 2007-08-18
Open System/Administration/Network

Is your wireless connection listed? Is it enabled? Are the properties set correctly?

What Modem are you using?

---

### Post by Saulie on 2007-08-19
Heya I found a thread with someone using the same wireless thing as me which seemed to get resolved with installing a driver. [http://ubuntuforums.org/showthread.php?t=378286](http://ubuntuforums.org/showthread.php?t=378286)

However I have dowloaded the file it says and then opened the read me file which just tells you to run codes or something. I have come from xp where you just click install ands stuff and i dont know where to start with any of this. Someone please help me.

Thanks.

---

### Post by Jimmyfj on 2007-08-19
Have you checked your System>Administration>Restricted Drivers Manager to see if the device is listed, nad enabled in there?

Edit: Alternately you could try and download the iso for 7.10 Tribe 4 which is far more prepared for wirelss, easier to use that is.

---

### Post by Saulie on 2007-08-19
No it's not listed in the restricted drivers. From the thread i understand that you have to install the driver and then run somethign in the terminal. i can run somethign in the terminal just I don't know how to install the driver. In the read me file it reads.

==================
Build Instructions
==================

    1. Unpack the driver sources and go to the Module directory:
          $ tar -xvzf rt73-cvs-daily.tar.gz
          $ cd ./rt73-cvs-YYYYMMDDHH/Module

    2. Compile the driver sources:
          $ make

    3. Install the driver (as root):
          # make install

    4. Check your install (load module, bring interface up and scan):
        # modprobe rt73 [debug=<mask>]

        <mask> is a decimal or hex number. See TESTING file. Ignored
        if driver compiled without debug support.

        # ifconfig wlan0 up
        # iwlist wlan0 scan

If everything is ok, you should see a list of surrounding Access
Points. It means you can jump to the configuration section.
Otherwise, check out the following install notes...

Which i understand none of.. any help please.

---

### Post by Saulie on 2007-08-19
Okay I have confused myself now, lets start again from scratch.

I have a Belkin G+ MIMO F5D9050B Wireless Adapter. I can see my connection and I type in the password but when i connect i cannot connect. It just wont connect for some reason but it does see my connection.

I have been looking around the forums all this morning and looking t threads of people having the same problem as me and then fixing it but I don't understand how.

Someone please help..

P.S: I have found this thread but i dont know if this is what i need [http://ubuntuforums.org/showthread.php?t=400236](http://ubuntuforums.org/showthread.php?t=400236)

---

### Post by mikeyphi on 2007-08-19
> **Saulie said:**
> Okay I have confused myself now, lets start again from scratch.

I have a Belkin G+ MIMO F5D9050B Wireless Adapter. I can see my connection and I type in the password but when i connect i cannot connect. It just wont connect for some reason but it does see my connection.


More info please!!

When you say " type in my password" is that for access to your ISP or to connect to your router?

If you can see your connection then your wireless adapter is recognised....it's just a question of correct settings.
Open System/Administration/Network....select your adapter....select properties....put in the correct info...if you enter your "password" make sure the WEP enrty is correct.....especially check if you need to enter the password in hex...and not text.

---

### Post by linque on 2007-08-19
Are you using WEP? If you're using WPA, you've got a few more steps ahead of you. WPA is not supported "out of the box" in Ubuntu.

---

