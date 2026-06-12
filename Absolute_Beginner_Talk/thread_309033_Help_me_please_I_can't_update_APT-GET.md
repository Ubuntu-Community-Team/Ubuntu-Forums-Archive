---
title: "Help me please: I can't update APT-GET"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by iClouseau88 on 2006-11-29
Hi,

I have a P3 Toshiba laptop with XP Pro SP2 and Ubuntu Dapper 6.06.1 LTS.  It is hooked up to a D-Link DI-624C by wire and an ADSL Modem. Through Windows I can reach the Net either wirelessly or as a DHCP Client (Not dare to try WPA yet).  I can ping both the router default gateway or the Ethernet card (eth0 @ 192.168.0.117).  However, lately I have been frustrated with these problems after installing Automatix2:

1) Can't install individual packages like Adobe Reader,even though Automatix2 installation is confirmed (Error msg: fatal apt failure,etc., or connection refused)

I don't want to remove Automatix2 yet, since I finally was able to install it after some problems with Automatix.
2) Can't update apt-get, i.e. sudo apt-get update
3) Can't install gnome splash-screen manager

The common error message seems to be like the following:

QUOTE:
sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg
  Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Err [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg
  Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Err [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg
  Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg) Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg) Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg) Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg) Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/Release.gpg](http://www.getautomatix.com/apt/dists/dapper/Release.gpg) Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg](http://archive.canonical.com/ubuntu/dists/dapper-commercial/Release.gpg) Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used instead.

END QUOTE

Could you please show me how to solve this problem? TIA!
By the way, I have not setup Firestarter firewall or any AV for Dapper. I use KPF for Windoz but it shouldn't affect Linux.

:(

---

### Post by CatKiller on 2006-11-29
It sounds like something's not right with your networking setup - you're not getting DNS results. As you can see, it thinks that the Internet is contained in your computer (192.168.0.117). I don't know enough to help you fix it, but hopefully that will point you in the right direction.

---

### Post by konst88 on 2006-11-29
Do you have an intenet connection? Programs like gaim,evolution,firefox works?

---

### Post by PartisanEntity on 2006-11-29
Judging by the error output this is probably not the case, but if you installed something like anon-proxy it could be a problem.

---

### Post by apral on 2006-11-29
If connection refused comes up then it will probably be a permissions problem.

---

### Post by iClouseau88 on 2006-11-30
Problem solved!

What had happened was I had put in the DHCP-suplied IP of the native Ethernet card when configuring proxy for Automatix. Problem persisted even after I removed Automatix(2) and the proxy program from my laptop. I just did the following and problem was solved:

1. sudo gedit /etc/apt/apt.conf
2. Clear out the whole content of apt.conf file, i.e. delete "ACQUIRE {http::proxy "192.168.0.117:8118/"}
3. save file and exit
4. sudo apt-get update

VOILA! Ca 'y est!

iClouseau88

---

### Post by bruban on 2007-07-06
I had the same problem on a Debian 4.0 server that I use as a firewall.

The resolution was that I had to allow outgoing connections from that server via TCP port 80.

Bruce


QUOTE:
sudo apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to 192.168.0.117:8118 (192.168.0.117). - connect (111 Connection refused)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg
 
:([/QUOTE]

---

