---
title: "Deleting Trash on USB Flash Drive (Ubuntu Fiesty)"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by goclimb4123 on 2007-08-16
Hi, I have searched all relevant posts and haven't been able to find anything to help me. 

I can't delete the .Trash file on my USB Flash Drive, even with something like:

rm -- /media/MINI\ TD/.Trash-lucas

as "lucas" is my username. when I finally do get the command right, it says that the flash drive is read-only, so then I go into the flashdrive and under Properties->Permissions I attempt to switch it to read-and-write but I can't. I am the only user on the computer so I'd assume administrator as well but I don't know how to change that if I'm not, but I doubt that's the problem. 

Does anyoneknow how to change my flash drive to read-and-write so I can delete the .Trash file?

I have a Memorex 2GB.

thanks, 
Luke

---

### Post by sourjax on 2007-08-16
try

```
sudo rm -R /media/MINI\ TD/.Trash-lucas
```

or just...

```
sudo rm -R /media/MINI
```


I had trouble with the same thing. I used basically the same code but mine was different because my USB was named differently.

```
sudo rm -R /media/disk
```

---

### Post by goclimb4123 on 2007-08-16
ok, I tried all three and the first one works, as in, it knows what file im talking about, but it still says:

lucas@ubuntu:~$ sudo rm -R /media/MINI\ TD/.Trash-lucas
rm: cannot remove `/media/MINI TD/.Trash-lucas/ g\033 \r&#9573;¡k., \027': Read-only file system
rm: cannot lstat `/media/MINI TD/.Trash-lucas/v&#9579;&#9563;nídi\\.«¬è/\030b&#8805;&#8805;&#9524;\020\a@.&#948;7N/"&#920;\030i\v&#9618;å\031.&#9472;\032ñ': Input/output error

I think we have to figure out how to change it from read only to read-and-write.

---

### Post by sourjax on 2007-08-16
That's something I'm trying find out in another thread as well...

I tried

```

sudo chmod 0777 /media/Storage/

```

but it just says

```

chmod: changing permissions of `/media/Storage': Read-only file system

```

so I'm at a loss myself? :confused:

---

### Post by goclimb4123 on 2007-08-16
ok, thanks for your help man... I guess im going to keep plugging away with the 'chmod' command and see if I can get any results.

if you come up with anything let me know please!

thanks for your help,

luke

---

### Post by sourjax on 2007-08-17
Okay try this, it worked for me. :guitar:

```

sudo umount /media/MINI\ TD/.Trash-lucas

```

then

```

sudo mount -o rw /media/MINI\ TD/.Trash-lucas

```

This should unmount your USB drive and then mount it w/ read/write permissions. Then you can delete what you need. :)

Let me know if this works or not. In an effort to learn more about Linux in general, I was playing around w/ re-mastering the  Knoppix LiveCD and found it (the code) in the book "Linux Live CDs" and tried it and it worked!

---

### Post by goclimb4123 on 2007-08-24
I tried:

sudo umount /media/MINI\ TD

and 

sudo umount/media/MINI\ TD/.Trash-lucas

and then, after sucessfully unmounting the drive I tried:

sudo mount -o rw /media/MINI\ TD

but it says:

mount: only root can do that

what does this mean?

thanks, Luke

---

