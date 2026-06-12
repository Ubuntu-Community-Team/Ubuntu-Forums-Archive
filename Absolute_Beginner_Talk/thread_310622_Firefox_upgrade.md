---
title: "Firefox upgrade"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by livearevolution on 2006-12-01
How do you upgrade to firefox 2.0, I am used to using, the "check for updates link" and when I download it from Mozilla, I have no idea what to do with the file, please let me know how the steps work, thank you much

---

### Post by steve.horsley on 2006-12-01
Unpack the file you downloaded from Mozilla by right-clicking and choosing Extract Here. This creates you a mozilla directory. Personally, I install stuff in /opt, so I'll assume you want to install it there. Start a command terminal and enter the command:
**sudo cp firefox /opt**
to copy the extracted directory to /opt.
Now you can remove the downloaded file and the extracted directory.

You can try this new version of firefox with the command
**/opt/firefox/firefox**

You probably want this to be your default firefox version, so you can open a command terminal and link /usr/bin/firefox this new version of firefox instead of the original one. These commands do that:
sudo mv /usr/bin/firefox /usr/bin/firefox-origingal
sudo ln -s /opt/firefox/firefox /usr/bin/firefox

If you use a java plugin, you will need to configure the plugin to the new firefox install. This command will do it, but you will need to specify your own java jre plugin directory - it probably isn't the same as mine:
**sudo ln -s /opt/jdk1.6.0/jre/plugin/i386/ns7/libjavaplugin_oji.so /opt/firefox/plugins/libjavaplugin_oji.so**

---

### Post by aysiu on 2006-12-01
To automate the process a bit, try this script:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

