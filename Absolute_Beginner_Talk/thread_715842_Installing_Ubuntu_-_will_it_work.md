---
title: "Installing Ubuntu - will it work?"
date: 2008-03-05
forum: Absolute Beginner Talk
---

### Post by steffenlaursen on 2008-03-05
Hello there,

I am about to install ubuntu, or at least i think i am.

I have a small problem, though, as i dont seem to have enough space to dual-boot (and the little i have is very fragmentet, which i instinctively believe to be bad anyway). Besides, if ubuntu works properly, i should not want to ever use Windows again (for obvious reasons ;) ), and it would just take up much needed laptop-space.

However, my computer did not ship with a windows reinstall CD, and i have heard that the ubuntu install may occassionally screw the install files on the computer. I have asked for a CD at the store, but they were unsure they could get one, and may even charge a bit for it (no way i'm gonna pay more money for MS products!).

So my question is: Does anyone know of any hardware compatibility problems there might be with an IBM R50e? Or any other known issues? Things i might as well be prepared for?

Everything might of course run smoothly, but I guess growing up with windows has made me somewhat OS-xenophobiac. Just tell me it will be alright  :grin:

- Steffen

---

### Post by dstew on 2008-03-05
The main risk is in the partitioning step. If you have to shrink a Windows partition to make room for Ubuntu, and some glitch occurs, you will need to re-install Windows. One way to avoid having to shrink your Windows partition is to install another disk, and install Ubuntu there.

The other issue people have is installing the grub boot loader. You will need this to dual boot. It is very safe to install grub into the MBR (Master Boot Record) of your Windows disk, because the MBR is not part of the Windows partition. And, if you don't like the way grub behaves, you can reinstall the Windows boot loader without installing Windows again.

People get in the most trouble when they try to "fool" the installer into not seeing the Windows disk, by unplugging it or something like that, to "make sure" that Windows is not touched. But, when you plug in the Windows disk again, usually neither Windows nor Ubuntu will boot properly. Be brave, and leave the Windows disk in there when you install Ubuntu to a second disk.

---

### Post by hyper_ch on 2008-03-05
Download the DesktopCD and test it - it's a live cd so it won't touch anything. If everything runs fine, you can then install it.

---

### Post by steffenlaursen on 2008-03-08
Thanks,

I ran the live DC just now, and it was very smooth and clean compared to what I'm used to from Windows, even though it had to run from the CD. I'm impressed :-)

However, I was unable to connect to the internet... is that a normal when you run from cd? Do I have to set up the connection seperately for Ubuntu?

(Intel PRO/100 VE Network Connection and secondarily Intel PRO/Wireless 2200BG Network Connection).

- Steffen

---

### Post by jan quark on 2008-03-08
please post the results of these terminal commands during your live cd session

they will help to clarify your current network status:

```
sudo lshw -C network
```
```

iwconfig
```

---

### Post by steffenlaursen on 2008-03-08
Here it comes

```
ubuntu@ubuntu:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interfaceTo run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo lshw -C network
  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:d0:90:8f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:d0200000-d0200fff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 81
       serial: 00:0a:e4:c3:ca:50
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.8 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:d0201000-d0201fff ioport:7000-703f irq:11
ubuntu@ubuntu:~$ sudo lshw -C network
ubuntu@ubuntu:~$ 

       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@02:02.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:d0:90:8f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=unassociated
       resources: iomemory:d0200000-d0200fff irq:11
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 81
       serial: 00:0a:e4:c3:ca:50
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSIubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ 
D:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ 
ation=on broadcast=yes driver=e100 driverversion=3.5.17-k2-NAPI duplex=full firmware=N/A ip=192.168.1.8 latency=66 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: iomemory:d0201000-d0201fff ioport:7000-703f irq:11
ubuntu@ubuntu:~$ sudo lshw -C network
ubuntu@ubuntu:~$ 
```

```
ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ubuntu@ubuntu:~$ 

```

It should perhaps be noted, that I do not at present use my wireless connection.

- Steffen

---

### Post by Fleece Flamingo on 2008-03-08
yes

---

