---
title: "Ktorrent won't start..."
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by diggs on 2006-01-23
Hi there, I have been trying to get Ktorrent to work for a while now, it worked fine one day, but now it just won't open. I tried removing and then adding it, still nothing happen. Is it maybe running in the background? (like the system tray in windows maybe?) how would I find this out and ultimatly get it going again? 

Thanks!

P.S. all you slacker canadians out there better have voted today!

---

### Post by rudelerius on 2007-06-28
I am having the same problem.  My system froze once while downloading the torrent file.  When I rebooted, it said the files for the tracker could not be found and asked if I wanted to re-download them.  No matter what I selected, it would automatically crash KTorrent and it would close.  This happened to me again and now KTorrent won't start at all.  When I click the launcher, it slows down my entire system like it is trying to open, but never comes up.  I have to restart the system to clear it.  I'd love it if someone could help explain/fix this problem.

---

### Post by notwen on 2007-06-28
Hmm, not sure on what may be causing your system slow down, but I can help you see if it's running in the background.  Open up a terminal and type 
```
ps ux
```
The above command will give you a list of all running processes.  Once you locate kTorrent you can use
```
kill XXXX
```
XXXX being the process id of your kTorrent process.  As w/ any command in terminal you can look at it's man page for more info regarding that command.  Hope this helps you. =]

---

### Post by jamieh on 2007-07-17
Use another torrent app, BitTorrent is in the package manager waiting to be downloaded.

---

### Post by deadlikeoscar on 2007-07-17
I personally use Deluge as it is the best I have tried, so I haven't used Ktorrent in a while. Ktorrent didn't work with many of the private trackers I tested it with. Anyway, when I did use Ktorrent, if you closed it I'm pretty sure it minimized to the top right of your screen. Look by the clock for the Ktorrent icon. That *may* be your problem.

---

### Post by QCompson on 2007-07-18
rudelerius (and possibly diggs):

Try backing up your ktorrent user folder (located in /home/[YOUR USERNAME]/.kde/share/apps/ktorrent), and deleting the entire folder from that location; then start ktorrent.  You will lose all your settings and the torrent files that were loaded, but it might wipe the slate clean and eliminate whatever was causing the problem.

---

### Post by Hallvor on 2007-07-19
What happens if you type

> ktorrent

in a terminal?

---

### Post by gigabyt2k5 on 2007-10-03
> **QCompson said:**
> rudelerius (and possibly diggs):

Try backing up your ktorrent user folder (located in /home/[YOUR USERNAME]/.kde/share/apps/ktorrent), and deleting the entire folder from that location; then start ktorrent.  You will lose all your settings and the torrent files that were loaded, but it might wipe the slate clean and eliminate whatever was causing the problem.

This worked for me, I did have a rather large Torrent file downloading, and perhaps ktorrent would not come up til it had checked the files...

---

### Post by Mdakait on 2007-11-30
> **diggs said:**
> Hi there, I have been trying to get Ktorrent to work for a while now, it worked fine one day, but now it just won't open. I tried removing and then adding it, still nothing happen. Is it maybe running in the background? (like the system tray in windows maybe?) how would I find this out and ultimatly get it going again? 

Thanks!

P.S. all you slacker canadians out there better have voted today!

when u click ktorrent icon .. ktorrent loads up and in a sec disappears if thats the case then on yr top pannel see if u hav notification area if nt add it to pannel .. coz if u check system monitor and ktorrent is running then its running in background once u add noti area u cod maximize it again ..!! sorry if i am not clear :S if u dun understand i will try again its just that i am in a hurry
!!!

---

