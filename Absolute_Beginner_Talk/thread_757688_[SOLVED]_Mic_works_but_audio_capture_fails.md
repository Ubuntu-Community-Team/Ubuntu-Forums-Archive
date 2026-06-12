---
title: "[SOLVED] Mic works but audio capture fails"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by rkakkar on 2008-04-17
The Recording level monitor shows that the microphone is working, but whenever I try to start sound recorder to test it, it throws an error. See screenshot. Also, in Skype when I try to make a test call, it throws an errors saying "audio capture failed". I have a Sony Vaio VGN-FZ240E laptop.

---

### Post by northern lights on 2008-04-17
Can you please post the output of ```
cat /proc/asound/cards
``` Thank you.

---

### Post by sayakb on 2008-04-17
> **rkakkar said:**
> The Recording level monitor shows that the microphone is working, but whenever I try to start sound recorder to test it, it throws an error. See screenshot. Also, in Skype when I try to make a test call, it throws an errors saying &quot;audio capture failed&quot;. I have a Sony Vaio VGN-FZ240E laptop.
 
The screenshot shows that your Mic capture is Muted.

---

### Post by northern lights on 2008-04-17
Nope, not quite. The direct sound output of the recording is muted, but if you were to record to a file and thereupon play back, it should work.

Anyway,what error does sound recording software (have you tried more than one?) throw at you?

---

### Post by rkakkar on 2008-04-17
> **northern lights said:**
> Can you please post the output of ```
cat /proc/asound/cards
``` Thank you.

```
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc400000 irq 22
```

---

### Post by rkakkar on 2008-04-17
> **northern lights said:**
> Nope, not quite. The direct sound output of the recording is muted, but if you were to record to a file and thereupon play back, it should work.

Anyway,what error does sound recording software (have you tried more than one?) throw at you?

after sound recorder i tried the 'test call' feature of skype and it threw me the error i mentioned in my first post so didn't try any other software after that.

---

### Post by trowa_zero on 2008-04-19
I have the same problem right now.  Just to let you know, if people call you on skype you can talk back with no problem.  I used to be able to make calls as well.  I'm not sure what's changed since then and now.  

cat /proc/asound/cards
 0 [V8237          ]: VIA8237 - VIA 8237
                      VIA 8237 with ALC650                                                                                                                                                    F at 0xe000, irq 22
 1 [Microphone     ]: USB-Audio - Logitech  USB Microphone
                      Logitech Logitech USB Microphone at usb-0000:00:10.2-2, full speed

---

### Post by rkakkar on 2008-04-19
It works now :). All it required was a reboot! :P

---