### Post by Myglaren on 2008-03-08
You should be good to go with perhaps a little fiddling to get the WiFi to connect.  I did the same with my laptop (Tosh Equium 100A) and everything worked fine - better than with the pre-installed Vista Home Premium) with the exception of the WiFi that wouldn't connect with my (encrypted) wireless router but instead jumped straight onto my neighbour's connection.

It may be that your windows installation files are on a - possibly hidden - partition on your HD.  You could possibly reinstall from there if the worst happened or you decided that Ubuntu was not for you.

The sugestion to remove your existing hard drive, replace it with another and install Ubuntu on that is a good one although perhaps a bit on the pricey side.  Then you can revert to Windows by just swapping the drives over as necessary.

If you are going to dual-boot, you should remove anything from windows that is superfluous, do a thorough disc cleanup (try [CCleaner](http://www.filehippo.com/download_ccleaner/) to root out rubbish that XP can't find) then defrag the drive, before partitioning for Ubuntu.

If you aren't bothered about dual booting the Ubuntu install process will clear out all Windows files for you.

---

### Post by timbounceback on 2008-03-08
Strange, I have a 2200 as my wireless card, have you configured it in the top right corner?

---

### Post by hyper_ch on 2008-03-09
if you have wifi troubles steps to do things:

(1) disable any encryption on your router

(2) try to connect with this unencrypted

and if that works, then add wpa/wpa2 as encryption  (if you need it)

---

### Post by ugm6hr on 2008-03-09
Indeed, both your wired and wifi *should* work, even from the LiveCD.

Hope you got it sorted.

The question is what kind of internet connection and modem you use.  If you use a modem-router, then it will just work.

If you use USB modem, or one that requires software to be installed on your computer to connect, then it will need a bit of fiddling after installation.

My advice - invest in a modem-router (or if on cable - a router) if you haven't already got one.  They are very cheap (if you don't need wifi).

---

### Post by steffenlaursen on 2008-03-09
Update:

I tried to unplug the wire and plug it in again, and Ubuntu imidiately found it (it also found our neighbour's wireless - see attachment). It seems that I am actually on the LAN.

Yet I still don't have any internet.

- Steffen

PS: Ubunut is really nice :)

---

### Post by ByteJuggler on 2008-03-09
> **steffenlaursen said:**
> 
However, I was unable to connect to the internet... is that a normal when you run from cd? Do I have to set up the connection seperately for Ubuntu?


No that's not normal as such.  However there are known issues with some consumer grade routers which do not cope well with some types IPv6 DNS queries.  This can manifest as an apparent lack of connectivity on fresh 7.10 installs. Perhaps I can ask you to boot up with the livecd, and do the following for me, to help me determine whether or not you actually have any network connectivity or whether it's possibly this issue I'm referring to:

Open a terminal (Applications->Accessories->Terminal).  Then copy and paste the following command into the terminal:

```
ping -c 3 64.233.183.147
```

Please copy the output and post it back here.  

Then run the following command: 

```
ping -c 3 www.google.com
```

Again please copy the output and post it back here.

The 2 commands are equivalent, but the second one will involve name resolution.  Comparing the output will help me establish whethr it's possibly this DNS IPv6 issue. If it is, I'll try to send you commands to update a library that contains a workaround for this issue, which you can then test, while still on the LiveCD, and if your internet then works, you'll know that you can fix the issue if and when you actually install.

---

### Post by steffenlaursen on 2008-03-10
```
ubuntu@ubuntu:~$ ping -c 3 64.233.183.147
PING 64.233.183.147 (64.233.183.147) 56(84) bytes of data.
64 bytes from 64.233.183.147: icmp_seq=1 ttl=243 time=22.4 ms
64 bytes from 64.233.183.147: icmp_seq=2 ttl=243 time=24.6 ms
64 bytes from 64.233.183.147: icmp_seq=3 ttl=243 time=22.5 ms

--- 64.233.183.147 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 22.446/23.190/24.615/1.022 ms
ubuntu@ubuntu:~$ 
```

```
ubuntu@ubuntu:~$ ping -c 3 www.google.com
ping: unknown host www.google.com
ubuntu@ubuntu:~$ 
```

I use 7.04 by the way...

---

### Post by steffenlaursen on 2008-03-10
> **Myglaren said:**
> It may be that your windows installation files are on a - possibly hidden - partition on your HD.  You could possibly reinstall from there if the worst happened or you decided that Ubuntu was not for you.
Would the /dev/sda2 on this image be the windows install files? I know that I never made anypartitioning...

- Steffen

---

### Post by xc3RnbFO8P on 2008-03-10
You can see wireless, try to disable wireless.

Rigth click on the internet connection icon and disable wireless.

---

### Post by ByteJuggler on 2008-03-10
> **steffenlaursen said:**
> ```
ubuntu@ubuntu:~$ ping -c 3 64.233.183.147
PING 64.233.183.147 (64.233.183.147) 56(84) bytes of data.
64 bytes from 64.233.183.147: icmp_seq=1 ttl=243 time=22.4 ms
64 bytes from 64.233.183.147: icmp_seq=2 ttl=243 time=24.6 ms
64 bytes from 64.233.183.147: icmp_seq=3 ttl=243 time=22.5 ms

--- 64.233.183.147 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 22.446/23.190/24.615/1.022 ms
ubuntu@ubuntu:~$ 
```

```
ubuntu@ubuntu:~$ ping -c 3 www.google.com
ping: unknown host www.google.com
ubuntu@ubuntu:~$ 
```

I use 7.04 by the way...

Well.  7.04 as far as I know, had a patch in for the IPv6 DNS problems, so I'm not sure why you're having problems then.  But even so, the above clearly shows you do have IP connectivity, because pinging Google works, if you use the internet IP address.  If you use the hostname, then it fails, implying that your name resolution is for some or other reason not working.  Now, if this was gutsy 7.10 then I'd have said IPv6 DNS is the problem (together with your router) but since you run 7.04 I'm a little unsure.  Even so I'll try post a suggestion or 2 when I get home.

---

### Post by steffenlaursen on 2008-03-10
I still only run Ubuntu (7.04 that was) from the Live CD, so I probably don't have the patch...

I think you might be right on with the problem.

Which would mean, that if I install and upgrade, it would probably be working... it's worth a try.

- Steffen

PS: Will I need a completely new installation to get 7.10 (like, say, when changing from XP to Vista). That is should I burn a 7.10 CD right away and install 7.10 instead?

---

### Post by xc3RnbFO8P on 2008-03-10
You could try upgrade to 7.10 and in april make a fresh install with Hardy Heron.

---

### Post by steffenlaursen on 2008-03-10
So I have to make a fresh install with every bi-annual release?

---

### Post by xc3RnbFO8P on 2008-03-10
No, just if you want to try it out.

---

### Post by ByteJuggler on 2008-03-10
> **steffenlaursen said:**
> So I have to make a fresh install with every bi-annual release?

No, you can stick to a previous release if you want.  Every release is supported for at least 18 months, and the LTS releases get 3 years.  (LTS = long term support.)  Hardy Heron will be an LTS release.

---

### Post by ByteJuggler on 2008-03-10
> **steffenlaursen said:**
> I still only run Ubuntu (7.04 that was) from the Live CD, so I probably don't have the patch...

I think you might be right on with the problem.

Which would mean, that if I install and upgrade, it would probably be working... it's worth a try.

- Steffen

PS: Will I need a completely new installation to get 7.10 (like, say, when changing from XP to Vista). That is should I burn a 7.10 CD right away and install 7.10 instead?

No you misunderstand me.  The patch *was* in on 7.04, so that casts doubt about whether this is indeed the issue.  The patch was *not* in the ISO of 7.10, hence the problem, hence why I thought you might be running into that issue.  

Even so, I'll shortly post instructions to update that library (even on the LiveCD) and that should allow you to test if this is the issue or not.

---

### Post by steffenlaursen on 2008-03-19
well?

---

### Post by aaaantoine on 2008-03-19
> **steffenlaursen said:**
> Would the /dev/sda2 on this image be the windows install files? I know that I never made anypartitioning...

- Steffen

It could be, but I can't guarantee it will work by itself.  However, If there is an OS loaded into that partition, GRUB will make a boot option for it, which should make it easy to perform a system recovery if you have everything you need.

By any chance, has your laptop ever asked you to make a recovery disk of any sort?  Mine didn't come with an install CD, either, but it asked me to make a backup using the provided software.  So I did, and I can go back to that if I ever get fed up with Ubuntu.  You want to have an exit strategy if you're not fully comfortable with Ubuntu yet, or you might be stuck with it.

---

### Post by steffenlaursen on 2008-03-19
No, it didn't.

I asked for an actual CD at the store, but they couldnt get me one. But "if you somehow delete the install files, we can send your laptop to IBM and they will reinstall for 90$" :mad:

- Steffen

---

### Post by ByteJuggler on 2008-03-19
My apologies, I forgot about this thread.  I'll post the instructions now... (be right back.)

---

### Post by ByteJuggler on 2008-03-19
Gutsy instructions to work around DNS resolution problems in some routers, where all or some DNS queries resolve to for example 10.0.0.1 or another private network address:

Description/Overview of solution: Replace the libc6 library on the Gutsy CD straight after boot-up, with a patched version that works around the issue, without relying on DNS resolution.  The library in question is here: [http://packages.ubuntu.com/gutsy-updates/libc6](http://packages.ubuntu.com/gutsy-updates/libc6)

Perform these steps:

1. Open a terminal window. (Clickn Applications->Accesories->Terminal)

2.) Directly download the updated i386 library package from a mirror site (a UK one is used below), by entering the following command.
```
 wget http://194.169.254.10/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb 
```

3.) Install it by entering the following command:
```
sudo dpkg -i libc6_2.6.1-1ubuntu10_i386.deb
```

