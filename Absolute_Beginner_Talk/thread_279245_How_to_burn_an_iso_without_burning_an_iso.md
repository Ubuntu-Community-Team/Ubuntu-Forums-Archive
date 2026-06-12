---
title: "How to burn an iso without burning an iso"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by man-man on 2006-10-17
I went to burn the Ubuntu iso but it turns out the cruddy pre-installed disk burner that came with my computer doesnt "do" isos - it has an option clearly labelled "save/burn disk images" but this just leads to an advert for some other product from the same company :evil: 

So, if i unpacked the iso using winrar, then put all the files inside onto a disk in the regular "not-iso-burning" way would it have the same effect?

Or should i just put some effort in and find myself a decent disk burner ;) 
There has to be something thats free and downloadable, there always seems to be... :)

---

### Post by taurus on 2006-10-17
Probably best to go with a new burner since it's so cheap now...  Grab one from newegg (if you are in the US) and you can just burn whatever you want.  ;)

---

### Post by Sef on 2006-10-17
What operating system are you using?

If you are using Windows XP to get an iso recorder,  [click here.]("http://isorecorder.alexfeinman.com/isorecorder.htm")

---

### Post by igknighted on 2006-10-17
I am sure this is a software issue rather than a hardware one.  Go to [http://www.download.com](http://www.download.com) (or just google search) for and iso burner and there are hundreds of free products that will work

---

### Post by xpod on 2006-10-17
I found "cdburner xppro" that was advised on the ubunto site really simple...and free.(im sure it`s the ubu site?)

If it`s simple iso burning you want in xp

---

### Post by man-man on 2006-10-17
ok, great 
hehe.. when I'm feeling lazy it often leads to some ideas that are actually harder - for example, unpacking the iso etc etc (although I'm still curious as to whether that would work..)

I'll check out these links and find something useful :D

---

### Post by man-man on 2006-10-17
ack! Turns out the new drive we just got (to replace an old one that flat out stopped working) has some stupid problem of its own. I turn on, computer boots, Windows begins to load, computer freezes. I turn off and remove CD drive, everything works fine.

I suspected that it was trying to boot from the CD drive, and checked my BIOS settings, CD/DVD drive is at the bottom of the boot order (although the top entry was "diskette drive" which I dont beleive I own one of..) Also tried using the one-time boot menu to boot from the Hard disc, same problem

I swear this computer is trying to stop me from running Ubuntu - first the whole system crashes, then the CD drive fails, then the ISO download gets interrupted by windows update, then the CD burning *software* isnt up to it, now the CD burning *hardware* isnt up to it and makes my whole system not work

But I shall prevail! (Eventually I'll get a new PC that either wont have issues or will have a warranty, thats the maximum amount of time this can go on for ;))

---

### Post by steve.horsley on 2006-10-17
> **man-man said:**
> ok, great 
hehe.. when I'm feeling lazy it often leads to some ideas that are actually harder - for example, unpacking the iso etc etc (although I'm still curious as to whether that would work..)

Absolutely not. The files will all be there, but the boot code will be missing - the CD will not boot. It would be as much use as an ashtray on a motorbike.

---

### Post by catlett on 2006-10-17
> **man-man said:**
> ack! Turns out the new drive we just got (to replace an old one that flat out stopped working) has some stupid problem of its own. I turn on, computer boots, Windows begins to load, computer freezes. I turn off and remove CD drive, everything works fine.

I suspected that it was trying to boot from the CD drive, and checked my BIOS settings, CD/DVD drive is at the bottom of the boot order (although the top entry was "diskette drive" which I dont beleive I own one of..) Also tried using the one-time boot menu to boot from the Hard disc, same problem


Did you check the jumper on the cd drive? If the jumper is in the wrong place it will cause on error and mess up your boot. The coputer searches for the drive masters and slaves during boot. It will search for your cd drives and expect a master and maybe a slave. Anyways if you have only one cd it needs to be set as a master or it will cause an error. (there are some that use no jumper if there is only 1 drive and some have a 'cable select' option but it wouldn't hurt to set the jumper to the master position just to be safe)
Check the documentation that came with the cd or look at the cd drive itself, sometimes the jumper settings are printed on the body of the drive. You can also browse to the manufacturer's website for the jumper positions. It will be under support somewhere. It may not be the problem but it is something you can try. Also make sure the cable is connected securely to the motherboard. It wouldn't hurt to try a different power cable off your power supply as well. Again they may not be the issue but at least they are things you can do quickly to troubleshoot and you may get lucky.

---

### Post by RKCole on 2006-10-17
Hello there.

I had quite a time when ti came to burning the ISO for Ubuntu.  Back then I thought I had a lot more computer experience than I did, but now I know better.  It's always great to learn new things.

When it comes time that your new drive is up and running, [DeepBurner Free]("http://www.deepburner.com/?r=download) is a very good, free program which has an easy interface for burning an ISO to a CD.  I had tried to use CDBurnerXP Pro back then, but it did not seem to work well for me at all.  I would highly recommend DeepBurner.  On the page which the above link will take you to, just downlaod the DeepBurner Free 1.8 installation file.

I hope that this will be of some help to you.

Please take care.

---

