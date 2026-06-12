---
title: "Trouble with Wireless Connection"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by USR612 on 2007-05-09
Hi,
I just installed Feisty within the last two days, and I'm having trouble connecting to the internet.  Ubuntu recognizes my wireless adapter, and I can see my default network that I use with all my windows computers, but I can't connect to it.
The part that makes this strange (at least for me) is the fact that I was able to access the internet for a while two days ago, but I have had no more luck since then.
I'm using a Linksys WUSB 54GC adapter, but I don't think this is the problem since ubuntu can see my network.
Any help would be greatly appreciated!
(I'm completely new to Linux so you'll have to be simple)

---

### Post by benanzo on 2007-05-09
I can't really picture what the problem would be, but we're going to walk through it in the terminal and have a look to see why NetworkManager isn't connecting.

Open a terminal and type
```
sudo killall NetworkManager
```

then you should see the little icon disappear from your status bar.

Now, in the same terminal type

```
sudo NetworkManager --no-daemon
```

that will start NetworkManager in the terminal and it will show everything it is doing.  you will see the icon reappear in your status bar.  try to connect to your network while watching that terminal for errors. If you close that terminal, the icon will go away again and NetworkManager will die.  To start NM without having to have the term open, just type

```
sudo NetworkManager
```

or log out and back in.

Have a look and see if you see anything that looks like errors etc.  You can post the output back here.

---

### Post by USR612 on 2007-05-09
What the ???
I just tried your tip, and after typing the 'NetworkManager --no-daemon', command I looked up to see if the icon was there, and noticed I was connected.
I'm not sure if this has anything to do with the command, however, as I recall, the last time I connected was also right after restarting into Ubuntu from the Vista partition.  I'll post what came up here (as I really don't have a clue what I'm looking for) and then try and find out if the commands aid me in connecting.

-Just tried to post the info and it would not let me kill Network Manger.  I'll reboot completely and try again.

---

### Post by USR612 on 2007-05-09
No doubt about it now, ubuntu connects fine after the computer has been restarted from the Vista partition, not that this is how I want to keep it.
when I ran the "NetworkManager' --no-daemon command it came up with 10 pages of what looks like a foreign language to me.  As is seemed to become somewhat repetitive, I'll just post the first page (still quite lengthy).


NetworkManager: <information>   wpa_supplicant(5977): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 39 35 31 2d 32 00 
NetworkManager: <information>   wpa_supplicant(5977): Cancelling scan request 
NetworkManager: <information>   wpa_supplicant(5977): WPA: clearing own WPA/RSN IE 
NetworkManager: <information>   wpa_supplicant(5977): Automatic auth_alg selection: 0x1 
NetworkManager: <information>   wpa_supplicant(5977): WPA: clearing AP WPA IE 
NetworkManager: <information>   wpa_supplicant(5977): WPA: clearing AP RSN IE 
NetworkManager: <information>   wpa_supplicant(5977): WPA: clearing own WPA/RSN IE 
NetworkManager: <information>   wpa_supplicant(5977): No keys have been configured - skip key clearing 
ioctl[SIOCSIWAUTH]: Operation not supported 
WEXT auth param 5 value 0x0 - NetworkManager: <information>     wpa_supplicant(5977): _set_drop_unencrypted 
NetworkManager: <information>   wpa_supplicant(5977): State: SCANNING -> ASSOCIATING 
NetworkManager: <information>   wpa_supplicant(5977): wpa_driver_wext_set_operstate: operstate 0->0 (DORMANT) 
NetworkManager: <information>   wpa_supplicant(5977): WEXT: Operstate: linkmode=-1, operstate=5 
NetworkManager: <information>   wpa_supplicant(5977): wpa_driver_wext_associate 
NetworkManager: <information>   wpa_supplicant(5977): Association request to the driver failed 
NetworkManager: <information>   wpa_supplicant(5977): CTRL_IFACE monitor send - hexdump(len=40): 2f 76 61 72 2f 72 75 6e 2f 4e 65 74 77 6f 72 6b 4d 61 6e 61 67 65 72 2f 77 70 61 5f 63 74 72 6c 5f 35 39 35 31 2d 32 00 

I'm not sure if the first few lines are here, if needed I can run the command again and get them.
The only lines farther down that jumped out at me were:

NetworkManager: <information>   wpa_supplicant(5977): Trying to associate with SSID 'default' 
ioctl[SIOCSIWMODE]: Device or resource busy 

NetworkManager: <information>   wpa_supplicant(5977): State: ASSOCIATING -> DISCONNECTED 

Thanks again for all the help!

---

### Post by USR612 on 2007-05-10
Just found out, ubuntu does not indefinately remain connented after restarting from the Vista partition.  I don't know if this helps though.
I really would like to solve this problem, any help is very appreciated!

---

