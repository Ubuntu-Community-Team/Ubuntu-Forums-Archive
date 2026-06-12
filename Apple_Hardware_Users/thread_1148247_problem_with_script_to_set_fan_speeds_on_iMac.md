---
title: "problem with script to set fan speeds on iMac"
date: 2009-05-04
forum: Apple Hardware Users
---

### Post by moviemaniac on 2009-05-04
**UPDATE: fugettaboutit! Just a minute after posting this I found out what the error was: I started the script with sh which doesn't support "let". Starting the script with "bash applesmc.sh" works and the script does its job!**

Hi guys,

I've always wanted to have a script that automatically sets the fan speeds (mainly the CPU fan speed) on my iMac 8,1 but I've never found the possibility to do this.

Yesterday I found a script based on one written by Joerg Mertin on the net by accident, edited it to match my particular needs but it fails to run.

I have a basic understanding of shell-programming (being mainly a web-developer) but I can't figure out the problem.

When I run the script I get the error:

```
root@klaus-imac:/home/klaus/Desktop# sh applesmc.sh
applesmc.sh: 224: Syntax error: "(" unexpected (expecting "}")

```

The piece of code in question:
```
###############################################################################
# Get's CPU Temperature. In dual-core env - returns max temp detected
# adjusted to only reflect core0 temp - removed calculations which temp is higher as I only get core0-temp
get_temp() {
    TEMP=`cat $CPU_CORE0`
    let DTEMP=($TEMP / 1000)
} # get_temp
```

line 224 is that one:
```
let DTEMP=($TEMP / 1000)
```

I have no idea on what's wrong here (the original vanilla script fails at this exact spot too so it's not my editing the script that broke something).

Could anyone point me in the right direction?
The full script is attached.

Cheers,
Klaus

---

### Post by moviemaniac on 2009-05-04
After some testing I changed the script to use both CPU and GPU readings. It seems to work pretty well when running as a daemon. I'll test it for a few days before choosing to run it as a daemon on system-startup.

---

