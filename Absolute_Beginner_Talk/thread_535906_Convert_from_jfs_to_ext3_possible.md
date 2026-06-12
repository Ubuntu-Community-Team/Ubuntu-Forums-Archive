---
title: "Convert from jfs to ext3 possible?"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by wootwoot123 on 2007-08-27
Is there a way to convert my filesystem from jfs to ext3?

---

### Post by felicity on 2007-08-27
If by "convert" you mean reformatting, sure you can do it. If you mean keeping your current files, you'll have to save them elsewhere first.

---

### Post by wootwoot123 on 2007-08-30
I just tried to copy my files off using dd but ran into problems. I made an image and after this I formatted the drive as ext3. I then put the image back on and it reformatted to jfs. What is the correct way of doing this?

---

### Post by Paulmd on 2007-08-31
> **wootwoot123 said:**
> I just tried to copy my files off using dd but ran into problems. I made an image and after this I formatted the drive as ext3. I then put the image back on and it reformatted to jfs. What is the correct way of doing this?

You can't do an image, for that reason.

Copy the files into a a different location, then reformat, and copy them back. 

At least in theory. What were the problems you got with dd?

---

### Post by Paulmd on 2007-08-31
> **wootwoot123 said:**
> I just tried to copy my files off using dd but ran into problems. I made an image and after this I formatted the drive as ext3. I then put the image back on and it reformatted to jfs. What is the correct way of doing this?

You can't do an image, for that reason.

Copy the files into a a different location, then reformat, and copy them back. 

At least in theory. What were the problems you got with dd? And why didn't you use the more normal cp?

---

### Post by wootwoot123 on 2007-08-31
Will copying the files keep the correct file permissions?

---

### Post by Bushwack on 2007-08-31
cp -a will preserve permissions, but depending on the capabilities of the filesystem you back your files up to some information may be lost

Making a tar of the files will preserve the permission (add the -p --some-owner flags when extracting if you aren't doing it as root).

---

### Post by wootwoot123 on 2007-09-01
I have copied all of the files, reformatted the partition as ext3 and copied the files back over. I changed fstab to say ext3 instead of jfs but I am stuck. When I boot up I get to the splash screen but it does not progress at all. I know I am missing something but am not sure what. What else do I need to change to get this working? Thank you.

---

### Post by Paulmd on 2007-09-03
> **wootwoot123 said:**
> I have copied all of the files, reformatted the partition as ext3 and copied the files back over. I changed fstab to say ext3 instead of jfs but I am stuck. When I boot up I get to the splash screen but it does not progress at all. I know I am missing something but am not sure what. What else do I need to change to get this working? Thank you.

Out of morbid curiosity, what happens if you change fstab back to jfs? (back it up) this is a TOTAL GUESS.  I suppose the worst that could happen is it still won't work.

---

