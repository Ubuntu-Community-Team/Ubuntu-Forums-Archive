---
title: "How to configure internet connection..."
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by Evergrey on 2006-10-15
I have Thompson Speedtouch 530 DSL modem.

Does anyone know how to configure my connection and be able to see when internet is active (something like miniature computer icon in system tray (Windows), and be able to disconnect at any time?
I forgot how I configured internet in the first place... 
I entered ppoeconf or something in terminal. ](*,)

---

### Post by adwait on 2006-10-15
You must have used
```
sudo pppoeconf
```

After the connection is setup, you can use
```
sudp pon dsl-provider
``` to connect and 
```
sudo poff dsl-provider
``` to disconnect

jonrkc is right, I stand corrected.

---

### Post by jonrkc on 2006-10-15
You may find you have to enter "sudo pon provider" to get the pon command to work--despite what the manual page says.

It used to be that "sudo pon" by itself would turn the connection (back) on, but since moving to Dapper I've had to use the argument with it.

I made it a bit simpler by copying the file /etc/ppp/peers/provider to /etc/ppp/peers/isp and now I can type "sudo pon isp" instead of "sudo pon provider".

Apparently if you do away with the file "/etc/ppp/pppoe_on_boot" you can then just type "sudo pon" and get connected.  The manual indicates that if this file is present, the argument given in it determines what file is used with "pon" to make the connection.  Since I figured some of the other stuff in the file(s) in question might be necessary or desirable, I just copied the filename given above to a little simpler one.  

I know that doesn't sound too clear, but it's what I had to figure out and do.  Why it all got changed with Dapper, I have no idea.

---

