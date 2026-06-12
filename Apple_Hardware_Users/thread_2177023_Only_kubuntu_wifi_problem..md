---
title: "Only kubuntu wifi problem."
date: 2013-09-26
forum: Apple Hardware Users
---

### Post by stefan9 on 2013-09-26
Hello I'm a very new user in unix systems. I installed ubuntu 64 bit 12.04 LTS on my macbook pro 4,1 early 2008. I fix the problem in ubuntu with the wifi but always if I wanted to connect to wifi I have to connect to random hidden network to show my network is complicated I know. I installed kubuntu and now the wifi does not work. I cant see my wifi connection and when I tried to connect as hidenn via konsole:

```
boo@boo-MacBook:~$ iwconfig wlan0 essid sarmale key 2358085701Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not permitted.
boo@boo-MacBook:~$ dhclient wlan0
RTNETLINK answers: Operation not permitted

```

```
iwconfig: eth0      no wireless extensions.

lo        no wireless extensions.


wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```
lspci | grep Network:

02:00.0 Network controller: Broadcom Corporation BCM4321 802.11a/b/g/n (rev 03)
```
Thank you I really need help I don't know what to do anymore this problem is bothering me since last week.

---

### Post by SeijiSensei on 2013-09-27
Commands like "iwconfig" and "dhclient" require root privileges.  You must run them with sudo like this:

```
sudo dhclient wlan0
```

You'll be asked for your password the first time you enter a sudo command.  Afterwards, you'll have root privileges for a while and won't need to re-enter the password.  Read this for details: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by stefan9 on 2013-09-28
Thank you solved... I really sorry for creating new thread for a minor thing but I didn't find anywhere, thank you

---

