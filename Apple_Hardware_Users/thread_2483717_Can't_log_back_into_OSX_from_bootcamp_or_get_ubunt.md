---
title: "Can't log back into OSX from bootcamp or get ubuntu to work now"
date: 2023-02-07
forum: Apple Hardware Users
---

### Post by rahulkohli82 on 2023-02-07
Hi  everyone. I made a bootcamp partition years ago, and use it  infrequently. Recently I installed Ubuntu on my iMac too. Anyway I can't  get to the mac boot loading screen to select which OS I want to load  up. It just keeps looping back to windows.

I can't even get into Ubuntu. If I could I could set the boot loader to try the loading Mac OS again.



**Tried: All with a usb keyboard**

Pram reset: With option, cmd + p + r but it doesn't work.

Boot menu: Holding down Option. doesn't work.

Checking for the Mac disk with paragon in windows and it's still there and hasn't been wiped or anything.

Tried logging into recovery mode with cmd + r, and also option + cmd + r

Trying to change boot disk with EasyUefi on Windows but there's nothing there on the list. 

Tried to change boot disk with bootcamp app on windows, but doesn't work. 

Tried to get into ubuntu with a USB installer but just logs me into windows and Ubuntu installer doesn't come up. 

Tried a different keyboard in a different USB slot. 



**My options**

I have access to another mac and also windows.



Thanks in advance.

---

### Post by gsahli on 2023-02-08
Sounds like you over-wrote the EFI boot partition, which OS X needs.
Read up on EFI boot:
[https://rodsbooks.com/refind/installing.html](https://rodsbooks.com/refind/installing.html)
[https://youtu.be/3xGoQogKH8c](https://youtu.be/3xGoQogKH8c)
[https://apple.stackexchange.com/questions/57597/how-to-fix-broken-efi-partition#:~:text=Try%20this:%201%20Back%20up%20drive%20on%20time,EFI%20error%20message%20no%20longer%20appears.%20More%20items](https://apple.stackexchange.com/questions/57597/how-to-fix-broken-efi-partition#:~:text=Try%20this:%201%20Back%20up%20drive%20on%20time,EFI%20error%20message%20no%20longer%20appears.%20More%20items)

---

