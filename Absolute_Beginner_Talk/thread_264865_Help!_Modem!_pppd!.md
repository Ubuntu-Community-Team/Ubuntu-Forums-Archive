---
title: "Help! Modem! pppd!"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by someonedumb on 2006-09-25
Trying to get my modem working, I've used two different driver packages and they both have the same behavior so I'm thinking the error is in the pppd configuration somewhere.

The following log is from /var/log/messages, the first pppd attempt is with a valid password, the second is with an invalid password. The two connection attempts are identical as shwon by the log, can I conclude from this that the connection is dying before it even attempts to do authentication?

I cannot find anything in the setup program 'pppconfig' that looks like it could be the cause of this problem.

What kind of problem causes this behavior?

> Sep 24 23:15:39 localhost pppd[5297]: pppd 2.4.4b1 started by root, uid 0
Sep 24 23:15:40 localhost chat[5298]: abort on (BUSY)
Sep 24 23:15:40 localhost chat[5298]: abort on (NO CARRIER)
Sep 24 23:15:40 localhost chat[5298]: abort on (VOICE)
Sep 24 23:15:40 localhost chat[5298]: abort on (NO DIALTONE)
Sep 24 23:15:40 localhost chat[5298]: abort on (NO DIAL TONE)
Sep 24 23:15:40 localhost chat[5298]: abort on (NO ANSWER)
Sep 24 23:15:40 localhost chat[5298]: abort on (DELAYED)
Sep 24 23:15:40 localhost chat[5298]: send (ATZ^M)
Sep 24 23:15:40 localhost chat[5298]: expect (OK)
Sep 24 23:15:40 localhost chat[5298]: ATZ^M^M
Sep 24 23:15:40 localhost chat[5298]: OK
Sep 24 23:15:40 localhost chat[5298]:  -- got it 
Sep 24 23:15:40 localhost chat[5298]: send (ATDT2492701^M)
Sep 24 23:15:40 localhost chat[5298]: expect (CONNECT)
Sep 24 23:15:40 localhost chat[5298]: ^M
Sep 24 23:16:12 localhost chat[5298]: ATDT2492701^M^M
Sep 24 23:16:12 localhost chat[5298]: CONNECT
Sep 24 23:16:12 localhost chat[5298]:  -- got it 
Sep 24 23:16:12 localhost chat[5298]: send (\d)
Sep 24 23:16:13 localhost pppd[5297]: Serial connection established.
Sep 24 23:16:14 localhost pppd[5297]: Exit.
Sep 24 23:18:39 localhost pppd[5316]: pppd 2.4.4b1 started by root, uid 0
Sep 24 23:18:41 localhost chat[5317]: abort on (BUSY)
Sep 24 23:18:41 localhost chat[5317]: abort on (NO CARRIER)
Sep 24 23:18:41 localhost chat[5317]: abort on (VOICE)
Sep 24 23:18:41 localhost chat[5317]: abort on (NO DIALTONE)
Sep 24 23:18:41 localhost chat[5317]: abort on (NO DIAL TONE)
Sep 24 23:18:41 localhost chat[5317]: abort on (NO ANSWER)
Sep 24 23:18:41 localhost chat[5317]: abort on (DELAYED)
Sep 24 23:18:41 localhost chat[5317]: send (ATZ^M)
Sep 24 23:18:41 localhost chat[5317]: expect (OK)
Sep 24 23:18:41 localhost chat[5317]: ATZ^M^M
Sep 24 23:18:41 localhost chat[5317]: OK
Sep 24 23:18:41 localhost chat[5317]:  -- got it 
Sep 24 23:18:41 localhost chat[5317]: send (ATDT2492701^M)
Sep 24 23:18:41 localhost chat[5317]: expect (CONNECT)
Sep 24 23:18:41 localhost chat[5317]: ^M
Sep 24 23:19:13 localhost chat[5317]: ATDT2492701^M^M
Sep 24 23:19:13 localhost chat[5317]: CONNECT
Sep 24 23:19:13 localhost chat[5317]:  -- got it 
Sep 24 23:19:13 localhost chat[5317]: send (\d)
Sep 24 23:19:14 localhost pppd[5316]: Serial connection established.
Sep 24 23:19:15 localhost pppd[5316]: Exit.

---

