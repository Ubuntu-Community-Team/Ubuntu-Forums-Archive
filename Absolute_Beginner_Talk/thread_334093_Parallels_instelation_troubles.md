---
title: "Parallels instelation troubles"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-01-08
Hi there,

I´m a little confused...

I´m busy installing Parallels and I got stuck at some point. Been reading on the forums and it seems there could be alternatives.

Can I install Windows in my Ubuntu machine using VMware player?

If not can some one please help me install Parallels. I have downloaded the app and installs fine. At the point where you have to configure parallels I get an error. Here is what I did:
> 

rudolf@rudolf:~$ sudo parallels-config


[: 141: ==: unexpected operator
     Compiling Parallels Workstation 2.2 drivers...
     Drivers have been compiled successfully.
/usr/bin/parallels-config: 175: pushd: not found
/usr/bin/parallels-config: 186: popd: not found
     Installing drivers...
     Starting drivers...
/usr/lib/parallels/autostart/drivers_start: 19: Syntax error: "(" unexpected
Parallels Workstation drivers were successfully configured
and compiled but cannot be started (insmod command failed).
Run 'dmesg' command for more information.
exit: 3: Illegal number: -1




Any help would be greatly appreciated!

Thanks,

Rudolf

---

### Post by RudolfMDLT on 2007-01-08
Please!

---

### Post by gjtoth on 2007-01-08
> **RudolfMDLT said:**
> Hi there,

I´m a little confused...

I´m busy installing Parallels and I got stuck at some point. Been reading on the forums and it seems there could be alternatives.

Can I install Windows in my Ubuntu machine using VMware player?

If not can some one please help me install Parallels. I have downloaded the app and installs fine. At the point where you have to configure parallels I get an error. Here is what I did:



Any help would be greatly appreciated!

Thanks,

Rudolf


You have to go into the scripts and change the first line to (or from -- can't remember exactly) /sh to /bash (or the other way around).  You'll still get one small error but it WILL run after you do a parallels-config.

---

### Post by RudolfMDLT on 2007-01-08
Here is the file


> #!/bin/sh

run="/usr/lib/parallels/parallels-linux $@"

if [ -e "/etc/linspire-version" ]; then
    aw=`which audiowrapper 2> /dev/null`
    if [ "$aw" -a -x "$aw" -a "`$aw 2> /dev/null | grep -c oss-native`" != 0 ]; then
        run="sh $aw --oss-native $run"
    fi
fi

eval $run

I changed the /bin/sh to /bin/bash

But I still get the same output. Thank you for your help!

---

### Post by RudolfMDLT on 2007-01-09
Anybody feeling board and know something about parallels? :rolleyes:

---

### Post by visik7 on 2007-01-09
run
```

for file in `dpkg -L parallels`; do head -n1 $file |grep "^#\!/bin/sh"; if [ $? -eq 0 ] ; then echo $file ; fi; done 2> /dev/null

```
these are files that needs to be modified
better than modified default sh that if it points do dash there is a reason :)

---

### Post by RudolfMDLT on 2007-01-09
> **visik7 said:**
> run
```

for file in `dpkg -L parallels`; do head -n1 $file |grep "^#\!/bin/sh"; if [ $? -eq 0 ] ; then echo $file ; fi; done 2> /dev/null

```
these are files that needs to be modified
better than modified default sh that if it points do dash there is a reason :)

Please explain the above, in detail if you have the time. I would really be thankfull if you could because I´m struggling to get the nitty gritty text base stuff! But thanks, I&#314;l try it tonight!

Thanks,

Rudolf

---

