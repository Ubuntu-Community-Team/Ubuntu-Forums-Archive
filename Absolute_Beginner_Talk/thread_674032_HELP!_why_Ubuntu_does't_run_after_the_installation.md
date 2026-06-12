---
title: "HELP! why Ubuntu does't run after the installation?"
date: 2008-01-21
forum: Absolute Beginner Talk
---

### Post by midian86 on 2008-01-21
Hello everybody!
I'm an absolute beginner italian linux user and I don't understand why I can't run Ubuntu on my notebook HP Pavilion dv6132eu(AMD Turion 64x2, 1GB Ram, Nvidia Geforce Go 6150 128 MB).
I first tried Ubuntu Studio 7.10, than feisy fawn 7.04 and others, but the result is the same.:(
I use the alternate installation dvd and the installation goes on with no errors until the end when it stops at this string: 

"sending SIGTERM to all process".

Then i switch off the computer and reboot, i select the ubuntu partition and then i wait (a long time)until appear this:


kinit: name_to_dev_t (/dev/sda6) = sda6(8,6)
kinit: trying to resume from /dev/sda6
kinit: No resume image, doing normal boot


* Setting preliminary keymap...         [OK]
* Preparing restricted drivers...        [OK]
* Setting the system clock...             [OK]
* Starting basic networking...            [OK]
* Starting kernel event manager...    [OK]
* Loading hardware drivers...               _

then it gets stuck.

I really don't know what to do and why this happens!:confused:
Please help if you can!
thanks!

---

### Post by ibizatunes on 2008-01-21
Im only quite new to this myself (way off being able to debug kernal issues)
.... but i download from the oxford uni mirror a corrupt ubuntu x64  version from that mirror! Im not say u download it from there but it maybe u should check the CD\DVD to see if it pass it verification test!?
Let me know

---

### Post by Cypher on 2008-01-21
You should have two options in the GRUB menu for Ubuntu, the first one is the default and the second one has the words "(recovery mode)" on it. Can you boot into the (recovery mode) option to see if it will successfully boot up?

---

### Post by cybertron3000 on 2008-01-21
I am new too, but my install on an older computer had no problems.  Did you download the Ubuntu, or did you have a pre-made CD-Rom mailed to you?  Mine was mailed - I don't personally think downloading is a guaranteed way of getting a perfect install.  I would recommend having Ubuntu mail you a copy if the offered solutions don't work.

---

### Post by ibizatunes on 2008-01-21
Downloading is fine, as long as u check the CD\DVD before installing it! Download from the cannical mirror is always going to be a safe bet, even if its not the fastest!

---

### Post by midian86 on 2008-01-22
I download from the official ubuntu and ubuntu studio site, and no, the recovery mode gives me exactly the same result. 
I have also checked the CD\DVD with the test and found no error.

---

### Post by Het Irv on 2008-01-22
Is all of your hardware OK?  
To more expericenced peoples: Is there a way to see which driver it is hanging on?

---

### Post by midian86 on 2008-01-22
I haven't had no hardware problem until now. 
I have also recently formatted the entire hard disk with the HP recovery system before partitioning.

---

### Post by Michl on 2008-01-22
I wouldn't blame the download assuming you did a checksum.

One problem that comes to mind is HP Pavillion.  I had an HP
Pavillion and they are quirky because they have their own
drivers.  I tried an alternate install, dual boot, on it and it
didn't work.  My next option was to reformat the whole
disk and do a clean install of windows without the
Pavillion set-up disk, and then install ubuntu.  I didn't
do it, though, and found a faster used computer.

---

### Post by hyper_ch on 2008-01-22
Can you run the DesktopCD?

---

### Post by midian86 on 2008-01-22
Maybe I have tried the desktop cd, but now i don't remember and can't verity, i'll do as soon as possible.
A question for Michl, 
will i be able to use HPdisk again if I do a clean install of windows without pavilion set-up disk ?

---

