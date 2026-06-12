---
title: "Temperature Monitoring"
date: 2007-01-22
forum: Absolute Beginner Talk
---

### Post by mural on 2007-01-22
Hello,

Here is my computer specs:

Mobo - Gigabyte M55SLI-S4 (AM2) - nForce4 SLI chipset
Proc   - AMD64 X2 4200+
Ubuntu - Edgy (Kernel 2.6.17-10-generic)

I would like to monitor various hardware settings, such as temperature and fan speed.  I have followed HOW TOs on lm-sensors but it is not working for me.  Sensor-detect cannot detect any devices.  

Is there something extra that needs to be done for AMD64 in order for lm-sensors to work? 

Are there any other applications that the community has used on a AMD64?

Reply and help is much appreciated.

---

### Post by taurus on 2007-01-22
Maybe this would help.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)

---

### Post by Frank Golden on 2007-01-22
The tools I use computertemp in Ubuntu and Notebook Hardware Control in XP
depend on S.M.A.R.T. sensors with HDD's and integral sensors in CPU's and GPU's.
It is possible your hardware has no sensors.

---

### Post by mural on 2007-01-23
> **taurus said:**
> Maybe this would help.

[https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto)


Hi,

I tried the above and it still did not work for me.  I could not successfully complete sensors-detect.

---

### Post by samienela on 2007-02-14
I am having the same problem as the OP.  sensors-detect says there are no sensors, which has to be wrong, because the BIOS screen shows data for CPU and case temp, and fan speeds.  (Earlier posts in this thread: [http://www.ubuntuforums.org/showthread.php?t=358202](http://www.ubuntuforums.org/showthread.php?t=358202))  

Like the OP, I visited [https://help.ubuntu.com/community/SensorInstallHowto](https://help.ubuntu.com/community/SensorInstallHowto), installed lm-sensors, and tried to create the script file mkdev.sh as instructed on the website. No joy.

I was able to create the file in gedit (didn't know where to save it, so saved it to my home directory).  The chmod 755 went fine too.  BUT when I tried to run the script by typing sudo ./mkdev.sh from inside the home directory, I got the error message 

sudo: Unable to execute ./mkdev.sh:  No such file or directory 

This is baffling.  The file shows up with proper permissions when I type ls -la;  I can rename it, I can list the contents.    Why can it not be found when I try to execute it? 

OS/Equipment: Ubuntu Dapper on an Opteron 165 CPU, Gigabyte GA-K8B51GNF-9-RH mobo, 1 GB DDR 400, 40 GB HDD.  

Please help.

---

### Post by Vil on 2007-03-15
> **samienela said:**
> 
sudo: Unable to execute ./mkdev.sh:  No such file or directory 

Try: sudo ./home/<your username>/mkdev.sh

I think the problem is that sudo gives you root access, and root doesn't share your home directory, so it was looking in / for mkdev.sh instead of looking for it in /home/<your username>

I hope that helps

---

### Post by Matt1632 on 2007-03-15
I installed sensors-applet from the repositories and it worked fine right out of the box.

---

### Post by pelago on 2007-03-16
> **Vil said:**
> Try: sudo ./home/<your username>/mkdev.sh

I think the problem is that sudo gives you root access, and root doesn't share your home directory, so it was looking in / for mkdev.sh instead of looking for it in /home/<your username>

I hope that helps
No, that won't be the problem. sudo uses the current directory of the 'normal' user, not the 'root' user. And even if that wasn't the case, the command would be sudo /home/<yourusername>/etc not sudo ./home/<yourusername>/etc

---

