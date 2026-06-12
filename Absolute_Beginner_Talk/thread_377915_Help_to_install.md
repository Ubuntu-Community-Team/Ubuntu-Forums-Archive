---
title: "Help to install"
date: 2007-03-06
forum: Absolute Beginner Talk
---

### Post by ajmannen on 2007-03-06
Hi, i just downloaded Ubuntu 6,10 and wanted to first try the live cd then install it. 
But i can't try the live cd, i don't know how to "boot" in a cd. When i start the computer the only buton i can push is F2, which gives me a choice of Windows vista normal mode or windows vista security mode.................. i realy wan't ubuntu. ***** vista, it's taking all of my memory and stops all the time, and while it stops it says: Hello mr. virus and mr. spyware, why don't you come in :(

Sry if my English is bad

---

### Post by crom on 2007-03-06
First of all, make sure you have burned the CD right.
If you only have one file on the cd afer you've burned it (the .iso file), you've done it wrong.
[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

Second you need to make sure you're able to boot from your cdrom. 

Go into your bios setup (often started by pressing <F1>, <F2> or <Del>) , and check the boot order there. 

This is something you need to do before the Vista bootloader kicks in. 
(i.e where you choose Vista normal mode or secure mode)

---

### Post by r4ik on 2007-03-06
Your computer's BIOS must be set to boot from CD first; otherwise, Windows will just load up again. To get into the BIOS settings, you usually have to press one of these keys during boot-up: Escape, F1, F2, F12, or Delete. Usually your computer will tell you.

From: [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by Michl on 2007-03-06
You need a bootable CD.  Afte you download
a mirror image, you need to burn the image
to a CD, and not just copy.  You can download
free windows programs that burn images, e.g.
Infra Recorder.

Maybe this is obvious.  The other thing you need
to do is make sure that the boot sequence has
the CD drive before the hard disk.  You need to
go into BIOs before Vista loads.  As the bios loads
at the very start when you turn on your computer,
there will be info on how to get into set-up, usually
it is F2 or delete or something like this.

Good luck.

By the way, once you do load 6.1, you will run into
a problem with setting-up the modem in 
Administrators -> Networking.  Ignore the modem;
it doesn't work.  But check DialupModemHowTo
follow the directions for wvdial (except add 
S19=0 to Init 2 and delete ';' in the password,
name and ISP tel. # lines).  Then you're set
to download some of the repositories, including
gnome-ppp, which then makes your life quite 
easy.  There is information here on the forum on 
where to find gnome-ppp -- it isn't part of the basic 
or standard package.

The learning curve is a little steep, I think, but it
is well worth it and it doesn't last long.

Michael

---

### Post by ajmannen on 2007-03-06
i burned it with clone cd, when i right click and press explore i can see .disk, bin, install, autorun, isolinux, programs etc. 
I've treyed F12, F2, F2 and F3 now. none of em work

---

### Post by smartalecks on 2007-03-06
> **ajmannen said:**
> I've burned it with clone cd, but i only got 1 iso file on the cd :confused: 
I'll try with infra recorder


Hi there.

An .ISO is a cd image, and that file needs be written onto that image. In your cd writing application, look for an option such as "Write Image to CD". That is what you need to use.

ex. 
When you insert the CD and open it, **there should not be a single .iso file.**
When you insert the CD and open it, there *should* be many files.

edit: saw your edit :D

You will have to set up your mother boards BIOS to boot from the CD rom drive. Look for an option/key to press to get into BIOS when it boots up, otherwise try common keys such as ESC constantly while it boots. :D

---

### Post by ajmannen on 2007-03-06
Ok, there are now many files, but i still can't boot with it

---

### Post by smartalecks on 2007-03-06
You need to edit your motherboards BIOS. Do you know how to do this?

---

### Post by ajmannen on 2007-03-06
I'm a .........noob:lolflag: 

I know alitle about HTML, .CSS .Java and that microsoft sucks but apart from that, nothing

---

### Post by smartalecks on 2007-03-06
When you are booting up your computer, look for a message that says something like

```
F2 = Setup
```
or
```
Press ESC for setup options.
```

Press whatever key it says, and that should take you to the BIOS. From there, find something like "Boot Options" and make sure that your computer boots from the CD Drive. Be careful in BIOS!!

---

### Post by ajmannen on 2007-03-06
F12 brings me to a screen that says do you wan't to start windows vista in normal mode or recovery mode? 
If i press ESC i just exits and turns on Vista, if i press F10 i can change some windows startup things or sumething, if i press F5 i get the option "do you want to start windows is safety mode?!:mad:

---

### Post by crom on 2007-03-06
You must press the correct key _before_ vista bootloader starts. 

I'd recommend pulling out your manuals for your computer or motherboard, or look them up on the internet. 

Read up on how to enter the BIOS and change boot options.

Note: some screens takes a while after power on to show a picture, it sometimes hides the bios message.
try pressing esc, f10, f12, whatever while the screen is still black.

---

### Post by smartalecks on 2007-03-06
> **ajmannen said:**
> F12 brings me to a screen that says do you wan't to start windows vista in normal mode or recovery mode? 
If i press ESC i just exits and turns on Vista, if i press F10 i can change some windows startup things or sumething, if i press F5 i get the option "do you want to start windows is safety mode?!:mad:

f12 and f5 dont sound like it, what else do you get when you press f10?

ps, is your computer from a brand, such as dell?
btw, the bios interface is probably blue :D

---

### Post by fdrake on 2007-03-06
Explain better. What do you see when you press f10. Do you read anything like " Booting Devices Order"

---

### Post by ajmannen on 2007-03-06
I made it :) :)  it was the PrtSc SysRq buton (werid right).$ Buy now i have 2 partiotions on my computer, one with 50 gig and one with 70 gig, the one with 50 gig has vista on it, so i can't use that. But if i install Ubuntu on the 70 gig partition, wil i still be able to download, browse and see the 70 gig partiotion with ubuntu on vista?????????

---

### Post by fdrake on 2007-03-06
windows won't recognize the linux partition. but there are special software under windows that may help.
[http://news.softpedia.com/news/Access-Linux-partitions-files-under-Windows-48292.shtml](http://news.softpedia.com/news/Access-Linux-partitions-files-under-Windows-48292.shtml)
so at the end yes you can

---

