---
title: "Missing Properties Button in Service Settings"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by weiyang on 2006-05-12
Making headway with Ubuntu, slowly. Notice that when go to Service settings by clicking System---> Adminstration----> Services ----> the Service settings panel showed up with all my running application. But the Properties button is missing ie I cannot adjust the properties of the highlighted programme but help, cancel ang OK buttons are present. ???? Any idea what happen to the Properties Button? Must I  start from scratch again.:(

---

### Post by skippy81 on 2006-05-12
Don't worry there isnt supposed to be a properties button.  

These services are not in need of fine tuning - they have fixed configuration files and run according to their configuration. The name in brackets ie (fetchmail) is the name of the process.  You could open a terminal window and type "fetchmail --help" or "man fetchmail" to learn more about the process.  As you become accustomed to linux you will learn that everything in linux has a configuration file - this differs greatly to the windows posistion where program settings are all tied into one registery.

Linux services are in many ways independant of the operating system, you could copy your config files to another linux system easily.

---

