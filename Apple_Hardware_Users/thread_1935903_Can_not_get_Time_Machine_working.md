---
title: "Can not get Time Machine working"
date: 2012-03-05
forum: Apple Hardware Users
---

### Post by pinjan on 2012-03-05
Hi !

Have installed Ubuntu Server 11.10 64-bit to serve as NAS for Windows (Win 7), Linux and Mac's (OS X Lion). Everything else has been quite easy to set-up:
- SSH
- VNC
- Webmin 
etc. , but I can not get Time Machine folders visible from Ubuntu. Have tried many different solutions found from these forums & via Google e.g. : [http://ubuntuforums.org/showthread.php?t=1895084]("http://ubuntuforums.org/showthread.php?t=1895084")

[]("http://thecybergal.blogspot.com/2011/12/share-ubuntu-network-to-mac-lion-using.html")

So basically what  I have done:

1.```
sudo apt-get update
```
2. ```
sudo apt-get install netatalk
```
3.Configured : ```
sudo nano /etc/netatalk/afpd.conf 
```
adding end of line: ```
- -tcp -noddp -uamlist uams_dhx.so,uams_dhx2_passwd.so -nosavepassword 
```
 4.```
sudo nano /etc/netatalk/AppleVolumes.default
```
adding:
```
/mnt/nas/TimeMachine "TimeMachine" allow:geroge,ringo,paul,yoko cnidscheme:dbd options:tm
/mnt/nas/Data "Data" allow:geroge,ringo,paul,yoko cnidscheme:dbd
/mnt/nas/Media "Media" allow:geroge,ringo,paul,yoko cnidscheme:dbd
/mnt/nas/Users/george "george" allow:george cnidscheme:dbd
/mnt/nas/Users/ringo "ringo" allow:ringo cnidscheme:dbd
/mnt/nas/Users/paul "paul" allow:paul cnidscheme:dbd
/mnt/nas/Users/yoko "yoko" allow:yoko cnidscheme:dbd
```

5. Installing Avahi: ```
sudo apt-get install avahi-daemon
```
6. Configuring Avahi: ```
sudo nano /etc/nsswitch.conf
```
Adding : mdns
6.1 New file: ```
sudo nano /etc/avahi/services/afpd.service
```
File :
```
<?xml version="1.0" standalone='no'?><!--*-nxml-*-->
<!DOCTYPE service-group SYSTEM "avahi-service.dtd">
<service-group>
<name replace-wildcards="yes">%h</name>
<service>
<type>_afpovertcp._tcp</type>
<port>548</port>
</service>
<service>
<type>_device-info._tcp</type>
<port>0</port>
<txt-record>model=Xserve</txt-record>
</service>
</service-group>
```

7. Restarted Avahi: ```
sudo service avahi-daemon restart
``` and Netatalk ```
/etc/init.d/netatalk restart
```

8. Saw Ubuntu folder in Finder and tried to connect to it : ```
afp://<server ip>
```  but get error message saying: There was a problem connecting to server <server ip> 

So basicly I have installed and configured Netatalk & Avahi according to these instruction but can not connect to server even manually (afp://<server ip>)

My netatalk version is:
```
an@ubuntu:/tmp$ dpkg -s netatalk
Package: netatalk
Status: install ok installed
Priority: extra
Section: net
Installed-Size: 2884
Maintainer: Jonas Smedegaard <dr@jones.dk>
Architecture: amd64
Version: 2.2.1.1-0utm5+oneiric
Depends: libc6 (>= 2.11), libdb4.8, libgcrypt11 (>= 1.5.0-0), libgssapi-krb5-2 (>= 1.8+dfsg), libpam0g (>= 0.99.7.1), libwrap0 (>= 7.6-4~), perl, netbase, libpam-modules
Recommends: lsof, rc, db4.8-util, procps, cracklib-runtime, libpam-cracklib
Suggests: texlive-base-bin, groff, quota, db4.2-util, db4.7-util
Conffiles:
 /etc/pam.d/netatalk 01dc501e2d43ffc9f76b338e24a55e80
 /etc/netatalk/AppleVolumes.system 6e955fbed0833d5027c9dad13f381a6e
 /etc/netatalk/AppleVolumes.default addb4bbe61e731ddac52269927813735
 /etc/netatalk/afpd.conf 3e4acf07d8c5efe9ecab106a3f801386
 /etc/init.d/netatalk 991215e2fb6bcace7d4871cf880f9a59
 /etc/logcheck/violations.ignore.d/netatalk c7889e80639044d35c0bd614410f1891
 /etc/logcheck/ignore.d.server/netatalk cbc2dade09bce7bfa4fcb4cc0c4f9ba6
 /etc/default/netatalk cebe96b362b30d3ceb5a2b2f2a3cd4f6
Description: AppleTalk user binaries
 Netatalk is an implementation of the AppleTalk Protocol Suite for
 BSD-derived systems.  The current release contains support for
 EtherTalk Phase I and II, DDP, RTMP, NBP, ZIP, AEP, ATP, PAP, ASP, and
 AFP.
 .
 This package contains all daemon and utility programs as well as Netatalk's
 static libraries.
Homepage: http://netatalk.sourceforge.net/
```

I am quite puzzled and do not know what to try/change next, any ideas ?

---

### Post by MisterGaribaldi on 2012-03-05
Do you mean that the Time Machine client on your Mac cannot access or see previously-written data files and directories, or that other non-Mac OS X systems are unable to access the data?

Not sure about the former, but with the latter quite possibly you might need to ensure you have all the necessary filesys support on the relevant systems.

Time Machine partitions, IIRC, are Mac OS Extended Journaled, so you need to make sure you have full support for that before this is likely to work.

Also, I thought Apple was very restrictive in what it would let a user write to.

---

### Post by pinjan on 2012-03-05
> **MisterGaribaldi said:**
> Do you mean that the Time Machine client on your Mac cannot access or see previously-written data files and directories, or that other non-Mac OS X systems are unable to access the data?

I am setting up new fileserver with Ubuntu, so there is no previously written data. What I am trying to achieve is to use my new Ubuntu server to store Time Machine back-ups. I am able to connect server successfully with SMB, but that is not enough for Time Machine.

> **MisterGaribaldi said:**
> 
Not sure about the former, but with the latter quite possibly you might need to ensure you have all the necessary filesys support on the relevant systems.

Time Machine partitions, IIRC, are Mac OS Extended Journaled, so you need to make sure you have full support for that before this is likely to work.

Based on many how-to's I have been reading I thought that file system does not matter ? e.g. [http://greghesp.com/2011/09/how-to-setup-an-osx-lion-time-machine-share-on-ubuntu/]("http://greghesp.com/2011/09/how-to-setup-an-osx-lion-time-machine-share-on-ubuntu/") 
and here: [http://www.trollop.org/2011/07/23/os-x-10-7-lion-time-machine-netatalk-2-2/]("http://www.trollop.org/2011/07/23/os-x-10-7-lion-time-machine-netatalk-2-2/")

It seems that it is rather issue of Netatalk and AFP3.3 compatibility (lack of a “replay cache”, which was introduced in AFP 3.3 )

Many seem to have succeeded to fix however this, unfortunately not me even I have spent many hours trying to follow different instructions :cry:

---

### Post by MisterGaribaldi on 2012-03-05
Remember that you'll also be playing a sort of cat-and-mouse game here, since Apple fundamentally does not want you using anything other than a local HDD or an Apple "Time Capsule" network drive. If you get this to work, then good luck, but there's no way to know if Apple won't at some point brick your solution and, therefore, your data backups.

---

### Post by gennatolls on 2012-03-06
[http://ubuntuforums.org/showthread.php?p=11101453](http://ubuntuforums.org/showthread.php?p=11101453)

This worked for me under Ubuntu 11.10 as my server and Mac OS X 10.7. It works great, I decided not to share my home folder in ubuntu on my network. This method doesn't require you to enter the command in terminal (on OS X) to allow TM to backup to unsupported disks. Good luck

---

### Post by pinjan on 2012-03-07
Thanks !

I tried these instructions and now Time Machine sees at least my Ubuntu share (finder as well). Unfortunately it cannot connect still, after inputting my username and pwd I get error message: There was a problem connecting to the server &#8220;ubuntu.local&#8221;.

What to try next ? I guess this has to do something with access rights ?


EDIT: there is some error messages related to this problem in my iMac's log:
7.3.2012 18.58.46,000 kernel: ASP_TCP CheckReqQueueSize: increasing req queue from 32 to 128 entries. so 0xffffff800bfa9108 

7.3.2012 18.58.56,000 kernel: ASP_TCP CancelOneRequest: cancelling slot 2 error 89 reqID 4 flags 0x9 afpCmd 0x13 so 0xffffff800bfa9108

---

### Post by pinjan on 2012-03-07
I gave up. It seems that Apple logo is requirement on backup device for Time machine to work. Fortunately there are other vendors who provide backup solutions free. Now backup is running and will be ready next morning :D

---

### Post by pinjan on 2012-03-08
Just for info what is error message on Ubuntu server side:

```

Mar  8 11:27:14 ubuntu afpd[6951]: ===============================================================
Mar  8 11:27:14 ubuntu afpd[6951]: INTERNAL ERROR: Signal 11 in pid 6951 (2.2-beta4)
Mar  8 11:27:14 ubuntu afpd[6951]: ===============================================================
Mar  8 11:27:14 ubuntu afpd[6951]: BACKTRACE: 3 stack frames:
Mar  8 11:27:14 ubuntu afpd[6951]:  #0 /usr/sbin/afpd(netatalk_panic+0x1c) [0x7fface76449c]
Mar  8 11:27:14 ubuntu afpd[6951]:  #1 /usr/sbin/afpd(+0x4d59c) [0x7fface76459c]
Mar  8 11:27:14 ubuntu afpd[6951]:  #2 /lib/x86_64-linux-gnu/libc.so.6(+0x36420) [0x7ffacd740420]

```

Seems to be something wrong there, just do not have any idea myself how to troubleshoot this.

---

### Post by pinjan on 2012-03-08
Ok, just couldn't leave this issue so googled a bit about this panic and found this:

[http://sourceforge.net/tracker/index.php?func=detail&aid=3418627&group_id=8642&atid=108642]("http://sourceforge.net/tracker/index.php?func=detail&aid=3418627&group_id=8642&atid=108642")

Especially this is interesting:
```

Workaround can be found at
https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732.

In short, edit the '-uamlist' in /etc/netatalk/afpd.conf and replace
'uams_dhx2.so' with 'uams_dhx2_passwd.so' so that it looks like for
instance '-uamlist uams_dhx.so,uams_dhx2_passwd.so' and restart netatalk.

```

Changed that in my afpd.conf and now it works !  

Concidering I am newbie for Linux (have just few days experience) I am gonna tap my self now on my shoulder and say : Good Job ! I think I deserve one beer tonight for solving this issue myself:guitar:

---

### Post by pinjan on 2012-03-09
Ok, so TimeMachine is doing backup's nicely, but how about when you try to "Enter Time Machine" ?

Well, that did not work. However after spending few hours I was able to solve that as well ):P

---

### Post by MisterGaribaldi on 2012-03-10
Interesting.

The only thing, pinjan, is that you're really playing with fire here. Apple actively polices the Internet looking for instances of people getting around what they've set up, and then they update things which brick these various work-arounds.

In my opinion, it is not safe to back up your data the way you're doing here because chances are Apple will brick what you've done. Sure, it works now and for the moment, but what about a week from now? A month from now? A year from now? You have to look down the road a bit further than what, with all due respect, it seems like you are.

Apple DOES NOT WANT people using non-Apple products with their solutions, period. I back my Mac up with Time Machine to a local HDD. I refuse to spend the ridiculous money they want for a Time Machine capsule, and there's no way in the world I'm going to set something else up only to risk losing access to all my data simply at Apple's whim.

---

### Post by pinjan on 2012-03-10
> **MisterGaribaldi said:**
> Interesting.

The only thing, pinjan, is that you're really playing with fire here. Apple actively polices the Internet looking for instances of people getting around what they've set up, and then they update things which brick these various work-arounds.

In my opinion, it is not safe to back up your data the way you're doing here because chances are Apple will brick what you've done. Sure, it works now and for the moment, but what about a week from now? A month from now? A year from now? You have to look down the road a bit further than what, with all due respect, it seems like you are.

Apple DOES NOT WANT people using non-Apple products with their solutions, period. I back my Mac up with Time Machine to a local HDD. I refuse to spend the ridiculous money they want for a Time Machine capsule, and there's no way in the world I'm going to set something else up only to risk losing access to all my data simply at Apple's whim.

Yep, you are right about what Apple wants. There are however other vendors providing NAS solutions with Time Machine support/compatibility e.g QNAP : [http://www.qnap.com/features/Complete_backup_solution/Apple_time_machine_support.aspx?index=2&ap_id=71&lang=eng]("http://www.qnap.com/features/Complete_backup_solution/Apple_time_machine_support.aspx?index=2&ap_id=71&lang=eng")

If Apple will brick something, it will effect these other vendors too ?  I guess these NAS's are also having Linux based OS's inside. I think there will be many furious customers if Apple would do something like that.

I agree as well with you about the risks of doing this, therefore I will be having another timemachine backup on local HDD as well. You can never have too many backups !

---

### Post by MisterGaribaldi on 2012-03-10
I am unaware of (which is not to say none exist) any third party NAS product that Time Machine works with.

And, as far as "pissing people off" is concerned, Apple isn't obligated to make any of their offerings compatible with anything else, and I'm quite certain that's the response anyone complaining to them about this will get.

Apple will no doubt treat this kind of thing as a licensing opportunity. If you see any commercial products out there claiming Time Machine compatibility, that means they're paying Apple a fee.

---

### Post by Afinity on 2012-03-17
Thought I might chime in, since I've spent some time with netatalk.

I too keep a TM backup on a netatalk share.

Apple is not forcing you to use only their supported solutions, they just have the unsupported option turned off by default. You can enable unsupported time machine volumes on your mac by running this command...
> sudo defaults write com.apple.systempreferences TMShowUnsupportedNetworkVolumes 1

My afpd.conf file looks like this...
> # - -tcp -noddp -uamlist uams_randnum.so,uams_dhx2.so -nosavepassword
keeping "uams_dhx.so" in your file is pointless as apple has depreciated that protocol in lion.

My typical AppleVolumes.default share looks like...
> /backups "Backups" allow:user cnidscheme:dbd options:usedots,upriv,tm

Sorry I'm mostly just providing examples.

---

### Post by MisterGaribaldi on 2012-03-17
Oh, no no no, that's very cool. It is a pleasure to be dealing with others here who are at and beyond my own knowledge level in these matters of interoperability. With people like you and Khayyam, I'm certain anything is possible! :)

I honestly didn't know Apple provided *any* kind of access to using "3rd party" solutions with Time Machine. If, in fact, this all provides a way to use Time Machine safely and dependably over a network with Linux, I may well add another HDD to my in-home server and do backups that way.

---

### Post by Afinity on 2012-03-19
> **MisterGaribaldi said:**
> 
I honestly didn't know Apple provided *any* kind of access to using "3rd party" solutions with Time Machine. If, in fact, this all provides a way to use Time Machine safely and dependably over a network with Linux, I may well add another HDD to my in-home server and do backups that way.

I find it quite handy on my more limited budget. Although, I agree with your previous comment that it is important to be cautious when dealing with third party solutions. In that mindset, I also maintain occasional backups on two other mediums as well.

---

### Post by RandomByte on 2012-06-11
> **pinjan said:**
> Ok, so TimeMachine is doing backup's nicely, but how about when you try to "Enter Time Machine" ?

Well, that did not work. However after spending few hours I was able to solve that as well ):P

Hi!

I´m currently stuck with this problem (Backups run nicely but I can´t enter Time Machine - didn´t noticed this for about a month yet :-& ).

Do you remember any of the steps you did in order to get this running?

Thanks a lot!

---

### Post by mazac on 2012-07-20
> **RandomByte said:**
> Hi!

I´m currently stuck with this problem (Backups run nicely but I can´t enter Time Machine - didn´t noticed this for about a month yet :-& ).

Do you remember any of the steps you did in order to get this running?

Thanks a lot!

Hi, I have exactly the same problem, did you manage to get it working ? :confused:

---

### Post by pinjan on 2012-08-10
> **RandomByte said:**
> Hi!

I´m currently stuck with this problem (Backups run nicely but I can´t enter Time Machine - didn´t noticed this for about a month yet :-& ).

Do you remember any of the steps you did in order to get this running?

Thanks a lot!


Unfortunately I do not remember anymore :( I was tinkering with all config files. Just upgraded to Mountain Lion and it is still working perfectly :)

Too bad I didn't write solution down at that time, we could compare all config files to find differences and solve your problem ?

---

### Post by pinjan on 2012-08-10
I was checking my "installation manual" and I had written down some notes about this issue. 

To fix it you need to fix permissions of the sparsebundle. When those are corrected enter time machine works ok. To do that enter in Finder as root and change permissions of main directories where there is red sign to Read & Write, Read Only and Read only. 

Thats it !  Then entering time machine works. :guitar:

However I do not understand what has changed those permissions in first place. As I made backup from my wifes macbook first time, permissions were correct from the beginning :confused:

---

### Post by eyekode on 2012-11-20
Thanks for posting your response! Now for a stoopid question: How do I change the permissions of this dir?
On my linux box they say drwx--S---.
On my Mac they say drwx--x--x@
If I add read permission on my linux box it doesn't seem to affect what the mac sees. And I cannot change the permissions from the mac side (I did sudo su - , then chmod a+r on the dir and I got "Unable to change file mode on...:Operation not permitted"

Thanks in advance!
Salem

---

### Post by zasf on 2012-12-15
> **pinjan said:**
> Ok, just couldn't leave this issue so googled a bit about this panic and found this:

[http://sourceforge.net/tracker/index.php?func=detail&aid=3418627&group_id=8642&atid=108642]("http://sourceforge.net/tracker/index.php?func=detail&aid=3418627&group_id=8642&atid=108642")

Especially this is interesting:
```

Workaround can be found at
https://bugs.launchpad.net/ubuntu/+source/netatalk/+bug/810732.

In short, edit the '-uamlist' in /etc/netatalk/afpd.conf and replace
'uams_dhx2.so' with 'uams_dhx2_passwd.so' so that it looks like for
instance '-uamlist uams_dhx.so,uams_dhx2_passwd.so' and restart netatalk.

```

Changed that in my afpd.conf and now it works !  

Concidering I am newbie for Linux (have just few days experience) I am gonna tap my self now on my shoulder and say : Good Job ! I think I deserve one beer tonight for solving this issue myself:guitar:

THANKS!! I added '-uamlist uams_dhx.so,uams_dhx2_passwd.so' to /etc/netatalk/afpd.conf and now I'm able to restore my timemachine backup from osx install cd. Before afp would not mount the share (saying error 89).

Thanks a lot

---

