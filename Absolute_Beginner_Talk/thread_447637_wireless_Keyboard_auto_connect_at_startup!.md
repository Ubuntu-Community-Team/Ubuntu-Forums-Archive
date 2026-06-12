---
title: "wireless Keyboard auto connect at startup!"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by marlau on 2007-05-18
how is possible, at startup  to make auto connect the Logitech DiNovo wireless keyboard on Feisty? 
many thanks!

---

### Post by Kobalt on 2007-05-18
It's connectiong through bluetooth, so the trick would be to start the bluetooth services at boot time, perhaps adding it to System > Pref. > Session : programs at boot
Did you already got your keybord to work wirelessly ? How ?

---

### Post by esoterica on 2007-05-18
That's an interesting looking keyboard, don't know if I'd ever spend $200 for just a keyboard when you can buy a laptop from Dell for almost that much though.

Looks like people are getting it to work in Linux, but everyone seems to be claiming that getting it to do so isn't much fun...'

[http://www.google.com/search?hl=en&q=Linux+Drivers+for+Logitech+DiNovo+wireless+keyboard&btnG=Search](http://www.google.com/search?hl=en&q=Linux+Drivers+for+Logitech+DiNovo+wireless+keyboard&btnG=Search)

There are some pretty bizarre solutions listed in that search to what people have done to make it work, I'm doubtful theres a need to go as extreme as some of them have done.

---

### Post by marlau on 2007-05-18
->Kobalt,
At boot screen, in BIOS all works.
bu then when i get login Welcome screen...
nothing works, till i remove... and then stick back "Logitech BT mini receiver" in USB port. After that Keyboard & Mouse works fine :)

so, i think problem is- i must some way auto mount "Logitech BT mini receiver"... 

in Session configuration i have at startup "Bluetooth Manager with command bluetooth-applet"

maybe something is wrong with "Syst->Pref.->Removable Drives & Media"...?!  :/

---

### Post by redman5087 on 2007-06-05
The problem why your Dinovo is not responding at the login screen is because you must enable it to connect at boot.
Open the file "bluetooth", it is located "/etc/init.d/bluetooth"
When you open the file you will see an opttion like "HIDD_ENABLED=0", set it to "1"
Then you will see an option like "HIDD_OPTIONS=" --master --server". Add a connect option with mac address of your keyboard. Example:
   HIDD_OPTIONS="--connect 00:07:61:1A:95:AE --connect 00:07:61:1D:91:14 --connect                          00:07:61:15:9A:6F --master --server"

save the file and restart your bluetooth system and you're ready to go.
Now when you reboot and you come to the login screen, press any key on the keyboard: the keyboard will autoconnect.

Let me now if this helps

---

### Post by trannel on 2007-06-05
redman, thank for your answer.

I have the same issues as the starter of this thread.
At welcome screen my DiNovo keyboard/mouse wont respond.
When a disconnect and reconnect the bluetooth dongle it start to work fine.

I tried your suggestion and edited the bluetooth file but it seems not to help.

&trannel

---

### Post by redman5087 on 2007-06-05
I'm sorry I forgot.
You need to change a line in the same script (/etc/init.d/bluetooth)
Comment the following line
HID2HCI=/usr/sbin/hid2hci  like this   #HID2HCI=/usr/sbin/hid2hci
reboot and I think it should be fine.
Your dongle will stay in HID proxy mode.

---

### Post by trannel on 2007-06-06
Thanks, its working fine now :)

---

### Post by FunkWarrior on 2007-07-03
Works fine for me too!

Thank You! :);)

---

### Post by caish5 on 2007-09-19
How do i know which numbers are supposed to be master and server?

---

### Post by londoner on 2007-11-02
i can't save the file.

i also have the same problem with the keyboard

i have tried the same it miracously works 1 out of 8 restarts and when i plugin plug out while booting
i tried editing the file but i can't save it?

:confused:

---

