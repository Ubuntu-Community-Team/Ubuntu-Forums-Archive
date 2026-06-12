---
title: "Problem Installing BPAlogin"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by Jordy on 2006-07-30
Hi,
I am very new to linux - 1st attempt... Installed Ubuntu 6.06 last thursday as dual boot with XPHome SP2, internet access via Bigpond Cable (Australia) and try as I might I can't get PBALogin to install. Have searched and followed all instructions I can find but somehow It all fails miserably.
I have follwed the advice in the thread "BPALogin & Bigpond Cable (Australia) but when I type "sudo ./bpalogin-2.0-linux-2.4.bin" into the terminal window, I get an invalid command error. The file resides in the "Desktop" folder, should I run it from elsewhere?
I have also tried to follow the BPALogon tutorial supplied by sourceforge.net but when trying to run "./configure" i get the message that a compiler cannot be found in $Path...
If you have any suggestions I will be forever greatful.
Also When I try to access my XP volumes I get the message that "pmount" has failed. Any ideas? it's frustrating having to burn all the downloads to disk first - at east it will be until I get my cable connection working...

thanks

Jordy

---

### Post by jordilin on 2006-07-30
when you do:
```
"sudo ./bpalogin-2.0-linux-2.4.bin"
```
the file bpalogin-2.0-linux-2.4.bin must have execution permissions:
type 
```
chmod +x bpalogin-2.0-linux-2.4.bin
```
and try again.

---

### Post by Jordy on 2006-07-30
Thanks for the help. Do I type this after "sudo ./" or just by itself?

---

### Post by jordilin on 2006-07-30
Firstly:
```
chmod +x bpalogin-2.0-linux-2.4.bin
```
Secondly:
```
"sudo ./bpalogin-2.0-linux-2.4.bin"
```

---

