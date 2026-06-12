---
title: "RAR split archieves problem"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by protenniser on 2008-02-16
Hi all,
This question has nothing to do with ubuntu but I hope so&#305;me of you can help me about this issue.
Let's say that I have a 800 mb. file, I rared it with winrar (by splitting 400 mbs.) so I get
a.part1.rar -> 400 mb.
a.part2.rar -> 400 mb.
After that somehow I deleted a.part1.rar, and re rared the original file by the same winrar (again splitting 400 mbs.) and I get,
a.part1.rar -> 400 mb.
a.part2.rar -> 400 mb.
My question is can I use the second a.part1.rar with the first a.part2.rar? And recreate the or&#305;ginal file?
Any help would be appreciated, thanks...

---

### Post by ashmew2 on 2008-02-16
I think so Yes , if you created the second set of archives with exactly the same settings as the first set , i think you can use them interchangably.

How about giving it a try ? :P

---

### Post by protenniser on 2008-02-16
Thanks for the morale!
The problem is that my file is 8 gbs. and I have used the options splitting 400mbs. and putting a password and creating a recovery point with 10% in my original rar. Then I have lost 2 parts, and rerared. However this time the rerared files gave a CRC error in the 3rd arcieve (I want to emphasize that every rar process takes 2.5 hours!) and so my lost parts (11 and 20), I couldn't use it from the 2nd rar process. However I also think that this is because that there happened a problem during the second rar process that gives me CRC error at the 3rd part.
So I am still optimist and try for a 3rd time, (with your support) and will report back as soon as I find out. (I wanted to ask before 3rd time since every rar process takes 2.5 hours :()
Thanks for support!

---

### Post by protenniser on 2008-02-16
Hi all,
It didn't work unfortunately :( I am getting CRC error (wrong password?) All gurus, please help me! Is there no way to bypass this?
Thanks all...

---

### Post by asmoore82 on 2008-02-16
I'm very confused, if you have the ability to "rerar" this implies that you have the original files...
and so, if you have the original, why would you need to bother extracting from the broken archive?

---

### Post by protenniser on 2008-02-16
Hi,
You are right I haven't told the whole story. The problem is that, I am trying to upload the splitted parts to a ftp server in order a friend of mine to download them from there and recreate the original file. I have already uploaded 18 parts (7.2 gbs.) but as I mentioned 2 parts are missing and now the files that I upload and now create from the original file canNOT be used interchangably. Now either somebody will help me to use them interchangably or I am doomed to upload another 8gbs. of data. So that's the problem.
Thanks...

---

### Post by 444 on 2008-02-16
I would play around with the rar repair feature to get unrared pieces of the file, then try to mash those together properly.

Oh, and don't recompress videos, if this is a video. Use "store" level compression so you don't waste hours.

---

### Post by asmoore82 on 2008-02-16
BitTorrent can do all of the splitting/uploading/downloading/combining/data integrity checking *for* you.
I would say start a private tracker and have your friend torrent the data directly from you.

---

### Post by Vadi on 2008-02-16
Yeah, I'd say too that using bittorent is the best way to go here. It handles everything for you, so you just press a button to seed, and you're done.

---

### Post by protenniser on 2008-02-16
I couldn't understand this totally, can you explain a little?

> **444 said:**
> I would play around with the rar repair feature to get unrared pieces of the file, then try to mash those together properly.

Oh, and don't recompress videos, if this is a video. Use "store" level compression so you don't waste hours.

Yes the file is a video, from what I understand you are suggesting me to directly store the video without compressing since there is not too much gain from compression? Is that right?

---

### Post by protenniser on 2008-02-16
> **asmoore82 said:**
> BitTorrent can do all of the splitting/uploading/downloading/combining/data integrity checking *for* you.
I would say start a private tracker and have your friend torrent the data directly from you.

Thanks for suggestion, but it won't matter, I will be uploading 8 gbs. again in that matter too (I guess) so I am trying to find a backdoor for my working 7.2 gbs. Is there no suggestion aobut the file interchangibility?

---

### Post by asmoore82 on 2008-02-16
RAR is proprietary and, IMHO, a pain in the hind quarters, I avoid it like the plague.
It pains me that it has gained such popularity for its ability to do a
simple trick like file splitting and concatenating

For future headache-free use of Free Software,
if you and your friend are both on *NIX systems, the `split` command line utility
can break apart files and `cat` can concatenate them back together.
this method, combined with `md5sum` is foolproof and much cleaner
and more efficient than any proprietary what-have-you.

---

### Post by Vadi on 2008-02-16
Now if there was an easy tool which would allow you to use those commands within 5 mins of opening an app, that would be great. Otherwise, not everybody wants to spend time understanding man pages and the syntax.

---

### Post by protenniser on 2008-02-16
> **asmoore82 said:**
> RAR is proprietary and, IMHO, a pain in the hind quarters, I avoid it like the plague.
It pains me that it has gained such popularity for its ability to do a
simple trick like file splitting and concatenating

For future headache-free use of Free Software,
if you and your friend are both on *NIX systems, the `split` command line utility
can break apart files and `cat` can concatenate them back together.
this method, combined with `md5sum` is foolproof and much cleaner
and more efficient than any proprietary what-have-you.

Hi, as I said, this suggestion may be ok for the upcoming file transfers however, now I am trying to recover my 7.2 gbs. so I need some winRAR advise. Thanks for another advise though.

---

### Post by 444 on 2008-02-16
> **protenniser said:**
> I couldn't understand this totally, can you explain a little?



Yes the file is a video, from what I understand you are suggesting me to directly store the video without compressing since there is not too much gain from compression? Is that right?

Yeah,

---

### Post by protenniser on 2008-02-16
444, thanks for suggestion! I'll use it for the next archieves, it saves a lot of time! Now there is only left to recover 2 rar files :)

---

### Post by protenniser on 2008-02-16
Hi all,
I have a new information that may help:
This logic works perfectly with the files that are not added a password, however since my files have a password, I am failing. Any ideas how to bypass password, it is really silly to get a password error, although the files are identical and have the same pass. I tkink I am having that error because I have rared them in different times. Any ideas?
Thanks...

---

### Post by protenniser on 2008-02-17
Hi all,
I have been mailing with winRAR support and they told me that it is impossible to recover the original fiel in my case, thanks for all help though. I am writing this as an information that may help in the future.
If you want to get interchangible rar split files using winRAR, do NOT use password!

---

