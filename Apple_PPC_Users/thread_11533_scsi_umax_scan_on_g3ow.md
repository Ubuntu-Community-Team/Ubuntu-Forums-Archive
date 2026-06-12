---
title: "scsi umax scan on g3o/w"
date: 2005-01-17
forum: Apple PPC Users
---

### Post by trash on 2005-01-17
Actually I have two questions...
Old world g3 266 all in one with Ubuntu on sda hard drive, I am trying to get my Umax astra 1220s scanner going but xsane won't detect it(as root or user). SG module loads fine and can be seen in /dev/sg0. I am not clear on what i am missing here so can anybody with some scsi experience can give me any pointers?

Second question:
This install is on a rather small drive,
 df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             1.8G  1.6G  185M  90% /
tmpfs                  94M     0   94M   0% /dev/shm

so I am wondering if it is possible at all to move my /home directory to another hard drive on the same machine?
Or is there another way i can better deal with this situaton?

thanks!

---

### Post by trash on 2005-01-17
I've added 'sg' to my etc/modules and the scanner was detected on boot:)

sudo xsane did detect my scanner... user didn't, so I changed permissions

@g3:/dev $ sudo chown kenji /dev/sg0
@g3:/dev $ sudo chmod 0600 /dev/sg0

it worked but then i noticed I can't access my scsi hardrive or anything on it.. 

help!


EDIT:
ok I was able to reboot with scanner OFF so it didn't load dev/sg0(read only filesystem!!!!).. changed the permission to 0660 instead of 0600... and all seems good!

---

### Post by trash on 2005-01-19
... all seems good till I try to scan after a preview!!

i am getting an error message saying that xsane can't write to a temp (read only filesystem).
after turning the scanner off and rebooting, my drive is once again r/w.
I've search quite a bit on this and haven't come across any talk of this happening, can anybody help clarify this situation?

---

### Post by Ernest Pons-Worley on 2006-07-02
Same computer, same scanner... tried your suggestions, but no luck.

When I installed Breezy Badger, I had turned on the scanner and it was apparently configured automatically.  It worked perfectly then, so obviously it's compatible and the drivers are there.

When I upgraded to Dapper Drake, however, I did not remember to turn on the scanner first and now I am getting the error message from XSane Image Scanner:

"Scanning for devices... no devices available"

Clicking on "Help" produces:

"Possible reasons:
1) There really is no device that is supported by SANE
2) Supported devices are busy
3) The permissions for the device file do not allow you to use it -- try as root
4) The backend is not loaded by SANE (man sane-dll)
5) The backend is not configured coreectly (man sane-"backendname"
6) Possibly there is more than one SANE version installed"

I can rule out 1, 2, 3 and 6.  Now if I could just figure out what all that stuff in man means...

Does anyone know how to configure Xsane manually?

Thanks,
Ernest

---

### Post by Ernest Pons-Worley on 2006-07-02
OK! Nevermind!

I got it to work.  I discovered that I could detect the scanner as root, but not as myself.  I changed the permissions and it now works.  The trick was that on my computer the scanner is sg2, not sg0.

So, your instructions did work.  Thanks!

Ernest

---

