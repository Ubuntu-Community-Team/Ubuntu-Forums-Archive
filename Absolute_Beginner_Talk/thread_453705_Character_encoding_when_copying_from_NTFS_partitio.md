---
title: "Character encoding when copying from NTFS partition"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by sergiodlc on 2007-05-24
Hi folks:

Some days ago I copied several gigabytes from an NTFS hard disc in order to move this information to a DVD. I mounted that filesystem using the customary ```
mount -t ntfs /dev/hdb8 /media/winfs
```

I observed that there were problems with accented characters but I didn't worried a lot about it. The problem is that GnomeBaker, K3B and similar programs are not letting me to burn the data into a DVD complaining about the character encoding mismatch.

Searching on the web, I found out that I should have mounted the disk using ```
mount -t ntfs -o utf8 /dev/hdb8 /media/winfs
```

Now I gave back the hard disc and i can't ask for it again.  Is there a way to recode the copied filenames and burn the data on a DVD?

Thanks in advance,

Sergio.

---

### Post by gvoima on 2007-05-24
Do you know what character encoding are on the filenames you copied? Maybe you can apply the following on those.

There's a filename encoding conversion tool in the reposities named **convmv**.

e.q. convert a folder content (filenames) recursively from iso-8859-1 to utf-8
```
convmv -f iso-8859-1 -t utf-8 --notest -r *
```

See manual for more information. (Remember to use the encoding you have on the current files instead of the ISO i gave as an example.)


There's also a way to convert the file content to another, but that usually breaks the whole file.
I had some binary files copied from a iso-8859 to utf8, the program worked even if I saw the content with weird characters.
After changing them, it broke (obviously).

---

### Post by sergiodlc on 2007-05-24
Thanks.

I tried that and didn't worked. The awful characters are just even more awful. Can this be undone?

---

### Post by sergiodlc on 2007-05-24
I have already worked out a solution from the hint suggested by gvoima. The problem was that the original encoding was cp850 instead of iso-8859-1, so I undid his suggested command using ```
convmv -f utf-8 -t iso-8859-1 --notest -r *
``` and then recoded the filesystem using ```
convmv -f cp850 -t utf-8 --notest -r *
```  and this worked like charm.

Thanks a lot, gvoima!

---

### Post by gvoima on 2007-05-25
I'm glad it worked! :)

What comes to the ISO-8859 encoding, it was only an example, i didn't mean you to use it.
I wrote on my first post, if you missed it; > (Remember to use the encoding **you have** on the current files **instead of the ISO** i gave as an example.)

---

