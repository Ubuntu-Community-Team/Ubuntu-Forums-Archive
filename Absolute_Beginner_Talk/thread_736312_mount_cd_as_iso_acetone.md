---
title: "mount cd as iso acetone?"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-03-26
Hi, I've succesfully installed acetoneiso2 on 64 bit 8.04. Very easy installing from source and everything appears to be working. Only one problem I'm having and I think it has to do with how the cd's are mounted  in Ubuntu or Linux in general. 

When I choose to convert a cd/dvd to an iso image, the file browser opens and the only option available is iso, img, nrg, etc. (image files).

Is there a way to mount my /dev/scd1 as an iso instead of mounting it to a folder? Like all of the other mounting programs, it seems that my only option is to mount it to a folder so it is a directory and not an image. Acetone is looking for an image though.

Thanks

---

### Post by maybeway36 on 2008-03-26
You can't mount it as an image, but you can copy it:
```
dd if=/dev/scd1 of=something.iso
```

---

### Post by iansane on 2008-03-26
Thanks Maybeway36. That code appears to do the trick for personal cd's. But when I try it on a movie dvd I get this.

```
 ian@lotus-control:~$ sudo dd if=/dev/scd1 of=hitman.iso
[sudo] password for ian: 
dd: reading `/dev/scd1': Input/output error
759264+0 records in
759264+0 records out
388743168 bytes (389 MB) copied, 86.6214 s, 4.5 MB/s

```

and looking at the resulting iso it appears to only have copied some of the ifo's and a couple of short vob's that aren't encrypted for copy protection.

Is that why the error?

Don't copy right laws say that I can make one recording for personal use?

Is there a way to copy cd/dvd to iso even if it's copyrighted? If I could, I would just use a microscopic camera and take a picture. That's basically all I want anyway. Is there anything that just makes an image without regard for encryption or content of the image?

---

### Post by bulletxt on 2008-03-26
first of all you AcetoneISO2 has a specific option to convert cd/dvd to ISO, but it seems you are using the feature "convert image to iso" ! anyways, it will only convert to iso normal data cd and not copyprotected games. there is no way to do such a thing. just copy the cd to a folder and then burn the folder. then when you install the game just apply a no-cd file. google for such files.

if you are asking: I need to do a 1:1 copy of a copyprotected cd, then NO, there is no way to do it on linux. there a some chances on windows with clonecd but it depends on the copyprotection and your cd/dvd device capabilities.

---

