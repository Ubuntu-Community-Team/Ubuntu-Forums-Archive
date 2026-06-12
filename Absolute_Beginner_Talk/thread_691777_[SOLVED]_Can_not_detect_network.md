---
title: "[SOLVED] Can not detect network"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by arjayes on 2008-02-09
I don't get it  . just yesterday the network was working fine . today it isn't ..
I've configured my network settings for a LAN . I can't access the net . even when i try pinging local addresses i get a "Could not detect a network " message ....
as i said i have absolutely no idea what could have caused this and i am clueless about what to do .... please help

---

### Post by spiderbatdad on 2008-02-09
you should be using roaming mode i believe, if you are using dhcp.

---

### Post by houstonbofh on 2008-02-09
Bring up a terminal and type "ifconfig" and see what you have.  Post it back here if you can.  Remember that the Live CD can show you what the settings should look like if you changed them.  It is also a good test to see if it is a hardware or configuration problem.

---

### Post by arjayes on 2008-02-09
the output of ifconfig --
> 

eth0      Link encap:Ethernet  HWaddr 00:1B:24:10:D3:80  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23676 (23.1 KB)  TX bytes:0 (0.0 b)
          Interrupt:18 


if it helps the output of > lshw -C network
is
> 
*-network
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=ipw3945 latency=0 module=ipw3945
  *-network
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 11
       serial: 00:1b:24:10:d3:80
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.18 duplex=full firmware=N/A latency=0 link=yes module=sky2 multicast=yes port=twisted pair speed=100MB/s


---

### Post by arjayes on 2008-02-09
some one pls help .....

---

### Post by arjayes on 2008-02-09
<bump>

---

### Post by houstonbofh on 2008-02-10
This may sound silly, but swap the cable.  For some reason you are recieving packets but not sending any...  Do you have network on the Live CD?  And we are trying the LAN port, not WiFi, correct?

---

### Post by arjayes on 2008-02-11
Windows i hav installed on the same comp. detects the network fine . And it's not a question of hardware not being detected coz it was working fine for a month after i installed ubuntu only to conk out suddenly a couple of days back ... and yes its a LAN port ... regarding the live CD .. i actually don't have one .. i did my install from a text based installer ... i don't think its necessary coz it was working fine after i installed ubuntu .. if it has some other purpose other than checkin if the hardware is compatible pls let me know and i'll try to beg borrow or steal one .. 
i do most of my work on the net and the lack of it on ubuntu has severly iimpaired me ... someone plz could u think of something fast ... i'm outta ideas :(

---

### Post by houstonbofh on 2008-02-11
The Live CD is a VERY handy tool for things just like this.  If it works, and your install does not, you have known good config files to refer to.  It also lets you know if it is an Ubuntu issue, or a config issue.  Otherwise it is a matter of asking you to paste a lot of config files here to see what stands out.  It also gives you an "Emergency" system when everything has gone to pot.  I have even used it to recover data from blown hard drives that would never boot again...  That said, I too install from the text based installer.  I am personally filling a small landfill with CDs. :)

But if you can't get one, we can try comparing config files in /etc and see if we find it.

PS:  Is it a Intel (G/P/X)35 based motherboard?  There is a known issue with WOL and some of these boards.  Configure "Wake On Lan" in both the BIOS and Windows.

---

### Post by arjayes on 2008-02-12
sorry for the late reply ... but yeah this is very wierd .. i managed to get a live CD and guess what it doesn't connect to or detect the network .... so what do i do now ??? i'm totally stumped .. why .. coz of the foll. reasons :
1. If its a driver problem and there is a lack of support why did it when i first installed Ubuntu
2. If its coz i messed up some config files .. y doesn't the net work on the live CD 
3. If its a hardware problem Y does it work wonderfully on windows ...
or am I wrong ??

---

### Post by bumanie on 2008-02-12
Very strange that your internet had been working. To me it sounds very muc like the ipv6 issue that has been a problem for some users. But why it would work yesterday and not today is a mystery to me, if no settings have been changed. However, if you like, you can try and disable or blacklist ipv6 and see if that works. You can reverse the changes if it doesn't work. There are two methods you can try.
Method 1.
> gksudo gedit /etc/modprobe.d/blacklist in terminal
then add 
blacklist ipv6
at the bottom of the gedit list and save.
After reboot, all should work fine.
Method 2 (is to diable ipv6 in firefox)
Type about:config in your firefox address bar
Type "ipv6" in the filter 
Change the value of "network.dns.disableIPv6" to true
Hope this helps.

---

### Post by houstonbofh on 2008-02-13
> **houstonbofh said:**
> PS:  Is it a Intel (G/P/X)35 based motherboard?  There is a known issue with WOL and some of these boards.  Configure "Wake On Lan" in both the BIOS and Windows.
If you run my board, a Gigabyte GA-P35-DS3L on just Linux, it is fin.  On just windows it is fine.  Duel boot is a problem.  Windows will put the nic hard to sleep and it will into function on shutdown.  The fix is to enable wake on lan in both the BIOS, and in the Windows nic driver.  This fits exactly with what you are saying which is why I asked what board you are using.

---

### Post by Presto123 on 2008-02-13
Wonder if this is an issue with Windows not releasing the card? Did you switch over by restarting the computer to get into Ubuntu? Or did you let it shut down? My sound card will buck if I don't first shut down the computer after using Windows.

---

### Post by oedha on 2008-02-13
this thing also happened.....to me
what i did was.....( i used static ip )
i deleted the DNS...then fill it again
then in the ESSID box....i changed from "any" to the "accesspoint name"
then sudo /etc/init.d/networking restart
done...it's fix...would you like to try ?

---

### Post by arjayes on 2008-02-13
> **oedha said:**
> this thing also happened.....to me
what i did was.....( i used static ip )
i deleted the DNS...then fill it again
then in the ESSID box....i changed from "any" to the "accesspoint name"
then sudo /etc/init.d/networking restart
done...it's fix...would you like to try ? 


What do u mean by thr ESSID box

---

### Post by arjayes on 2008-02-13
@bumanie
I tried blacklistiing ipv6 and the firefox method . neiither worked 
@Presto123
I tried restarting and sthutting down annd booting . nothing works .
@oedha 
I can't find an ESSID box . i'm really sorry if this sounds naive but i jjust cant find it 
@houstonbofh 
how do i go about finding my mother board  details . what command ?


@ all the above 
thanks for taking the time for answering . pls bear with me .

---

### Post by arjayes on 2008-02-13
another interesting and most important  thing ...
sudo /etc/init.d/networking restart gives 
> 
 * reconfiguring network interfaces ...
ifdown : failed to open statefile /var/run/network/ifstate : No such file or directory 
ifup : failed to open statefile /var/run/network/ifstate: No such file or directory
                                                                                                                                            [fail]


---

### Post by arjayes on 2008-02-17
Hey !!! problem solved .... thanks in particular to oedha . 
i tried >  /etc/init.d/networking restart  and got the above mentioned errors ...
that set me googling and i came across[ this thread]("http://ubuntuforums.org/archive/index.php/t-165994.html")
see the last post ... that was it i just had to create the /var/run/network directory 
and then /etc/init.d/networking restart worked fine and the internet is up and running ... i'm writing his post from ubuntu :) after nearly a week withut net access on ubuntu i'm very relieved .... thanks to all of u who helped me get it working again :):guitar::KS

---