That should be it, after performing these steps your net connection should work normally.   (Please note, I've not tested these exact steps on a fresh non-working gutsy install, but they should work as is.  Please also note: this instructions do assume a gutsy install - that version of lib was never released on feisty, so I have no idea what will happen if you try this instructions on for example Feisty.  As an aside: The Feisty-updates repository contains no updates to this package.)

---

### Post by steffenlaursen on 2008-03-22
It doesnt seem to work with Feisty...

```
To run a command as administrator (user "root"), use "sudo <command>".

See "man sudo_root" for details.



ubuntu@ubuntu:~$ wget http://194.169.254.10/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb

--14:08:46--  http://194.169.254.10/ubuntu/pool/main/g/glibc/libc6_2.6.1-1ubuntu10_i386.deb

           => `libc6_2.6.1-1ubuntu10_i386.deb'

Connecting to 194.169.254.10:80... connected.

HTTP request sent, awaiting response... 200 OK

Length: 4,183,514 (4.0M) [application/x-debian-package]



100%[====================================>] 4,183,514    189.02K/s    ETA 00:00



14:09:08 (188.10 KB/s) - `libc6_2.6.1-1ubuntu10_i386.deb' saved [4183514/4183514]



ubuntu@ubuntu:~$ sudo dpkg -i libc6_2.6.1-1ubuntu10_i386.deb

dpkg: regarding libc6_2.6.1-1ubuntu10_i386.deb containing libc6:

 libc6 conflicts with tzdata (<< 2007e-2)

  tzdata (version 2007b-0ubuntu1) is installed.

dpkg: error processing libc6_2.6.1-1ubuntu10_i386.deb (--install):

 conflicting packages - not installing libc6

Errors were encountered while processing:

 libc6_2.6.1-1ubuntu10_i386.deb

ubuntu@ubuntu:~$ 
```

Is there a chance that it will work if I install to disc instead of just running the live CD?

- Steffen

---

### Post by ByteJuggler on 2008-03-22
Ok I'm sorry I kinda lost track of the specifics of this case.   The instructions I gave you would've been fine, for Gutsy.  But not for Feisty.  

Let me just reiterate the facts:

0.) You are running Feisty.
1.) Feisty's livecd_* **already included **a*_ workaround for a common DSN / IPv6 problem present in many ADSL router/modems.
2.) **_Gutsy's_** livecd unfortunately **lost this workaround **for this problem
3.) Your machine does have internet connectivity as shown by the ping working by IP address
4.) Your machine does not have proper DNS as shown by the ping failing by hostname.

