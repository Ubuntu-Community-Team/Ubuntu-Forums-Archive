---
title: "Dell 355 Bluetooth connection successful"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by uzd4ce on 2007-03-28
I was having problems with getting my Dell 355 (BCM2045) bluetooth module to be able to connect to my mouse, and wanted to post this as a reference for future Googlers.

I was receiving ```
sudo hcitool scan
Device is not available: No such device
```

and

```
hcitool dev
Devices:
```

The problem was not solved by the ```
hciconfig hci0 reset
``` fix, either.

After installing and uninstalling the Bluez utils many times, and browsing the web for hours trying to figure out what was wrong, I finally realized that all I had to do was cycle the radio with function-F2 and it magically came to life and a ```
sudo hidd --search
``` connected it to my mouse just fine.

Yeah, I know, I'm an idiot...

---

### Post by varaonaid on 2007-03-30
I'd love some tips on getting this working.  I have the same 355 bluetooth chip and went through all the steps shown above.  I tried to cycle it on with F2 like suggested but nothing happens.  Also getting the same "no device found" type of errors.  Any suggestions would be greatly appreciated.  Thanks in advance!

---

### Post by uzd4ce on 2007-03-30
Well, I might have spoken too soon.  While my main problem was that I was trying to get it to connect with the radio off, I've since rebooted and now cannot get it to connect again.

Now, when I do a scan, it seems like it's looking, but it won't find the mouse even when it's in pairing mode.

I'm going to look at it again tonight, and will post if I figure anything out.  Would appreciate any other advice also.

---

