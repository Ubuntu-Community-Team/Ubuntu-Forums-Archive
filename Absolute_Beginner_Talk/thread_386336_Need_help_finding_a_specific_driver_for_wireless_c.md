---
title: "Need help finding a specific driver for wireless card"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by bobthebiker on 2007-03-16
I need the bcmw15a.inf file which will make my F5D7000 wireless card actually work with my computer.  if someone could tell me where to find this file, or extract it from the exe file, please feel more than free to explain it to me.

---

### Post by kevinlyfellow on 2007-03-16
From [http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide](http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide)
is says to download the following file
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R74092&SystemID=INS_PNT_PM_600M&category=5&os=WW1&osl=en&deviceid=3355&devlib=5&fileid=96794](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R74092&SystemID=INS_PNT_PM_600M&category=5&os=WW1&osl=en&deviceid=3355&devlib=5&fileid=96794)
Good luck!

---

### Post by bobthebiker on 2007-03-16
already downloaded that file, cant figure out how the heck to make use of it.

---

### Post by kevinlyfellow on 2007-03-16
There's a neat little trick.  You go to your terminal and unzip it if its on your desktop, put it in the folder ~/Desktop/wireless, then
```
unzip ~/Desktop/wireless/R74092us.EXE
```

Then just grab the file bcmwl5a.inf from the AR directoy.  I'm going to post the file, since I've gone through the steps, so you can just download it from here :-)

Edit: ARGH, mods, remove the attachment :-(  The file says I can't pass it along

---

### Post by bobthebiker on 2007-03-17
The file you attached isnt the one I need anyways, its the 15a, not I 5.

---

### Post by kevinlyfellow on 2007-03-18
I am at a loss for the 15a instead of the l5a, I've looked around and I'm not convinced that there is a difference (lots of typos I suspect).  I could very well be wrong, but I have no other guess.  Have you tried the l5a file?

---

### Post by bobthebiker on 2007-03-18
I tried the file supplied, it didnt work. unless it does and I'm just an idiot.

---

### Post by kevinlyfellow on 2007-03-19
I'm sure your not an idiot.  Its really just the fault of people who don't take into consideration that linux is becoming more popular so they don't develop the driver.  

Well, this site [http://www.jinx.com/forum/topic.asp?TOPIC_ID=45498](http://www.jinx.com/forum/topic.asp?TOPIC_ID=45498) suggests grabbing a file from a driver cd.  Do you have the belkin cd?

This site [http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide](http://www.linuxquestions.org/linux/answers/Networking/Belkin_F5D7000_USA_Wireless_Card_in_Linux_Complete_Guide)
suggests using that pesky bcmwl5a.inf file.  But I'm assuming that this is more or less what you were trying.

BTW I know that these are for Breezy, but they very well could still work on dapper/edgy.

---

