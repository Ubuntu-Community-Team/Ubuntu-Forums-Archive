---
title: "master and slave issues"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by lordvolo on 2006-12-05
I have my master HDD dualbooted with Xubuntu and Windows XP.i have another HDD and i want to install it my computer. I did on the second connection on the cable that goes from my master to the mother board.this is the problem it only works as master in the first port.  I need help making it the slave.

Specs
Maxtor
model:  5T040H4
40GB
formated to fat32

it seems stange to ask this but if i make my master i can only boot in to windows and not Xubuntu because it looks for the file system in the master.

---

### Post by tempest152 on 2006-12-05
> **lordvolo said:**
> I have my master HDD dualbooted with Xubuntu and Windows XP.i have another HDD and i want to install it my computer. I did on the second connection on the cable that goes from my master to the mother board.this is the problem it only works as master in the first port.  I need help making it the slave.

Specs
Maxtor
model:  5T040H4
40GB
formated to fat32

it seems stange to ask this but if i make my master i can only boot in to windows and not Xubuntu because it looks for the file system in the master.

Make sure you check for jumper switch on the HDD, not as important on some newer drives, but I dualboot with XP on master and Ubuntu on the slave.. I think I set my Slave to "CS" (Cable Select)
, which was the last jumper position.

---

### Post by kakalaky on 2006-12-05
probably a jumper issue.  Follow the instructions here:
[https://maxtor.custhelp.com/cgi-bin/maxtor.cfg/php/enduser/std_adp.php?p_faqid=653&p_created=985375652&p_sid=8s2PJooi&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD01VDA0MEg0IGp1bXBlcg**&p_li=&p_topview=1]("https://maxtor.custhelp.com/cgi-bin/maxtor.cfg/php/enduser/std_adp.php?p_faqid=653&p_created=985375652&p_sid=8s2PJooi&p_accessibility=0&p_lva=&p_sp=cF9zcmNoPTEmcF9zb3J0X2J5PSZwX2dyaWRzb3J0PSZwX3Jvd19jbnQ9MSZwX3Byb2RzPSZwX2NhdHM9JnBfcHY9JnBfY3Y9JnBfc2VhcmNoX3R5cGU9YW5zd2Vycy5zZWFyY2hfbmwmcF9wYWdlPTEmcF9zZWFyY2hfdGV4dD01VDA0MEg0IGp1bXBlcg**&p_li=&p_topview=1")

---

### Post by Snowmayne on 2006-12-05
Once you made the jumper change, double check you bios setting to make sure that the motherboard is recognizing both drives and the roles they're playing.

On my PC I made sure my main drive was set as master and secondary was set as slave since, for the life of me I couldn't figure out which drive would be master - the one attached on the cable closest to the motherboard or the one furthest.:rolleyes: (still can't for that matter)

Installed ubuntu on the second drive (since it was only holding music at the time), and both OSes are happy that way ;)

---

### Post by lordvolo on 2006-12-05
thanks a lot! it worked, but i went into my disk-admin and i need to have an access path for it to enable it.  what should i put?

---

### Post by lordvolo on 2006-12-05
anything?

---

### Post by CatKiller on 2006-12-05
> **lordvolo said:**
> anything?

Anything. It doesn't matter. A subdirectory of /mnt is traditional, although if you make it a subdirectory of /media you'll get an icon on the Desktop for it, if you happen to like that sort of thing.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

