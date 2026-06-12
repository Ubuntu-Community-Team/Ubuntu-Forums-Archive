---
title: "Fontconfig Error"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Blue_Sky on 2006-12-29
Hi,
I'm trying to edit the file "/etc/X11/xorg.conf", but when I try "sudo gedit xorg.conf" I get the following error:
Fontconfig error: "~/.fonts.conf", line 1: no element found

The word processor window appears, but there is nothing there. I have tried to search for the file with "Search For Files..." , and found it, but I can not save any changes. Btw, I get the above error whenever I try to open a file of type "plain text document".
Is there another way to edit the xorg.conf file, or ultimately get rid of the error?

Thanks, Blue

---

### Post by angkor on 2006-12-29
I don't know how to get rid of that error, but what happens when you try a different editor:

```
sudo nano /etc/X11/xorg.conf
```

btw, what's the output of:

```
cat .fonts.conf
```

---

### Post by Blue_Sky on 2006-12-29
Using nano worked just fine. Thanks for introducing it - it helped a lot. 
I get no output when I try "cat .fonts.conf"; the terminal doesn't even skip a line. Just to check I tried "cat fonts.conf" and got an error telling me that the file does not exist.
When I tried "sudo nano .fonts.conf" there was nothing there. It was telling me that the file is 0 lines long. Does this mean I'm missing the file?

---

### Post by angkor on 2006-12-29
Yes, nano is a nice editor to use.

My .fonts.conf looks like this:

```

<?xml version="1.0"?><!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
 <match target="font" >
  <edit mode="assign" name="hinting" >
   <bool>true</bool>
  </edit>
 </match>
 <match target="font" >
  <edit mode="assign" name="hintstyle" >
   <const>hintmedium</const>
  </edit>
 </match>
</fontconfig>
```

You can try inserting these lines in your .fonts.conf (this is a hidden file in my home dir). I don't remember changing it so maybe this is edgy's default .fonts.conf. You can see if gedit works after the change. If not you can always delete the file again.

```
nano .fonts.conf
```

Copy paste the lines into the empty file and save and exit.

---

### Post by Blue_Sky on 2006-12-29
I am no longer getting the error. Thanks a lot for your help.
Blue

---

### Post by angkor on 2006-12-29
> **Blue_Sky said:**
> I am no longer getting the error. Thanks a lot for your help.
Blue

Your welcome. I'm glad it worked, now you at least have a choice between nano and gedit. :)

---

