---
title: "The dreaded Speedtouch USB modem woes"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by jfrancis on 2006-11-06
I am a total linux newbie.

I use Windows XP.

I own a USB speedtouch 330 modem.  It is red :-k 

I installed the edgy 6.10 latest version for 64bit amd. 

I read the guide(s) to installing said modem.

I have read many, many threads on this subject.

I know this topic is visited many many times.. :twisted: 

Lets start at the beginning.  I will refer to [the guide]("https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch")

Step 1 - Find out the revision of firmware.  According to guide, this code should be used:

grep -B 1 "THOMSON ALCATEL" /proc/bus/usb/devices

I did this.  It told me no such file or directory exists.  Then lists a bunch of code that does not appear to show me what i want.

I would copy the results and paste it here, but I can only post here via XP - and I cant mount that either.. but thats another thread (yes, again followed a few guides and read many, many threads).

I feel that an instruction is missing here.  Something before I do the above.  So, any clues?

Best,

JF

---

### Post by jfrancis on 2006-11-06
A ha!

So.  The guide I linked to does not work for me at the 1st step of discovering the revision of the modem.  However a different guide has a different command to do this, and this one worked:

awk '/4061/ {print $5}' /proc/bus/usb/devices

Something to bare in mind if anyone else has trouble at this 1st hurdle.

I will attempt the rest of the steps tomorrow when I have time.

---

### Post by jfrancis on 2006-11-07
Ok.

I can't figure this out.

From the guide, when you need to split the file using the firmware-extractor program:

[B]cd speedtouch &&
chmod +x firmware-extractor &&
./firmware-extractor KQD6_3.012[/B]

When I do this, I get this error:

[B]bash: ./firmware-extractor: No Such File or Directory

[/B]

I have checked many times the spelling and that the files are in the right directory... can anyone let me know what I am missing?

Thanks.

---

### Post by jfrancis on 2006-11-07
After more searching, I have discovered it is because the firmware extractor program will not work in the 64bit version of this OS...  ](*,) 

So.. I am asking for further help in another thread now.  Sorry to post this as well, but I am sure there will be others with the same problem and it all helps.

---

### Post by scaley on 2006-11-09
I am having the same problem. Surely someone somewhere has figured out how this is done. Obviously the firmware extractor wont work, so surely we must acquire another firmware extractor, to create the bin files?

Also, i had a problem with the first simple commands. 

mkdir speedtouch

mv SpeedTouch330_firmware_3012.zip speedtouch

cd speedtouch

unzip SpeedTouch330_firmware_3012.zip


It then tells me there is no such dir 'speedtouch'. Im pulling my hair out here. ](*,)

---

### Post by jfrancis on 2006-11-09
Yes, very annoying.

Basically, the 64bit version has trouble with the firmware extractor program.  You can get around this by having someone else extract the files for you, and download those and skip this part of the process.

In another thread, a very nice guy did just that.  Go here to follow: [http://www.ubuntuforums.org/showthread.php?t=283188&page=4](http://www.ubuntuforums.org/showthread.php?t=283188&page=4)

---

