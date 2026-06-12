---
title: "networking help plz"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by inmate#001 on 2006-08-15
i have a netgear wg111v2 adapter and have been trying to make it work on my linux comp and i found this post but i have no clue what to do do you enter the comands in terminal if so all i get is a comand not found error 
can somebody plz give me a step by step to get this working 
and one more question i want to use my linux computer like a bridge and have my windows computer hooked up to the ethernet card so i can access the network with that computer too

     [I]After a few day's pain on making NetGear WG111 v2 work on my laptop, I work out this problem today. Let's share the experience below:

# ndiswrapper -i netwg111.inf /*install the windows xp driver*/
# ndiswrapper -l /*check if it is installed*/

# modprobe ndiswrapper /*if works, you can see the light on*/

# ndiswrapper -m /*boot it as a module*/

# iwconfig wlan0 /*you can see some information about the setting*/
# iwlist wlan0 scan /*you can see some information about your AP*/

In my case, use 128 bits WEP

# iwconfig wlan0 essid ESSID key restricted XXXXXXXXXXXXXXXXXXXXXXXXXX

There is a trick on finding the key -- find it in the windows xp's registry database.
Anybody found "key restricted s:XXXXX" works? I can't use string as the key.

# dhcpclient wlan0

After it is done, the network is up. Now you can use "network-admin" to write the /etc/network/interfaces.

Have fun![/I]

---

### Post by siacs on 2006-08-15
Make sure you have ndiswrapper-utils installed.

---

### Post by inmate#001 on 2006-08-15
i installed ndiswrapper-utils but now when i run it i get an error that **says couldn't copy netwg111.inf at /usr/sbin/ndiswrapper line 135**. line 135 reads     
[B]copy("$inf", "$confdir/$driver_name/$driver_name.inf") or
      die "couldn't copy $inf";[/B]

---

### Post by inmate#001 on 2006-08-15
i have one more question regarding networking i was wondering if you can set linux up like a bridge so my other computer can access the internet and my home network

---

