---
title: "synaptic not seeing repositories"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-03-21
I posted this problem in another thread and was not able to acquire some resolution.

I'm trying to deb repositories.  After having added deb addresses to the sources.list file, synaptic fails to load and tells me that the requests time out.

I can, however, use Firefox to visit the addresses.

**My question**:  Why are the requests timing out and connections failing through synaptic and not through Firefox  (Note:  IPV6 in FF had to be altered in order to access the web).

Your help is appreciated!

gs

---

### Post by WoodyMahan on 2006-03-21
OK Guy.

I got this from Pragmatist whe I was having a problem with repositories.
Basically it instructs you to backup the sources.list, then create a blank file named sources.list, open it and paste in this limited number of repositories.  Let's get your repositories back in order, then try adding freenx back in.  OK?

Here we go:

Ok, for testing purposes, backup your /etc/apt/sources.list (I would call it BACKUP_sources.list some people use sources.list.bak Use whatever is memorable for you). EDIT:  code for this in the terminal is: 
sudo cp /etc/apt/sources.list /etc/apt/(your new filename)

Now open the sources.list:
sudo gedit /etc/apt/sources.list
Highlight everything and delete it.  Click Save.  (Remember you have a backup if necessary)

Now copy and paste the following into the sources.list

Quote:
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 

End of Quote.
Open Synaptic and Reload.  You should not get errors.  Then try adding the freenx repository.

---

### Post by guysmiley on 2006-03-21
Woody,

Thanks soooooo much for your continued support.  I'm going to try this right now.

gs

---

### Post by guysmiley on 2006-03-21
Ok,

security.ubuntu and archive.ubuntu both failed (i.e. archive.ubuntu.com:80 (1.0.0.0), connection timed out).

So, still no go.

gs

---

### Post by WoodyMahan on 2006-03-21
What the crap????

Ok.  Try it through the terminal.

sudo apt-get update

Does that kick back errors too?

---

### Post by guysmiley on 2006-03-21
k,

It's trying to connect but isn't.  It's holding at 0% and "Connecting to security.ubuntu.com..."

**Same error.  Connection Timed out.**

[COLOR="Red"]**All connections timed out.**[/COLOR]

---

### Post by guysmiley on 2006-03-21
I'm VERY suspicious that this is similar to the IPv6 problem I had with FF when I first loaded it up.  I couldn't browse the web at all.  I had t:

about:config (in FF) then filter by IPV6 and change it's setting to "true" in order to browse the web.

Does this sound like it might be the source of the problem?  If so, do you know how I can fix it for synaptic and any other browser/server client I might install?

gs

---

### Post by WoodyMahan on 2006-03-21
We need to go up the chain here.  I'm at the limit of my knowledge.  Any gurus out there who might have any suggestions?  Keep checking that other thread too.  Someone might be posting to it.

Sorry dude.

---

### Post by guysmiley on 2006-03-21
Thanks, Woody.  Know any experts I can contact?

---

### Post by WoodyMahan on 2006-03-21
Brunellus and Arnieboy are both pretty sharp.

---

### Post by WoodyMahan on 2006-03-21
Bump

---

### Post by guysmiley on 2006-03-21
K,

My problems continue.  I've tried disabling ipv6 system wide by creating a bad_list as suggested by mhael here: [http://ubuntuforums.org/showthread.php?t=87798](http://ubuntuforums.org/showthread.php?t=87798)

And, still cannot synaptic.  What's more, I can ping some places and not others (i.e. ping [www.ubuntu.com](www.ubuntu.com) works but not [www.ubuntuforums.com)](www.ubuntuforums.com)).

I've searched all over and can't find anything...  Please help!

gs

---

### Post by WoodyMahan on 2006-03-21
Hey guy

I just found this.

