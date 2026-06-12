---
title: "Cant boot from disk for ubuntu"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by XRichX on 2007-06-24
Hey again lol, i decided to burn a copy of ubuntu onto a 700MB bland CD using Infrarecorder and its all correct, i havent burned an image, i burned the files which is stated in the documentation that i must do. I try to boot from disk but it goes to a blank screen, reads from disk and just boots XP (from HDD) so i changed the priority in BIOS to put the CD drive first and HDD second, same thing happened again. 

Have i done something wrong? the CD works fine in Windows.

Thanks

Rich

---

### Post by foxmulder881 on 2007-06-24
Are you sure you burnt the ISO image and didn't just drag and drop the files from the ISO?

---

### Post by XRichX on 2007-06-24
it says not to burn an image, so i added the files in infrarecorder and burned the files onto the disk, i can use the disk in windows fine and install firefox, thunderbird etc. i just cant get it to boot up from the CD lol.

---

### Post by foxmulder881 on 2007-06-24
You MUST burn the image, not the files. That's why it's not working.

Reburn the image.

---

### Post by XRichX on 2007-06-24
oh, haha i swear it told me to burn files, ok thanks for you time and help :)

feel like a right plonker now...

---

### Post by mattg89 on 2007-06-24
I think you've got a little mixed up, no worries, I did that too!

You want to burn the image to the CD, but not the image file. (You don't want a .iso on the cd).

---

### Post by foxmulder881 on 2007-06-24
No probs mate. 1000 other people have done the same thing.

---

### Post by XRichX on 2007-06-24
ok im confused, so im in infrarecorder, i have added all the files to the burn section ready for burning, but how do i burn it as an image? the CD i jsut did that isnt working i clicked on 'burn the current compilation to a physical disk'.

@ Mattg89: yeah i was like thinking not to burn an iso not to burn an iso lol.

thanks for you help :)

Rich

---

### Post by mattg89 on 2007-06-24
Usually there's an option in burners to "burn image". I don't have the recorder you do, so I don't know the way around. I'll have a little look on google.

EDIT: It definitely can do ISO images.

---

### Post by XRichX on 2007-06-24
yeah im burning an image now, but wont that be an iso which isnt what i want or am i getting the wrong end of the stick and i just really need to burn an iso onto a blank disk as i would for anything else?

thanks again :)

EDIT: i think i got it :) just burning it now :P

thanks again guys

Rich

---

### Post by XRichX on 2007-06-24
ok, i burnt the iso zip/rar i downloaded from ubuntu without extraxting it this time and the exact same thing occurs... i dont know what im doing wrong right now.

---

### Post by mattg89 on 2007-06-24
Did you select "Burn Image" from the actions menu? If not, that's what you need to do.

---

### Post by XRichX on 2007-06-24
yep i did, i selected the compress download that i got from ubuntu.

---

### Post by mattg89 on 2007-06-24
Was the download just an ISO, not a zip or rar?

---

### Post by XRichX on 2007-06-24
its a rar, i selected it when i selsected 'burn image', if i extract it i cant burn an image i can only burn the files.

---

### Post by mattg89 on 2007-06-24
The image should be in .iso format, not .rar
How did you download it?
If it was from the ubuntu main page it should be in .iso format.
The iso file is what you burn from the "Burn Image" menu.

---

### Post by XRichX on 2007-06-24
i downlaoded it from a Great Britain mirror on the main site, it came in a rar file, should i try a different mirror to see if its an iso there?

thanks for your help thus far Matt :)

EDIT: it is actually an iso file, but winrar sees it as a rar file. It becomes a winrar archive when downloaded, might try uninstall winrar and then download it or try again.

---

### Post by mattg89 on 2007-06-24
Are you using XP?

If so, go to the folder where the image is, go Tools --> Folder Options. Click on the View tab, and deselect "Hide extensions for known file types", then hit apply. The image should have a .iso after it. I don't know what's going wrong if that is the case, because the burner should be working.

Do you get any screen at all when you put the CD in, or does it just boot to XP?
Are you sure you've changed the boot order (might be wrong CD drive if you have 2), and did you save the changes, or just exit the BIOS?

---

### Post by XRichX on 2007-06-24
well im using XP, i go to a black screen with a flashing little line as if text is going to appar but then it just boots to XP. when i did the file extension thing it shows as an iso but still a winrar archive lol, so i uninstalled winrar and its now showing as an iso. so im gonna try burn it again. I have changed the boot sequence in the boot menu but not the BIOS as i have tried that already but no sucess :(

thanks still :)

---

### Post by XRichX on 2007-06-24
ok, its doing the exact same thing, thats 3 disks all doing the exact same problem, just booting XP instead of Ubuntu.

EDIT: couldn't i like disable boot from floppy and HDD so it only boots from CD, wouldnt that force it to boot from CD?

---

### Post by XRichX on 2007-06-24
sorry for the triple posting but i tried it on my dads pc force booting it from the CD and it comes up with 'BOOT ERROR PLEASE INSERT SYSTEM DISK' so its the disk but thats 3 disks that does that... im using panasonic 700MB/80min CD-R disks.

---

### Post by Rabindranath on 2007-06-24
Burn image option will be available under Actions.

---

### Post by steve.horsley on 2007-06-24
XRichX - if you burn the image properly, all you have to specify to the burner is the name of the .iso file to burn, but then when you look at the CD afterwards you will see a load of files on there, not the .iso file you named. 

The difference between unpacking the files from the .osi and burning them to CD and burning the image file as an image is that the latter method also puts a bootable bootsector at the front of the CD.

If you really can't get it working, drop me a mail on [email]steve.horsley@gmail.com[/email] and I'll put a CD in the post for you.

---

### Post by XRichX on 2007-06-24
i have done that twice now, still doesnt work, the CD works in windows but i cant boot from it...

@ steve, yeah i burned the image twice and the files were all there not the image, i just cant get the dam thing to boot, i shall drop you an e-mail that would be brilliant thanks :)

---

