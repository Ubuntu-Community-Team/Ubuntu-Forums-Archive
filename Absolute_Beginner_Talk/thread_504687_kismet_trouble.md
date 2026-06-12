---
title: "kismet trouble"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by tennvolsmb on 2007-07-19
ok guys I'm not sure if I'm even in the right place but for two days now I have been trying to configure kismet and everytime there is an error saying I need to configure packet files.

here is what happens when i try to enter kismet

```
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before starting UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
[1] + Done(1)                    ${BIN}/kismet_server --silent ${server}

```

can someone help me to figure out how to configure my packet source it is driving me crazy!!!

---

### Post by plettpc on 2007-08-10
The Kismet server needs to know where to get it's data from :::::
edit  :   /etc/kismet/kismet.conf
restart server

source=sourcetype,interface,name[,initialchannel]



While u're at it check out the other options too.

---

