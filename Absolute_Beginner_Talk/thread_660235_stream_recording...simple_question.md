---
title: "stream recording...simple question"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-01-06
i need a programm which acts like streamer-recorder and also do 
seperating-naming the streams-tracks according to the radio tags after recording them....
i have no idea i tried streamtuner but doesn't work...

suggestions?

---

### Post by philinux on 2008-01-06
I've used audacity to record streaming stuff also "sound recorder" works too.

---

### Post by mcduck on 2008-01-06
Streamtuner is just for browsing the internet radios. THe tool you are looking for is Streamripper. It will rip the stream, cut it into separate files and name them for you.

Streamripper is a command-line tool, but if you also have Streamtuner installed you can use them together by selecting the stream you want to rip from Streamtuner and hitting the record-button.

---

### Post by someoneouthere on 2008-01-06
i came through a "script" : [http://ubuntuforums.org/archive/index.php/t-325430.html]("http://ubuntuforums.org/archive/index.php/t-325430.html")

for ripping through amarok using streamripping
dont know if it works

---

### Post by someoneouthere on 2008-01-06
...or i could just install the script....silly me...:P

---

### Post by someoneouthere on 2008-01-06
> **mcduck said:**
> Streamtuner is just for browsing the internet radios. THe tool you are looking for is Streamripper. It will rip the stream, cut it into separate files and name them for you.

Streamripper is a command-line tool, but if you also have Streamtuner installed you can use them together by selecting the stream you want to rip from Streamtuner and hitting the record-button.

streamtuner works but doesnt seperate them...

---

### Post by mcduck on 2008-01-06
> **someoneouthere said:**
> streamtuner works but doesnt seperate them...
Then it might be that the station you are ripping doesn't broadcast information about track changes. Streamripper should, by default, rip into individual files as long as it gets information about track changes and you don't specifically tell it to rip into single file.

Try from a terminal, I use the following command to rip streams and for all stations that broadcast track names it will rip them into separate files:
```
streamripper http://scfire-chi-aa04.stream.aol.com:80/stream/1050 -d /home/mcduck/Downloads -r
```
(replace the stream url with correct one, and of course the download directory as well. The -r option creates a relay stream so if you wish to listen to the stream at the same time you don't need 2 connections to the stream but can instead point your player to "http://localhost:8000" to listen to the stream.)

---

### Post by someoneouthere on 2008-01-06
i've tried the frontend kstreamripper and it works...

---

