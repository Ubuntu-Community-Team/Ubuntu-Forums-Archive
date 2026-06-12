---
title: "Installing Speedtouch firmware"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by BillyBeag on 2007-01-30
I am a newbie. Feeling really stupid right now too.
I have been following the instructions on installing the firmware for the speedtouch USB modem  from [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch)

I get to the point where I am supposed to do this:
```
./firmware-extractor KQD6_3.012
```
And I get "no file or folder"
now I have looked and it is there, it is executable at least I did the chmod bit
```
chmod +x firmware-extractor
```
and it just returns the prompt, so I gather that worked.
I have done an ls on the speedtouch folder and the firmware-extractor is listed in there, so I highlight the name in the terminal and copy and paste the name behind the period and forward slash adding the correct firmware file to absolutely duplicate the code as above.
```
./firmware-extractor KQD6_3.012
```
Just like that. But I still get the "no file or folder" output.
I did copy it all into a text file and save it to floppy so I could show the output here, but strangely that text file is not on the floppy now.

Can anyone tell me why I am not getting anywhere? I am feeling really really stupid right now.
I am not actually **that** much of a newbie, I have had linux installed before, mandrake and Gentoo. But I am feeling rather silly now.

---

### Post by BillyBeag on 2007-01-30
I didn't solve my problem, but I did find a way around it. :D 

I just copied the firmware files from the .deb firmware I had downloaded previously on another attempt.
I am making this post from Ubuntu on my speedtouch modem.
WooHoo.

---

### Post by diahane on 2007-02-22
dude i have EXACTLY THE SAME problem you had with the SPEEDTOUCH modem!!!
so can you just link me the right place to download the RIGHT .deb firmware you used?????

i'm begging you.....................

---

### Post by christhemonkey on 2007-02-22
You could just press <tab> to autocomplete?
So type:
```
./fir<tab> (then the rest should appear like this:)
./firmware-extractor K<tab> (should then append it to this:)
./firmware-extractor KQD6_3.012 (or something similar)
```

---

