---
title: "Corrupt OSX hard drive"
date: 2008-04-02
forum: Apple Intel Users
---

### Post by ccslaxer44 on 2008-04-02
I've searched for this all over and have yet to see anything that can help me, Yesterday while surfing my macbook running OSX leopard froze solid. i held down the button to shut if off, and then turned it back on, i was able to log in and then got an error that said i had inserted a bad disk, and then nothing would load other than my wall paper. i've tried to mount the partition in ubuntu using a live cd, but i get the error "mount: not a directory" all i want to do is either recover stuff off the drive, mainly 12500 songs, or possibly fix the corruption. i'm a newb so bear with me

---

### Post by hackersmovie on 2008-04-02
just a shot in the dark here:

Did you try to boot from the OS X CD? If not, do that (hold "C" while booting) and run Disk Utility to repair disk permissions. It may get your OS X partition back, I would also do a "Disk Repair" while your in Disk Utility. At the same time, when your booting, holding "Option-Command-P-R" will reset the PRAM which could also help. These are the first steps I take when trying to solve any disk issues. 90% of the time, it fixes it. . . 

Worth a shot. . .

---

### Post by ccslaxer44 on 2008-04-02
i've booted to the OSX disk to try the disk utility, but when i run it i get an error and it stops repairing, i'll try to reset the pram,

---

### Post by hackersmovie on 2008-04-02
> **ccslaxer44 said:**
> i've booted to the OSX disk to try the disk utility, but when i run it i get an error and it stops repairing

Stops repairing what? Permissions or Disk? Does it give you any errors or codes as to why it quit?

---

### Post by ccslaxer44 on 2008-04-02
when i boot to the OSX cd, the option to repair the permission is grayed out and not an option, when i click on the repair disk, it will run for afew seconds, and then i get an error and a window pops up that says "first said failed disk utility stopped repairing disk0s2 because the following error was encountered: The underlying task reported failure on exit"

---

### Post by hackersmovie on 2008-04-02
[[img]http://img.skitch.com/20080402-xeuwhanak14eqnh1bfcr3s9ywu.preview.jpg[/img]](http://skitch.com/hackersmovie/e32p/disk-utility-ubuntu-forums1)[Click for full size](http://skitch.com/hackersmovie/e32p/disk-utility-ubuntu-forums1) - [color=#A7A7A7]Uploaded with [plasq](http://plasq.com)'s [Skitch](http://skitch.com)[/color]

---

### Post by ccslaxer44 on 2008-04-02
I don't have those available, i also dont have a partition thats labeled Macintosh HD, all there is is disk0s2 and disk0s3

---

### Post by cyberdork33 on 2008-04-02
I started getting similar errors a while back and my hard drive died. 

I have seen people get that error message though and Disk Utility not be able to fix it. DiskWarrior ought to be able to fix it though. Unfortunately it costs money...

Another option would be to install OSX from the cd to an external hard drive, then boot from the external and mount the internal drive in order to recover any files you can get to. 

Your Ubuntu error just sounds like you were mounting it incorrectly, but if journaling is not disabled, you cannot mount your OSX partition in Linux anyway.

EDIT:

Have you tried starting up in single-user mode? Hold CMD+S during startup and follow the disk repair instructions.

---

### Post by ccslaxer44 on 2008-04-02
i'll try that, thanks

---

