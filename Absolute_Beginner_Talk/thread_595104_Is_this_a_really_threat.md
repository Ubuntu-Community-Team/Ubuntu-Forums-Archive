---
title: "Is this a really threat?"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by AngelBreath on 2007-10-28
Hi, i was online but away pc , and when come back i saw a message in Firestarter that i was attacked from an IP. With who is i took this message:

Information related to '212.27.60.0 - 212.27.63.255'

inetnum:        212.27.60.0 - 212.27.63.255
netname:        FR-PROXAD
descr:          Free SAS (ProXad)
descr:          internal infrastructure (servers)
descr:          Paris, France
country:        FR
admin-c:        ACP23-RIPE
tech-c:         TCP8-RIPE
status:         ASSIGNED PA
mnt-by:         PROXAD-MNT
source:         RIPE # Filtered
remarks:        INFRA-AW

role:           Administrative Contact for ProXad
address:        Free SAS / ProXad
address:        8, rue de la Ville L'Eveque
address:        75008 Paris
phone:          +33 1 73 50 20 00
fax-no:         +33 1 73 92 25 69
remarks:        trouble:      Information: [http://www.proxad.net/](http://www.proxad.net/)
remarks:        trouble:      Spam/Abuse requests: mailto:abuse@proxad.net
admin-c:        RA999-RIPE
tech-c:         FG4214-RIPE
nic-hdl:        ACP23-RIPE
mnt-by:         PROXAD-MNT
source:         RIPE # Filtered
abuse-mailbox:  [email]abuse@proxad.net[/email]

role:           Technical Contact for ProXad
address:        Free SAS / ProXad
address:        8, rue de la Ville L'Eveque
address:        75008 Paris
phone:          +33 1 73 50 20 00
fax-no:         +33 1 73 92 25 69
remarks:        trouble:      Information: [http://www.proxad.net/](http://www.proxad.net/)
remarks:        trouble:      Spam/Abuse requests: mailto:abuse@proxad.net
admin-c:        RA999-RIPE
tech-c:         FG4214-RIPE
nic-hdl:        TCP8-RIPE
mnt-by:         PROXAD-MNT
source:         RIPE # Filtered
abuse-mailbox:  [email]abuse@proxad.net[/email]

% Information related to '212.27.32.0/19AS12322'

route:        212.27.32.0/19
descr:        ProXad network / Free SA
descr:        Paris, France
origin:       AS12322
mnt-by:       PROXAD-MNT
source:       RIPE # Filtered

Is it a threat for me? or just someone tried something? and I suppose to inform his ISP?

---

### Post by Crafty Kisses on 2007-10-28
> **AngelBreath said:**
> Hi, i was online but away pc , and when come back i saw a message in Firestarter that i was attacked from an IP. With who is i took this message:

Information related to '212.27.60.0 - 212.27.63.255'

inetnum:        212.27.60.0 - 212.27.63.255
netname:        FR-PROXAD
descr:          Free SAS (ProXad)
descr:          internal infrastructure (servers)
descr:          Paris, France
country:        FR
admin-c:        ACP23-RIPE
tech-c:         TCP8-RIPE
status:         ASSIGNED PA
mnt-by:         PROXAD-MNT
source:         RIPE # Filtered
remarks:        INFRA-AW

role:           Administrative Contact for ProXad
address:        Free SAS / ProXad
address:        8, rue de la Ville L'Eveque
address:        75008 Paris
phone:          +33 1 73 50 20 00
fax-no:         +33 1 73 92 25 69
remarks:        trouble:      Information: [http://www.proxad.net/](http://www.proxad.net/)
remarks:        trouble:      Spam/Abuse requests: mailto:abuse@proxad.net
admin-c:        RA999-RIPE
tech-c:         FG4214-RIPE
nic-hdl:        ACP23-RIPE
mnt-by:         PROXAD-MNT
source:         RIPE # Filtered
abuse-mailbox:  [email]abuse@proxad.net[/email]

role:           Technical Contact for ProXad
address:        Free SAS / ProXad
address:        8, rue de la Ville L'Eveque
address:        75008 Paris
phone:          +33 1 73 50 20 00
fax-no:         +33 1 73 92 25 69
remarks:        trouble:      Information: [http://www.proxad.net/](http://www.proxad.net/)
remarks:        trouble:      Spam/Abuse requests: mailto:abuse@proxad.net
admin-c:        RA999-RIPE
tech-c:         FG4214-RIPE
nic-hdl:        TCP8-RIPE
mnt-by:         PROXAD-MNT
source:         RIPE # Filtered
abuse-mailbox:  [email]abuse@proxad.net[/email]

% Information related to '212.27.32.0/19AS12322'

route:        212.27.32.0/19
descr:        ProXad network / Free SA
descr:        Paris, France
origin:       AS12322
mnt-by:       PROXAD-MNT
source:       RIPE # Filtered

Is it a threat for me? or just someone tried something? and I suppose to inform his ISP?

Was the person trying to DDoS you or something? I don't get it.

---

### Post by AngelBreath on 2007-10-28
> **Codename said:**
> Was the person trying to DDoS you or something? I don't get it.

I really dont know. I just had this message in Firestarter. I have fail2ban installed too, but i checked the logs and nothing was there. (suppose to ban attacks from ips that are trying more than 3 times)

---

### Post by Crafty Kisses on 2007-10-28
> **AngelBreath said:**
> I really dont know. I just had this message in Firestarter. I have fail2ban installed too, but i checked the logs and nothing was there. (suppose to ban attacks from ips that are trying more than 3 times)

Not sure then, looks to me like it's a mini DDoS, but I guess call up their ISP. :KS

---

### Post by AngelBreath on 2007-10-28
And at firestarter events log i have this message:

Time: 28 October 14:52
Port : 48594
Source:perso146-g5.free.fr
Protocol:TCP
Service: Uknown

Any idea?

---

### Post by Crafty Kisses on 2007-10-28
> **AngelBreath said:**
> And at firestarter events log i have this message:

Time: 28 October 14:52
Port : 48594
Source:perso146-g5.free.fr
Protocol:TCP
Service: Uknown

Any idea?

No idea, but Ubuntu has built in iptables, so even if they did a portscan, it would show all ports closed.

---

