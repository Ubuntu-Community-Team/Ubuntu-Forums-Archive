---
title: "how to identify a memory leak"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by CareySchug on 2007-12-24
I have a memory leak, and it seems to be getting worse, or I now have more than one.

I used to run Ubuntu, had no problems.   Discovered Kubuntu had a better system load monitor (would show what was used at nice 15 by boinc) so switched to that. Either immediately or shortly after, I had a slight memory leak, had to reboot every 7-10 days as the swap file became full.

I thought the problem might be boinc (the @home series) so I didn't run it for a week, but still had the leak.

I thought the problem was firefox, so I tried to use it less.

but still, now the swap file gets filled after 18-36 hours.  I can come up to my computer after having been away and see several step increments in the swap file while it was idle (except for boinc).

I still run ubuntu on my fileserver, which is only serving via ftp at the moment (I never could get filesharing working), and it stays up for many weeks with no problems.  i don't run thunderbird but do run boinc there).

My kubuntu was 6.06LTS and was current as of yesterday on updates.

How do I identify what is filling swap?

How do I go back to ubuntu?  I switched to kubuntu after a hard disk crash so that was a clean install.  I would like to go back keeping my files and as much as possible of what I have installed (not a lot, because I don't remember what I did to find and install them.

Below is the first few lines of tht top command, and everything that was significant in the VIRT column.  I have 640 M of ram, so that seems to pretty much match up.

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
13571 carey     39  19  172m  87m   20 R 62.9 13.9 170:29.61 rosetta_beta_5.
 4685 root      15   0  212m 124m 3880 S 11.9 19.7  79:55.34 Xorg
 4872 carey     16   0 30360  14m  12m S  9.3  2.3  63:26.11 ksysguard
 4867 carey     15   0  131m  79m  21m S  8.3 12.5  22:24.03 konqueror
 5434 carey     25  10  127m  21m  14m R  2.6  3.5  37:17.40 nspluginviewer

ps either my sound card failed or kubuneu forgot how to talk to it, I think sound worked at first, but doesn' t any moer, and I did nothing to change it.

---

### Post by dnvikram on 2007-12-24
Filling up swap...This is a bad thing for any machine.It directly signals to severe performance issue.Top will just show you what process is consuming how much mem or cpu time.If you want to dig deep ,then use the ,"strace" utility to trace from the system call levels.Run strace on the pid from the below line from the top output or run strace on the pid which is being used by bionic,which you referred to.Also check the system logs to see if we can find anything.

**13571** carey 39 19 172m 87m 20 R 62.9 13.9 170:29.61 rosetta_beta_5.

strace should give some pointers as to at what the pid or process is hogging memory and ultimately causing swapping.

Do let Me know.Can you also let Me know the size you alloted to swap partition.Is it atleast 1400MB?

Below is a link to help you with setting up strace:
[https://wiki.ubuntu.com/Strace](https://wiki.ubuntu.com/Strace)

Hope you find this info helpful.

---

### Post by jeffus_il on 2007-12-24
An Easy graphical way to go is to use the Gnome System Monitor.
Run it in the processes view, add to the view columns virtual and resident memory and any others that may interest you, click on the top of the virtual column to sort and see the biggest virtual memory hogger at the top.

---

### Post by jeffus_il on 2007-12-24
Sorry, you use KDE, Can you find the KDE process Monitor?

---

### Post by argie on 2007-12-24
To switch to kubuntu from ubuntu:
```
sudo aptitude install ubuntu-desktop
```

However, this will retain all your kde applications too. And the boot splash will probably change.

---

### Post by SOULRiDER on 2007-12-24
You can use KSysGuard to see all your processes and the ammount of memory theya re using. I only had problems with memory leaks in Azureus AFAICR.

---

### Post by dnvikram on 2007-12-25
Everyone seems to be giving the redundant answers asking the poster to check the system monitor in kde or gnome and there is no need to switch to kde just for the kde-monitor.system monitor only shows the top resource hogger.But ,the poster needs to know deeper than that and for that strace  tool needs to be run on the problematic pid or the resource hogging pid which is identified through top or the system monitor.

Please use strace to investigate the problem pid.

---

### Post by lamalex on 2007-12-25
and just for completeness, regardless of your desktop environment, you can use top.
```
user@host:~$ top
```

---