[http://www.ubuntuforums.org/showthread.php?t=97277](http://www.ubuntuforums.org/showthread.php?t=97277)

It explains how to install FreeNX and has a different repositry address.  Maybe this will get things started for ya.

---

### Post by guysmiley on 2006-03-21
Thanks, Woody.

I've seen this post and tried it out.  My problem remains:

I can't apt-get via terminal (connection times out) nor through synaptic though I can browse with ease in FF.  I suspect the problems are the same.

Does ANYONE have any idea why this is the case?

gs

---

### Post by guysmiley on 2006-03-21
So,

Still having problems...  This is the output of ifconfig:

eth0      Link encap:Ethernet  HWaddr 00:80:C6:E9:81:8B
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7727 errors:0 dropped:0 overruns:0 frame:0
          TX packets:328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:2610450 (2.4 MiB)  TX bytes:40515 (39.5 KiB)
          Interrupt:10 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:57908 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57908 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5246390 (5.0 MiB)  TX bytes:5246390 (5.0 MiB)

Should my inet address be 127....  Is this why I can't apt-get or synaptic?  Anyone?  Buler?

gs

---

### Post by guysmiley on 2006-03-22
Bump

---

### Post by WoodyMahan on 2006-03-22
I have requested assistance through PM from a couple of other Sr. Members who have assisted me in the past.  Hopefully we will get something soon.

---

### Post by nocturn on 2006-03-22
Just a thought, but do you have a proxy set in FireFox?

---

### Post by guysmiley on 2006-03-22
No, FF has no proxy set but I did need to disable IPV6.

---

### Post by nocturn on 2006-03-22
You could try to disable ipv6 completely.  this thread explains how:
[http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6](http://ubuntuforums.org/showthread.php?t=87798&highlight=ipv6)

You will have to reboot.

---

### Post by guysmiley on 2006-03-22
Thanks for the idea, Nocturn...

I tried this and even ran the script "ip a | grep inet6" to ensure it was fully disabled.  Still no go.... grr.

---

### Post by LKRaider on 2006-03-22
Try using another program that requires network connection. For example, try elinks (*sudo apt-get install elinks*).
Then run it on a terminal: *elinks [www.google.com](www.google.com)*

Does it works out of the box?

Try searching for errors on the logs, after you run an *apt-get update*:
*cat /var/log/messages /var/log/dmesg | egrep 'IP|ip|net|eth|link|error'*

Look for anything relating to a network error or something strange.

---

### Post by guysmiley on 2006-03-22
Thanks LKRaider,

I'll give this a go and post my results here in a bit.  I really appreciate the guidance.

gs

---

### Post by guysmiley on 2006-03-22
So, still no go.  [COLOR="Red"]In the terminal I tried[/COLOR]:
sudo apt-get install elinks
Password:
Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/ma in Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_m ain_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/re stricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-upd ates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packa ges (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_ Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe P ackages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_bina ry-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse  Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted  Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_ binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-securi ty_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy- security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/ universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-se curity_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://seveas.ubuntulinux.nl](http://seveas.ubuntulinux.nl) breezy-seveas/ all Packages (/var/lib/apt/lists/seveas.ubuntulinux.nl_dists_breezy-seveas_all_b inary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package elinks

[COLOR="Red"]Then I tried:[/COLOR]

sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory

Any ideas?

---

### Post by guysmiley on 2006-03-22
I also checked the error logs after running the update and got this:
Mar 21 08:42:21 localhost kernel: [4294672.547000] audit: initializing netlink socket (disabled)
Mar 21 08:42:21 localhost kernel: [4294673.015000] io scheduler anticipatory registered
Mar 21 08:42:21 localhost kernel: [4294673.027000] IP: routing cache hash table of 1024 buckets, 8Kbytes
Mar 21 08:42:21 localhost kernel: [4294674.616000] PIIX4: chipset revision 1
Mar 21 08:42:21 localhost kernel: [4294679.725000] Linux Tulip driver version 1.1.13 (May 11, 2002)
Mar 21 08:42:21 localhost kernel: [4294679.745000] tulip0: no phy info, aborting mtable build
Mar 21 08:42:21 localhost kernel: [4294679.745000] eth0: Macronix 98715 PMAC rev 37 at 0001e400, 00:80:C6:E9:81:8B, IRQ 10.
Mar 21 08:42:21 localhost kernel: [4294719.828000] agpgart: Detected an Intel 440BX Chipset.
Mar 21 08:42:21 localhost kernel: [4294735.752000] IPv6 over IPv4 tunneling driver
Mar 21 08:42:32 localhost hp: unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 75
Mar 21 11:31:06 localhost kernel: [4294672.268000] audit: initializing netlink socket (disabled)
Mar 21 11:31:06 localhost kernel: [4294672.736000] io scheduler anticipatory registered
Mar 21 11:31:06 localhost kernel: [4294672.749000] IP: routing cache hash table of 1024 buckets, 8Kbytes
Mar 21 11:31:06 localhost kernel: [4294674.338000] PIIX4: chipset revision 1
Mar 21 11:31:06 localhost kernel: [4294679.461000] Linux Tulip driver version 1.1.13 (May 11, 2002)
Mar 21 11:31:06 localhost kernel: [4294679.482000] tulip0: no phy info, aborting mtable build
Mar 21 11:31:06 localhost kernel: [4294679.482000] eth0: Macronix 98715 PMAC rev 37 at 0001e400, 00:80:C6:E9:81:8B, IRQ 10.
Mar 21 11:31:06 localhost kernel: [4294720.022000] agpgart: Detected an Intel 440BX Chipset.
Mar 21 11:31:12 localhost hp: unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 75
Mar 21 11:34:33 localhost kernel: [4295007.623000] IPv6 over IPv4 tunneling driver
Mar 21 16:08:17 localhost kernel: [4294672.467000] audit: initializing netlink socket (disabled)
Mar 21 16:08:17 localhost kernel: [4294672.936000] io scheduler anticipatory registered
Mar 21 16:08:17 localhost kernel: [4294672.949000] IP: routing cache hash table of 1024 buckets, 8Kbytes
Mar 21 16:08:17 localhost kernel: [4294674.537000] PIIX4: chipset revision 1
Mar 21 16:08:17 localhost kernel: [4294679.661000] Linux Tulip driver version 1.1.13 (May 11, 2002)
Mar 21 16:08:17 localhost kernel: [4294679.682000] tulip0: no phy info, aborting mtable build
Mar 21 16:08:17 localhost kernel: [4294679.682000] eth0: Macronix 98715 PMAC rev 37 at 0001e400, 00:80:C6:E9:81:8B, IRQ 10.
Mar 21 16:08:17 localhost kernel: [4294720.700000] agpgart: Detected an Intel 440BX Chipset.
Mar 21 16:08:28 localhost hp: unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 75
Mar 22 16:46:50 localhost kernel: [4294672.165000] audit: initializing netlink socket (disabled)
Mar 22 16:46:50 localhost kernel: [4294672.634000] io scheduler anticipatory registered
Mar 22 16:46:50 localhost kernel: [4294672.647000] IP: routing cache hash table of 1024 buckets, 8Kbytes
Mar 22 16:46:50 localhost kernel: [4294674.235000] PIIX4: chipset revision 1
Mar 22 16:46:50 localhost kernel: [4294679.367000] Linux Tulip driver version 1.1.13 (May 11, 2002)
Mar 22 16:46:50 localhost kernel: [4294679.388000] tulip0: no phy info, aborting mtable build
Mar 22 16:46:50 localhost kernel: [4294679.388000] eth0: Macronix 98715 PMAC rev 37 at 0001e400, 00:80:C6:E9:81:8B, IRQ 10.
Mar 22 16:46:50 localhost kernel: [4294721.435000] agpgart: Detected an Intel 440BX Chipset.
Mar 22 16:46:59 localhost hp: unable to open /var/run/hplip/hpssd.port: No such file or directory: prnt/hpijs/hplip_api.c 84
Mar 22 16:46:59 localhost hp: unable to connect hpssd socket 50002: Connection refused: prnt/hpijs/hplip_api.c 710
[4294669.994000] Calibrating delay loop... 894.97 BogoMIPS (lpj=447488)
[4294672.165000] audit: initializing netlink socket (disabled)
[4294672.634000] io scheduler anticipatory registered
[4294672.647000] IP: routing cache hash table of 1024 buckets, 8Kbytes
[4294674.235000] PIIX4: chipset revision 1
[4294679.367000] Linux Tulip driver version 1.1.13 (May 11, 2002)
[4294679.388000] tulip0: no phy info, aborting mtable build
[4294679.388000] eth0: Macronix 98715 PMAC rev 37 at 0001e400, 00:80:C6:E9:81:8B, IRQ 10.
[4294721.435000] agpgart: Detected an Intel 440BX Chipset.

Looks to me like there may be a problem with:
[COLOR="Red"]/var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 75[/COLOR]
o[COLOR="Red"]r
audit: initializing netlink socket (disabled)[/COLOR]
or
[COLOR="Red"]tulip0: no phy info, aborting mtable build[/COLOR]

but I honestly have no idea if there is anything wrong here or not.  Do you?

---

### Post by guysmiley on 2006-03-22
Hello All,

apt-get still does not work nor does Synaptic.  I'm becoming very frustrated.

I've been digging for days now through the posts in this forum and just tried deleting everything in /var/lib/apt/lists (because someone in another thread suggested this as a solution) and *still *nothing (all connections timing out, "Could not connect" errors)!

If anyone has the patience to be able to help me apt-get, I'd be very appreciative!

---

### Post by Mustard on 2006-03-22
Are you connecting with your browser through a proxy?

---

### Post by LKRaider on 2006-03-22
Okay, my suggestion about elinks was stupid (how could you apt-get it, heh)

Get it from this link: [elinks-lite from Breezy repositories]("http://archive.ubuntu.com/ubuntu/pool/universe/e/elinks/elinks-lite_0.10.4-7ubuntu1_i386.deb")

install it by running "*sudo dpkg -i elinks*.deb*" on the folder you saved it. Then try running it by typing "*elinks [www.google.com](www.google.com)*". See if it connects.

From the logs, it seems IPv6 is still being enabled (_IPv6 over IPv4 tunneling driver_ shouws up there). Did you try all options to remove IPv6? (tho I am not sure why it would be causing troubles)

The hplip stuff is probably from a HP printer or scanner you have, so shouldn't be related to this.

The [Tulip thing](http://www.scyld.com/tulip.html) is your network card driver. I don't know what that message means tho, and don't know whether tulip drivers have trouble with IPv6. Their website links to some mailing lists that could be helpful. They also have a diagnostics program there.
They have a page about the [mtables stuff](http://www.scyld.com/tulip_media.html), but I couldn't figure it out.
It may be worth trying loading the module with extra debug info (*sudo modprobe tulip debug=2*) and try to figure out what's wrong (*dmesg | grep tulip*), or better yet, get another card to replace this one. ;)

You may want to look at your internet connection too. It could be a hub/router/firewall/etc that is causing the problems. If possible, try bypassing them and see how it works out. If you are in a controlled enviroment, try getting in touch with the system administrator and query about your conectivity problems.

Anyways, do a "*dmesg | grep tulip*" and post it here.

(bookmark: [this message](http://beowulf.es.embnet.org/listarchives/linux-tulip-bug/2000/02/0018.html) has a list of commands where to look for extra info)

---

### Post by nocturn on 2006-03-23
From the command line, can you ping a site?

let's say 

```

ping www.google.com

```

If so, can you download some file with wget (should be installed)

```

wget http://archive.ubuntu.com/ubuntu/pool/main/s/schoolbell/schoolbell_1.2.2-1_all.deb

```

---

### Post by nocturn on 2006-03-23
Can you also list the files/directories under /var/lib/apt/lists/

Maybe there's something wrong with the directory...

---

### Post by nocturn on 2006-03-23
Can you get on irc?

If so, visit ubuntuforums.org.  I can join you there and help you one-on-one.
I have to be out before 16:00 UTC though.

---

### Post by guysmiley on 2006-03-23
Thanks again for the help...

wget returned this:
wget [http://archive.ubuntu.com/ubuntu/pool/main/s/schoolbell/schoolbell_1.2.2-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/schoolbell/schoolbell_1.2.2-1_all.deb)
--06:42:13--  [http://archive.ubuntu.com/ubuntu/pool/main/s/schoolbell/schoolbell_1.2.2-1_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/s/schoolbell/schoolbell_1.2.2-1_all.deb)
           => `schoolbell_1.2.2-1_all.deb'
Resolving archive.ubuntu.com... 82.211.81.182
Connecting to archive.ubuntu.com|82.211.81.182|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30,820 (30K) [application/x-debian-package]

100%[====================================>] 30,820        96.95K/s

06:42:13 (96.80 KB/s) - `schoolbell_1.2.2-1_all.deb' saved [30820/30820]

and the only files in /var/lib/apt/lists/ are lock and a directory called partial.

Another weird thing is that I just got prompted with 73M of updates that are available.  It identified packages and everything.  I'm going to try to download/install them now...

gs

---

### Post by guysmiley on 2006-03-23
K,

I downloaded and installed elinks via sudo.  Then, I did elinks [www.google.com](www.google.com).  A terminal window opened and asked for a url.  I entered [www.google.com](www.google.com) and it hung on "Making Connection".

I then typed  dmesg | grep tulip and got:
[4294677.116000] tulip0: no phy info, aborting mtable build

I hope this stuff means something to you guys.  I'm learning as fast as I can!

---

### Post by nocturn on 2006-03-23
[QUOTE=guysmiley]
and the only files in /var/lib/apt/lists/ are lock and a directory called partial.
gs[/QUOTE]

Is there anything in partial?  If so, clear it.

Could you try this:
1- Make a backup of /etc/apt/sources.list
2- Create an empty /etc/apt/sources.list
3- Apt-get update
4- Restore backup (or create a new sources file)
5- apt-get update

---

### Post by guysmiley on 2006-03-23
So,

I deleted everything in partial.  Made a new sources.list (blank).  Ran ap-get update and returned "Done".
Next, put back sources.list and returned:
sudo apt-get update
Password:
Reading package lists... Done
geoff@webserver:~$ sudo apt-get update
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release .gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Pa ckages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restric ted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Pa ckages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can not be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restric ted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can not be used to add new CD-ROMs
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://ca.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to ca.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

Any thoughts?

---

### Post by nocturn on 2006-03-23
Ok, I see...  your hosts are being resolved to 1.0.0.0!

Can you do sudo -s to get a root shell.

Then 

```
host security.ubuntu.com
```

And

```
ping security.ubuntu.com
```

---

### Post by guysmiley on 2006-03-23
Thanks, Nocturn.

I will do this  roughly 3 hours from now.  I have some other things I need to attend to though I'd really rather get this working.  Any idea why my hosts are resolving to 1.0.0.0?

---

### Post by nocturn on 2006-03-23
[QUOTE=guysmiley]Thanks, Nocturn.

I will do this  roughly 3 hours from now.  I have some other things I need to attend to though I'd really rather get this working.  Any idea why my hosts are resolving to 1.0.0.0?[/QUOTE]

No, it puzzles me because it seems to be working from your user account, but not from root.  Maybe automatix had something to do with this, maybe not.

But we have found the cause of your problems, we do not need to fix apt or your sources, but the  way your system resolves hosts.

I will not be here in 3 hours anymore, so I'll see how it went tomorrow.

---

### Post by guysmiley on 2006-03-23
Thanks, Nocturn.  I will look around for resolution on 1.0.0.0 issues.

---

### Post by LKRaider on 2006-03-23
Try posting the output of:
*sudo iptables -L*
*sudo ifconfig*

they show the network info

---

### Post by guysmiley on 2006-03-23
Hey Raider,
[COLOR="Red"]
sudo iptables -L returns:[/COLOR]
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

[COLOR="Red"]
and, sudo ifconfig returns:[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:80:C6:E9:81:8B
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:458663 (447.9 KiB)  TX bytes:26532 (25.9 KiB)
          Interrupt:10 Base address:0xe400

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1114 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:88706 (86.6 KiB)  TX bytes:88706 (86.6 KiB)

---

### Post by guysmiley on 2006-03-23
Is it possible that in the above the Bcast is incorrect?

Bcast:[COLOR="Red"]192.168.1.255[/COLOR]

This dosen't look right to me...

---

### Post by vaebn on 2006-03-23
I've had the very same problem on all three of the computers I've tried Ubuntu on.
Could it be something to do with a router you're using perhaps?

My DNS servers and Search Domains are set to my routers I.P address. The web is fine but whenever I want to apt-get something, I've got to ping it first.

Sorry I can't offer anything to help ](*,)

---

### Post by guysmiley on 2006-03-23
I've been reading through a lot of posts and this issue has come up repeatedly with regard to d-link routers.  What kind of router are you using (I'm d-link)....

Is there a router setting I should be looking at?

---

### Post by vaebn on 2006-03-23
Yeah, mines a D-link too. Must be some default setting that's making it go funny...

---

### Post by guysmiley on 2006-03-23
I'll let you know if I hear anything about our d-links  (mine's 504T modem/router)...

Hopefully Nocturn & Raider can help,

gs

---

### Post by vaebn on 2006-03-23
Ok, thanks.

I think mine's a G604_T

---

### Post by w3ath3rman on 2006-03-23
Very interesting problem here.  I was using apt-get and Synaptic yesterday and it worked fine.  I was hardwired at the time.  I am now wireless and an getting the "Couldn't stat source..." message.

Your ifconfig looks right.

I am going to connect to my ethernet and see if the problem goes away.

Please keep us posted on any resolution you may find.  I would like to be able to install software from my wireless.

---

### Post by w3ath3rman on 2006-03-23
BTW.  I am using a Netgear router.

---

### Post by w3ath3rman on 2006-03-23
No surprise.  The problem must not be in the interface.  I am on my wired connection and get the same error.

I too, can ping the archive.ubuntu.com name from a terminal session.

---

### Post by guysmiley on 2006-03-23
Alright,

I think I've confirmed that this is a router/modem problem and that IPv6 is the culprit.  I've found this thread: [www.ubuntuforums.org/archive/index.php/t-78271.html](www.ubuntuforums.org/archive/index.php/t-78271.html)
which seems to have helped lots of people.  I'll get back to you when I've first tried a firmware update on the router (easier said than done since I just found out the modem I purchased locally was imported from another country; hence, upgrading firmware becomes problomatic)...

gs

---

### Post by guysmiley on 2006-03-23
Thanks to all of you who helped me along the way!!  After a long, long search, here's the solution:

Go to COMPUTER--->SYSTEM CONFIGURATION--->NETWORKING (you will need to be superuser (root))

Then go to the DNS tab (probably 192.168.blah.blah as entry)

Find out your ISPs DNS nameservers, for example, Tiscali is 212.74.112.66 and 212.74.112.67.

Enter those bad boys in. Take 192.168.blah.blah OUT!



Then go to /etc/resolv.conf
Make sure that these two entries are there:

nameserver 212.74.112.66
nameserver 212.74.112.67

Your ISPs nameservers replacing mine ;-P
Nameserver 192.168.blah.blah should either be commented out (preceded with a #) or not be there at all.



Finally, go to /etc/dhcp3/dhclient-script and comment out this:

# Modified for Debian. Matt Zimmerman and Eloy Paris, December 2003

# The alias handling in here probably still sucks. -mdz

#make_resolv_conf() {
# if [ -n "$new_domain_name" -o -n "$new_domain_name_servers" ]; then
# local new_resolv_conf=/etc/resolv.conf.dhclient-new
# rm -f $new_resolv_conf
#
# if [ -n "$new_domain_name" ]; then
# echo search $new_domain_name >> $new_resolv_conf
# else # keep 'old' search/domain scope
# egrep -i '^ *[:space:]*(search|domain)' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
# 
# if [ -n "$new_domain_name_servers" ]; then
# for nameserver in $new_domain_name_servers; do
# echo nameserver $nameserver >>$new_resolv_conf
# done
# else # keep 'old' nameservers
# egrep -i '^ *[:space:]*nameserver' /etc/resolv.conf >> \
# $new_resolv_conf
# fi
#
# chown --reference=/etc/resolv.conf $new_resolv_conf
# chmod --reference=/etc/resolv.conf $new_resolv_conf
# mv $new_resolv_conf /etc/resolv.conf
# fi
#}

This should do it! (Thanks to Python for his solution!!)  This should really be stickied somewhere, I think.  D-Link North America does not yet support ipV6 on ANY of their modems!!!!  This info given as of today's date!

gs

---

### Post by guysmiley on 2006-03-23
It would appear I spoke too soon...

At least now I can download updates and synaptic works with the default sources.list.  HOWEVER, I added freenx (the whole reason for this process in the first place) and now, in order to download a package, I had to ping the seveas repository first.  Then, and only then, was I able to download.

Anyone know why this is?

---

### Post by mingchen on 2006-03-24
Tried many times to get my ubuntu behind proxy to get software packages from 'universe'.
Have configured http proxy correctly so I can do internet access without problem and security.ubuntu.com, achive.ubuntu.com.

Modified sources.list as suggested in prior reply:
root@ubuntu:/etc/apt# cat sources.list
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
root@ubuntu:/etc/apt# 

But, I still have connection failed. Could anyone help me to resolve this ?

Thanks,
Ming


root@ubuntu:/etc/apt# apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg    
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release                               
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources                
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources                
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages                   
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages                         
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages         
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages                     
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources                
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages                   
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources    
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Sources
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Sources
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages   
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Sources    
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Sources
  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/main/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/main/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/universe/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/multiverse/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/breezy/restricted/source/Sources.gz)  Connection failed
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@ubuntu:/etc/apt

---

### Post by saphil on 2006-03-26
If this is still a problem, you might try using better DNS servers at the router level::

[http://www.dslreports.com/faq/13016](http://www.dslreports.com/faq/13016) had this to say
------------
DNS server addresses should be automatically configured by DHCP to use the proper servers assigned to your area.

If you believe you are having problems related DNS server issues, try using one of these DNS servers:

**209.244.0.3** = resolver1.level3.net
**209.244.0.4** = resolver2.level3.net

The above servers are popular because they are probably the fastest and closest non-your-ISP DNS servers on the internet. These servers are multi-homed and the IPs listed above will take you straight to the server at the nearest Level3 peering point, which is probably also the nearest Adelphia peering point due to network arrangements between the two companies: »[www.level3.com/press/5357.html]("http://www.level3.com/press/5357.html")

**4.2.2.1** = vnsc-pri.sys.gtei.net
**4.2.2.2** = vnsc-bak.sys.gtei.net
------------------------------
I find my local ISP DNS Servers crap out on occasion. I put 4.2.2.4 and 4.2.2.1 on my router. We have as many as 9 PC on the network at a time, and it is annoying to have to update dns on them pc-by-pc.

If your router is searching for heavy-duty DNS Servers, then your PC can be getting DNS from the router (192.168.0.1) This troubleshoots the dns, and you can quit worrying abt it. 

Are you on a heavilly subscribed dsl or cable connection? You can get all sorts of 404 errors because your internet connection is down, or because there is no path from here to there - really, some internet locations are at the end of a long single path - It is not common but it happens. 

Have you tried to make the updates at different times of day? If the server can take only 20 connections and you are #21, you get a 404 error - server cannot be found.

If you can go to the repository by FireFox, you should be able to get there by synaptic.

---

### Post by guysmiley on 2006-03-26
Hey Saphil,

Thanks for the idea... I never knew there were DNSs like the ones you suggest above.

I did fix the problem (see post 52) but am still having a weird ping problem (see post 53)...  Any thoughts on this?

gs

---

### Post by kiff on 2006-03-27
[QUOTE=guysmiley]Hey Saphil,

Thanks for the idea... I never knew there were DNSs like the ones you suggest above.

I did fix the problem (see post 52) but am still having a weird ping problem (see post 53)...  Any thoughts on this?

gs[/QUOTE]

I'm having the same trouble, so I'd be interested to find out if anyone has any suggestions.

---

