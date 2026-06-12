---
title: "No sound on a new MAcbook 7.1 with 10.10"
date: 2010-11-23
forum: Apple Hardware Users
---

### Post by arandomperson on 2010-11-23
When I installed I noticed no sound was emanating from my computer and a red light coming out the headphone jack. s there any reason why there wouldn't be any working sound? Everything else seems to be working fine! Thanks for any help! I installed the additional drivers but the only ones listed were graphics and wireless.

---

### Post by ryanczak on 2010-11-23
Look at the guide here:

[https://help.ubuntu.com/community/MacBookPro7-1/Maverick#preview](https://help.ubuntu.com/community/MacBookPro7-1/Maverick#preview)

It will explain how to get sound working.

---

### Post by arandomperson on 2010-11-23
thanks that totally worked!

---

### Post by JRazalas on 2010-12-13
1.) Try this command in terminal:
    gksudo gedit /etc/modprobe.d/alsa-base.conf

2.) Then scroll to the very end of the file, and add this line:
    options snd-hda-intel model=mbp55

--don't forget to save the file

3.) Delete ~/.pulse

4.) Reboot

5.) In terminal,run "gnome-alsamixer"

6.) Uncheck the box next to "IEC958", but leave
    the "Surround Speaker" and "IEC958 Default PCM" 
    boxes checked.

7.) Look into your headphone jack
    --the red light should be gone

8.) Try to listen to an .mp3 or something before trying
    sound in a browser

---

