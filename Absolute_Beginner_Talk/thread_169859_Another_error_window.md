---
title: "Another error window"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by Guns90 on 2006-05-03
When I click on Sound Juicer at Applications>Sound & Video, I get
Cannot launch entry

Details: Failed to execute child process "/home/gary/Billy" (No such file or directory)

I did a sudo apt-get remove sound-juicer, then a sudo apt-get install sound-juicer, I rebooted, and I still get the same error message.  I sure would appreciate some help. Thanks

---

### Post by Guns90 on 2006-05-03
If it helps, I have Breezy, on a ASUS A7N8XE-Deluxe, Athlon 2500+, ATI Radeon 9200

---

### Post by nanotube on 2006-05-03
what happens if you try to launch it from a terminal (with command "sound-juicer" ?)

---

### Post by Guns90 on 2006-05-03
Maybe I'm not understanding your question.  The only terminal I know is going through Applications>Accessories>Terminal.  That's where I input the remove and install commands.

---

### Post by nanotube on 2006-05-03
[QUOTE=Guns90]Maybe I'm not understanding your question.  The only terminal I know is going through Applications>Accessories>Terminal.  That's where I input the remove and install commands.[/QUOTE]

right. so in that same terminal, try typing the command
```
sound-juicer
```
and see what it says.

---

### Post by Guns90 on 2006-05-03
It first brought up this..

gary@GARY:~$ sound-juicer

(sound-juicer:9489): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: asserti on `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(sound-juicer:9489): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: asserti on `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

** (sound-juicer:9489): WARNING **: No HAL devices found for UDI '/org/freedeskt op/Hal/devices/storage_model_SAMSUNG_CDRW/DVD_SM_352B'

in a window, then it brought up a empty Sound Juicer window.  The only thing I could do at that point was eject the CD.

---

### Post by Guns90 on 2006-05-04
Would appreciate some help with this please.

---

### Post by nanotube on 2006-05-04
hmm... well i am kinda out of ideas at this point. maybe someone else can throw out some things to try?

a "workaround" you can always fall back on is to try installing another cd ripper program and give that a whirl. :)

---

