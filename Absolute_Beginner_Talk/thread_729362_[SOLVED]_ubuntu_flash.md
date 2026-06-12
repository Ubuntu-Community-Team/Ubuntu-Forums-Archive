---
title: "[SOLVED] ubuntu flash?"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2008-03-19
ive installed adobe flash via firefox but it keeps asking to install it agian so i reinstalled via synaptic but it still doesent work!!!

please help (T_T)

---

### Post by glennric on 2008-03-19
Try it from a command line.  Type
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by kamitsukai on 2008-03-19
> **glennric said:**
> Try it from a command line.  Type
```
sudo apt-get install flashplugin-nonfree
```

This is what i get

```
carl@carl-desktop:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for carl:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  konqueror-nsplugins ttf-xfree86-nonfree xfs
The following NEW packages will be installed
  flashplugin-nonfree
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/18.1kB of archives.
After unpacking 160kB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package flashplugin-nonfree.
(Reading database ... 106857 files and directories currently installed.)
Unpacking flashplugin-nonfree (from .../flashplugin-nonfree_9.0.48.0.2+really0ubuntu12_i386.deb) ...
Setting up flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) ...
Downloading...
--00:15:23--  http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 88.221.178.70
Connecting to fpdownload.macromedia.com|88.221.178.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3,036,127 (2.9M) [application/x-gzip]

    0K .......... .......... .......... .......... ..........  1%   25.77 KB/s
   50K .......... .......... .......... .......... ..........  3%   48.85 KB/s
  100K .......... .......... .......... .......... ..........  5%  176.10 KB/s
  150K .......... .......... .......... .......... ..........  6%  171.43 KB/s
  200K .......... .......... .......... .......... ..........  8%  109.61 KB/s
  250K .......... .......... .......... .......... .......... 10%  189.45 KB/s
  300K .......... .......... .......... .......... .......... 11%  290.89 KB/s
  350K .......... .......... .......... .......... .......... 13%  176.06 KB/s
  400K .......... .......... .......... .......... .......... 15%  105.90 KB/s
  450K .......... .......... .......... .......... .......... 16%  500.10 KB/s
  500K .......... .......... .......... .......... .......... 18%  596.11 KB/s
  550K .......... .......... .......... .......... .......... 20%  657.89 KB/s
  600K .......... .......... .......... .......... .......... 21%  624.45 KB/s
  650K .......... .......... .......... .......... .......... 23%  658.54 KB/s
  700K .......... .......... .......... .......... .......... 25%  694.36 KB/s
  750K .......... .......... .......... .......... .......... 26%  657.64 KB/s
  800K .......... .......... .......... .......... .......... 28%  694.75 KB/s
  850K .......... .......... .......... .......... .......... 30%  691.53 KB/s
  900K .......... .......... .......... .......... .......... 32%  726.47 KB/s
  950K .......... .......... .......... .......... .......... 33%  704.78 KB/s
 1000K .......... .......... .......... .......... .......... 35%  594.92 KB/s
 1050K .......... .......... .......... .......... .......... 37%  596.08 KB/s
 1100K .......... .......... .......... .......... .......... 38%  728.67 KB/s
 1150K .......... .......... .......... .......... .......... 40%  502.95 KB/s
 1200K .......... .......... .......... .......... .......... 42%  693.60 KB/s
 1250K .......... .......... .......... .......... .......... 43%  695.42 KB/s
 1300K .......... .......... .......... .......... .......... 45%  764.37 KB/s
 1350K .......... .......... .......... .......... .......... 47%  451.08 KB/s
 1400K .......... .......... .......... .......... .......... 48%  694.03 KB/s
 1450K .......... .......... .......... .......... .......... 50%  479.53 KB/s
 1500K .......... .......... .......... .......... .......... 52%  330.40 KB/s
 1550K .......... .......... .......... .......... .......... 53%  520.83 KB/s
 1600K .......... .......... .......... .......... .......... 55%  222.76 KB/s
 1650K .......... .......... .......... .......... .......... 57%  368.46 KB/s
 1700K .......... .......... .......... .......... .......... 59%  236.00 KB/s
 1750K .......... .......... .......... .......... .......... 60%  271.75 KB/s
 1800K .......... .......... .......... .......... .......... 62%  134.38 KB/s
 1850K .......... .......... .......... .......... .......... 64%  134.42 KB/s
 1900K .......... .......... .......... .......... .......... 65%  211.46 KB/s
 1950K .......... .......... .......... .......... .......... 67%  166.95 KB/s
 2000K .......... .......... .......... .......... .......... 69%  140.33 KB/s
 2050K .......... .......... .......... .......... .......... 70%  186.72 KB/s
 2100K .......... .......... .......... .......... .......... 72%  195.30 KB/s
 2150K .......... .......... .......... .......... .......... 74%  431.23 KB/s
 2200K .......... .......... .......... .......... .......... 75%  154.16 KB/s
 2250K .......... .......... .......... .......... .......... 77%  266.46 KB/s
 2300K .......... .......... .......... .......... .......... 79%  166.62 KB/s
 2350K .......... .......... .......... .......... .......... 80%  141.74 KB/s
 2400K .......... .......... .......... .......... .......... 82%  190.00 KB/s
 2450K .......... .......... .......... .......... .......... 84%  166.62 KB/s
 2500K .......... .......... .......... .......... .......... 86%  152.46 KB/s
 2550K .......... .......... .......... .......... .......... 87%  245.10 KB/s
 2600K .......... .......... .......... .......... .......... 89%  119.01 KB/s
 2650K .......... .......... .......... .......... .......... 91%  104.19 KB/s
 2700K .......... .......... .......... .......... .......... 92%  337.77 KB/s
 2750K .......... .......... .......... .......... .......... 94%  134.33 KB/s
 2800K .......... .......... .......... .......... .......... 96%  432.20 KB/s
 2850K .......... .......... .......... .......... .......... 97%  154.29 KB/s
 2900K .......... .......... .......... .......... .......... 99%  137.36 KB/s
 2950K .......... ....                                       100%  464.77 KB/s

00:15:40 (202.20 KB/s) - `./install_flash_player_9_linux.tar.gz' saved [3036127/3036127]

