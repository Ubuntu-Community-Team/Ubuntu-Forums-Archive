---
title: "what is this partition?"
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by will954 on 2007-01-02
[IMG]http://i10.photobucket.com/albums/a126/cuffless_remz/Screenshot.png[/IMG]

the first one. i need to see if i need it. when i try to make a swap partition (i have the unallocated space) i get the error message

it is not possible to create more then 4 primary partitions.

can anyone help

---

### Post by earobinson on 2007-01-02
I cant tell you waht it is, you could mount it and explore it, however yes hdds only support 4 primary partitions!

---

### Post by will954 on 2007-01-02
how would i go about mounting?

---

### Post by raul_ on 2007-01-02
```

sudo mount /dev/sda1 /mnt

```

and see what's in it

---

### Post by earobinson on 2007-01-02
> **raul_ said:**
> ```

sudo mount /dev/sda1 /mnt

```

and see what's in it

close first you need to make a new dir in mnt ```
sudo mkdir /mnt/<new dir name>
``` then mount it with the above command ```

sudo mount /dev/sda1 /mnt/<new dir name>

```

and you guessed it your dir is now mounted to /mnt/<new dir name>

---

### Post by raul_ on 2007-01-02
i usually just mount them in /mnt :-k why create another folder?

---

### Post by will954 on 2007-01-02
how do i see whats in it? i did what raul_ said

---

### Post by mxrten on 2007-01-02
Browse /mnt in a file manager or:

```
ls /mnt
```

As the error message states there cannot be more than 4 *primary* partition on a disk. To have more one of them must be an *extended* partition which is a container for *logical* partitions.

---

### Post by bodhi.zazen on 2007-01-02
> **raul_ said:**
> i usually just mount them in /mnt :-k why create another folder?

1 directory for each partition you wish to mount (for those of us who have more then 1).

---

### Post by earobinson on 2007-01-02
you can use your terminal or file browser to go to that location eg ```
cd /mnt
``` in the terminal or in your gnome browser type /mnt in the path name

---

### Post by earobinson on 2007-01-02
> **raul_ said:**
> i usually just mount them in /mnt :-k why create another folder?
> Mount points for temporary mounts by the system administrator. [http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html](http://www.comptechdoc.org/os/linux/usersguide/linux_ugfilestruct.html)

/media is where most mounts go today neways

---

### Post by bigken on 2007-01-02
partitions like this are usually the makers diagnostic tools


or a small group of files to implement a OEM install over a network

I very much doubt you will find anything of any use in the partition

---

### Post by will954 on 2007-01-02
right next bit. i have made a swap partition of around 2gb. i then get onto this screen and have no idea what it means. i have a 48gb partition for linux which is sda3 and my swap partition is sda1

[IMG]http://i10.photobucket.com/albums/a126/cuffless_remz/Screenshot2.png[/IMG]

---

### Post by bigken on 2007-01-02
change it to the 2gig partition

---

### Post by will954 on 2007-01-02
change what? if any of you can help me on msn or aim it would be a lot easier

think i got you. i changed it from 54 mgs to 2gb

---

### Post by The Noble on 2007-01-02
Might want to blur the IM names as well. I doubt that anyone will be prownling around here, but you never know... ;P

---

### Post by bigken on 2007-01-02
if you click on the partition you will find you can change them

---

### Post by earobinson on 2007-01-02
im not really sure i understand your question

---

### Post by bigken on 2007-01-02
delete 55mb partition and and format the 1.95 gig as swap

---

### Post by will954 on 2007-01-02
> **The Noble said:**
> Might want to blur the IM names as well. I doubt that anyone will be prownling around here, but you never know... ;P

they are msn names. you would need the addy

---

### Post by raul_ on 2007-01-02
i have 1GB RAM, 150MB swap file, and i never use more than 10% of swap...maybe 2GB is a waste

---

### Post by louieb on 2007-01-03
What is is sda3? If you want to use the unallocated space there are two options.
One is to resize sda4 larger to use up the space..
The other is to delete sda3 or sda4 and add it back as an EXTENDED   partition.
Then you can create logical partitions inside of the unallocated space. (up to 14 logical partitions on a SATA drive). 
Got to go to work now. Hope this helps.

---

### Post by Lord Illidan on 2007-01-03
Just make an extended partition. I have one too, and it's incredibly useful.

---

