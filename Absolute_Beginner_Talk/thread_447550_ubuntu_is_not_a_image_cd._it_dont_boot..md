---
title: "ubuntu is not a image cd. it dont boot."
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by giorgiomartini on 2007-05-18
hi i downloaded ubuntu , but it is a rar archive , i read it was a image cd , but its a folder in rar.

i extracted it and copied it into a cd , i though like this , when i boot the computer and the cd was in , it would detect it and load ubuntu , but it dont.


what do i have to do ? do i have to convert this into a image cd?

i just copied it into a cd , but when i boot the computer it dont boot from the cd.

this is what i copied into the cd:

---

### Post by nvteighen on 2007-05-18
Hi! Are you sure it is .rar?? It should be .iso!

Try to follow this guide: [http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso) and tell me your results

Cheers!

---

### Post by derred on 2007-05-18
you might have WinRAR associated with .ISO files so that it will automatically open them. The best way to check is to open the folder you have the image in under Explorer. Then go to Tools/Folder options select the view tab and uncheck the box called *Hide file extensions for known file types*. Look at the file. Does it end in .iso?
If so than you can open it in your CD burner application and write it from there. Be sure to write it with the option that says something like "write image to disk" and not write it as a data CD containing the .iso
Hope this helps, Cheers!

---

### Post by librano on 2007-05-18
@esoterica: can we keep the discussion in the ubuntu spirit please...

@giorgiomartini: open you cd burning program and look for something like 'burn image to cd', 'write image' or something like that and point it to the file you have downloaded. I am sure this file if you downloaded it from an official source is not a .rar file. you just have winrar set to open .iso files... unpacking the files from the iso and burning them to cd will not work. 

remember... burn image is what you are looking for in you cd burning program.

---

### Post by AlexenderReez on 2007-05-18
hm....i don't sure whether you have succeed  it or not.....but this is my way....usually i use write-read disc(cd rw) ...so i use it for other cd image afterwards.....but you also can extract all iso image ....into usb pendrive  ...then when reboot...choose to boot usb first...then it will install it....or

use


> [https://wiki.ubuntu.com/install.exe/Prototype](https://wiki.ubuntu.com/install.exe/Prototype)

good luck:)

---

### Post by esoterica on 2007-05-18
Make sure you also follow the instructions on how to do the MD5 check on the file you downloaded.

I'd also highly recommend turning down the burn speed in the CD burning software you are using once you do find the right file and confirm it with the MD5 check. I used my normal burn speed I always use and for someone reason the first 2 copies I burned would boot but not install due to disk errors (you'll see an option to check the disk once you get booted to it, I think even if you don't select the option it checks the disk for errors anyhow before running). I found that I had to slow my burn speed way down before I could get a working disk for the install.

Get yourself past all that, then you can break out the martinis and celebrate.

---

### Post by proalan on 2007-05-18
never extract from ISO and burn. It makes the burnt disk unbootable

---

### Post by rajeev1204 on 2007-05-18
> **giorgiomartini said:**
> hi i downloaded ubuntu , but it is a rar archive , i read it was a image cd , but its a folder in rar.

i extracted it and copied it into a cd , i though like this , when i boot the computer and the cd was in , it would detect it and load ubuntu , but it dont.


what do i have to do ? do i have to convert this into a image cd?

i just copied it into a cd , but when i boot the computer it dont boot from the cd.

this is what i copied into the cd:


Hi

The file u downloaded *is * the image file . It does show as rar in windows but dont bother about that .DO NOT extract that file .

Just use a cd burning program and select * burn as image file* to disk.

---

### Post by esoterica on 2007-05-18
I just posted this in another thread here, applies to this one as well...

Check for hardware compatibility and great step by step instructions here...

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

Software for Windows and Linux to check the MD5 as well as the hash can be found here, there's also Windows software linked there that's free that can be used for burning the ISO file since the built in burner in Windows XP and Vista does not handle ISO files for some stupid reason...

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by UbuntuniX on 2007-05-18
It's an ISO, you just have WinRAR set to open ISOs. Download InfraRecorder from SourceForge.net.

---

