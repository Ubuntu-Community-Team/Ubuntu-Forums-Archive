---
title: "java problem"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by dksau on 2007-04-25
I have been using 6.06 and now 7.04.  the reason I went to 7.04 is my problem with java on 6.06.  I uderstood java among otherapplets would be included with 7.04.  Maybe it is.  I've tried 100 methods posted on websights , discussion boards and blogs and I still have as yet to find a way to download have it recognized and install java of any version.  I had no trouble at all with flash player.  I can't find anything I want to install in repositoris nor can I find a way to get it there. I've read tutorials and tried recommendations and even tried some ideas of my own with the few commands I've learned but there is always a roadblock like not recognized command, not leagal command not this not that.  I'd like to replace windows on our 4 computers and I did start with VIC 20 and a 286 with MSDos 3.30. with the Vic 20 I had to write all of my progams and wit 3.30 there were alot of require manipulatons in dos but here I'm getting nowhere help.

---

### Post by thefoolisme on 2007-04-25
When I was having Java issues, I found this site for downloading, installing and configuring Java 6.  My big issue was the configuration.  I had Java installed, but the config wasn't pointing to the right one.  
[http://daveshuck.instantspot.com/blog/index.cfm/2007/2/7/Installing-Java-6-16-in-Linux](http://daveshuck.instantspot.com/blog/index.cfm/2007/2/7/Installing-Java-6-16-in-Linux)

Hope this helps.

---

### Post by dksau on 2007-04-25
thanks thefoolisme 
I like that websight and I tried the suggetion on there but when I type sudo chmod +x jdk_6_linux-i586.bin I get cannot access:no such file exists. When I go to download a box comes up asking open with or save to disk. I seem to have to save to disk to download but then I gat the above message:confused:

---

### Post by holdinout on 2007-04-25
I tried it too, and sudo chmod worked and made the file executable but the command to run the executable isn't working... I'm in the directory of the file, but ./jdk-6-linux-i586.bin won't work (No such file or directory). Any help running this so I can move on to the next step?

Dksau, Use the command "cd" followed by the directory of java file. Then try the sudo chmod +x, thats what worked for me.

---

### Post by dksau on 2007-04-25
thanks holdinout  I was able to install java this way.. enable all repositories.  go to add/remove software under applications.  find and select both avaiable java applets and then follow on screen instructions
good luck.

---

### Post by oilchangeguy on 2007-04-25
use automatix. [www.getautomatix.com](www.getautomatix.com)

---

### Post by tehbeermang on 2007-04-25
I installed JDK and JRE through Synaptic, which is on a menu that escapes me. (I'm on a win box right now.)

I also downloaded/installed Eclipse at the same time.

I was coding within a half hour of the thought entering my head.

---

### Post by zvacet on 2007-04-25
> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.

This will download Java and other stuff you need.

---