From this I deduce the following:
1.) Your problem is **possibly not the actual IPv6 problem **I originally suggested, since Feisty had/has a patch for this issue, but it does appear to be something similar.
2.) Your problem is definitely DNS/name-resolution related.  So, lets try to investigate that a bit further. 

Can you please post me the contents of your /etc/resolv.conf file, e.g. perhaps do

```
gedit /etc/resolv.conf
```

and post back the contents.

Anyway, what I'm wanting to try is for you to specify an alternate DNS server and bypass your router's DNS proxy altogether, which should fix your problem instantly.

You could do this, for example, by replacing the contents of your /etc/resolv.conf file with, say:

```
nameserver 208.67.222.222
```

That is [OpenDNS's ]("http://www.opendns.com/") main nameserver and is free for public use.

Hope that helps.

---

### Post by steffenlaursen on 2008-03-23
Indeed, that did the trick!

Thank you so much :)

:KS

- Steffen

---

### Post by steffenlaursen on 2008-03-23
Well, it workED :s

I installed as dualboot, and now suddenly the internet access is gone again. I tried doing the gedit /etc/resolv.conf again, but this time the file was blank... there was nothing in it at all.

And I of course didnt copy the content before, so I'm kinda lost...

What is the standard content og the resolv.conf?

---

### Post by ByteJuggler on 2008-03-23
Ah yes. Normally it contains one (or sometimes 2) nameserver specifications, which (typically) is put there as part of the DHCP IP assignment process by the DHCP client.  This implies that your router is somehow not setting/specifying a DNS server when it assigns you an IP, which perfectly ties in/explains your previous symptoms.  

