---
title: "is it safe to..."
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-30
delete ntfs files (from winxp partition) when you are logged to ubuntu ?
yeah I know it sound like a stupid question but it's better "safe" then "sorry".

---

### Post by joshrobinson on 2006-06-30
[QUOTE=MAXDDARK]delete ntfs files (from winxp partition) when you are logged to ubuntu ?
yeah I know it sound like a stupid question but it's better "safe" then "sorry".[/QUOTE]

you cant write to NTFS partitions with ubuntu unless you added ntfs write support for it.. even then its not a good idea

if you want a partition that both OS's can use go for fat32

---

### Post by MaximB on 2006-06-30
you misunderstood me...I meant delete files from ntfs partition in ubuntu ?

---

### Post by raptros-v76 on 2006-06-30
what? you cant delete stuff in an ntfs partition from ubuntu. and ubuntu itself is usually installed on an ext3 partition

---

### Post by Kilz on 2006-06-30
[QUOTE=MAXDDARK]you misunderstood me...I meant delete files from ntfs partition in ubuntu ?[/QUOTE]
Deleting is actualy a write operation. You could corrupt the disk and lose everything.

---

### Post by steve.horsley on 2006-06-30
It is safe to try, but nly because you will get an error about the file being read-only. This is because writing to ntfs, as you suspected, is **not** safe. MS won't release the specs, so the writers of the Linux driver have to guess. It's safe to read ntfs of course, but writing is risky when you aren't sure what the exact format should be.

---

### Post by joshrobinson on 2006-06-30
[QUOTE=Kilz]Deleting is actualy a write operation. You could corrupt the disk and lose everything.[/QUOTE]

thanks for explaining that to him

[QUOTE=MAXDDARK]you misunderstood me...I meant delete files from ntfs partition in ubuntu ?[/QUOTE]

when i said you cant write, i meant delete.. same thing.. its still a disc writing situation

---

### Post by Kilz on 2006-06-30
[QUOTE=joshrobinson]thanks for explaining that to him
[/QUOTE]
Not a problem, whenever I post to the beginers forum I try and give as much info as I can. Some people may not realise that when they delete something the write head actualy writes to the fat (file alocation table) area of the disk, It actualy overwrites the data to get rid of it.

[One of the most amusing things]("http://www.ubuntuforums.org/showpost.php?p=1173438&postcount=2") I have ever read on the forums was on this subject.
[quote=x64Jimbo]You heard experimental like "cutting edge," but in this case, the NTFS write support is experimental like "I designed a nuclear reactor out of paper clips. Let's test it!"
Three words:
DON'T DO IT
It's extremely likely that you'll fubar the entire filesystem.[/quote] I hope this gives others an idea about why not to try it. It still makes me smile when I read it. :grin:

---

### Post by joshrobinson on 2006-06-30
[QUOTE=Kilz]Not a problem, whenever I post to the beginers forum I try and give as much info as I can. Some people may not realise that when they delete something the write head actualy writes to the fat (file alocation table) area of the disk, It actualy overwrites the data to get rid of it.

[One of the most amusing things]("http://www.ubuntuforums.org/showpost.php?p=1173438&postcount=2") I have ever read on the forums was on this subject.
 I hope this gives others an idea about why not to try it. It still makes me smile when I read it. :grin:[/QUOTE]

awhile ago when i used to run suse, i enabled NTFS writing on a test partition (something i wouldnt mind losing some data on) and it worked, but was HORRIBLY slow.. now this was awhile ago it could have gotten better.. i disabled it right away.. i didnt lose any data for the few days i messed with it.. but i decided i was just better off using fat32.. but since then im pure ext3

---

### Post by MaximB on 2006-06-30
thanx for the replyes...there are some files and folders on my winxp partition (ntfs) that winxp just refuses to delete it always saying that the file is curently in use - but it's not true as far as I know , and I want to find a way to get rid of thouse files.
so now I know I can't delete them in ubuntu too....what am I suppose to do now..I don't want to format it and reinstall winxp.
mmm...

---

### Post by joshrobinson on 2006-06-30
[QUOTE=MAXDDARK]thanx for the replyes...there are some files and folders on my winxp partition (ntfs) that winxp just refuses to delete it always saying that the file is curently in use - but it's not true as far as I know , and I want to find a way to get rid of thouse files.
so now I know I can't delete them in ubuntu too....what am I suppose to do now..I don't want to format it and reinstall winxp.
mmm...[/QUOTE]

have you tried booting into windows safe mode to try to delete them? thats all i can really think of now.. havent used windows in a while

---

### Post by Kilz on 2006-06-30
[QUOTE=MAXDDARK]thanx for the replyes...there are some files and folders on my winxp partition (ntfs) that winxp just refuses to delete it always saying that the file is curently in use - but it's not true as far as I know , and I want to find a way to get rid of thouse files.
so now I know I can't delete them in ubuntu too....what am I suppose to do now..I don't want to format it and reinstall winxp.
mmm...[/QUOTE]
[Here is a solution. ]("http://www.softwarepatch.com/software/moveonboot.html")I had the same problem on XP with 2 directories that I added but could not remove because I got the " File is in use" errors. I think it was caused by some spyware, because it kept happeneing to diffrent files and folders. Thank god my spyware days are behind me because of Linux/Ubuntu.

[quote=joshrobinson]awhile ago when i used to run suse, i enabled NTFS writing on a test partition (something i wouldnt mind losing some data on) and it worked, but was HORRIBLY slow.. now this was awhile ago it could have gotten better.. i disabled it right away.. i didnt lose any data for the few days i messed with it.. but i decided i was just better off using fat32.. but since then im pure ext3[/quote]
Im another ex SuSE user. :grin:

---

