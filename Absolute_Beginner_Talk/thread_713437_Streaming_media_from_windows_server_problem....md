---
title: "Streaming media from windows server problem..."
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by upforthedownstroke on 2008-03-02
I recently installed Ubuntu Gutsy on my Thinkpad (love it!) and I've had few problems thus far. One issue that I've had is how I can stream music from my Windows Server 2003 system. I can access it via smb shares, but when I try to play it in Amarok, I get this message:

No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.
smb://mothership/D$/My Music/Pink Floyd/Dark Side Of The Moon/01 - Speak To Me , Breathe.mp3

How can I fix this?
I'm pretty sure I have the mp3 input plugin, among others...

---

### Post by ohzopants on 2008-03-19
The problem is that amarok doesn't (as far as I know) support the smb:// protocol.

If you want this to work you will need to mount the smb share directly.  Search the forums, there are plenty of good howtos for this.

However, make sure that you don't set it to mount automatically, since this will give you errors whenever you are not on your local network or if ever mothership is down.

---

### Post by OffAxis on 2008-03-19
Regarding the aforementioned how-tos...
[https://help.ubuntu.com/community/SettingUpSamba]("https://help.ubuntu.com/community/SettingUpSamba")
pay particular attention to the 'Mount Windows Shares Permanently' link, which goes here:
[https://help.ubuntu.com/community/MountWindowsSharesPermanently]("https://help.ubuntu.com/community/MountWindowsSharesPermanently")

PS. The title of this post is a little misleading; a stream is generally regarded as a data transmission or broadcast that you can tap into. This situation that you've detailed is more of a remote file access problem .

---

### Post by upforthedownstroke on 2008-03-20
thanks, I'll let you know how things turned out.

Edited 22:10
results:
I mounted the share per the instructions on the "Mount Windows Shares Permanently" tutorial and was able to access all my data through /mnt.

Thanks again.

---

