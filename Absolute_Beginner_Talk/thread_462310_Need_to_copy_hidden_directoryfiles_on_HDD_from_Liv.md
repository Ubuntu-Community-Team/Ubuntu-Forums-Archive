---
title: "Need to copy hidden directory/files on HDD from Live CD"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by TRex on 2007-06-02
[Newbie, but can usually follow directions] I totally fouled up my installation (please don't ask! :redface: ) and need to re-install. But first I need to save data on the HDD, including hidden files and hidden directories. If possible, I'd like to copy stuff to a Windoze network share. I would really appreciate someone providing me specific steps. TIA.

---

### Post by bodhi.zazen on 2007-06-02
> **TRex said:**
> [Newbie, but can usually follow directions] I totally fouled up my installation (please don't ask! :redface: ) and need to re-install. But first I need to save data on the HDD, including hidden files and hidden directories. If possible, I'd like to copy stuff to a Windoze network share. I would really appreciate someone providing me specific steps. TIA.

1. Configure your windows share.

2. Boot the Ubuntu Live CD.

3. Go under Places -> Network (in the top menu).

4. Navigate you you windows share ...

5. Copy away ...

---

### Post by TRex on 2007-06-02
Thanks, but the BIGGEST problem I have is getting access to hidden directories and files. I don't have proper permission. I suspect there may be a 'sudo' command, but it only seems to refer to the Live CD, not the HDD.

---

### Post by bodhi.zazen on 2007-06-02
> **TRex said:**
> Thanks, but the BIGGEST problem I have is getting access to hidden directories and files. I don't have proper permission. I suspect there may be a 'sudo' command, but it only seems to refer to the Live CD, not the HDD.

You will need to mount the hard drive first of course (mount it at /mnt if you want)

```
sudo mount /dev/hdxy /mnt
```Wher /dev/hdxy is the partition to be mounted.

Then you can open nautilus with :

```
gksudo nautilus /mnt/
```

Copy away ...

---

### Post by TRex on 2007-06-02
I think I managed to mount the hard drive -- [sudo mount /dev/hda1] gets this:
mount: according to mtab, /dev/hda1 is already mounted on /media/disk
(so I already got it, right?)

I think I managed to mount a flash drive -- [sudo mount /dev/sde1] gets this:
mount: according to mtab, /dev/sde1 is already mounted on /media/CORSAIR
(so I already got it, right?)

but the command [gksudo nautilus /mnt/] opens a browser that seems to only see the Live CD

So I tried this on terminal:
cp /dev/hda1/home/username/.mozilla/*.* /dev/sde1/username
and got this:
cp: accessing `/dev/sde1/username': Not a directory

I tried again:
cp /dev/hda1/home/username/.mozilla/*.* /dev/sde1/username/
and got this:
cp: accessing `/dev/sde1/username/': Not a directory

Then I tried:
cp /dev/hda1/home/username/.mozilla/*.* /dev/sde1/username/*.*
and got this:
cp: accessing `/dev/sde1/username/*.*': Not a directory

What am I doing wrong?

---

### Post by bodhi.zazen on 2007-06-02
Well, it will be easier to use the terminal perhaps.

First sudo the copy command.

Second, use the -r flag for directories.

Third, use the actual username and not "username".

```
sudo cp -r /media/disk/home/TRex/.mozilla/  /dev/sde1/
```

And on ...

Heck, you can 

```
**[Color=navy]sudo cp -r /media/disk/home/ /media/CORSAIR[/color]**
```


BUT YOU CAN NOT READ/WRITE THE DEVICE ITSELF :(

So > cp **[color=red]/dev/hda1**[/color]/home/username/.mozilla/*.* **[color=red]/dev/sde1**[/color]/username

IS A BIG NO-NO :twisted:

_Note_: Don't worry, I did the same thing when I was learning as well :rolleyes:

---

### Post by TRex on 2007-06-02
:) -- I'm making progress. The [.mozilla] directory copied ok. But then I tried to do the same with the [.mozilla-thunderbird] directory. I got this:
cp: cannot create regular file `/media/CORSAIR/TRex/.mozilla-thunderbird/nb2klqlt.default/Mail/Local Folders/STML ': Invalid argument

Regarding your warning:
BUT YOU CAN NOT READ/WRITE THE DEVICE ITSELF 
(I don't know how to do quotes or how to make stuff appear in the code box)
I appreciate the warning. That's why 'Newbie' rhymes with 'Booby'!

Once I get the Thunderbird folder copied, I'll be ready to re-install. Thanks for all the help.

---

### Post by bodhi.zazen on 2007-06-02
Can you post the exact command that gave that error ?

Or, you can go back to nautilus now that you know where to go :)

```
gksudo nautilus /media/disk/home/TRex
```

* You can tell nautilus to show hidden files

View -> Show Hidden

---

### Post by TRex on 2007-06-02
The command I entered was:
[sudo cp -r /media/disk/home/TRex/.mozilla-thunderbird/  /dev/sde1/]
The error message it produced was:
cp: cannot create regular file `/media/CORSAIR/TRex/.mozilla-thunderbird/nb2klqlt.default/Mail/Local Folders/STML ': Invalid argument

I tried the nautilus command -- this time with the [/media/disk/home/TRex] added so it took me right there and did a GUI drag-n-drop to copy and then checked the results. It is missing one file:
/media/disk/home/TRex/.mozilla-thunderbird/nb2klqlt.default/Mail/Local Folders/STML
This file appears to be a mail store :-( -- it opens with gedit and has lots of plain text of mail, the icon is a purplish diamond with gears, right-clicking and choosing properties for the file says 'Type: Mailbox file' and 'MIME type: application/mbox'

I have tried to drag-n-drop the single file, but nothing happens: it doesn't copy and no error msg comes up.
I have even tried to drag-n-drop the file to a network share -- same results. The file just doesn't want to copy. (grrrrr)  :-/

So close.

---

### Post by bodhi.zazen on 2007-06-02
I am not so sure about that file ... I think it contain secure personal information and I am not sure it needs to be copied.

But, I am not positive.

---

### Post by TRex on 2007-06-02
Came up with a workaround.

Copied the Sent file (same type and MIME type as SMTL) and renamed the copy 'SMTL', then opened it in gedit and deleted everything, opened original SMTL file, copied contents and pasted them into the newly created SMTL file and saved. File size matches, type and MIME type still match. I am hopeful.

Thanks for everything.

Is there a way to mark this 'Resolved'?

---

### Post by bodhi.zazen on 2007-06-02
Yes, thank you fro taking the time to do that.

Edit your first post.

at the very bottom you will see an option to tag it as resolved.

* I hope our work around is effective.

---

