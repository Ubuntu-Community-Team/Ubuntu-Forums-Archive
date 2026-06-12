---
title: "Kali Live USB persistence error(Kernel Panic)"
date: 2018-01-02
forum: Any Other OS
---

### Post by erikdz on 2018-01-02
Ive been trying to create a usb persistence live with Kali for 4 days now. The thing is that when I have configured persistence, reboot it and enter persistence this shows up and it stays frozen (sometimes it even appears without selecting live persistence):
*Ive attached an image (not sure, im new)*

---

### Post by ian-weisser on 2018-01-03
> **erikdz said:**
> ...when I have configured persistence, reboot it and enter persistence...

That is very confusing.
That kind of terminology leads me to think you might not be creating your LiveUSB properly.
Are you following some kind of instructions? If so, a link would be helpful.

---

### Post by sudodus on 2018-01-03
**mkusb** can create a persistent live USB drive with Kali.

See the following links,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

and the attached photo and screenshot.

I tested with the iso file **kali-linux-light-2017.3-amd64.iso** (and installed **scrot** to take the screenshot), and it works without any tweaks (I selected 67% of the remaining space for persistence in a 16 GB pendrive).

---

### Post by erikdz on 2018-01-03
[https://www.youtube.com/watch?v=SEVGxIUkhSA](https://www.youtube.com/watch?v=SEVGxIUkhSA)

---

### Post by erikdz on 2018-01-03
Alright, ill try it that way thx

---

### Post by sudodus on 2018-01-03
Good luck and please let us know the result :-)

---

### Post by erikdz on 2018-01-11
It still gives me the same error :(

---

### Post by sudodus on 2018-01-11
Maybe there is a compatibility problem between the version of Kali that you are trying and your computer's hardware.

- If you tell us details about your computer's hardware, we (I or someone else) can give you more relevant advice: So please specify your computer

- Brand name and model
- CPU
- RAM (size)
- internal drive (size)
- graphics chip/card
- wifi chip/card

[hr][/hr]
- You can try the persistent live USB drive in some other computers.

- You can try if Ubuntu works for you (in the computer, where Kali does not work).

---

