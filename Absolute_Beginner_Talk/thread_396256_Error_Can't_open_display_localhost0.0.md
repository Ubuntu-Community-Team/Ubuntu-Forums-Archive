---
title: "Error: Can't open display: localhost:0.0"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by abcuser on 2007-03-29
Hi,

I think something is wrong configured with x-windows. Running several applications all of them return "diplay" error. For example running: "xcalc" (without quotes) I got error:
Error: Can't open display: localhost:0.0

I was trying to set display variable:
export DISPLAY=my_ip_adress:0.0

Then the error is:
Error: Can't open display: my_ip_address:0.0

Any help would be appreciated. I have been googlin the web for three hours and no success.
Thanks,
Abcuser

---

### Post by abcuser on 2007-03-29
Hi,
I forgot to write I am using Ubuntu Linux 6.10 Desktop Edition on x86 (Intel box).
Thanks,
Abcuser

---

### Post by ceeg on 2007-03-29
You can try the following:

Add localhost to the X server's list of connectables
```

sudo xhost + localhost

```

Update DISPLAY (as you, not root):
```

export DISPLAY=localhost:0

```

---

### Post by abcuser on 2007-03-30
Hi,
thanks for help. BTW, I have reinstalled the Ubuntu because of problem [Ubuntu can't start: Failed to start the X server](http://www.ubuntuforums.org/showthread.php?t=396894&highlight=abcuser) and this "can't open display" problem disappeared. Thank goodnes reinstalling makes miracles. :)
Thanks,
Abcuser

---

### Post by abcuser on 2007-04-02
Hi,
after few days the problem reappeared. I have executed:
```
sudo xhost + localhost
```
and then 
```
export DISPLAY=localhost:0
```
but after executing command: ```
xcalc
```
I get error: "Error: Can't open display: localhost:0"

How to fix this problem? Why has this problem reappeared?
Thanks,
Abcuser

---

### Post by pdk on 2007-04-12
xauth -list will tell you the hosts allowed to connect.
I have problems connecting to a sun box, so I have not solved all the settings.
I can set the display to :0.0 and hostname/unix:0
DISPLAY=0:0
export DISPLAY
You can set the display when you becomming root to :0.0
localhost:0 does not work , why ??? I do not know.
Peter

---

### Post by abcuser on 2007-04-15
pdk, as I see "localhost" doen't work it should be only "local".

I have now successfully run xcalc and all other X-Windows programs. As I see each new system user needs to be configured separetly.

So I did the following:
1. Export DISPLAY variable:
```
export DISPLAY=:0
```

2. Asign x-host privileges:
```
xhost local:db2inst1
```Assuming db2inst1 is a user I would like to asign xhost privileges.

3. Run x-window program:
```
xcalc
```


I have found the above solution at official IBM DB2 forum in thread [Ubuntu 6.10 and DB2 Express-C](http://www-128.ibm.com/developerworks/forums/dw_thread.jsp?message=13915464&cat=19&thread=150513&treeDisplayType=threadmode1&forum=805#13915464).

BTW, DB2 Express-C is free of charge (not open source) IBM database to use on Windows and Linux x86 (also x64) systems.
Abcuser

---