Anyway, you should probably configure the DHCP client to leave the resolv.conf alone (should've told you about that before, but it didn't occur to me at the time that it's going to cause problems!)

Basically, go edit the DHCP configuration file (press alt-f2 and paste the following: "sudo gedit /etc/dhcp3/dhclient.conf"), find the following text:

```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, ***domain-name-servers, ***host-name,
        netbios-name-servers, netbios-scope;

```

Remove the bold part, so it looks as follows:

```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, host-name,
        netbios-name-servers, netbios-scope;

```

Now restart your networking:
```

sudo /etc/init.d/networking restart

```

That should prevent DHCP from overwriting the DNS servers in /etc/resolv.conf.  Now go back and edit /etc/resolv.conf and add in whatever DNS server you want to use.  Job done. :-)

---

### Post by steffenlaursen on 2008-03-24
I will try that in a minute.

EDIT: Results:

When I enter "sudo /etc/init.d/networking restart" this keeps repeating ad infinitum:

```
DHCPREQUEST on eth0 to 255.255.255.255.255 port 67
parse_option_buffer: option host-name (15) larger than buffer.
parse_option_buffer: option host-name (15) larger than buffer.
parse_option_buffer: option host-name (15) larger than buffer.
parse_option_buffer: option host-name (15) larger than buffer.
DHCPREQUEST on eth0 to 255.255.255.255.255 port 67
DHCPOFFER from 192.168.1.1
parse_option_buffer: option host-name (15) larger than buffer.
parse_option_buffer: option host-name (15) larger than buffer.
....
```

However, here's something completely different: as I was running through the earlier recommended steps in this thread, I tried to ping google using "ping -c 3 64.233.183.147".

When I did so from the live CD (while still only considering ubuntu) I got

```
ubuntu@ubuntu:~$ ping -c 3 64.233.183.147
PING 64.233.183.147 (64.233.183.147) 56(84) bytes of data.
64 bytes from 64.233.183.147: icmp_seq=1 ttl=243 time=22.4 ms
64 bytes from 64.233.183.147: icmp_seq=2 ttl=243 time=24.6 ms
64 bytes from 64.233.183.147: icmp_seq=3 ttl=243 time=22.5 ms

--- 64.233.183.147 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 22.446/23.190/24.615/1.022 ms
ubuntu@ubuntu:~$ 
```

But when I did it today (with Ubuntu actually installed), I got

```
steffen@steffen-laptop:~$ ping -c 3 64.233.183.147
PING 64.233.183.147 (64.233.183.147) 56(84) bytes of data.
From 169.254.9.43 icmp_seq=1 Destination Host Unreachable
From 169.254.9.43 icmp_seq=2 Destination Host Unreachable
From 169.254.9.43 icmp_seq=3 Destination Host Unreachable

--- 64.233.183.147 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2008ms
, pipe 3
steffen@steffen-laptop:~$ 
```