### Post by deadgobby on 2006-09-25
[https://help.ubuntu.com/community/DialupModemHowto?highlight=%28pppd%29](https://help.ubuntu.com/community/DialupModemHowto?highlight=%28pppd%29)

---

### Post by zxee on 2006-09-25
I asked this at your other thread: Did you run 'pppconfig' and set up your dial up through that program? pppconfig will create the files you need to connect with. 
There are not a lot of people using dial up anymore-particularly developers so dial up can be troublesome.
Also try using 'pon' from a terminal to connect and post the output.

---

### Post by someonedumb on 2006-09-25
Yes, as I stated above my method of configuring is pppconfig. And to connect I have been using pon.

It was someone's suggestion (probably yours) in the other thread that got me using pppconfig.

Oh yeah, and to clarify my username and password are correct, and the phone number is right too. I'm using the connection right now in Windows XP.

---

### Post by someonedumb on 2006-09-25
I went over [https://help.ubuntu.com/community/DialupModemHowto?highlight=%28pppd%29](https://help.ubuntu.com/community/DialupModemHowto?highlight=%28pppd%29) again and found a command I missed before - plog. I had been relying on /var/log/messages.

This is a snippet of what plog had to say (its the same as var/log/messages except for one added line, this is that line and the lines above and below it):

> 
Serial connection established.
Couldn't set tty to PPP discipline: Invalid argument
Exit


---

### Post by maaronB on 2006-09-25
Have you looked at these two threads:
[http://ubuntuforums.org/showthread.php?t=198730&highlight=ltmodem](http://ubuntuforums.org/showthread.php?t=198730&highlight=ltmodem)
[http://ubuntuforums.org/showthread.php?t=93852](http://ubuntuforums.org/showthread.php?t=93852)

They both are about Lucent/Aegis Modems using the ltmodem.

The first stills seems like it might be active, so you might be able to get advice from people who have the same modem as you.

---

### Post by maaronB on 2006-09-25
Possibly relevent info from here:
[http://phep2.technion.ac.il/goldberg/post-install.html](http://phep2.technion.ac.il/goldberg/post-install.html)

edit /etc/wvdial.conf. Uncomment lines made idle by ; . Replace username, password and phone number by those supplied by your ISP (Internet Service Provider). Add the line Stupid Mode = yes

failed to authenticate? verify that there is no matching entry in /etc/ppp/chap-secrets. If you see your username and password in that file, comment the line with a leading # and retry. Warning: wvdial version 1.40 creates the line again, so use a more recent version.

modem has connected but ppp does not start. Look at the ppp log for the reason. Have you forgotten to add Stupid Mode = yes in your wvdial.conf?

---

### Post by maaronB on 2006-09-25
From: [http://pptpclient.sourceforge.net/howto-diagnosis.phtml#tty_einval](http://pptpclient.sourceforge.net/howto-diagnosis.phtml#tty_einval)


Couldn't set tty to PPP discipline: Invalid argument
Symptom: the following messages appear before connection is established:

```
Serial connection established.
Couldn't set tty to PPP discipline: Invalid argument
Hangup (SIGHUP)
```

Diagnosis: pppd has failed to change the pty over to run it in PPP mode. This may be because you have no ppp_async module built for your kernel. Most kernels are built with this already, but if you have customised your kernel you may not have built it.

Solution: rebuild your kernel with CONFIG_PPP_ASYNC set. While you are at it, you should set CONFIG_PPP as well, and both should be set to "m" so that they are built as modules. We've found they don't work compiled statically.

---

### Post by maaronB on 2006-09-25
Sorry to keep annoying you, this is the last post I promise.
going back through this thread.
[http://ubuntuforums.org/showthread.php?t=198730&highlight=ltmodem](http://ubuntuforums.org/showthread.php?t=198730&highlight=ltmodem)
you might try using your martian driver again.

make sure you remove the stock ltmodules   <---Clashes between two modules   can cause hangup
run martian_helper
setup wvdialconf with
Carrier Check = no   <--This is required on martian driver
Stupid Mode = yes

---

### Post by someonedumb on 2006-09-26
It turns out the problem was the ppp_async module. It was installed on my system already, I simply had to modprobe it. Once I did that I dialed up and pinged [www.google.com](www.google.com) sucessfully :D 
HOOOOORAY the modem finally works :) :) :)

You are my hero maaronB! Thanks a million!!

---

