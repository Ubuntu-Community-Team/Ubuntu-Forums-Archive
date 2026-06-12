---
title: "HELP! Cannot assess file partition as an user"
date: 2006-06-10
forum: Absolute Beginner Talk
---

### Post by boom2k1 on 2006-06-10
I have just reformatted a partition to FAT32, and have mounted it to /documents.

However, I cannot write to it, as it says "Error while moving... You do not have permissions to write to this folder."

I then tried "sudo nautilus" and in there I can write to the partition..
How would I change the file permission so users can write to it?
After "sudo nautilus", I have tried to edit the permission in the system properties: go into the permission tab and try to check the write checkbox for group and others. What is weird is that everytime I do that, it automatically unchecks for me a second later!
How should I deal with that?

Thanks!

---

### Post by aysiu on 2006-06-10
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by boom2k1 on 2006-06-10
Perfect Aysiu, you saved my day once again! :)

---

### Post by twotonz on 2006-06-10
Hi Boom2k1,
I think the commands you are looking for are chmod & chown. With Nautilus you will not have a lot of luck, there seems to be a small bug which prevent the changes actually taking place (at least on this machine).
Personally, for the sake of comfort, I use "sudo mc" (of course you first have to have midnite commander installed), and change the permissions/ownership with the menu. You can also type the commands in manually, type in the console, "man chmod" - "man chown" for a full list of commands available, or for a shorter list, "chmod --help" or "chown --help".

Hope this helps

Love & Peace
anthony

****edit****
ooppps, misunderstood, sorry

---

### Post by aysiu on 2006-06-10
anthony, under ordinary circumstances, you may be correct, but I don't believe you can *chmod* or *chown* FAT32 partitions, as FAT32 doesn't support user permissions.

---

### Post by twotonz on 2006-06-10
#aysiu,
:-) , thanks, another thing learnt.

---

