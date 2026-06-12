---
title: "WindowX manager"
date: 2007-08-28
forum: Absolute Beginner Talk
---

### Post by rakoth132 on 2007-08-28
Help....

I am totally new to Ubuntu and Linux as a matter of fact so please help a n00b! 

I installed Ubuntu and got it running all ok (Ubuntu 7.0.4) and found that to look at the Desktop effects settings i had to Enable the Nvidea Drivers, so i did. 

The OS asked me to restart, so thought might as well... and then it wouldnt boot, an error message said that the WindowX Manager (i think thats what it was called) had failed to start, and asked if i wanted to see that Log. 

I have a Nvidea 8800GTS, Core 2 Duo (E6600), 2 Gb RAM and 1TB HDD

Please help me and shed some light to my problem! 

Thanks

---

### Post by FuturePilot on 2007-08-28
The problem is that none of the Nvidia drivers in the Feisty repos support your card. But luckily there is a solution. Boot Ubuntu, X will fail, say no when it asks to see the logs. Then login through the terminal and run these commands.
```
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure -phigh xserver-xorg
```
When it asks you for the graphics driver to use, use the "nv" for now. After it's done run this command
```
sudo /etc/init.d/gdm start
```
You should now be back in a graphical environment
Now go to this page [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
And download Envy. Double click on the file to install it along with it's dependencies. Then go Applications>System Tools>Envy. Select Install the Nvidia Driver, then let it do its thing. At the end say yes when it asks to configure your xorg.conf file and then reboot.

---

### Post by rakoth132 on 2007-09-01
Thanks FuturePilot, but when i do that i still have the problem of it saying that its not configured! any other suggestions?!

---

### Post by Lord Illidan on 2007-09-01
What is the exact error?

---

### Post by Outrunner on 2007-09-01
> **rakoth132 said:**
> Thanks FuturePilot, but when i do that i still have the problem of it saying that its not configured! any other suggestions?!

When you highlighted 'nv'(the driver) did you press Enter or the space bar? You have to press space to apply the drivers and then press enter

---

