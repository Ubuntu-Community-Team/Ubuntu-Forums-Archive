---
title: "LTSP setup - some questions"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by plockery on 2007-02-26
I have a couple of pc's at home running windows XP or win2000 and am trying to setup a ubuntu pc with ltsp and login from my windows XP pc.
Ultimately i would like to convert my home network to a ltsp network. [I know about edubuntu but that seems to come with a lot of stuff i don't need because it is looking at the scholl environment.]
I setup a clean ubuntu edgy on the pc with a static IP address of 192.168.1.200.
My adsl modem/dhcp server/gateway is 192.168.1.254.
I went to the LTSP web site under documentation and clicked on the ubuntu link which brought up this page [https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall]("https://help.ubuntu.com/community/UbuntuLTSP/LTSPQuickInstall")
I followed the instructions there, but was not sure where to go from there or if I needed to do other configuration stuff.
I have changed the dhcpd.conf to reflect the static address and the hosts file as well and restarted the dhcp server.
I also updated the sshkeys as per the instructions.

There also seem to be different howtos for setting up the new muecow system eg like this recent link in this forum [http://www.ubuntuforums.org/showthread.php?t=368869&highlight=lts]("http://www.ubuntuforums.org/showthread.php?t=368869&highlight=lts")
This second howto talks about configuring the lts.conf file (in /opt/ltsp/i386/etc). I discovered I did not even have such a file. Am I supposed to?
How does one know what are the latest instructions? It is very confusing for the newbie.

I thought that the muecow system was supposed to save a lot of space by using ubuntu's own packages. But when I built the client (sudo ltsp-biuild-client) ubuntu downloaded 225 packages from the ubuntu archive! The /opt/ltsp directory has close to half a gig of files (about 452meg). Is that normal? Am i misunderstanding something?

Regarding my windows PC, can I simply login to the ubuntu ltsp server simply by using windows remote desktop or do I need to do something else to make this work eg with samba for example?
At the moment remote desktop just says that it "cannot connect to the remote computer".

Any help in clearing up my confusion would be much appreciated.

---

### Post by solar george on 2007-02-26
The ubuntu alternate cd can build a preconfigures LTSP system. These systems are designed to be booted up over the network, so if your XP computer has a bootable network card then you could use that.

edit: Apparently it is only xubuntu that has an ltsp option but you could add gnome to this

---

### Post by crmanski on 2007-02-26
> **plockery said:**
> 
Regarding my windows PC, can I simply login to the ubuntu ltsp server simply by using windows remote desktop or do I need to do something else to make this work eg with samba for example?
At the moment remote desktop just says that it "cannot connect to the remote computer".

Any help in clearing up my confusion would be much appreciated.

You cannot use rdp to login to the terminal server. The client machines have to netboot using PXE or something similar. If you have a built-in nic on motherboard of the client machine you can change the boot device order in the BIOS.
If you want a remote desktop login you can install FreeNX ( [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX) ) on the terminal server and login with the nxclient.

---

### Post by crmanski on 2007-02-26
> **plockery said:**
> 
There also seem to be different howtos for setting up the new muecow system eg like this recent link in this forum [http://www.ubuntuforums.org/showthread.php?t=368869&highlight=lts]("http://www.ubuntuforums.org/showthread.php?t=368869&highlight=lts")
This second howto talks about configuring the lts.conf file (in /opt/ltsp/i386/etc). I discovered I did not even have such a file. Am I supposed to?
How does one know what are the latest instructions? It is very confusing for the newbie.


I forgot to reply to this part in the first post...
Yes, you should have one. This wiki page covers the basics...
[http://www.edubuntu.org/ThinClientConfig](http://www.edubuntu.org/ThinClientConfig)

Mine looks like this...
```
[Default]
SERVER=192.168.0.254
XSERVER=auto
X_COLOR_DEPTH=16
SOUND=True
NBD_SWAP=True
SYSLOG_HOST=server

```

---

### Post by plockery on 2007-02-26
Thanks for the information.
I need some clarification in order to try and get my head around some things.
Sorry if the questions seem obvious.
I have worked with LTSP some time back and I used it like I use windows terminal server at work - boot up basic terminal pc (on windows or linux) and login to server via rdp.
This is what I would still like to do again at home as i have never worked with PXE or network booting of terminals.
But I gather that was the old system (LTSP tarball install).

1. If I install FreeNX and the NX client do I just install those after the normal LTSP Muecow install instructions [[https://help.ubuntu.com/community/Ub...SPQuickInstall]](https://help.ubuntu.com/community/Ub...SPQuickInstall]) or do I have to go back to a tarball install?

2. The FreeNX link provided by crmanski says that these packages no longer come with ubuntu edgy but the dapper packages work. Does that mean that there is no future with ubuntu for an rdp login from a remote machine - the only possibility will be PXE or network?

3. I would still like to know why unbuntu downloads 225 packages and uses 452 meg of disk space for this "space saving" install. Is this because it is setting up an environment for a PXE or network boot? I don't remember the LTSP tarball taking up that sort of space but i maybe entirely mistaken here.

4. Can anyone tell me why with the default install I did not have an lts.conf file? do I have to make one up? If so how do I activate the settings?

Thanks again for the help.

---