So it seems that I am no longer on the network at all... meaning something new is the problem, I suppose.

- Steffen

---

### Post by ByteJuggler on 2008-03-24
> **steffenlaursen said:**
> I will try that in a minute.

EDIT: Results:

When I enter "sudo /etc/init.d/networking restart" this keeps repeating ad infinitum:

[code]DHCPREQUEST on eth0 to 255.255.255.255.255 port 67
parse_option_buffer: option host-name (15) larger than buffer.


Hmm ok, well that suggests that something's now wrong with the DHCP config file.  Please therefore post the contents of the entire file here.

The above fault will prevent you from doing the ping test probably (as you machine will not be able to get an IP address without DHCP working), so your connectivity problem will go away once we properly fix the DHCP issue.

---

### Post by steffenlaursen on 2008-03-24
Here comes:
```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

PS: My newly reinstalled windows crashed on me for the first time today. Seems setting the clock was a bit over the top for the most expensive OS in the world :lolflag:

---

### Post by ByteJuggler on 2008-03-24
Hmmm.  The thot plickens, as they say.   Your conf file seems fine, so I'm a little mystified by the error messages... so I'll suggest just removing the "host-name" option as well (you don't need/want DHCP to send you a hostname either.)   I have also found/realised you can actually insert/specify the alternate DNS server to use in that conf file, so, edit your file so it looks as follows:

```
# Configuration file for /sbin/dhclient, which is included in Debian's
#	dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#	man page for more information about the syntax of this file
#	and a more comprehensive list of the parameters understood by
#	dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#	not leave anything out (like the domain name, for example), then
#	few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
[COLOR="Red"][COLOR="Red"]***prepend domain-name-servers 208.67.222.222;***[/COLOR][/COLOR]
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, 
	netbios-name-servers, netbios-scope;
```

It might also be an idea to simply put back the entry you removed to see if the "hostname" errors go away.

---

### Post by steffenlaursen on 2008-03-25
Nope, the hostname error persists.

And still nothing.

- Steffen

---

### Post by ByteJuggler on 2008-03-25
> **steffenlaursen said:**
> Nope, the hostname error persists.

And still nothing.

- Steffen

OK so let me be clear, you've put back the "domain-name-servers," bit in the "request" line, and the hostname errors then also persist???

Edit: You know what, I think I've just got another clue about what the thing is complaining about - I think the hostname is too long.  The message is saying effectively that the hostname (15) is longer than the buffer space allocated, and your hostname is indeed 14+1 characters long (14 actual characters and 1 terminating null character making 15.)  So perhaps it would be an idea to reduce your hostname length... (It also helps explain why the liveCD worked - its hostname is a lot shorter...)  One page explaining how to change the hostname is [here]("http://codeghar.wordpress.com/2007/11/04/change-hostname-in-ubuntu/").

---

### Post by steffenlaursen on 2008-03-25
Yes, that is correct.

I tried shortening the hostname, but for whatever reason, after editing /etc/hosts I can not open the terminal again to edit /etc/hostname. And after a reboot, everything is back to normal. I also tried just "sudo hostname steffen" which lasted until reboot as well.

I tried running the liveCD again, and I have *the same problems* as with the actual install. So obviously, something happened when I formated and reinstalled.

Thank you for your efforts, I hope we'll get this thing up and running soon.

- Steffen

---

### Post by ByteJuggler on 2008-03-25
So, from the LiveCD, are you getting those hostname buffer errors?  This is getting stranger and stranger...

---

### Post by steffenlaursen on 2008-03-25
Indeed.

Maybe I should just get 7.10, close my eyes and hope it goes away :confused:

- Steffen

---

### Post by ByteJuggler on 2008-03-25
Actually, I'm tempted to suggest you try 8.04 Beta, just to see what happens... What dsl router have you got btw?

---

### Post by steffenlaursen on 2008-03-27
I've decided to put the ubuntu project on a standby... there's a bit too much trouble finding this problem.

Maybe later, with a different internet provider, a different router and a different computer, I might try again. :)

Thanks for all the help, but it's getting a little too complicated for my taste

- Steffen

---

