---
title: "wifi command question"
date: 2008-03-27
forum: Apple Intel Users
---

### Post by pdbeard on 2008-03-27
i have done the madwifi steps as follows for gutsy on my macbook. I have an anthros card
```
sudo apt-get install build-essential autoconf automake
wget http://snapshots.madwifi.org/madwifi-ng-current.tar.gz
tar -zxvf madwifi-ng-current.tar.gz
cd madwifi<tab>
make
sudo make install-modules
echo -e '#!/bin/sh\n/sbin/iwpriv ath0 bgscan 0' | sudo tee -a /etc/acpi/resume.d/99-madwifi-bgscan.sh
sudo chmod 755 /etc/acpi/resume.d/99-madwifi-bgscan.sh
```

but im unsure if the commands from echo onwards worked (im completely new to linux) 

I get a list of wireless networks but it still doesn't seem to get internet from it. Is there anyway i can check to see if the instillation worked correctly? or perhaps a way to redo it? 


also the install build-essentials didn't work until i did it without autoconf and automake.

---

### Post by cyberdork33 on 2008-03-27
if you can see APs then the driver install is good. you should now be able to use network manager to select an AP and connect.

---

