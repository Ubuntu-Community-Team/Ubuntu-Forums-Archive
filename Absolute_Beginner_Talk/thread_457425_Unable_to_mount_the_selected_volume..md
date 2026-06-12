---
title: "Unable to mount the selected volume."
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by lilro on 2007-05-28
i got a new cd/dvd combo drive and it won't work...the drive i had before worked and when i installed this one, i just took the cables directly out the 1st one and put them in the new drive. when i turn on the computer, i can here my cd spinning and the light is blinking but when i go to nautilus and double click > CD-ROM 1 it says > Unable to mount the selected volume. i clicked on show more details and it says > mount: special device /dev/hdc does not exist

any ideas on what i'm doing wrong?

---

### Post by Pragmatist on 2007-05-29
Please give the output of these commands:

```
ls /dev/hd*  /dev/sd*
```
```
lshal -s | egrep '(DVD|CD)'
```

---

### Post by lilro on 2007-05-29
its alright i got it now.

---

### Post by Pragmatist on 2007-05-29
> **lilro said:**
> its alright i got it now.

Please post your solution.

---

### Post by Inxsible on 2007-05-29
yeah ..please do post your solution,

I have that CD Rom -1 drive too ever since I upgraded to kernel 16 from kernel 15

Its a phantom drive. I have another mount point CD DVD RW -- its called which works fine

---

### Post by lilro on 2007-05-29
i opened up my pc again to take a look and it was set to slave. so i fixed it.

---

### Post by HeresJohnny on 2007-06-01
Hello  everyone, I have this same problem, but my CD/DVD burner is internal, and somehow not being recognized.  Following is the output of the commands Pragmatist asked for.
```

heresjohnny@heresjohnny-laptop:~$ ls /dev/hd*  /dev/sd*
ls: /dev/sd*: No such file or directory
/dev/hda  /dev/hda1  /dev/hda2  /dev/hda5
heresjohnny@heresjohnny-laptop:~$ lshal -s | egrep '(DVD|CD)'
heresjohnny@heresjohnny-laptop:~$ lshal -s | egrep '(DVD|CD)'
```


Note that there was no output for the second command.  I was surprised about that, so I ran it twice.  I'd appreciate your help on this!

---

### Post by Pragmatist on 2007-06-01
```
lshal >>heresjohnny_lshal.zip
```

Then attach the file "heresjohnny_lshal.zip" 

(Note: Your not actually compressing a file, your just appending the extension .zip because of attachment size limitations of the ubuntu forums--don't ask!)

---

