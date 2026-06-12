---
title: "Icecast / IceS help."
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by Unknowndeepness on 2006-05-13
Hello there!
I need some help getting a radiostream working.

I have changed password in both configs to the same, and IceS is on the right protocol. But still it wont work.
Here is my output:


IceS:
```

root@inject:/usr/local/etc# ices -c ices.conf
Logfile opened
Playing /media/hd/music/rock/h/Him-Peoples-2006-VOiCE/01_him_-_this_we_know.mp3
Error during send: Mount failed on http://localhost:8000/ices, error: Login failed
Error during send: Mount failed on http://localhost:8000/ices, error: Login failed
Error during send: Mount failed on http://localhost:8000/ices, error: Login failed
Error during send: Mount failed on http://localhost:8000/ices, error: Login failed
Ices Exiting...

```

IceCast:
```

root@inject:/usr/local/etc# icecast -c icecast.conf
[13/May/2006:14:17:13] ERROR: Could not find a suitable directory for template files, something might be wrong!
Icecast Version 1.3.12 Initializing...
Icecast comes with NO WARRANTY, to the extent permitted by law.
You may redistribute copies of Icecast under the terms of the
GNU General Public License.
For more information about these matters, see the file named COPYING.
Starting thread engine...
[13/May/2006:14:17:13] Icecast Version 1.3.12 Starting..
[13/May/2006:14:17:13] Starting Admin Console Thread...
-> [13/May/2006:14:17:13] Starting main connection handler...
-> -> [13/May/2006:14:17:13] WARNING: Resolving the server name [Unknowndeepness] does not work!
-> [13/May/2006:14:17:13] Listening on port 8000...
-> [13/May/2006:14:17:13] Listening on port 8001...
-> [13/May/2006:14:17:13] Using 'Unknowndeepness' as servername...
-> [13/May/2006:14:17:13] Server limits: 100 clients, 100 clients per source, 10 sources, 5 admins
-> [13/May/2006:14:17:13] WWW Admin interface accessible at http://Unknowndeepness:8000/admin
-> [13/May/2006:14:17:13] Starting Calender Thread...
-> [13/May/2006:14:17:13] Starting UDP handler thread...
-> [13/May/2006:14:17:13] Starting relay connector thread...
-> [13/May/2006:14:17:13] [Bandwidth: 0.000000MB/s] [Sources: 0] [Clients: 0] [Admins: 1] [Uptime: 0 seconds]
[COLOR="Red"]-> [13/May/2006:14:17:16] Kicking unknown 1 [127.0.0.1] [Failed to execute admin command], connected for 0 seconds
-> [13/May/2006:14:17:16] Kicking source 2 [127.0.0.1] [Bad Password] [encoder], connected for 0 seconds, 0 bytes transfered. -1 sources connected[/COLOR]
-> [13/May/2006:14:17:16] Kicking all 0 clients for source 2
-> [13/May/2006:14:19:13] [Bandwidth: 0.000000MB/s] [Sources: 0] [Clients: 0] [Admins: 1] [Uptime: 2 minutes]

```

As you can se, where i highligted red, it connects but it sais wrong pass.

---

### Post by Unknowndeepness on 2006-05-13
Double post. Sry.

---

### Post by andlinux21 on 2006-05-13
I honestly wish i could help you I use shoutcast so I dont know much about icecast.  If you are using a router make sure you have the proper ports forwarded and everything should work just fine.. :D

---

### Post by Unknowndeepness on 2006-05-13
Yep. But theres no router ^^

Thx anyway.

---

### Post by Unknowndeepness on 2006-05-13
Double post. Sry. (And yes, my computer HATES me. )

---

