---
title: "Anyone tell me what this means? (image attached)"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by kaiserb_uk on 2007-10-30
[IMG]http://farm3.static.flickr.com/2019/1805845866_b3b60fde07_o.jpg[/IMG]

I get this screen when starting Ubuntu 7.10, I did a clean build over 7.04 (i.e. I reinstalled from ISO CD and chose to format the partition).

In order to boot into the OS from this point I have to CTRL-ALT-F1 where I get a screen with messages about some sort of error and "doing normal boot", then I CTRL-ALT-DEL and some sort of startup process kicks off and launches the X session.

Thanks in advance.

---

### Post by kerry_s on 2007-10-30
sounds like a bad install. use the check cd option. remember burn at 4x as a image to get the best results.

---

### Post by floke on 2007-10-30
You might also want to do a fsck on your partition there.

---

### Post by kaiserb_uk on 2007-10-30
Yeah, funnily enough it seems to run okay...

What's the proper syntax for fsck and do I run it from within Gnome?  I'm a linux noobie so spelling it out would be appreciated ;)

---

### Post by kaiserb_uk on 2007-10-30
Okay, so I ran ```
sudo fsck -a
```

and got

```
  Start cluster beyond limit (2529285685 > 1046186). Truncating file.
/030\0000000.\000z'/\010OZ&#65533;&#65533;&#65533;]&#65533;.&#65533;\222\235
  Directory has non-zero size. Fixing it.
/030\0000000.\000z'/\010OZ&#65533;&#65533;&#65533;]&#65533;.&#65533;\222\235
  Start cluster beyond limit (1277753368 > 1046186). Truncating file.
/030\0000000.\000z'/103\0000000.\000Q&#65533;
  Directory has non-zero size. Fixing it.
/030\0000000.\000z'/103\0000000.\000Q&#65533;
  Start cluster beyond limit (591522340 > 1046186). Truncating file.

```

where it stuck indefinitely.  So is a corrupt install the best guess?

---

### Post by snickers295 on 2007-10-30
> **kaiserb_uk said:**
> Okay, so I ran ```
sudo fsck -a
```and got

```
  Start cluster beyond limit (2529285685 > 1046186). Truncating file.
/030\0000000.\000z'/\010OZ&#65533;&#65533;&#65533;]&#65533;.&#65533;\222\235
  Directory has non-zero size. Fixing it.
/030\0000000.\000z'/\010OZ&#65533;&#65533;&#65533;]&#65533;.&#65533;\222\235
  Start cluster beyond limit (1277753368 > 1046186). Truncating file.
/030\0000000.\000z'/103\0000000.\000Q&#65533;
  Directory has non-zero size. Fixing it.
/030\0000000.\000z'/103\0000000.\000Q&#65533;
  Start cluster beyond limit (591522340 > 1046186). Truncating file.

```where it stuck indefinitely.  So is a corrupt install the best guess?
ya a corrupt install sounds right.
md5sum and burn the cd again and use the cd check when the cd boot menu starts up.

---

### Post by floke on 2007-10-30
You MUST run fsck on an unmounted disc - so best to do it from another OS/Live CD - I think the syntax is sudo fsck /dev/sda1 (or whatever the partition is) - the hope would be that the error might be fixable without a reinstall.

---

### Post by snickers295 on 2007-10-31
> **floke said:**
> You MUST run fsck on an unmounted disc - so best to do it from another OS/Live CD - I think the syntax is sudo fsck /dev/sda1 (or whatever the partition is) - the hope would be that the error might be fixable without a reinstall.
seems logical...

---

### Post by kaiserb_uk on 2007-10-31
CD checked out fine, also ran a memtest while I was there with no issues.

I tried to run fsck after booting from the CD but although I could see the partition listed in Places/Computer it wasn't mounted so I had no idea how to see its path or specify it in the fsck command?

---

### Post by hyper_ch on 2007-10-31
it's
```

/dev/hd**

```
or
```

/dev/sd**

```

Run 
```

sudo fdisk -l

```

That will list all the partitions.

---

