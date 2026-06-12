---
title: "thunderbird install-printer help?"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by geordiejohn on 2008-02-23
hello i am a complete novice to linux-ubuntu and i need to know how do i install a program like thunderbird?
when i used windows i downloaded to program files and double clicked to run,i would like to know where to install program files too and how to open them please,also how do i make ubuntu recognize my lexmark printer?
i think i saw on the forums saying i do not need a firewall or a/v program-is this correct?
sorry if these questions sound stupid but linux is so different to windows,please reply in idiot proof answers.
thank you very much in advance.

---

### Post by erginemr on 2008-02-23
Hello and Welcome to Ubuntu / Linux:

1. Installing programs in Ubuntu is much simpler than installing in Windows. You even don't need to go fetch any download package from websites. There is a centralized package management system (apt-get/synaptic) which will bring almost all software you may ever need at your finger tips.

To get yourself familiar with software installation in Ubuntu, please read the following tutorials:
[http://www.monkeyblog.org/ubuntu/installing/](http://www.monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

2. You can install Thunderbird easily by entering:
```
sudo aptitude install thunderbird
```
from the terminal (Main Menu -> Applications -> Accessories -> Terminal).
Or by using Main Menu -> Add/Remove -> Use the search area for thunderbird

There is a more advanced version of Add/Remove Tool, Synaptic Package Manager, which you can find under: 
Main Menu -> System -> Administration

You may need to enable all software resources first by either:
Add/Remove -> Preferences button
or
Main Menu -> System -> Administration -> Software Sources
(See the attached screenshot)
Don't worry about where to install, in a Linux installation, everything is predetermined for you by the installer. It will not ask you where to install. 

3. Unfortunately, Lexmark printers are notoriously known as unsupported in Linux. But this is not a fault of Linux; it is the Lexmark company, not providing enough support to Linux users, which should be held responsible. You should check out the following site to see if your printer is supported:
[http://openprinting.org/printer_list.cgi](http://openprinting.org/printer_list.cgi)

4. Linux is a lot safer than Windows and there are virtually no viruses running under Linux. So, it is correct that you don't need a firewall in Ubuntu. If you feel the urge, you can install firestarter from the Add/Remove tool (or from synaptic), which acts as a front-end and config tool to the firewall system already available in Ubuntu.

5. Finally, I suggest you to read:
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community/](https://help.ubuntu.com/community/)
thoroughly to learn your new operating system inside out.

I hope you will enjoy Ubuntu as much as we do. Take care yourself.

---

### Post by Moop on 2008-02-23
The easiest way to install programs is to go to Applications-Add/Remove and look for the application you want to install. Make sure in the box marked "show" that you have all available applications chosen from the drop down menu. 

You can also install packages from Synaptic Package Manager in the System menu. 

You don't need to worry about anti-virus or a firewall at this point. Once you find your way around you can decide if you want them. The default install is safe. 

For your printer go to System-Administration-Printing and add new printer. Choose your printer from the list and it should install the driver.

---

### Post by erginemr on 2008-02-23
On a final note, to whet your appetite on what you can achieve with Ubuntu, please check out this video:
[http://www.youtube.com/watch?v=bYsxaMyFV2Y](http://www.youtube.com/watch?v=bYsxaMyFV2Y)

And to learn why Linux is better than Windows, see following site:
[http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/)

---

### Post by geordiejohn on 2008-02-23
thank you very much everyone i will look up the links given and try and teach myself what i need to know,please forgive me if i post for help again,

---

