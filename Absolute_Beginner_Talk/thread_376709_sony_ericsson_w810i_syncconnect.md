---
title: "sony ericsson w810i sync/connect"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by jvc26 on 2007-03-05
Hey there all just a brief question has anyone had any luck with connecting the w810i to an ubuntu box? I havent had any real need to sync them up but it would be nice to be able to do so - I get absolutely no response from the box when I plug my phone in - does that mean that its a no-go? What is the process to go about getting it hooked up - even some links would be helpful as google has thrown up absolutely nothing. Thanks for any help,
Il

---

### Post by SurR3AL on 2007-03-12
check [this]("http://stefans.datenbruch.de/k750i/#usbcable") out mate....dono how helpful it'll be

---

### Post by Sweet Spot on 2007-03-12
Mine is doing it RIGHT NOW. :)

But unfortunately, there are some issues which I've experienced while transferring files, from time to time. Transferring ringtones (after I've edited w/Audacity) or theme files works fine USUALLY, but at times I get corrupted files, and I'm not sure why it happens. I also had issues with songs that I've deleted playing back in the middle of a song (which gets cut off and replaced w/said deleted file). I think this was solved by deleting the entire trash and root trash folder from within the sudo apt-get nautilus browser. 

But for all intents and purposes, syncing works just fine.

---

### Post by jvc26 on 2007-03-16
Sweet Spot: Did your phone get recognised as soon as you plugged in the USB Cable? Mine doesn't even recognise, which is odd presuming yours did instantly.
Il

---

### Post by ahmatti on 2007-03-16
I can transfer files with my W800i with bluetooth and even sync the calendar with multisync. allthough there are some occasional problems with the syncing. The cable doesn't work for me.

---

### Post by smellydog on 2007-04-23
I had no problems with ubuntu edgy, well except for music issues.  But since I upgraded to feisty, now my phone is not even detected.  It did not detect my apple Ipod at first when I plugged it in the USB, but i restarted with it still plugged in and now it detects it every time so far.  Hmmm...  no clue

---

### Post by FuturePilot on 2007-04-23
I don't have a W810 but I have a W300. But when I plug it in, it gets recognized immediately after I select File Transfer mode and then I get 2 icons on the desktop. One is the phone, the other is the memory stick.

---

### Post by blakegrover on 2007-04-25
I have a 810i and these ttoriales helped me

[http://www.williambrownstreet.net/wordpress/?p=37](http://www.williambrownstreet.net/wordpress/?p=37)
[http://www.williambrownstreet.net/wordpress/?p=27](http://www.williambrownstreet.net/wordpress/?p=27)

Blake

---

### Post by jvc26 on 2007-04-29
Hi there, well since the last mission and with the help of some of the posters here with the links managed to get file and music transfers going. Does anyone have any idea how to sync over the usb cable? I have multisync and all of its plugins installed. On opening multisync I choose to sync a device with evolution, and then choose the sony ericsson device, however I have to tell it which USB device or other device to attach it to - how can I find this out as everything I've tried hasnt come up right yet... any ideas?
Thanks for your help thus far guys,
Il

---

### Post by dumas33 on 2007-05-02
I changed my phone to w810 week ago. 
Now I trying to sync address books and calendars with Kontact. One time just by accident kontact synchronized phonebook with local resource. But I was not able to repeat it...

My discovery: 
1. You can use bluetooth for file transfer. It works OK.
2. You can use bluetooth with Kmobiletools 0.5 beta. In this program you can see address book, stored sms. Even make a call from PC. Everythin works fine. BUT all non-Latin letter are lost (e.g. Lithuanian letters). metadata is lost (company names, birthdays etc.)
3. You can use Kmobiletools with usb cable. w810 is connected like /dev/ttyACM1 device.
4. Multistage work perfect with w810 using bluetooth. I just made back up copy of addresses of phone. did not try to sync with evolution (i use Kontact)
5. You can use w810 with usb cable and Multisync (with irMC library). In synchronization pair select "irMC mobile device" > options Connection type Cable, manually enter device - /dev/ttyACM1
6. Kytchensync (default Kontact synchronize) detects phone via bluetooh. But synchronization is unsuccessfully for addresses and for calendar. 
7. Kytchensync can't detect phone via usb. If you set device manually to /dev/ttyACM1 kontact crashes.

The last two points are very are most important to me. Maybe you can help me out to make things work. Any suggestion welcome.

---

