---
title: "truecrypt"
date: 2006-08-25
forum: Absolute Beginner Talk
---

### Post by airzer0 on 2006-08-25
this is the error i recieve when i try to mount and map my volume:
Enter password for '/dev/sda1': 
device-mapper: reload ioctl failed: Invalid argument
Command failed
i just installed truecrypt and excrypted my exter hd, but will not mount any ideas would be greatly appriciated

---

### Post by orb9220 on 2006-08-25
You want to list out the commands to type like mine to I use:

sudo truecrypt /home/orb/Drives/hdd1/Work/img/home/orb/Drives/hdd1/Work/temp/

this takes my truecrypt volume img and maps it to another folder path on same drive.

What are you using to mount volume. Also go to the truecrypt forums for more help.

---

### Post by airzer0 on 2006-08-26
yea thanks i didn't do my home work, i have 120gb hard drive and i wanted to encrypt the whole drive so i did "sudo truecrypt -c" then i followed to guide . it asked me a few questions and when i got to the "what partition do you want to encrypt" i put "/dev/sda1". it took 4hrs and it is encrypted, but it will not mount. so i guess i fubard it. back to the drawing boards...

---

### Post by 454redhawk on 2006-08-26
> **airzer0 said:**
> yea thanks i didn't do my home work, i have 120gb hard drive and i wanted to encrypt the whole drive so i did "sudo truecrypt -c" then i followed to guide . it asked me a few questions and when i got to the "what partition do you want to encrypt" i put "/dev/sda1". it took 4hrs and it is encrypted, but it will not mount. so i guess i fubard it. back to the drawing boards...

I think you may have encrypted it incorrectly. If you wanted to do the whole drive I think it should have been /dev/sda not /dev/sda1.

When you mount it you will the same /dev/sda.

Also did you use FAT? if so you will need the -u option

So you mounting command might look like this if you used FAT

```
truecrypt -u /dev/sda /somedir/mountpoint
```

At first try putting your container in your /home/user/ dir and also try mounting it in your home as well /home/user/mountpoint

---

