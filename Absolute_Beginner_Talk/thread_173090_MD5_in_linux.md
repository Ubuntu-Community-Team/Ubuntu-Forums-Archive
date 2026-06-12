---
title: "MD5 in linux?"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Belathor on 2006-05-09
Hi, this is has a really easy answer I think, but I can't figure it out. I'm trying to check MD5 of Austrumi and BASH is telling there is "no such file or directory" when there clearly is! Therefore, I think I'm typing it wrong.

```
kyle@kyle-xfcedesktop:~$ md5sum austrumi-1.2.0.iso
md5sum: austrumi-1.2.0.iso: No such file or directory
```

and this:

```
kyle@kyle-xfcedesktop:~$ md5sum -c  austrumi-1.2.0.iso
md5sum: austrumi-1.2.0.iso: No such file or directory

```

I can confirm that austrumi is typed in right because I dragged the iso into BASH to see if I was typing it wrong.

Grr... How do I check iso's in linux? Thanks!

---

### Post by skippy81 on 2006-05-09
I know this seems a bit silly, but have you tried doing an > ls first to make sure that the file is in your current working directory?  AFAIK md5sum will work with any type of file, so there shouldnt be a special rule for ISOs.

After youve entered the md5sum command, you should be able to use the tab key to assist in automatically completing the name of the file for the sake of accuracy.  > md5sum aus and then hit tab a couple of times, bash should write the full name of the iso in for you.

---

### Post by cgjones on 2006-05-09
Have you tried this:
```

md5sum -b austrumi-1.2.0.iso

```
This will run md5sum in binary mode, which may be what you need for an .iso.

---

