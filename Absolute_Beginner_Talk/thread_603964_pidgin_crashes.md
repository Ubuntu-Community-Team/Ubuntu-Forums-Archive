---
title: "pidgin crashes"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by tast01 on 2007-11-05
When I start pidgin up it loads in the taskbar, then crashes and exits.  I never see my buddy list, it crashes before. Anyone else notice this?

---

### Post by Crafty Kisses on 2007-11-06
> **tast01 said:**
> When I start pidgin up it loads in the taskbar, then crashes and exits.  I never see my buddy list, it crashes before. Anyone else notice this?

Post the following output:
```
top
```

---

### Post by Call-Me-Kenneth on 2007-11-06
I'm having the same problem...


i tried that top command and it shows the pidgin task even when its not on the task bar anymore, problem is i don't know how to dump all that info (i could only see the pidgin process when i resized the terminal)

BTW... it started happening this morning on its own, i tried updating the system and uninstalling/installing pidgin...


bye, and thanks for any help.

---

### Post by sneezymelon on 2007-11-06
My pidgin starts normally but I have problem sharing files on it.

Any suggestions??

---

### Post by rboliver on 2007-11-06
Hi all,

Picking up on what Codename requested, I have the exact same problem, Pidgin starts and then crashes after showing the contact list for a few or several seconds. I have Ubuntu Gutsy and the latest updates (system and Pidgin). The result for the top command is:

rubens@vanilla-laptop:~$ top

top - 10:14:53 up  1:51,  2 users,  load average: 0.22, 0.16, 0.07
Tasks: 138 total,   1 running, 137 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.0%us,  0.3%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1025984k total,   914088k used,   111896k free,    90912k buffers
Swap:   979924k total,        0k used,   979924k free,   575684k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5592 root      15   0 38240  21m 7772 S    5  2.2   2:35.23 Xorg               
 2189 root      10  -5     0    0    0 S    1  0.0   0:02.82 scsi_eh_0          
 6022 rubens    17   0 60412  24m  18m S    0  2.5   0:07.86 gnome-panel        
 7371 rubens    15   0 72088  20m  11m S    0  2.0   0:03.15 gnome-terminal     
 7783 rubens    15   0  2368 1176  876 R    0  0.1   0:00.32 top                
 7791 rubens    15   0 72100  23m  15m S    0  2.3   0:00.91 pidgin             
    1 root      18   0  2948 1852  532 S    0  0.2   0:01.92 init               
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      10  -5     0    0    0 S    0  0.0   0:00.01 events/0           
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1           
   11 root      10  -5     0    0    0 S    0  0.0   0:00.01 khelper  

When I run as root (but using my settings) it runs longer but crashes due to this error:

(09:43:42) GLib: /build/buildd/glib2.0-2.14.1/glib/gmem.c:135: failed to allocate 1711341569 bytes
Cancelado (core dumped)

Any ideas? I want to use Pidgin but I'm tired of crashing and burning.

Thanks, Rubens.

---

### Post by Call-Me-Kenneth on 2007-11-07
it's working now...


didn't do much... just rebooted. now it just looses connection every 5 mins. xD

tried another client just to check if it wasn't my connection, it works fine... to bad, i liked pidgin. :(

---

### Post by sentientmachine on 2008-05-28
pidgin 2.4.1 running on Fedora 8...  Pidgin crashes during startup of pidgin (gaim).  What worked for me was clearing out the auto-login settings for pidgin:

1.  go to /home/yourusername/.purple
2.  login as root
3.  look for a file, mine was named accounts.xml  it contains auto login information and plaintext passwords (shame on pidgin).
4.  rename the file.   mv accounts.xml  accountsOld.xml
5.  restart pidgin.  You will be prompted to re-setup the login usernames and passwords and custom away message settings.

---

