---
title: "For god sake help me"
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by umairsaeed219 on 2006-10-01
Hi i have askedm this question previously both in forum and mailing list but didnt get response.

i have successfully installed my modem ie. Intel536ep 
Now i have configured my connection using "pppconfig'
[B]when i enter the command pon # connect to isp configured as "provider"  modem speaker create noise.
i have run "plog #" which shows the following message
[/B]
sep 30 14:52:08 localho chat [5205]: ATZ ^M ^M
sep 30 14:52:08 localho chat [5205]: OK
sep 30 14:52:08 localho chat [5205]: --got it
sep 30 14:52:08 localho chat [5205]:send (ATDT13121313 ^M)
sep 30 14:52:08 localho chat [5205]:expect(connect)
sep 30 14:52:08 localho chat [5205]: ^M

**After that modeem speaker becomes silent when i again run the "plog #"**
following message appear
sep 30 14:52:08 localho chat [5205]: --get it
sep 30 14:52:08 localho chat [5205]:send(ATDT13121313^M)
sep 30 14:52:08 localho chat [5205]:expect (connect)
sep 30 14:52:08 localho chat [5205]:  ^M
sep 30 14:52:08 localho chat [5205]:alarm
sep 30 14:52:08 localho chat [5205]:connect script failed
sep 30 14:52:08 localho chat [5205]:exit

tell me how can i fix it

---

### Post by sbergman27 on 2006-10-01
It's been a long time since I've done dialup.  

Are you using chat, pap, or chap?

From the looks of it, it never gets "CONNECT" back from the modem.

How long does the sound from the modem last before it goes silent? About 10 seconds or less?  Or longer?

---

### Post by umairsaeed219 on 2006-10-01
I use PAP and noise of modem lasts for almost 10 sec

---

### Post by sbergman27 on 2006-10-01
What is in /etc/chatscripts/your_connection_name

where your_connection_name is the name you gave to label the connection?

e.g. in a terminal:

cat /etc/chatscripts/your_connection_name 

will show what's in the file.

The only thing that I see that doesn't necessarily look right is that I would expect CONNECT to be capitalized.  The modem will send 'CONNECT' rather than 'connect'.  If the script is expecting "connect" it won't get it and will time out after 45 seconds.

The script may or may not be case sensitive.  I can't remember.

---

### Post by editrix on 2006-10-01
Had the same problem, and this worked for me:

In /etc/ppp/options comment out the line 
auth
that requires remote host to authenticate itself.

---

