---
title: "Locked out ._.; (password)"
date: 2006-06-21
forum: Absolute Beginner Talk
---

### Post by kuriku on 2006-06-21
I had a friend of mine install Ubuntu for me over half a year ago and now neither of us remembers the password to the system. I'm wondering if there's any way to "retrieve" the password or change it. At the moment I'm in the process of downloading Ubuntu.iso with the hope that I can reinstall the whole thing ;_; However I'm having doubts since I tried using a bootable Windows rom and it just went straight to Ubuntu...

Thanks in advance to anyone who answers my silly question ^^; So far I've looked around the "guides" with no luck.

- Jessica

---

### Post by oscar on 2006-06-21
When you see grub select recovery mode. Then go ```
passwd username
``` (where username is your username) and enter a new password.

---

### Post by rowanparker on 2006-06-21
Make sure you set up your BIOS to boot from floppy before hard disk.

Do you mean your user password or BIOS password or Grub password?

Rowan.

---

### Post by kuriku on 2006-06-21
...Ah? I have a graphic interface and really wouldn't know when/where to type 
> passwd username

And I'm ashamed to say that I don't know the difference between a BIOS and Grub password ;__; I'll go look it up now though ^^;

---

### Post by rowanparker on 2006-06-21
Well, can you boot Ubuntu?
If you can then it's nothing to do with Gurb or BIOS and it's your root pass your after.

To restore root pass do as oscar said.

Rowan.

---

### Post by kuriku on 2006-06-21
Thank you!

---

### Post by anaconda on 2006-06-21
And if you dont have "recovery mode" visible in your boot-loader (I assume it is Grub)

You can type "e" to edit the current boot entry.  Just go to where it reads "quiet ro" etc.. and add 
single
to that line. and select "esc" and "boot"

After that it should boot to text-mode with root rights.. after it stops loading you should press enter a couple of times to get the prompt, where you can type the "passwd username" or "adduser" to make a new user.. (if you dont remember your username)

Hope I wasn't too confusing...

---

### Post by rowanparker on 2006-06-21
[QUOTE=kuriku]Thank you![/QUOTE]
No Problem :D

---

