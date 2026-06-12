---
title: "Ktorrent to write to different file partition"
date: 2006-12-17
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-12-17
I need to get KTorrent to save the file I want to download to my file partition (ext3) and also save its tempory files there. The partition isn't the one I've installed kubuntu on, but is a separate partition on the same harddrive that I use to store files on. I've tried going into settings and changing the settings but I get the following error :

Cannot copy /tmp/kde-oliver/ktorrent7qtIAb.tmp to /home/torrent.downloads/incomplete/tor0/torrent: Could not write to /home/torrent.downloads/incomplete/tor0/torrent.


I think this means that KTorrent doesn't have the permissions to write to this drive; does this mean I need to run KTorrent with sudo/as root? How would I do this? Thankyou :D

---

### Post by Bachstelze on 2006-12-17
No, you don't need to run KTorrent as root and it would be a *very* bad idea to do so. Just change permissions of the folder so you have access to it :

```
sudo chown -R oliver:oliver /home/torrent.downloads
sudo chmod -R 644 /home/torrent.downloads
```

---

### Post by tartarian on 2006-12-17
I did that and got this:

Cannot copy /tmp/kde-oliver/ktorrentKX5NJb.tmp to /home/torrent.downloads/incomplete/tor0/torrent: Access denied.
Could not write to /home/torrent.downloads/incomplete/tor0/torrent.

what now? I think i need to change that torrent.downloads and all its subfolders, but don't know how to do it! thankyou :D

EDIT: It's ok, i've sorted it. just checked the little box in properties>permissions that said 'apply to all subfolders and files' and it worked. Thankyou!

---

