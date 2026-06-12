---
title: "Mine Problems"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by djpupeikis on 2006-11-18
I have some problems. 
I'm beginner.

1. I need to deactive and active each time after boot mine Internet connection.  ](*,) 
I using personal computer, ADSL, just installed Ubuntu. On windows everything is OK.
**REMOWED A BIT, BECAUSE  IS RESOLVED**


2. Mine router is Intracom JetSpeed 520. I can't find any drivers to Ubuntu.
So I can't get conneted by USB, only LAN, but  LAN is using antoher computer. ](*,) 

3. **IS RESOLVED**


Thnx for help 


djpupeikis

---

### Post by localuser on 2006-11-18
> **djpupeikis said:**
> I just don't have permission to edit whose files. Even when I use terminal and use root

For each of the files that you can't edit as root, go to their directory and issue the following command

```
$ ls -l {filename}
```

Copy the output that you get for each file and repost.

---

### Post by djpupeikis on 2006-11-18
> **localuser said:**
> 
Copy the output that you get for each file and repost.

```

-rw-r--r-- 1 root root 245 Nov 18 12:31 interfaces

```

```

-rwxr-xr-x 1 root root 306 May 31 03:50 rc.local

```

---

### Post by localuser on 2006-11-18
> **djpupeikis said:**
> ```

-rw-r--r-- 1 root root 245 Nov 18 12:31 interfaces

```

How are you trying to edit the file?

Try this:

```
$ sudo gedit /etc/network/interfaces
```

---

### Post by djpupeikis on 2006-11-18
> **localuser said:**
> How are you trying to edit the file?


I tryed with File Explorer and just directly: /etc/network/interfaces](*,) 

Your suggestion worked to edit, but Boot Issue not working to me.

> **djpupeikis said:**
> 
1. I need to deactive and active each time after boot mine Internet connection. I found answer how to fix it: [https://help.ubuntu.com/community/ADSLPPPoE](https://help.ubuntu.com/community/ADSLPPPoE) (Boot Isses) but problem is: i can't fix it.
I just don't have permission to edit whose files. Even when I use terminal and use root( sudo -i).
I using personal computer just installed Ubuntu.

This Way dont helped.
To make mine connection working I need to do  2 steps after each reboot:

After reboot this is the view: [http://img294.imageshack.us/img294/5089/1uz5.png](http://img294.imageshack.us/img294/5089/1uz5.png)

1. [http://img294.imageshack.us/my.php?image=2lf9.png](http://img294.imageshack.us/my.php?image=2lf9.png) **Deactivate**
2. [http://img294.imageshack.us/img294/490/3du4.png](http://img294.imageshack.us/img294/490/3du4.png)   **Atcivate**

Help

---

### Post by djpupeikis on 2006-11-18
> **djpupeikis said:**
> 
3. Mine Mouse is Samsung AnyZen SMOP1340 and It doesnt working correcly, so I am using antoher computer usb mouse. I downloaded some drivers, but what drivers setup is only for windows ofcourse where are some sys files in package. From here: [http://www.anyzen.net/en2/c_drive_down.htm](http://www.anyzen.net/en2/c_drive_down.htm)


Quite strange, but mouse strated working correcly.

So left First and second problems.

Please help

---

### Post by djpupeikis on 2006-11-18
AnyOne?
Please help

---

### Post by djpupeikis on 2006-11-19
Hey, I dont want to creat new Thread, please answer here, any one.

---

### Post by localuser on 2006-11-19
> **djpupeikis said:**
> Hey, I dont want to creat new Thread, please answer here, any one.

If no one is helping on this thread, I really don't think they will be able to help on a new thread.  What you can do is post to the same thread every so often as you just did.  That will bump the thread to the top of the list and perhaps someone who can help will see it.

---

### Post by Jussi Kukkonen on 2006-11-19
> **djpupeikis said:**
> 2. Mine router is Intracom JetSpeed 520. I can't find any drivers to Ubuntu.
So I can't get conneted by USB, only LAN, but  LAN is using antoher computer. ](*,)

I'm not an expert on these, but that device is actually a ADSL modem... If you can't find a driver I suggest you buy a cheap switch/router and attach it to the modem. Then you can attach all your computers to the router with ethernet cables.

---

### Post by djpupeikis on 2006-11-20
> **Jussi Kukkonen said:**
> I'm not an expert on these, but that device is actually a ADSL modem... If you can't find a driver I suggest you buy a cheap switch/router and attach it to the modem. Then you can attach all your computers to the router with ethernet cables.

I know what I am saying, jetSpeed 520 is router and modem, it depends from configuration.

---

