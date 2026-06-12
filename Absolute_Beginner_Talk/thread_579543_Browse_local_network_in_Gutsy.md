---
title: "Browse local network in Gutsy"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by tolremeno on 2007-10-18
I've got 3 or 4 computers at my office, and I want to be able to browse the shared files of the other computers. They run xp. They're just connected by a wireless router. There is no "server."

I seem to recall being able to do this OOTB in Feisty, but I can't for the life of me figure out how to do it in Gutsy. 

Any help? I'm sure there's an easy answer that I'm just missing.

---

### Post by mikeyphi on 2007-10-18
Perhaps if you install 'ntfs-config'  it might 'see' the other partitions?

---

### Post by tolremeno on 2007-10-18
Um, what? 

I'm talking about browsing a LAN, not browsing a windows partition. 

And gutsy comes with ntfs read/write OOTB.

---

### Post by lancest on 2007-10-18
Need to install Samba by going to **System/Administration/Shared Folders**. Then go to **Places/Connect to server** and click service type dropdown to choose **Windows Share** then put in IP addresses of Windows boxes several times. Haven't tried this on multiple computers but should work. Should see shares appear on desktop. File/Print sharing must be enabled on XP of course. Something like that for starters.

---

### Post by henkjan on 2007-10-18
I ran into a problem browsing my home LAN after upgrading to the 7.10RC. This may be firewall-related. For me the problem was exacerbated because I couldn't access the Firestarter GUI after the upgrade.

I don't know if it will help, but here are my posts on this [ [COLOR="Blue"][SOLVED] Network|Windows Network members no longer visible after 7.10RC upgrade[/COLOR] ]("http://ubuntuforums.org/showthread.php?t=577186")

---

### Post by tolremeno on 2007-10-18
Firestarter doesn't seem to be blocking it.

---

### Post by tolremeno on 2007-10-18
> **lancest said:**
> Need to install Samba by going to **System/Administration/Shared Folders**. Then go to **Places/Connect to server** and click service type dropdown to choose **Windows Share** then put in IP addresses of Windows boxes several times. Haven't tried this on multiple computers but should work. Should see shares appear on desktop. File/Print sharing must be enabled on XP of course. Something like that for starters.
Well, I figured you could do something like that, although I haven't tried it. But IP addresses aren't static, so this method wouldn't be perfect. And really, it should be able to browse the lan.

---

### Post by henkjan on 2007-10-18
When I ran **Firestarter,** It didn't initially show that anything was being blocked.

I went to the **Events** tab and clicked **Reload** (after going to **Places|Network**). That's when I saw that ports 137 (**Samba (SMB)**) and 32801 (**Sun-RPC portmap**) were being blocked. Enabling **Apply policy changes immediately** (in **Edit|Preferences**) and right-clicking a blocked entry for each port and selecting **Allow inbound service** cleared up the Windows Network browsing for me.

It sounds like this isn't your problem, but just in case...

PS I have **Samba** set up on my Ubuntu host also. I don't know if/how that plays into browsing the other devices (2 XP hosts and a NAS device) on my home LAN

---

### Post by tolremeno on 2007-10-19
Well, oddly enough, I've now got it so I can *see* the other computers on the network but cannot interact with them.

*sigh*

---

### Post by jimrz on 2007-10-19
> **tolremeno said:**
> Well, oddly enough, I've now got it so I can *see* the other computers on the network but cannot interact with them.

*sigh*

assuming you have already installed samba, check smb.conf and make sure that your "Workgroup" is the same on your ubuntu bax as the name of the workgroup/domain on the win boxes you are trying to share from. If not, from terminal:
```
sudo gedit /etc/samba/smb.conf
```
change the workgroup name to match win,save the file, re-start samba and you should be good

---

### Post by tolremeno on 2007-10-19
I tried that. I followed [this tutorial]("http://ubuntuforums.org/showthread.php?t=296668&highlight=vmware+printing+samba") for samba. 

I'm still not 100% sure what I did other than that and restarting several times (and restarting samba itself), but somewhere in there it started working somewhat. I can now access computers via their IP (which I assume will change from time to time, which will be a hassle). I can't access them through their names.

---

### Post by olavjunior on 2007-10-21
Tried doing it from linux with mounting a windows share as mentioned above, but then I was asked for a username and password... What shall I do?

---

