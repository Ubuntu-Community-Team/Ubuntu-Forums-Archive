---
title: "Wicd stopped loading"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by slight_disregard on 2008-02-14
This is so discouraging.

So I installed wicd and my wired connection stopped working and it still says no wireless connections found. I was trying to figure out how to set up my wired connection so I went to preferences and clicked always show wired connection. Exited, reloaded, wired connection is there. Entered in a profile name and clicked add a few times but nothing happened. Exited again and now it won't start at all.

Rebooted and it still won't open.

I just need my wireless to work. =\

---

### Post by Thingymebob on 2008-02-14
Does WiCD still appear in your startup programs?
System>Preferences>Sessions.

If it doesn't add it with
Name: WiCD
command: /opt/wicd/tray.py

Then you'll need to restart your session (logout and in again)

If that doesn't work start it from applications>Internet.

It can take a while to start up while it searches for networks. Once you have something set up to autoconnect to its almost instant

---

### Post by Whiffle on 2008-02-14
Sounds like the daemon may have crashed.  Close all the wicd windows and try

sudo /etc/init.d/wicd start

---

### Post by imdano on 2008-02-14
> **slight_disregard said:**
>  Entered in a profile name and clicked add a few times but nothing happened. Exited again and now it won't start at all.Clicking add multiple times might have caused a problem.  Nothing is supposed to happen when you click it, it just creates a wired profile.  There's an outside chance that clicking it a bunch of times screwed up the wired-settings.conf file.  Try running ```
/opt/wicd/gui.py
```From a terminal and see if you get any error messages.  As for your wireless problems, were you also having trouble with NetworkManager?  What's the output of ```
sudo lshw -C network
```

---

### Post by dinga on 2008-02-17
I am having a similar problem.

I setup my network at home using Network Manager, which worked fine. But I also want to connect to work, which uses a few more settings. I was told that WICD is the best choice. So I installed it by adding to the Synaptic Package Manager. It seemed to install fine and removed some other bits and pieces.

WICD worked well at home with basic WEP settings. But work has some different security settings, so i could see the newtork using WICD but could not find the right setup to connect.

 (See other post: [http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=369&sid=93b90efdb8b3eedcf4d8a30bfd01d37b](http://wicd.sourceforge.net/phpbb/viewtopic.php?f=3&t=369&sid=93b90efdb8b3eedcf4d8a30bfd01d37b))

Now after playing with it, the GUI won't appear. I have tried a few of the above terminal commands and I can get the tray icon to show at start up, but I can't get the GUI work work at all? 

Any help would be appreciated as I am completely new to linux, ubuntu.

Thanks
Dinga

---

### Post by Cain67 on 2008-03-30
im in the same boat.
cant get the tray icon to appear, can not get wicd to load...
just blank.

and so cant get online.
any help would be great.

installed it about an hour and a half ago, and it worked great, untill i shut down.... then i havnt been able to load it since iv restarted....

please help!!!
thanks

---

### Post by imdano on 2008-03-30
Delete /opt/wicd/data/wired-settings.conf and then try restarting the daemon with ```
sudo /etc/init.d/wicd start
```I think the tray will start up then.

---

### Post by Cain67 on 2008-04-01
ok. seeing as no1 has been able to help- this is all the output iv been given:

Blackbook=my pc :)

[PHP]m3@Blackbook:~$ sudo /opt/wicd/gui.py
[sudo] password for m3:
attempting to connect daemon...
daemon not running, running gksudo ./daemon.py...
You need to start the daemon before using the gui or tray.  Use the command 'sudo /etc/init.d/wicd start'.
daemon still not running, aborting.
Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined
m3@Blackbook:~$ sudo /opt/wicd/daemon.py
/opt/wicd
wicd daemon: pid 6037
m3@Blackbook:~$ lo        no wireless extensions.

wifi0     no wireless extensions.

eth0      no wireless extensions.


m3@Blackbook:~$ iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:857  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

m3@Blackbook:~$ iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:12:44:B0:15:00
                    ESSID:""
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:12:44:B0:15:01
                    ESSID:""
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:1C:F0:38:31:94
                    ESSID:"The Connection of Doom"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=13/70  Signal level=-82 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 04 - Address: 00:1C:F0:38:A5:DB
                    ESSID:"The HQ"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=48/70  Signal level=-47 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
                    Extra:ath_ie=dd0900037f01010020ff7f
          Cell 05 - Address: 00:18:4D:AD:43:46
                    ESSID:"VVV"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-47 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 06 - Address: 00:1B:FC:8F:E7:9C
                    ESSID:"JAY"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=10/70  Signal level=-85 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : PSK
          Cell 07 - Address: 00:12:44:B0:15:02
                    ESSID:"UCwireless"
                    Mode:Master
                    Frequency:2.412 GHz (Channel 1)
                    Quality=6/70  Signal level=-89 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : 802.1x
                    IE: WPA Version 1
                        Group Cipher : WEP-40
                        Pairwise Ciphers (1) : WEP-40
                        Authentication Suites (1) : 802.1x

eth0      Interface doesn't support scanning.



[/PHP]

---

### Post by imdano on 2008-04-01
It's not a driver issue, it's a wicd bug.  Did you delete /opt/wicd/data/wired-settings.conf?  If that didn't work, deleting manager-settings.conf and try again.  If it still doesn't work, delete wireless-settings.conf.

This error > Traceback (most recent call last):
  File "/opt/wicd/gui.py", line 36, in <module>
    daemon = dbus.Interface(proxy_obj, 'org.wicd.daemon')
NameError: name 'proxy_obj' is not defined Means that the daemon isn't running.  And since you had probably just started it, that means it must have crashed.  In probably 95% of cases where the daemon has been crashing right on startup, the problem is that a configuration file got corrupted.

---

### Post by _godbout_ on 2008-04-03
Hi there,

I've got exactly the same problem. Actually it worked pretty well until yesterday, after I upgraded Ubuntu. Then the tray disappeared, and I couldn't start wicd anymore.
I removed it, reinstalled it again, same thing. Remove all the folders, all the configuration files, reinstalled again, same. Then I decided to reinstall network-manager-gnome instead, doesn't work neither...
I cannot use any wireless connection now, I got stuck :-/

Any idea?

---

### Post by _godbout_ on 2008-04-03
For my case, the problem was due to the Notification Area. I had to reinstall it, and then the wicd tray and gui worked again!

---

### Post by Cain67 on 2008-04-03
just wanted to say that yes, it worked. one of the files must have been corrupted. after uninstalling wicd via the package manager, i then removed the directory from /opt/ and reinstalled it, and now wifi is working flawlessly :)

thanks alot imdano!!!

---

### Post by _godbout_ on 2008-04-03
Hey, I just have a small question, not really related to wicd but the question came by reading this topic so... :D

If I do 
> 
sudo /etc/init.d/wicd start

it works

But if I go to the /etc/init.d folder, and then do a sudo wicd start it doesn't work, what's the reason for that??!!
I found that I can do sudo ./wicd start instead and it works, but I'm really wondering why...

---

### Post by _godbout_ on 2008-04-03
Ok, I've got the tray, I've got the key, but I can't connect anymore :/

---

