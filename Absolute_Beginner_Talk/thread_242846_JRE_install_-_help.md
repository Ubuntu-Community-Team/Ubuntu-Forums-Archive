---
title: "JRE install - help?"
date: 2006-08-24
forum: Absolute Beginner Talk
---

### Post by horizonuser on 2006-08-24
I am having some problems installing JRE and configuring it for Firefox. I have followed Sun's installation instructions, as below, but I still cannot get a "Enable Java" option in Firefox. Can anyone suggest anything? I download the file and extracted as per instruction then cd to the plugins dir and run the following:
 sudo ln -s /programs/jdk1.5.0/jre/plugin/sparc/ns7/libjavaplugin_oji.so .

I can't figure out the importance of the last period (.) and if there should be a space after the .so. I did manage to get the libjavaplugin listed in the plugin directory but still no java.

---

### Post by Druidor on 2006-08-24
I installed Java using Automatix.

Do not think you need that last . though

---

### Post by kernelpanicked on 2006-08-24
> **horizonuser said:**
> I am having some problems installing JRE and configuring it for Firefox. I have followed Sun's installation instructions, as below, but I still cannot get a "Enable Java" option in Firefox. Can anyone suggest anything? I download the file and extracted as per instruction then cd to the plugins dir and run the following:
 sudo ln -s /programs/jdk1.5.0/jre/plugin/sparc/ns7/libjavaplugin_oji.so .

I can't figure out the importance of the last period (.) and if there should be a space after the .so. I did manage to get the libjavaplugin listed in the plugin directory but still no java.

The perios stands for the current working directory. You need to be in the firefox plugins directory to use the period or specify the entire path to the plugins directory in it's place.

---

