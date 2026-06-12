---
title: "Back to Windows for me"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-02-26
For some strange reason by USB Flash Memory Stick (Kingston 1GB Datatraveler) stopped responding in my 1st installation of Ubuntu/Xbuntu.

I have no reason why this occurred as it was working perfectly fine before that point.

So I decided to format and make a clean installation of Xbuntu and try again, this was fairly painless as I just reread my previous posts on the forum to get me back to pace.

Anyway, I attempted to use the key again, it was displayed on the screen with the name Kingston and when I attempted to browse it, it simply disappeared.

I have consequently rebooted the PC and re-inserted the device, but with no luck.

I don't understand why this has happened a 2nd time, I cannot afford to lose this device as this would have been an ideal situation transferring files instead having to burn RW discs.

chrome

BTW In my experience - I have found that if you install Ubuntu Edgy v6.10 and then use the Xbuntu desktop you do lose some of the formatting. Also a clean installation of Xbuntu seems to run slower than the installation of Ubuntu/Xbuntu .... strange.

---

### Post by Crooksey on 2007-02-26
You are in the wrong state of mind to be a Linux user, things always don't just work you need to have input.

Add the full path to the device into your fstab then mount it from the command line.

---

### Post by floke on 2007-02-26
It should be in the /media directory - so check for it there when its plugged in rather than looking on the desktop. Or - create a folder on the desktop - e.g. 'USB' , go to a terminal and try

sudo mount /media/usb[this might be usb1 or something though] /home/[yourusername]/Desktop/USB

You can't go throwing a wobbly anytime something doesn't work right else your head will explode and you'll end up back in Windows for ever :)

---

### Post by chrome307 on 2007-02-26
**You are in the wrong state of mind to be a Linux user**

Your most probably right - as they say 'If the cap fits - wear it'

**@Steve.K**

Nothing is reported in that folder, which is odd as this time round the LED on the disk lights up ........... looks like no-one's at home though :)

Thanks again guys!!!

---

### Post by floke on 2007-02-26
Does anything show up in the system monitor?

---

### Post by hardyn on 2007-02-26
i had the same thing happen... a usb stick that will mount in windows but not in ubuntu... all my other flash sticks worked; i chalked it up to defective or poorly engineered flash stick, and got rid of it; you may want to try reformatting to fat32 using ubuntu and see what happens.

---

### Post by floke on 2007-02-26
Whatever it is, it's not worth dumping Ubuntu over.

---

