---
title: "Troulble with IVTV installl on Dapper"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by dkenny on 2006-12-05
Guys
I am trying to install the IVTV drives (my first step on the wat to a MythTV install) and am having some issues.

I followed the Installation Instruction on [https://help.ubuntu.com/community/Install_IVTV_Dapper](https://help.ubuntu.com/community/Install_IVTV_Dapper)
and it seemed to work. i.e. it didn't throw any erros.

Then I tried to test it be running the follwoing command per 
[http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

> 
After this set of commands, if you execute

    ls -ltra /usr/lib/hotplug/firmware/

You should see

    drwxr-xr-x 3 root root 4096 2005-12-18 10:04 ..
    -rw-r--r-- 1 root root 262144 2005-12-23 20:05 ivtv-fw-enc.bin
    -rw-r--r-- 1 root root 262144 2005-12-23 20:05 ivtv-fw-dec.bin
    -r--r--r-- 1 root root 14264 2005-12-23 20:08 v4l-cx25840.fw
    -r--r--r-- 1 root root 376836 2005-12-23 20:08 v4l-cx2341x-enc.fw
    -rw-r--r-- 1 root root 155648 2005-12-24 13:33 v4l-cx2341x-init.mpg
    lrwxrwxrwx 1 root root 41 2006-01-03 00:40 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
    drwxr-xr-x 2 root root 4096 2006-01-03 00:40 .


But, when I run the command I get the following
> 
declan@main-desktop:~$ ls -ltra /usr/lib/hotplug/firmware/
total 400
drwxr-xr-x 3 root root   4096 2006-12-02 21:28 ..
-r--r--r-- 1 root root  14264 2006-12-02 21:36 v4l-cx25840.fw
-r--r--r-- 1 root root 376836 2006-12-02 21:37 v4l-cx2341x-enc.fw
drwxr-xr-x 2 root root   4096 2006-12-02 21:37 .
declan@main-desktop:~$


As you can see, I am only getting 4 of the 7 lines that should be there.
I have no idea how to fix this.
Anyone got a suggestion (and please be gentle - I'm a complete Noob at this)


Thanks

---

### Post by dannyboy79 on 2006-12-05
i was getting help from a user called superm1 and he helped me install the latest ivtv firmware and when I do a locate using one of the files, all my files are located within /lib/firmware/. they look like this:
ls -ltra /lib/firmware/
total 692
drwxr-xr-x  3 root root   4096 2006-09-15 12:52 2.6.15-26-686
drwxr-xr-x  3 root root   4096 2006-09-19 07:56 2.6.15-27-686
-rw-r--r--  1 root root 155648 2006-10-13 01:20 v4l-cx2341x-init.mpg
lrwxrwxrwx  1 root root     20 2006-11-16 19:03 v4l-cx2341x-init-mpeg.bin -> v4l-cx2341x-init.mpg
-rw-r--r--  1 root root 262144 2006-11-16 19:18 v4l-cx2341x-enc.fw
-rw-r--r--  1 root root 262144 2006-11-16 19:18 v4l-cx2341x-dec.fw
lrwxrwxrwx  1 root root     18 2006-11-16 19:19 ivtv-fw-enc.bin -> v4l-cx2341x-enc.fw
lrwxrwxrwx  1 root root     18 2006-11-16 19:19 ivtv-fw-dec.bin -> v4l-cx2341x-dec.fw
drwxr-xr-x  4 root root   4096 2006-11-16 19:19 .
drwxr-xr-x 20 root root   4096 2006-11-18 14:43 ..

did you try to do a "locate ivtv-fw-dec.bin" for the files you're missing? also, are you using the mythtv from the standard repo or the latest mythtv from superm1's repo? i would suggest pm'ing superm1, he is an expert with mythtv!

---

### Post by dkenny on 2006-12-05
I think I found the issue.

In the instructions on 

there is the following block

> 
cd utils
wget [ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip)
wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)
[B]unzip pvr_2.0.24.23035.zip 
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip[/B]
cp HcwMakoA.ROM /usr/lib/hotplug/firmware/v4l-cx25840.fw
cp HcwFalcn.rom /usr/lib/hotplug/firmware/v4l-cx2341x-enc.fw
mv /lib/modules/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/
mv /lib/modules/ivtv-fw-enc.bin /usr/lib/hotplug/firmware/
cp ../v4l-cx2341x-init.mpg /usr/lib/hotplug/firmware
ln -s /usr/lib/hotplug/firmware/ivtv-fw-dec.bin /usr/lib/hotplug/firmware/v4l-cx2341x-dec.fw 


The 2 lines that I have highlighed seem to be the problem. I can't get the send line to run - is this a run-on from the previous line? If so how do I run them?

---

### Post by dkenny on 2006-12-05
Can anyone explain how I would run these two lines in a terminal?

unzip pvr_2.0.24.23035.zip
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip

---

### Post by kakalaky on 2006-12-05
make sure you have a file named pvr_2.0.24.23035.zip and another named ivtvfwextract.pl in /usr/src/ivtv-0.4.4/utils/

```
ls /usr/src/ivtv-0.4.4/utils/
```

---

### Post by superm1 on 2006-12-06
The plan now is that all the necessary firmware is in the ivtv-firmware package that I assembled and am hosting at ivtvdriver.org.  You shouldn't need to extract the firmware yourself.  

As is currently, once you install ivtv firmware and the modules are built - you should be able to 

```
sudo modprobe ivtv
```

Check 
```
dmesg
```

and then see that everything loaded okay.

---

