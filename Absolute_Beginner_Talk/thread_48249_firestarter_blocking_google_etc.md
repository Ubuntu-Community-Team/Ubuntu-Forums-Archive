---
title: "firestarter blocking google etc"
date: 2005-07-11
forum: Absolute Beginner Talk
---

### Post by glandula on 2005-07-11
recently my firestarter has started blocking google of all things (it didnt before) it all started when i went to methlabs.com to ahve a look at peerguardian. the event log shows its blocked a traceroute from methlabs, and after that also from google. ive tried enabling traceroute and ms traceroute in the icmp filtering but it doesent make any difference

any idea whats wrong?

ps google works again after a reboot, by not methlabs. gotta disable firesterter to visit that site

---

### Post by hamiltonlight on 2005-07-11
I'm glad I am not the only one experiencing this! 

Each time I try to access Google Firestarter logs an event showing that ip 72.14.207.99 is trying to access a port in the range of 34101 to 34051. 

I left the pc for a while and I can now access Google again?? 

I've not changed any ICMP options in Firestarter or rebooted. Its very puzzling.  ](*,)

---

### Post by glandula on 2005-07-11
[QUOTE=][/QUOTE]
 thats the ip shown in my event log too..waiting for the gurus to help us :)

---

### Post by cwaldbieser on 2005-07-11
I get this problem when going to [http://www.tfarchive.com/](http://www.tfarchive.com/).  When I do the hostname lookup, it appears to be "isamail.meuserver.net".  I can reproduce this behavior on both Konqueror and Firefox, as well as with wget and curl.

---

### Post by bryan986 on 2005-10-07
in the /etc/firestarter/non-routables file, comment out the line that is "72.0.0.0/8"  (put a # in front of it...)

---

