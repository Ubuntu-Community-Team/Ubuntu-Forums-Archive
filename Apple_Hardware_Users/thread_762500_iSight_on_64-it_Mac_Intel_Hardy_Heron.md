---
title: "iSight on 64-it Mac Intel Hardy Heron"
date: 2008-04-22
forum: Apple Hardware Users
---

### Post by guj4_n3b3sk4 on 2008-04-22
Need step by step guide to set up iSight on 64-bit Intel Macbook with Hardy Heron on it.

(if moderators see this thread inapropriate, remove it)

Thank You.

---

### Post by cyberdork33 on 2008-04-22
> **guj4_n3b3sk4 said:**
> Need step by step guide to set up iSight on 64-bit Intel Macbook with Hardy Heron on it.

(if moderators see this thread inapropriate, remove it)

Thank You.
Get isight-firmware-tools:
[http://launchpadlibrarian.net/12950675/isight-firmware-tools_1.2-0ubuntu0%7Eppa1_amd64.deb](http://launchpadlibrarian.net/12950675/isight-firmware-tools_1.2-0ubuntu0%7Eppa1_amd64.deb)

---

### Post by guj4_n3b3sk4 on 2008-04-22
I am Ubuntu begginer. I have download it, what next? Sorry, but that's why I wrote step by step.

---

### Post by cyberdork33 on 2008-04-22
> **guj4_n3b3sk4 said:**
> I am Ubuntu begginer. I have download it, what next? Sorry, but that's why I wrote step by step.
double click the file to install it.

---

### Post by guj4_n3b3sk4 on 2008-04-22
I have instaled that, rebooted system, and nothing. Neither ekiga or Skype recognizes my webcam. What next?

---

### Post by cyberdork33 on 2008-04-22
> **guj4_n3b3sk4 said:**
> I have instaled that, rebooted system, and nothing. Neither ekiga or Skype recognizes my webcam. What next?
ok. did you point it to your iSight Firmware? you should have a file named isight.fw in /lib/firmware. If not you will have to extract it manually. from the AppleUSBVideoSupport file found on your Mac partition.

```
sudo ift-extract --apple-driver AppleUSBVideoSupport
```

[http://bersace03.free.fr/ift/](http://bersace03.free.fr/ift/)

---

### Post by guj4_n3b3sk4 on 2008-04-22
I have extracted it and isight.fw appeared. But still when I go to video devices in Skype or Ekiga on devices still writes: no devices found.

PS: I have set on Gutsy iSight cam and that setting was saved in one folder. After I have upgraded it to Hardy I've put that folder into trash, but trash won't empty. In that folder there's one folder called against-revision-140 and inside that folder there's one folder called src and it's empty. Dunno if there's something hidden, but when I try to empty my trash this appears:

There was an error deleting uvcvideo.mod

If it has to do anything with that, there's an info, and also how do I empty my trash?

Thank you for further steps.

---

### Post by cyberdork33 on 2008-04-22
> **guj4_n3b3sk4 said:**
> I have extracted it and isight.fw appeared. But still when I go to video devices in Skype or Ekiga on devices still writes: no devices found.

PS: I have set on Gutsy iSight cam and that setting was saved in one folder. After I have upgraded it to Hardy I've put that folder into trash, but trash won't empty. In that folder there's one folder called against-revision-140 and inside that folder there's one folder called src and it's empty. Dunno if there's something hidden, but when I try to empty my trash this appears:

There was an error deleting uvcvideo.mod

If it has to do anything with that, there's an info, and also how do I empty my trash?

Thank you for further steps.
it is because the permissions on the file do not let a normal user to delete it. look in ~/.Trash and you can delete it with sudo.

On that note, however, if you have used that installer, it replaces the version of uvcvideo that comes with Ubuntu and may be the source of the problem you are having.

---

### Post by mabovo on 2008-04-22
Does anybody have isight working with ift 0.2 and hal ?

---

### Post by guj4_n3b3sk4 on 2008-04-22
I have deleted that folder from my trash, installed that package you have sent me link to, rebooted macbook, and nothing again. None of programes is detecting my iSight cam.

UH!!! Dunno why is this so complicated and why isn't working, I remmember setting iSight on Gutsy in notime.

If anyone can help me (if I need to copy something from shell, anything... just say), I'd be grateful.

Thank You.

---

### Post by cyberdork33 on 2008-04-22
> **mabovo said:**
> Does anybody have isight working with ift 0.2 and hal ?
You should be using IFT 1.2

Sorry I don't know what else to tell you. IFT seems to be working for you since it is saying the firmware is loaded.

---

