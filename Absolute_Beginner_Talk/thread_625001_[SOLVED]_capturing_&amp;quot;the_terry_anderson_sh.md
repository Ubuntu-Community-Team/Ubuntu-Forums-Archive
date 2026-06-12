---
title: "[SOLVED] capturing &amp;quot;the terry anderson show&amp;quot; mp3 archives from wake up america's webs"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by thebestofall007 on 2007-11-27
I am a long time (now hardcore ex)  windoze user new in Ubuntu and I was wondering how I can  download/capture  (NOT JUST LISTEN TO) the MP3  archives from the website of a radio talk show called "the Terry Anderson show"  that talks about the illegal alien invasion of the USA.

 the website is [http://www.theterryandersonshow.com](http://www.theterryandersonshow.com).  Click on the "listen to past shows courtesy of wake up America" link for the archives and see what I am talking about. 

 In Windows Media Player I used to download the latest archives  by clicking on the archive link, opening windows media player. The file would download to a temporary folder before playing.  When the file finished downloading and began playing, I right clicked on the "now playing" file in the play list and selected the "open file location" option and dragged it out or copied the file to a memory device.

IS THERE A SIMILAR APPLICATION IN UBUNTU THAT ALLOWS  THIS?

---

### Post by candtalan on 2007-11-27
some possible methods:
I use kde generally and I have got used to the app 'KRecord - a Sound Recorder' package is krecord. It will record from the sound system (when playing)  into wav format, has a level indicator and is configured an d set up using the mixer. 
Alternatively I can use audacity in a somewhat similar way. Recorded files wil be (ogg?) unless you have already installed mp3 codec/s (see medibuntu to get repositories and then update, then install your choices.

A more penetrating way to do what you want can be done from that site using the command line  wget app.
Looking at the link of an archive I saw:
javascript : openwindow('http://www.thewakeupamerica.com/TERRY_ANDERSON_ARCHIVES/TerryAnderson_11_25_07.mp3', '80', '200', '340', '180')

the useful bit is:
[ http://www.thewakeupamerica.com/TERRY_ANDERSON_ARCHIVES/TerryAnderson_11_25_07.mp3]( http://www.thewakeupamerica.com/TERRY_ANDERSON_ARCHIVES/TerryAnderson_11_25_07.mp3)

Asuming you have wget installed (?)  -  I did as follows:
usert@my-pc:~$ wget  ttp://www.thewakeupamerica.com/TERRY_ANDERSON_ARCHIVES/Te                                                 rryAnderson_11_25_07.mp3
and the response was as follows:

Resolving [www.thewakeupamerica.com](www.thewakeupamerica.com)... 208.109.14.11
Connecting to www.thewakeupamerica.com|208.109.14.11|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 11,374,868 (11M) [audio/mpeg]

100%[=====================================================================>] 11,374,868    53.61K/s    ETA 00:00
21:25:12 (68.09 KB/s) - `TerryAnderson_11_25_07.mp3' saved [11374868/11374868]

as indicate dth emp3 file was downloaded and saved into the home directory

hth

---

### Post by thebestofall007 on 2007-11-27
Ur a lifesaver man. thanks! Now I can get the news about this scourge to our country; the news the liberal media fails to show; cheers to conservative talk radio. I found the wget command line option to be the fastest option and even better than windows media, I left windows because I was getting sick and tired of micro$oft making their operating systems fat and heavy while having to drop a dime every time i had to get important software etc. I ESPECIALLY HATE WINDOWS VISTA FOR HOW SLOW IT IS!!!


 
**THANKS A BUNCH.**

---

