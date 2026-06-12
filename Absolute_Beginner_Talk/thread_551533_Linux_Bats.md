---
title: "Linux Bats?"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by pactpc40 on 2007-09-15
Make living fixing MS Windows, do not know anything about Ubuntu, however I am tired of the gates money machine and want to switch to Linux. I have everything running fairly well but... having a little trouble with my dell-broadband wireless card. Every time that I start this machine I have to open a terminal and insert the following four lines...

sudo modprobe bcm43xx
password ***********
iwconfig
sudo iwlist ethX scan

though not a real big deal to do this EVERYTIME I log on I would however like to automate this process.

Windows I would write the above into a text editor and save it as a .bat maybe even write a script and place it into the start up file.

I am sure there is something that is parallel to that in the Linux world. Can someone please advise me as to what the parallel would be. And how to achieve it?
Thanks

---

### Post by Kilz on 2007-09-15
The linux equivlant of a bat file is a shell script. You can make one easy. Just start the file with #!/bin/bash and then a list of commands. I dont recommend storing passwords though, or even how it would be done.
Type in ```
gksudo gedit /usr/bin/NameYouCanRemember
```
Change the name to one of your choice. Copy and paste in the following. 

```
#!/bin/bash
gksudo modprobe bcm43xx
iwconfig
sudo iwlist ethX scan
```

then ```
sudo chmod 777 /usr/bin/NameYouCanRemember
```

Then all you will have to do is open a terminal and type the files name.

---

### Post by maddog39 on 2007-09-15
Don't forget that you need to go to System > Preferences > Sessions and add that script to your autostarted applications list.

---

### Post by Kilz on 2007-09-15
> **maddog39 said:**
> Don't forget that you need to go to System > Preferences > Sessions and add that script to your autostarted applications list.

Yes you can, and the password box will show each time you start the session and when you enter it, it will run the little script.

---

### Post by artir on 2007-09-15
There is a modules file to autoload the bcm43xx driver, isnt it?

---

### Post by jjalocha on 2007-09-15
As far (little) I understand, the right place to load kernel modules is the '/etc/modules' file. Adding the following line, you make sure the module gets loaded automatically at boot time:

```

bcm43xx

```

---

### Post by pactpc40 on 2007-09-15
Worked great Thanks everyone. To the last, reason I had to write script was I could not get the bcm43xx to autoload. I cannot even get my network manager to remember the connection once I log off. Thus the reason for the script. I would still like to ad this now usr/bin/wireless to the boot file if anyone knows how to do that... thanks again.

---

### Post by pactpc40 on 2007-09-15
jjalocha... Even Better... Loading that into the mod file worked great... inserted saved... restarted several times did not need the script... however was still good to learn how to work them... thanks again all.

---

