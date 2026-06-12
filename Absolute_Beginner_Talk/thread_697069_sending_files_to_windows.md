---
title: "sending files to windows"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by phoenix5002 on 2008-02-14
My printer is hooked up to a WindowsXP machine and I would occasionally like to send files to my windows computer for printing.

I don't want to share the printer so I'd like to just send the file directly to the computer not the printer.

I know about samba but It just seems like there should be a much easier way to do what I want.
Could I just right click the folder I want to share and go: Share folder.
and then somehow access it from my windows computer?

---

### Post by klytu on 2008-02-14
> **phoenix5002 said:**
> My printer is hooked up to a WindowsXP machine and I would occasionally like to send files to my windows computer for printing.

I don't want to share the printer so I'd like to just send the file directly to the computer not the printer.

I know about samba but It just seems like there should be a much easier way to do what I want.
Could I just right click the folder I want to share and go: Share folder.
and then somehow access it from my windows computer?

If the computers are networked already, you could do the reverse. You could set up a folder on your XP machine as shared and then copy the files you want to print into the shared folder. 

But really, I think the easier way would be to just share the printer connected to the Windows machine. Why don't you want to share the printer?

---

### Post by hollaburoo on 2008-02-14
Keep in mind if you're transferring plain text files to Windows that the line endings won't be the same.

---

### Post by stevejesus on 2008-02-14
Use paper airplanes instead.

---

### Post by zerhacke on 2008-02-14
It's possible his printer is not supported by Linux, which would explain wanting to send the files over to Windows pre-printing.

If you're going to connect to the Windows box regularly I suggest installing the smbfs package and setting up /etc/fstab accordingly.

---

### Post by solitaire on 2008-02-14
Here's an "out of the Box" idea?

Have both Comps got Bluetooth? I sometimes use Bluetooth to send files to my Windows PC at work when i've got my laptop there. saves in any complicated Network settings...

---

