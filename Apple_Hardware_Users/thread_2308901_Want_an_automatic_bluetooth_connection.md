---
title: "Want an automatic bluetooth connection"
date: 2016-01-06
forum: Apple Hardware Users
---

### Post by cduston on 2016-01-06
Running Xubuntu 14.03 on a MacBook Pro. In order to get my bluetooth speaker connected and working, I need to perform the following steps:

1) Turn on the speaker (appears in bluetooth device list, but not in sound device list)
2) Run the command ```
pactl load-module module-bluetooth-discover
```
3) Open bluetooth connections and run the setup assistant. Choose A2DP Sink, and the connection becomes active (now appears in sound device list).
4) Goto Volume Control, Output Devices, and set the bluetooth speaker as Fallback. (whatever this means exactly, there is a green check mark, currently on my internal speakers, which I then switch over to the bluetooth).
5) Now I click play on something (say Amazon streaming) and the sounds comes through the speaker. The volume controls on the keyboard work as well, which is cool.

The behavior I would like is to default to the bluetooth speaker whenever I turn it on. It seems like this might be possible, since it shows up in the bluetooth menu as soon as I turn the power on, but I need to load the module, manually make the connection, and also set it to default (fallback?). Anyone have a suggestion?

---

### Post by howefield on 2016-01-06
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by cduston on 2016-01-06
> **howefield said:**
> Thread moved to the "*Apple Hardware Users*" forum.

If you think it should be moved, then ok, but I should just point out that as soon as I turn on the speaker, it appears in the bluetooth menu, so the hardware seems to be working as intended. I assumed this was a software issue - I need to load the module and default to the speaker when the speaker appears in the bluetooth menu.

---

