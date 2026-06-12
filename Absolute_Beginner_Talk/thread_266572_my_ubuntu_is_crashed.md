---
title: "my ubuntu is crashed"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-09-27
my ubuntu is crashed.it happened first time since i have been using ubuntu for half of year.what happens is illustrated below.

    ubuntu starts fine.works fine.does every job ireques.this happens for a short time almost 30 minutes or bit longer. after this it slowly slows down.my mouse pointer stops moving instantly.it responds to my motion almost after a minute or long. windows buttons become dead.clicking on it does nothing.terminal also becomes slow.even if i type a character ,it is displayed on it after a long time. then i reboot my pc by pressing cpu restart button.
my pc is 933Mhz intel 256Mb ram.

note this is first day of this problem.

---

### Post by pbaehr on 2006-09-27
Next time it happens, see if you can manage the patience and mouse wrangling to open up the terminal.

Type ```
top
``` and press enter.
This will show you which processes are consuming the most resources. Report back with the first few processes and what they're using and if that's the problem, we'll see if we can fix it.

Did you install anything or make any system changes immediately prior to this happening?

EDIT: By the way, press 'q' to exit top after you're done checking it out.

---

### Post by u04f061 on 2006-09-27
> **pbaehr said:**
> Next time it happens, see if you can manage the patience and mouse wrangling to open up the terminal.

Type ```
top
``` and press enter.
This will show you which processes are consuming the most resources. Report back with the first few processes and what they're using and if that's the problem, we'll see if we can fix it.

Did you install anything or make any system changes immediately prior to this happening?

EDIT: By the way, press 'q' to exit top after you're done checking it out.

ok. thanks for your reply. plz be with me.i will post this when it will happen. i havn't installed any software.but as far as i think a week ago i  installed edubuntu on a different partition. after the installation of edubuntu , i was unable to boot ubuntu. then i installed another ubuntu on the same partition where edubuntu was installed to restore grub. after that my old ubuntu was ok .running fine. this happened after a week i think.

---

### Post by pbaehr on 2006-09-27
What is the size of the partition Ubuntu is running from? Do you still have Ubuntu installed twice on two separate partitions or did you merge the partitions back together? Also, do you happen to know the size of your swap partition?

EDIT: By the way, you can check the size of your swap partition using the same command (top) which we used before. It will be on the line under your memory. It should idealy be about twice the size of your RAM.

---

### Post by u04f061 on 2006-09-27
> **pbaehr said:**
> What is the size of the partition Ubuntu is running from? Do you still have Ubuntu installed twice on two separate partitions or did you merge the partitions back together? Also, do you happen to know the size of your swap partition?

EDIT: By the way, you can check the size of your swap partition using the same command (top) which we used before. It will be on the line under your memory. It should idealy be about twice the size of your RAM.

my swap is 270MB.yes still i have two ubuntus running on different partitions. i can't remove any one of them because one contains my softwares and other contains grub.there is 1.9Gbof free space in ubuntu which crashes.and there is too much which contains ubuntu with grub

---

### Post by pbaehr on 2006-09-27
Sounds like kind of a screwy configuration. I don't know if it's the cause of the problem, but I'd try and consolidate it, anyway.

Let me know next time you have the problem and if any program is using an abnormal amount of resources.

---

### Post by u04f061 on 2006-09-28
yes. this pappened aagain. i typed the command top with too much difficulty.it gave some output which is below 

ejaz@msiddique:/usr/share/vim$ top

top - 00:02:22 up  5:00,  6 users,  load average: 1.81, 1.32, 0.87
Tasks:  88 total,   1 running,  86 sleeping,   0 stopped,   1 zombie
Cpu(s): 11.3% us,  3.3% sy,  0.0% ni, 85.0% id,  0.3% wa,  0.0% hi,  0.0% si
Mem:    255148k total,   240624k used,    14524k free,      736k buffers
Swap:        0k total,        0k used,        0k free,    55092k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 6367 ejaz      15   0 56632 9732 2632 S  5.0  3.8   0:38.62 gnome-terminal
 4218 root      15   0 96264  15m 2512 S  4.3  6.1  15:04.50 Xorg
 4766 ejaz      15   0 89268  18m 4576 S  1.3  7.4   3:28.04 nautilus
 7469 ejaz      15   0  278m  19m 1432 S  1.0  7.9   2:11.46 java
 4741 ejaz      15   0 27272 3044  964 S  0.7  1.2   0:11.38 gnome-settings-
 4829 ejaz      15   0 14760 1944  844 S  0.7  0.8   0:12.74 gnome-screensav
18413 ejaz      15   0 85604 7600 2752 S  0.7  3.0   0:53.21 d4x
 4788 ejaz      15   0 54048 2500 1004 S  0.3  1.0   0:03.84 gnome-cups-icon
15356 ejaz      15   0  3252  720  456 S  0.3  0.3   0:10.61 aria2c
18019 ejaz      15   0  134m  28m 1680 S  0.3 11.3   2:06.86 firefox-bin
20235 ejaz      16   0  2192 1096  856 R  0.3  0.4   0:00.16 top
    1 root      16   0  1568  256  184 S  0.0  0.1   0:02.30 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    3 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.27 events/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    8 root      10  -5     0    0    0 S  0.0  0.0   0:00.22 kblockd/0



after this i tried to close firefix and totem.it took me 15 minutes. and i was done with a bit struggle.then after closing firefox and totem alongwith home file browser so that only my terminal was working ,my system was back. its speed was back.so i think there is problem in gui application loading

---

### Post by pbaehr on 2006-09-28
Hmmm...good work.

I was hoping for something would really be standing out as a problem. When I was having problems with my system getting bogged down it was plain as day which process was to blame. In this case, nothing seems to easy to blame.

I'll keep thinking about it, though. Maybe someone else can take a look at what we've done so far and offer some insight.

Also, I believe if you reinstall grub on your main ubunutu partition it should take over as the main instance of grub on your system and you'll be able to remove the other partition.

---

### Post by u04f061 on 2006-09-28
> **pbaehr said:**
> Hmmm...good work.

I was hoping for something would really be standing out as a problem. When I was having problems with my system getting bogged down it was plain as day which process was to blame. In this case, nothing seems to easy to blame.

I'll keep thinking about it, though. Maybe someone else can take a look at what we've done so far and offer some insight.

Also, I believe if you reinstall grub on your main ubunutu partition it should take over as the main instance of grub on your system and you'll be able to remove the other partition.

i was thinking of somewhat like this(to install grub on main ubuntu). can u tell me how can i install grub on main ubuntu partition?

---

### Post by u04f061 on 2006-09-28
what do u thin about virus? is there any virus on my pc? however i have installed calm av and it is scanning my pc

---

### Post by pbaehr on 2006-09-29
I doubt it is a virus. It doesn't sound like it based on what you describe, and Linux is particularly well guarded against viruses to begin with.

I *believe*, and you may want to start a new thread to verify this before you continue, that if you remove grub and then reinstall it you will wind up with all the necessary files on your current partition and the portion of grub that lives in the mbr will update to load those at boot.

If it was my computer I would try
```

sudo apt-get remove grub
sudo apt-get clean
sudo apt-get update
sudo apt-get install grub

```
But, like I said, I'm not 100% sure this will work and since it's not my computer, I'm more reluctant to break it. I would check with someone else before you go ahead with that.

---

