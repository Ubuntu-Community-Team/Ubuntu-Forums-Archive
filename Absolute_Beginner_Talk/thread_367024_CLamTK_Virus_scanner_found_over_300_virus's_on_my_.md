---
title: "CLamTK Virus scanner found over 300 virus's on my PC??????"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by madhouse on 2007-02-21
Installed and ran AUTOMATIX2.... ran the security suit with Firestarter and Clamtk virus scanner.. did a scan and I shut it off after a couple of hours scanning, it had found over 300 virus in that time???? freaked me out.... does anyone know what up on that one?? also after restart the firewall icon is gone??? is it running??? I have to start it again,password and then I see it.... should it not be running in the startup like the virus scanner is????????
    Hope someone has time to answer me some questions.....

---

### Post by mikewhatever on 2007-02-21
Does Clam have a log? Can you post it? Where were the viruses found, on Ubuntu, or another partition?

---

### Post by teaker1s on 2007-02-21
post log and be aware of false positives

---

### Post by george29 on 2007-02-21
firestarter is just the user interface allowing you to configure iptables built into the linux kernel - which is the actual firewall.

post clam logs and then someone will be able to let you know if you have a problem or not.

---

### Post by madhouse on 2007-02-21
> **mikewhatever said:**
> Does Clam have a log? Can you post it? Where were the viruses found, on Ubuntu, or another partition?
thanks for the answer... I'll remember to make the log thing next time.... sadly I dont know much about Ubuntu or anny other OS

---

### Post by madhouse on 2007-02-21
> **teaker1s said:**
> post log and be aware of false positives
was that a polite dig?????

---

### Post by madhouse on 2007-02-21
> **george29 said:**
> firestarter is just the user interface allowing you to configure iptables built into the linux kernel - which is the actual firewall.

post clam logs and then someone will be able to let you know if you have a problem or not.
thank you for the answer... not that I understood that thing about the firewall...

---

### Post by steve.horsley on 2007-02-21
As for firestrter, as george29 said, it's just the configuration GUI for the iptables firewall. iptables is the inbuilt firewall, and driven from the command line (or by scripts). The GUI simplifies the configuration so that mere mortals can manage it. To make sure the iptables is actually applying rules, use this command:
**sudo iptables -L**
If iptables is not doing any filtering, you response will be:
> Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

If it is filtering, you will see lots of rules listed.

There have been some reports here that if you use firestarter to configure the iptables then iptables is not properly configured after a reboot, but I'm not sure if this is actually the case. It may just be that the GUI isn't automatically launched after a reboot. I haven't tried firestarter myself.

---

### Post by madhouse on 2007-02-21
> **steve.horsley said:**
> As for firestrter, as george29 said, it's just the configuration GUI for the iptables firewall. iptables is the inbuilt firewall, and driven from the command line (or by scripts). The GUI simplifies the configuration so that mere mortals can manage it. To make sure the iptables is actually applying rules, use this command:
**sudo iptables -L**
If iptables is not doing any filtering, you response will be:

If it is filtering, you will see lots of rules listed.

There have been some reports here that if you use firestarter to configure the iptables then iptables is not properly configured after a reboot, but I'm not sure if this is actually the case. It may just be that the GUI isn't automatically launched after a reboot. I haven't tried firestarter myself.
Major thanks on the terminal thingy.. it is working... also i went and did a test on the firewall and it answers to pings??? would you know annything about such things????

---

### Post by madhouse on 2007-02-21
after reboot it was not working...so every time I start the pc I need to start the firewall???++++It is answering to pings???

---

### Post by Maestro23 on 2007-02-21
> **madhouse said:**
> after reboot it was not working...so every time I start the pc I need to start the firewall???++++It is answering to pings???

Read and Bookmark: [http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

### Post by the.phantom on 2007-02-21
hi
firestarter is just a GUI interface for the firewall you have now !
so you will not get a icon of firestarter unless you start it, but it is still giving 100 % protection ( once it is set right you can forget about it)
and one of the firestarter settings is  for ping
what do you show in 
preferences
firewall
icmp filtering


and advanced options.... silent?

now run your firewall test and it will show that you accept pings
do the firestarter change, then do a scan and see it is stealth now
now reboot the computer and don't start firestarter and run the test, the same, it blocks and you do not have firestarter "on"

---

### Post by steve.horsley on 2007-02-22
Madhouse - Do I understand you right that after a reboot, the command **sudo iptables -L** shows that iptables is not filtering? Please answer yes or no to this.

If it doesn't then I think that's disgusting. 

You can save the current iptables setting with this command:
**sudo iptables-save > /etc/iptables.conf**
but since iptables won't give this output to anyone but root, I guess you should protect that file too:
**sudo chown 600 /etc/iptables.conf**

The config  can be restored with this command:
sudo iptables-restore < /etc/iptables.conf

You could try to arrange for that command to be run at boot. I'm going to experiment, but I have to reboot to do so, so I'll post this now.

---

### Post by steve.horsley on 2007-02-22
OK - after a little trial and error, I find that adding this command:
**iptables-restore < /etc/iptables.conf**
to the file **/etc/rc.local** then this loads iptables up as the machine boots. You probably have to do iptables-save > /etc/iptables.conf every time you change the configuration with the firestarter GUI though.

---

### Post by linux_kid on 2007-02-22
Close all of your ports and don't use firestarter, it caused me many problems, too

---

### Post by steve.horsley on 2007-02-23
> **linux_kid said:**
> Close all of your ports and don't use firestarter, it caused me many problems, too

Actually, that's a good point. Why do you want to run a firewall at all? What are you trying to achieve with it? All I have seen so far is that you don't want your computer to respond to pings, but in fact responding to pings is not generally regarded as a security risk, especially if you don't respond to broadcast pings. Do you have a specific requirement, or is it just because you are used to Windows?

---

