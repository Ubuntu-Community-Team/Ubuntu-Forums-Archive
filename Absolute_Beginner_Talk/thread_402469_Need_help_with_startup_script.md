---
title: "Need help with startup script"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by becho on 2007-04-05
I'm running a Day of Defeat Source server and would like it to start at boot.I tried making a script as follows named srcds.sh:

#!/bin/bash
cd srcds_l && screen -S dod ./srcds_run -console -game dod -port 27016 +ip ???.???.???.??? +map dod_orange_sniper +maxplayers 16 -tickrate 33

Then i did: 
sudo chmod +x srcds.sh

Then i did:
sudo mv srcds.sh /etc/init.d

Then i did:
sudo update-rc.d srcds.sh defaults

It made the links but when i rebooted it did not start.The actual server files are located in my home folder.If i run the command in terminal it works but don't want to do that all the time.Thanks!!

---

### Post by bruenig on 2007-04-05
Just a stab, perhaps instead of having it cd into a folder, just use the absolute path. I assume something like this 
```
screen -S dod ~/srcds_l/srcds_run -console -game dod -port 27016 +ip ???.???.???.??? +map dod_orange_sniper +maxplayers 16 -tickrate 33
```

---

### Post by becho on 2007-04-05
Will give it a shot,thanks!!

---

### Post by becho on 2007-04-07
Did not work,says permission denied if i try to run in from init.d but if i move it back to my home folder the script works if i doulbe click on it.Must be some reason i can't get init.d to access a folder in my home directory.I even chmod 777 the srcds_l folder and the srcds_run.sh!!I'm lost

---

