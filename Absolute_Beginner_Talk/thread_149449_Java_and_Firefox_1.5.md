---
title: "Java and Firefox 1.5"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by conbrio on 2006-03-23
Hello again,

I have been trying to get Java to work with firefox 1.5. So far no luck. I have searched and read all the howto's and guides I could find. I believe that java has been installed correctly because I did not have any error messages or abort messages that some have reported. But for some reason I can not get it to work with Firefox. Any suggestions? Thanks

ConBrio

---

### Post by KansasJoe on 2006-03-23
Download the linux self extracting file from [http://www.java.com/en/download/linux_manual.jsp](http://www.java.com/en/download/linux_manual.jsp)
---easiest to put this in home folder as to avoid permission problems---

chmod a+x jre-1_5_0_06-linux-i586.bin

./jre-1_5_0_06-linux-i586.bin   (brings up a bunch of info...hit enter until you can type yes)

cd .mozilla/plugins

ln -s ~/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so

that's it...now restart mozilla

---

### Post by conbrio on 2006-03-23
thanks for the help. worked. the only thing i had to do differently was change 
cd .mozilla/plugins

to
 cd /opt/firefox/plugins

as that was where my install of firefox 1.5.0.1 resides. maybe that was my problem before. who knows as now it works. thanks again.

ConBrio

---

