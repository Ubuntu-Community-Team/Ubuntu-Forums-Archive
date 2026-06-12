---
title: "azureus"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by smurphv2 on 2006-08-07
Hey all,
    I'm trying to get azureus up and running. When I tried running it, I received the message in screenshot 1 (should be below). I was unable to hit the close button, the message would stay. I needed to kill the process for it to go away. So, I removed the program through apt-get, and deleted the .azureus directory from my home. Then I re-installed the program, and on startup, it looks like screenshot 2. From using the program in windows, I know it shouldn't look like that. Also, I think that the process is still running when I close the GUI. Should I be exiting another way? I feel that there is a bigger problem w/the install of the program, whether my java isn't installed correctly or what I'm not sure. Does anyone have any ideas?

---

### Post by steve.horsley on 2006-08-07
Firstly, I had trouble with Azureus and the default java that Ubuntu installs. I installed the Sun java and things went much better.

Secondly, yes, shutting the gui doesn't shut Azureus down. To shut Azureus down, you choose File > Exit in the GUI.

---

### Post by smurphv2 on 2006-08-08
steve -- thank you for your reply. Should I be downloading the RPM here: [http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp) for java? Do I need to uninstall previous versions of java before that (and if so, how - did not see that covered in the install instructions?) Lastly, after closing the GUI of azureus, is there a way to safely shut the program down without having to kill the process? Thanks again.

---

### Post by vanstrien on 2006-08-08
I had the same problem with Java versions.  I did an "apt-get remove gij" and  "apt-get install sun-java5-bin sun-java5-jre".  Of course you could easily do the same in Synaptic without any typing.

---

### Post by smurphv2 on 2006-08-08
Thanks, I'll try that at home tonight.

---