Download done.
md5sum mismatch install_flash_player_9_linux.tar.gz
The Flash plugin is NOT installed.

carl@carl-desktop:~$ 

```

---

### Post by glennric on 2008-03-19
Type
```
ls /var/lib/flashplugin-nonfree
```
and see if there is any output.  If there is then type
```
sudo rm /var/lib/flashplugin-nonfree/install-flash-player*.tar.gz
```
Then try to install again.  You might also check if there is a file install-flash-player*.tar.gz in the directory you are currently in.

---

### Post by kamitsukai on 2008-03-19
no output

---

### Post by glennric on 2008-03-19
How about 
```
ls /var/cache/flashplugin-nonfree
```

---

### Post by kamitsukai on 2008-03-19
```
carl@carl-desktop:~$ ls /var/cache/flashplugin-nonfree
install_flash_player_9_linux.tar.gz

```

---

### Post by glennric on 2008-03-19
Ok, then type
```
sudo rm /var/cache/flashplugin-nonfree/install_flash_player_9_linux.tar.gz 
```
then try to install it again.

---

### Post by kamitsukai on 2008-03-19
no it didnt work all i got was

```
carl@carl-desktop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
carl@carl-desktop:~$ 

```

---

### Post by glennric on 2008-03-19
Try
```
sudo apt-get install --reinstall flashplugin-nonfree
```

---

### Post by kamitsukai on 2008-03-19
no same as the second output it says downloaded but not installed...

---

### Post by glennric on 2008-03-19
Post the output of 
```
ls -l /etc/alternatives/firefox-flashplugin
```
and 
```
ls -l /usr/lib/firefox/plugins/flashplugin-alternative.so
```

---

### Post by kamitsukai on 2008-03-19
1st one
```
carl@carl-desktop:~$ ls -l /etc/alternatives/firefox-flashplugin
ls: /etc/alternatives/firefox-flashplugin: No such file or directory
carl@carl-desktop:~$ 

```

2nd one
```
carl@carl-desktop:~$ ls -l /usr/lib/firefox/plugins/flashplugin-alternative.so
ls: /usr/lib/firefox/plugins/flashplugin-alternative.so: No such file or directory
carl@carl-desktop:~$ 

```

---

### Post by glennric on 2008-03-19
Ok, as a last resort you may have to install flash manually.  Here is a tutorial on how to do it.
[http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash")

---

### Post by kamitsukai on 2008-03-19
lol thanks =P

---

### Post by kamitsukai on 2008-03-19
no that didnt work either lol never mind (T_T)

---

### Post by glennric on 2008-03-19
Try 
```
sudo apt-get remove --purge flashplugin-nonfree
```
then try to install it again.

---

### Post by glennric on 2008-03-19
If that doesn't work then try the following link.  This is the one I meant to give you before
[http://www.psychocats.net/ubuntu/flashpre710#adobe]("http://www.psychocats.net/ubuntu/flashpre710#adobe")

---

### Post by kamitsukai on 2008-03-20
> **glennric said:**
> If that doesn't work then try the following link.  This is the one I meant to give you before
[http://www.psychocats.net/ubuntu/flashpre710#adobe]("http://www.psychocats.net/ubuntu/flashpre710#adobe")

lol yer i found that link and it worked =P thanks

---

### Post by gandaran on 2008-03-20
kamitsukai
your problem installing flash was due to an  old broken package in synaptic,
you must update synaptic or « sudo apt-get update » first.

---

### Post by forrestcupp on 2008-03-20
You just needed to enable the backports and proposed update repos to get a newer version via apt that works.

System->Administration->Software Sources.  Click the Updates tab and check the boxes next to "Pre-released updates" and "Unsupported updates".  Then:

```
sudo apt-get update
sudo apt-get install flashplugin-nonfree
```

If you would have done that, it would have worked.

---

