---
title: "[SOLVED] Problems With Update Manager"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by mmmkile on 2007-12-05
Today I tried to update my computer using the Update Manager, and everything was running as normal. I had to install an update titled "tzdata". The installation of this package required my network-manager to be restarted. The system tries to restart the network-manager, but stops and gives me an error message about how it is unable to.
Any help will be appreciated and if you need more information, feel free to ask.

---

### Post by PmDematagoda on 2007-12-05
Could you please post the specific error that you got.

---

### Post by mmmkile on 2007-12-05
Never mind, I fixed the problem. I was just about to delete this thread. Thank you anyways and Happy Holidays.

---

### Post by PmDematagoda on 2007-12-05
> **mmmkile said:**
> Thank you anyways and Happy Holidays.

No problem, and same to you:).

---

### Post by TrioTorus on 2007-12-06
So, how did you solve this problem? I'm in the same situation. I can't install an update and get: ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```I tried that, but the computer hangs, I have to cold reboot.
The dpkg.log shows a half installed Network Manager:
```


2007-12-05 09:56:16 configure network-manager 0.6.5-0ubuntu16.7.10.0 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status unpacked network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status unpacked network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status unpacked network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status unpacked network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status unpacked network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status half-configured network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 11:27:51 startup packages configure
2007-12-05 11:27:51 configure network-manager 0.6.5-0ubuntu16.7.10.0 0.6.5-0ubuntu16.7.10.0
2007-12-05 11:27:51 status half-configured network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 11:45:29 startup packages configure
2007-12-05 11:45:29 configure network-manager 0.6.5-0ubuntu16.7.10.0 0.6.5-0ubuntu16.7.10.0
2007-12-05 11:45:29 status half-configured network-manager 0.6.5-0ubuntu16.7.10.0

```

---

### Post by vikramsharma on 2007-12-06
> **TrioTorus said:**
> So, how did you solve this problem? I'm in the same situation. I can't install an update and get: ```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```I tried that, but the computer hangs, I have to cold reboot.
The dpkg.log shows a half installed Network Manager:
```


2007-12-05 09:56:16 configure network-manager 0.6.5-0ubuntu16.7.10.0 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status unpacked network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status unpacked network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status unpacked network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status unpacked network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status unpacked network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 09:56:16 status half-configured network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 11:27:51 startup packages configure
2007-12-05 11:27:51 configure network-manager 0.6.5-0ubuntu16.7.10.0 0.6.5-0ubuntu16.7.10.0
2007-12-05 11:27:51 status half-configured network-manager 0.6.5-0ubuntu16.7.10.0
2007-12-05 11:45:29 startup packages configure
2007-12-05 11:45:29 configure network-manager 0.6.5-0ubuntu16.7.10.0 0.6.5-0ubuntu16.7.10.0
2007-12-05 11:45:29 status half-configured network-manager 0.6.5-0ubuntu16.7.10.0

```

All you have to do is to run 'sudo dpkg --configure -a' in the Terminal

---

### Post by TrioTorus on 2007-12-06
I had tried that before, but now it went ahead. Strange. Maybe a previous 'apt-get clean' helped. Solved now. Thanks.

---

