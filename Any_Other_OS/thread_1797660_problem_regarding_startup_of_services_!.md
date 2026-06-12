---
title: "problem regarding startup of services !"
date: 2011-07-05
forum: Any Other OS
---

### Post by meTroubled on 2011-07-05
[COLOR=Black]i'm running fedora 15 gnome 3....
everything was working fine when suddenly some things i noticed going wrong with my startup services.
whenever i hibernate or shutdown my system and restart then i find some services not working.
First,i found my _[COLOR=Indigo]wireless network[/COLOR]_ no longer popped on when turning switch on my laptop ON,so i started it with _[COLOR=Indigo]Fn+F5[/COLOR]_(my laptop custom shortcut)
Next time i discovered that _[COLOR=Indigo]bluetooth[/COLOR]_ is not working,so i started it by _[COLOR=Indigo]Fn+F8[/COLOR]_(again my laptop custom shortcut)
things didn't stopped here only....
Then i discovered that my _[COLOR=Indigo]touchpad[/COLOR]_ was not working,so i restarted it with _[COLOR=Indigo]Fn+F6[/COLOR]_.
what is all this going on ?
Please help....!!
These things are obviously not in sequence....
i feel that these services need to be started everytime i login ![/COLOR]

---

### Post by hawthornso23 on 2011-07-05
I'm not sure how likely you are to get a solution to a fedora problem on an ubuntu forum. 

Maybe you could install ubuntu 11.04.  Hey - that WOULD probably fix it.:lolflag:

---

### Post by meTroubled on 2011-07-05
> **hawthornso23 said:**
> I'm not sure how likely you are to get a solution to a fedora problem on an ubuntu forum. 

Maybe you could install ubuntu 11.04.  Hey - that WOULD probably fix it.:lolflag:

this is not exactly a fedora problem.
This is a very common issue and i don't understand how forums matter in this case anyone if knows anything about linux can help if he wishes to.
Real experts are not really limited only to a distro but they work and play with linux as general,i believe !:)

---

### Post by meTroubled on 2011-07-06
anyone ?

---

### Post by howefield on 2011-07-07
Thread title amended to include Fedora prefix.

---

### Post by meTroubled on 2011-07-07
> **howefield said:**
> Thread title amended to include Fedora prefix.


