---
title: "steam help please"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by monk3y on 2007-07-11
um i installed steam ok with wine.

but after i installed i opened steam up and it got stuck on the steam updater screen at 26% and after that it closes and gives an error saying that

there can only be one copy of steam running at a time

can anybody help me with this? 

also i installed steam in the default directory of c:/programfiles/steam (give or take somthing like that) but i cant find that file?

---

### Post by ZeroWing on 2007-07-11
> **monk3y said:**
> um i installed steam ok with wine.

but after i installed i opened steam up and it got stuck on the steam updater screen at 26% and after that it closes and gives an error saying that

there can only be one copy of steam running at a time

can anybody help me with this? 

also i installed steam in the default directory of c:/programfiles/steam (give or take somthing like that) but i cant find that file?

 It would be in ~/.wine/c_drive/Program Files/Valve/Steam, or something like that.

---

### Post by monk3y on 2007-07-11
i tried to find that directory but it says it dosent exist

---

### Post by bren on 2007-07-11
try the find command

[http://www.computerhope.com/unix/ufind.htm](http://www.computerhope.com/unix/ufind.htm)

and

ps -e | grep steam

will show you the process that is running together with the process no

kill <process no>

will help you get rid of the excess .... if you are sure it is ok to do this....


bren

---

### Post by dorath on 2007-07-11
You can try to kill the Steam process using the command line.  Open up a terminal window (Applications --> Accessories --> Terminal) and try the following:```
ps -e
```
This will list all of the processes running on your machine.  Look for one called steam and note the left-most number:  that is the PID (Process ID, I think), of Steam.  Now enter this into the terminal:```
kill -kill [PID_#_for_Steam]
```Wait a couple seconds and try running Steam again.  If you don't see Steam, but do see wineserver, then you can trill killing wineserver (a new wineserver will start next time you run WINE).

EDIT:
Of course, I wrote all that assuming that you're getting that Steam error message because Steam is still actually running.

---

### Post by kavon89 on 2007-07-11
Known and old bug for Wine. I am pretty sure it has been fixed, update to the latest version of Wine, 0.9.40.

[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

The Package Manager only has up to 0.9.33, follow the two step instructions on that page and you should be ready to go! :D

To kill a crashed Steam, enter this into your terminal.

```
wineserver -k
```
Note, this will also kill any other programs running under Wine, it works very well for emergency situations where you would have had to hard restarted if you didn't have a Terminal window to ALT+TAB to.

---

### Post by monk3y on 2007-07-11
i got it to work! thx everone for the advice!!

ps. windows sucks compared to this ubuntu rocks

---

### Post by KushMaster on 2007-09-10
monk3y how did you get it to work, becase i tryed everythink the people reposted told me to do and nothing worked for me, and i have the exact same problem as you did .

---

### Post by afonic on 2007-09-10
> **KushMaster said:**
> monk3y how did you get it to work, becase i tryed everythink the people reposted told me to do and nothing worked for me, and i have the exact same problem as you did .

Did you upgrade wine as kavon89 suggested?

---

### Post by KushMaster on 2007-09-10
yes i have wine 0.9.44 and i wave steam, with little icon on my desktop. when i start it it upgrades to 26% and it tells me that i can only run one copy of steam at a time. what do i do to fix this ?

---

### Post by bburns on 2007-12-07
Yeah... I have this problem, too. Wineserver killed, no steam running, wine-0.9.50 from winehq. Updates to 26%, dies, "blah blah blah, one copy of steam at a time people, save some steam for everybody else". I have tried deleting ClientRegistry.blob as suggested on another forum, reinstalling, repairing the install... I'm about out of ideas.

I know how to list and terminate processes and such. Steam and wineserver are both DEFINITELY dead :)

-b

---

### Post by bburns on 2007-12-07
Hmm. I got it. Just kept running it over and over, one time it worked.

Very, very, very, very strange indeed. Deterministic machines my foot.

Anyway.

-b

---

