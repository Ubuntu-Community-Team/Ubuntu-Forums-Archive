---
title: "vsound: 2 problems in recording realaudio streams"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by hanzj on 2006-03-20
Am trying to get vsound working for some audio streams. I have come up with 2 problems:


[SIZE="3"]Problem 1[/SIZE]

I can't seem to get the *[COLOR="Red"]-a[/COLOR]*; *[COLOR="red"]--autostop=SEC[/COLOR]* function working.  Can you? If I can't do this autstop function, I have to manually shutdown the realplayer program in order for vsound to finish its job. If I don't shut down realplayer, vsound will contiune recording the silence.

When I do: ```
vsound realplay http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram
```it works fine.

But when I do ```
vsound --autostop=5 realplay http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram
```I get this printout:

> hanzj@ubuntu:~$ vsound --autostop=5 realplay http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram
About to start the application. The output will not be available
until the application exits.
/usr/local/bin/vsound: line 177: --autostop=5: command not found
Missing file ./vsound8193.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from
  the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to
  run vsound as root.
 - Vsound was not properly installed and hence won't work at all.


I tried ```
sudo vsound -autostop=5 realplay http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram
``` but running as root doesn't help.

My goal is to record a real audio stream that automatically stops recording when it reaches the end of the stream. I would like to record while I'm in bed sleeping. And if I simply use "vsound realplay http://www.foo.com/abc.rm" the recorded audio on my hard drive will be very very huge when I wake up 8 hours later.


[SIZE="3"]Problem 2[/SIZE]
I have tried to get vsound record multiple ram files in sequence, but it seems to discard previous files in the "meta file'

So for example in my home directory, I have a file called spurgeon.rm. Inside "spurgeon.rm" is simply the following:

> 
http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20060101.ram
http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20060108.ram
http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20060115.ram
http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20060122.ram
http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20060129.ram


I do ```
vsound -d realplay spurgeon.rm
```. When all 5 ram files have finished, i shut down realplayer. I then check out the vsound.wav file that vsound produced in my home directory. But, lo, it contains only the last ram file (chs20060129.ram). What solution do you propose?


Thanks for any light you may shed on either of the 2 problems.


By the way, I am using RealPlayer 10.0.5.756 for Linux and vsound-0.6.

---

### Post by Pragmatist on 2006-03-20
> Here are some the possible reasons :
- You are trying to record a stream (RTSP or PNM protocol) from
the internet. You will **need to use the --timing option**.

What happens if you try this:

```
vsound --autostop=5 --timing realplay http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram
```

---

### Post by hanzj on 2006-03-20
[QUOTE=Pragmatist]What happens if you try this:

```
vsound --autostop=5 --timing realplay http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram
```[/QUOTE]

It doesn't work. I get the following:
> hanzj@ubuntu:~$ vsound  --autostop=5 --timing realplay [http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram](http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram)
About to start the application. The output will not be available
until the application exits.
/usr/local/bin/vsound: line 177: --autostop=5: command not found
Missing file ./vsound28807.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.


---

### Post by Pragmatist on 2006-03-20
Well, lets eliminate some other possibilities.  Try running the same command but preface it with **sudo**

```
sudo vsound --autostop=5 --timing realplay http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram
```

---

### Post by hanzj on 2006-03-20
Here's the printout with the sudo added.

> hanzj@ubuntu:~$ sudo vsound --autostop=5 --timing realplay [http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram](http://boss.streamos.com/real/swn/oneplace/rm/chs/chs20051225.ram)
About to start the application. The output will not be available
until the application exits.
/usr/local/bin/vsound: line 177: [COLOR="Red"]--autostop=5: command not found[/COLOR]
Missing file ./vsound29202.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.


As I noted with the red color, vsound doesn't understand the option  --autostop=5, even when we are following the correct syntax based on the vsound help.

---

