---
title: "Bug Reporting at Every Log In"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by wiseguy1515 on 2007-11-02
Every time I log in to Ubuntu,the but reporting tool pops up saying that it has information on the Deskbar application crash. However nothing seems to have crashed and deskbar works just fine. This happens every single time. Any ideas?
Here's the crash report:

Distribution: Ubuntu 7.10 (gutsy)
Gnome Release: 2.20.0 2007-09-17 (Ubuntu)
BugBuddy Version: 2.18.1

System: Linux 2.6.22-14-generic #1 SMP Sun Oct 14 21:45:15 GMT 2007 x86_64
X Vendor: The X.Org Foundation
X Vendor Release: 10300000
Selinux: No
Accessibility: Disabled
GTK+ Theme: Human
Icon Theme: Human

Memory status: size: 0 vsize: 0 resident: 0 share: 0 rss: 0 rss_rlim: 0
CPU usage: start_time: 0 rtime: 0 utime: 0 stime: 0 cutime:0 cstime: 0 timeout: 0 it_real_value: 0 frequency: 0



----------- .xsession-errors (7 sec old) ---------------------
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6e7820: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/utz/.evolution/tasks/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x6ed330: Received at thread 42845950
alarm-queue.c:2003 (alarm_queue_add_async) - 0x6e3b00
alarm-queue.c:581 (load_alarms_for_today) - From Fri Nov  2 15:56:45 2007
 to Fri Nov  2 15:56:45 2007
alarm-queue.c:518 (load_alarms) 
alarm-queue.c:547 (load_alarms) - Setting Call backs 
alarm-notify.c:337 (alarm_msgport_replied) - 0x6ed330: Replied to GUI thread
alarm-notify.c:393 (cal_opened_cb) file:///home/utz/.evolution/memos/local/system - Calendar Status 0
alarm-queue.c:2052 (alarm_queue_add_client) - Posting a task
alarm-notify.c:349 (alarm_msg_received) - 0x6eb240: Received at thread 42845950
ala
--------------------------------------------------
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/deskbar/core/CoreImpl.py", line 314, in on_module_initialized
    self._history.load()
  File "/usr/lib/python2.5/site-packages/deskbar/core/DeskbarHistory.py", line 113, in load
    saved_history = cPickle.load(file(HISTORY_FILE))
EOFError

---

### Post by wiseguy1515 on 2007-11-03
Anyone have any ideas?

---

### Post by uflo on 2007-11-05
Since a few days I have the same problem with same error message. Also my sound seems to be defect - may be the same cause?

florian

---

