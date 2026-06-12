---
title: "Mixed success with Streaming Radio"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by BertP on 2007-09-22
Hi guys,  I am  very new to Ubuntu and  I am a talk-radio junkie.  My results are mixed and I   would  appreciate any advice on how I might be able to get more stations to work under Ubuntu.

Using advice found in another thread,  I installed some gstreamer codecs and was able to get some streaming radio stations to work.
 
WABC in New York, for example,  works.   I just have to push the dark play button and Totem launches to play the stream ([http://www.wabcradio.com/](http://www.wabcradio.com/))  Many other stations work in a similar fashion
-----
however many of the stations from the very cool  talk station list ( [http://streamingradioguide.com/streaming-radio.php?format=1&radio-format=News/Talk](http://streamingradioguide.com/streaming-radio.php?format=1&radio-format=News/Talk))
do not play.   Instead I get the following error message in Totem: 

AN ERROR OCCURRED
Could not open location; You may not have permission to open the file.

Any suggestions for  getting these stations to work?

of course,  there are several other error messages that can be found on other station such as "Incompatible Browser, need IE6" and  "No Media Found"   but the error message above seems to be the most prevalent .

------

another oddity:
I have found one station that apparently doesn't need Totem to play.  The Station creates a player window that *visually* appears to work exactly like it does in Windows.  [http://www.am1410.com/](http://www.am1410.com/)
Anyone know why?

Some other stations,  (such as [http://www.wbt.com/programming/993fm.cfm](http://www.wbt.com/programming/993fm.cfm))
appear normally without the Totem play button but never start playing
----------

As an aside,  I will mention an oddity  about the station list:
[http://streamingradioguide.com/streaming-radio.php?format=1&radio-format=News/Talk](http://streamingradioguide.com/streaming-radio.php?format=1&radio-format=News/Talk))
While this is a great resource, It appears that some stations are added and removed from the list at different times during the day...despite the fact that those stations stream 24/7

---

### Post by Mud.Knee.Havoc on 2007-09-22
> **BertP said:**
> 
another oddity:
I have found one station that apparently doesn't need Totem to play.  The Station creates a player window that *visually* appears to work exactly like it does in Windows.  [http://www.am1410.com/](http://www.am1410.com/)
Anyone know why?


It's a flash-based player.

---

### Post by BertP on 2007-09-24
Thanks for the reply!
...

The most common error message is:
---
AN ERROR OCCURRED
Could not open location; You may not have permission to open the file.
---

I have played many of these stations play under Windows,  Is there anything that can be done to get these "permission" stations to play under Linux?


Thanks in advance!

---

### Post by tgalati4 on 2007-09-24
Install Flash 9 and you will have better luck.

---

