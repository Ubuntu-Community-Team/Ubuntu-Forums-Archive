---
title: "Symbolic Link"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by JNowka on 2006-01-29
I was wondering if there was a way to create a symbolic link automatically for my modem at startup.  It is annoying to have to make it everytime I boot up linux.

Currently I have to type

ls -s /dev/536ep0 /dev/modem

If anyone can help it will be very appreciated.

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=JNowka]I was wondering if there was a way to create a symbolic link automatically for my modem at startup.  It is annoying to have to make it everytime I boot up linux.

Currently I have to type

ls -s /dev/536ep0 /dev/modem

If anyone can help it will be very appreciated.[/QUOTE]
Maybe you could just put the command in a script and add it to the end of the system startup with the update-rc.d command.

---

### Post by JNowka on 2006-01-29
Thank you for your suggestion.

I have already had someone help me on the hardware support forum.

Thank you for your help :)

---

