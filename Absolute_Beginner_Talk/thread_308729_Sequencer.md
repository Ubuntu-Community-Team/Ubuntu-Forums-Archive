---
title: "Sequencer"
date: 2006-11-28
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-11-28
Currently every time I startup I find myself forced to put in the command "sudo modprobe snd_seq_oss" in order to have a sound sequencer. I was wondering if there was anyway to make this a permanent change so I would not have to do this.

---

### Post by HedonismBot on 2006-11-28
Put it in your /etc/inittab

That'll do it.

---

### Post by JNowka on 2006-11-28
No, that didn't work.  Did nothing really.

I still get the error 
> "ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory"
 in winecfg, until i put in the "modprobe snd_seq_oss" command.

---

### Post by JNowka on 2006-11-28
I just figured it out.  I edited the /etc/modules file and added on the last line snd_seq_oss.  Rebooted, and it worked just right.  :)  Thank you for you help.

---

