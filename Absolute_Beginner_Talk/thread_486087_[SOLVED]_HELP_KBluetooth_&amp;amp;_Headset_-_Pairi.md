---
title: "[SOLVED] HELP: KBluetooth &amp;amp; Headset - Pairing not allowed..."
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by wieman01 on 2007-06-27
Hello Folks, 

I am posting this in the "Absolute Beginner Talk" section because I feel like one... So have patience with me. I have been struggling to get my Bluetooth headset & device working for days, so I really need help.

**_Specs:_**
>> Kubuntu 7.04 (Feisty)
>> btsco v4.2
>> Billionton dongle
>> Plantronics 590 headset

It used to work in Dapper, but Feisty simply won't let me connect doing this:
> btsco -v 00:03:89:5F:C3:C4
Yields an error message:
> Password:
btsco v0.42
Device is 1:0
Voice setting: 0x0060
Can't connect RFCOMM channel: Permission denied
KBluetooth is no better (see screenshot). It says that "pairing is not allowed". Strangely this morning I was able to connect via "btsco" ones, but since then the system won't let me connect again. Any idea what is going on? I am at my wits' end. 

Last but not least... syslog:
> Jun 27 21:53:28 Winnie hcid[6491]: link_key_request (sba=00:10:60:30:17:95, dba=00:03:89:5F:C3:C4)
Jun 27 21:53:28 Winnie hcid[6491]: pin_code_request (sba=00:10:60:30:17:95, dba=00:03:89:5F:C3:C4)
Jun 27 21:53:30 Winnie hcid[6491]: link_key_request (sba=00:10:60:30:17:95, dba=00:03:89:5F:C3:C4)
Jun 27 21:53:30 Winnie hcid[6491]: pin_code_request (sba=00:10:60:30:17:95, dba=00:03:89:5F:C3:C4)

---

### Post by wieman01 on 2007-06-28
Need to bump...

What program should I run to activate the PIN applet?

---

### Post by wieman01 on 2007-06-28
Just in case anybody is interested I found [this]("https://bugs.launchpad.net/ubuntu/+source/kdebluetooth/+bug/97297") confirming that is a bug in Kubuntu Feisty. 

So I have to follow these steps in order to establish a connection via Bluetooth:

1. Delete temporary configuration file:
> sudo rm -r /var/lib/bluetooth/[COLOR="Red"]<mac address of bluetooth device>[/COLOR]
2. Invoke passkey:
> passkey-agent --default /usr/bin/bluez-pin
3. Connect through 'btsco':
> btsco -v [COLOR="Red"]<mac address of bluetooth device>[/COLOR]
This is a pretty annoying procedure as I need to run the first command as root. So everyime I reconnect my headset, I delete that file and the system would ask me for the PIN. Anyway, glad I got it working. Hope they are going to fix that bug anytime soon. Over & out!

---

### Post by Martin on 2007-07-01
I've been having problems for ages with bt headsets. Kind of got things working and was quietly confident that within a few weeks my problems would be over. Then I found this: [http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/](http://www.stgraber.org/2007/05/18/bluetooth-headset-manager/) and within about a minute I was talking away on Skype using bt. Amazing work by Stephane Graber. Probably won't work for everybody but give it a go.

---