i hope that helps....'coz i'm not receiving any help upto now !:(:(

---

### Post by meTroubled on 2011-07-08
**update**:
I don't know how but my touchpad issue is resolved !
When i did a yum update this morning,and then i restarted my laptop....i didn't need to turn it ON again using shortcut !
But other 2 issues are still not solved.

---

### Post by el_koraco on 2011-07-08
ATL + F2, and then 

```
gnome-session-properties

```

See if you have bluetooth and wifi enabled

---

### Post by meTroubled on 2011-07-08
> **el_koraco said:**
> ATL + F2, and then 

```
gnome-session-properties

```See if you have bluetooth and wifi enabled


there is bluetooth manager(bluetoth manager applet),which is marked...but there is no wifi

---

### Post by el_koraco on 2011-07-08
lemme just boot into fedora and see what it looks like on my machine.

---

### Post by meTroubled on 2011-07-08
> **el_koraco said:**
> lemme just boot into fedora and see what it looks like on my machine.


> here is my **chkconfig** outputabrt-ccpp          0:off    1:off    2:off    3:on    4:off    5:on    6:off
abrt-oops          0:off    1:off    2:off    3:on    4:off    5:on    6:off
auditd             0:off    1:off    2:on    3:on    4:on    5:on    6:off
backuppc           0:off    1:off    2:off    3:off    4:off    5:off    6:off
capi               0:off    1:off    2:on    3:on    4:on    5:on    6:off
cgconfig           0:off    1:off    2:on    3:on    4:on    5:on    6:off
cgred              0:off    1:off    2:off    3:off    4:off    5:off    6:off
cpuspeed           0:off    1:on    2:on    3:on    4:on    5:on    6:off
cups               0:off    1:off    2:on    3:on    4:on    5:on    6:off
dc_client          0:off    1:off    2:off    3:off    4:off    5:off    6:off
dc_server          0:off    1:off    2:off    3:off    4:off    5:off    6:off
dnsmasq            0:off    1:off    2:off    3:off    4:off    5:off    6:off
ebtables           0:off    1:off    2:off    3:off    4:off    5:off    6:off
firstboot          0:off    1:off    2:off    3:off    4:off    5:off    6:off
gfs2               0:off    1:off    2:off    3:off    4:off    5:off    6:off
gpsd               0:off    1:off    2:off    3:off    4:off    5:off    6:off
hsqldb             0:off    1:off    2:off    3:off    4:off    5:off    6:off
httpd              0:off    1:off    2:off    3:off    4:off    5:off    6:off
innd               0:off    1:off    2:off    3:off    4:off    5:off    6:off
ip6tables          0:off    1:off    2:on    3:on    4:on    5:on    6:off
ipsec              0:off    1:off    2:off    3:off    4:off    5:off    6:off
iptables           0:off    1:off    2:on    3:on    4:on    5:on    6:off
irda               0:off    1:off    2:off    3:off    4:off    5:off    6:off
iscsi              0:off    1:off    2:off    3:on    4:on    5:on    6:off
iscsid             0:off    1:off    2:off    3:on    4:on    5:on    6:off
isdn               0:off    1:off    2:on    3:on    4:on    5:on    6:off
jetty              0:off    1:off    2:off    3:off    4:off    5:off    6:off
ksm                0:off    1:off    2:off    3:on    4:on    5:on    6:off
ksmtuned           0:off    1:off    2:off    3:on    4:on    5:on    6:off
libvirt-guests     0:off    1:off    2:on    3:on    4:on    5:on    6:off
libvirtd           0:off    1:off    2:off    3:on    4:on    5:on    6:off
lvm2-monitor       0:off    1:on    2:on    3:on    4:on    5:on    6:off
mdmonitor          0:off    1:off    2:on    3:on    4:on    5:on    6:off
multipathd         0:off    1:off    2:off    3:off    4:off    5:off    6:off
mysqld             0:off    1:off    2:off    3:off    4:off    5:off    6:off
named              0:off    1:off    2:off    3:off    4:off    5:off    6:off
netconsole         0:off    1:off    2:off    3:off    4:off    5:off    6:off
netfs              0:off    1:off    2:off    3:on    4:on    5:on    6:off
network            0:off    1:off    2:off    3:off    4:off    5:off    6:off
nfs                0:off    1:off    2:off    3:off    4:off    5:off    6:off
nfslock            0:off    1:off    2:off    3:on    4:on    5:on    6:off
nmb                0:off    1:off    2:off    3:off    4:off    5:off    6:off
openct             0:off    1:off    2:on    3:on    4:on    5:on    6:off
openvpn            0:off    1:off    2:off    3:off    4:off    5:off    6:off
pcscd              0:off    1:off    2:on    3:on    4:on    5:on    6:off
portreserve        0:off    1:off    2:on    3:on    4:on    5:on    6:off
postgresql         0:off    1:off    2:off    3:off    4:off    5:off    6:off
psacct             0:off    1:off    2:off    3:off    4:off    5:off    6:off
rpcbind            0:off    1:off    2:on    3:on    4:on    5:on    6:off
rpcgssd            0:off    1:off    2:off    3:on    4:on    5:on    6:off
rpcidmapd          0:off    1:off    2:off    3:on    4:on    5:on    6:off
rpcsvcgssd         0:off    1:off    2:off    3:off    4:off    5:off    6:off
sandbox            0:off    1:off    2:off    3:off    4:off    5:on    6:off
saslauthd          0:off    1:off    2:off    3:off    4:off    5:off    6:off
sendmail           0:off    1:off    2:on    3:on    4:on    5:on    6:off
smb                0:off    1:off    2:off    3:off    4:off    5:off    6:off
smolt              0:off    1:off    2:on    3:on    4:on    5:on    6:off
snmpd              0:off    1:off    2:off    3:off    4:off    5:off    6:off
snmptrapd          0:off    1:off    2:off    3:off    4:off    5:off    6:off
spamassassin       0:off    1:off    2:off    3:off    4:off    5:off    6:off
speech-dispatcherd    0:off    1:off    2:off    3:off    4:off    5:off    6:off
squid              0:off    1:off    2:off    3:off    4:off    5:off    6:off
sshd               0:off    1:off    2:on    3:on    4:on    5:on    6:off
svnserve           0:off    1:off    2:off    3:off    4:off    5:off    6:off
vsftpd             0:off    1:off    2:off    3:off    4:off    5:off    6:off
wpa_supplicant     0:off    1:off    2:off    3:off    4:off    5:off    6:off
ypbind             0:off    1:off    2:off    3:off    4:off    5:off    6:off
zvbid              0:off    1:off    2:off    3:off    4:off    5:off    6:off

---

### Post by el_koraco on 2011-07-08
maybe you could try adding nm-applet to startup services? check it out, this is what it looks like on my system.

---

### Post by meTroubled on 2011-07-08
> **el_koraco said:**
> maybe you could try adding nm-applet to startup services? check it out, this is what it looks like on my system.

it is already there !

---

### Post by el_koraco on 2011-07-08
that's pretty weird. My chkconfig is similar to yours, don't see any differences. Might be something systemd related, but I'm way out of my depth here. For real, did you try the Fedora forums? There are people there who know the internals of Fedora much better than guys here do.

---

### Post by meTroubled on 2011-07-08
> **el_koraco said:**
> that's pretty weird. My chkconfig is similar to yours, don't see any differences. Might be something systemd related, but I'm way out of my depth here. For real, did you try the Fedora forums? There are people there who know the internals of Fedora much better than guys here do.


i've posted my question there too but no help !
this thing i feel is not actually fedora related, it suddenly came up....touchpad even suddenly worked out !

---

### Post by el_koraco on 2011-07-08
Wish I could help you, but I'm out of ideas.

---

### Post by meTroubled on 2011-07-08
> **el_koraco said:**
> Wish I could help you, but I'm out of ideas.


ohhkk...thanks...:D:D

---

### Post by meTroubled on 2011-07-09
**another update:**

i again don't know how but it happened again,my other two issues are solved too...
here i'm posting my **chkconfig** output after problem is solved,for those who care to look in my issue...

```
abrt-ccpp          0:off    1:off    2:off    3:on    4:off    5:on    6:off
abrt-oops          0:off    1:off    2:off    3:on    4:off    5:on    6:off
auditd             0:off    1:off    2:on    3:on    4:on    5:on    6:off
backuppc           0:off    1:off    2:off    3:off    4:off    5:off    6:off
capi               0:off    1:off    2:on    3:on    4:on    5:on    6:off
cgconfig           0:off    1:off    2:on    3:on    4:on    5:on    6:off
cgred              0:off    1:off    2:off    3:off    4:off    5:off    6:off
cpuspeed           0:off    1:on    2:on    3:on    4:on    5:on    6:off
cups               0:off    1:off    2:on    3:on    4:on    5:on    6:off
dc_client          0:off    1:off    2:off    3:off    4:off    5:off    6:off
dc_server          0:off    1:off    2:off    3:off    4:off    5:off    6:off
dnsmasq            0:off    1:off    2:off    3:off    4:off    5:off    6:off
ebtables           0:off    1:off    2:off    3:off    4:off    5:off    6:off
firstboot          0:off    1:off    2:off    3:off    4:off    5:off    6:off
gfs2               0:off    1:off    2:off    3:off    4:off    5:off    6:off
gpsd               0:off    1:off    2:off    3:off    4:off    5:off    6:off
hsqldb             0:off    1:off    2:off    3:off    4:off    5:off    6:off
httpd              0:off    1:off    2:off    3:off    4:off    5:off    6:off
innd               0:off    1:off    2:off    3:off    4:off    5:off    6:off
ip6tables          0:off    1:off    2:on    3:on    4:on    5:on    6:off
ipsec              0:off    1:off    2:off    3:off    4:off    5:off    6:off
iptables           0:off    1:off    2:on    3:on    4:on    5:on    6:off
irda               0:off    1:off    2:off    3:off    4:off    5:off    6:off
iscsi              0:off    1:off    2:off    3:on    4:on    5:on    6:off
iscsid             0:off    1:off    2:off    3:on    4:on    5:on    6:off
isdn               0:off    1:off    2:on    3:on    4:on    5:on    6:off
jetty              0:off    1:off    2:off    3:off    4:off    5:off    6:off
ksm                0:off    1:off    2:off    3:on    4:on    5:on    6:off
ksmtuned           0:off    1:off    2:off    3:on    4:on    5:on    6:off
libvirt-guests     0:off    1:off    2:on    3:on    4:on    5:on    6:off
libvirtd           0:off    1:off    2:off    3:on    4:on    5:on    6:off
lvm2-monitor       0:off    1:on    2:on    3:on    4:on    5:on    6:off
mdmonitor          0:off    1:off    2:on    3:on    4:on    5:on    6:off
multipathd         0:off    1:off    2:off    3:off    4:off    5:off    6:off
mysqld             0:off    1:off    2:off    3:off    4:off    5:off    6:off
named              0:off    1:off    2:off    3:off    4:off    5:off    6:off
netconsole         0:off    1:off    2:off    3:off    4:off    5:off    6:off
netfs              0:off    1:off    2:off    3:on    4:on    5:on    6:off
network            0:off    1:off    2:off    3:off    4:off    5:off    6:off
nfs                0:off    1:off    2:off    3:off    4:off    5:off    6:off
nfslock            0:off    1:off    2:off    3:on    4:on    5:on    6:off
nmb                0:off    1:off    2:off    3:off    4:off    5:off    6:off
openct             0:off    1:off    2:on    3:on    4:on    5:on    6:off
openvpn            0:off    1:off    2:off    3:off    4:off    5:off    6:off
pcscd              0:off    1:off    2:on    3:on    4:on    5:on    6:off
portreserve        0:off    1:off    2:on    3:on    4:on    5:on    6:off
postgresql         0:off    1:off    2:off    3:off    4:off    5:off    6:off
psacct             0:off    1:off    2:off    3:off    4:off    5:off    6:off
rpcbind            0:off    1:off    2:on    3:on    4:on    5:on    6:off
rpcgssd            0:off    1:off    2:off    3:on    4:on    5:on    6:off
rpcidmapd          0:off    1:off    2:off    3:on    4:on    5:on    6:off
rpcsvcgssd         0:off    1:off    2:off    3:off    4:off    5:off    6:off
sandbox            0:off    1:off    2:off    3:off    4:off    5:on    6:off
saslauthd          0:off    1:off    2:off    3:off    4:off    5:off    6:off
sendmail           0:off    1:off    2:on    3:on    4:on    5:on    6:off
smb                0:off    1:off    2:off    3:off    4:off    5:off    6:off
smolt              0:off    1:off    2:on    3:on    4:on    5:on    6:off
snmpd              0:off    1:off    2:off    3:off    4:off    5:off    6:off
snmptrapd          0:off    1:off    2:off    3:off    4:off    5:off    6:off
spamassassin       0:off    1:off    2:off    3:off    4:off    5:off    6:off
speech-dispatcherd    0:off    1:off    2:off    3:off    4:off    5:off    6:off
squid              0:off    1:off    2:off    3:off    4:off    5:off    6:off
sshd               0:off    1:off    2:on    3:on    4:on    5:on    6:off
svnserve           0:off    1:off    2:off    3:off    4:off    5:off    6:off
vsftpd             0:off    1:off    2:off    3:off    4:off    5:off    6:off
wpa_supplicant     0:off    1:off    2:off    3:off    4:off    5:off    6:off
ypbind             0:off    1:off    2:off    3:off    4:off    5:off    6:off
zvbid              0:off    1:off    2:off    3:off    4:off    5:off    6:off
```

---

### Post by el_koraco on 2011-07-09
welcome to the matrix :D

---

