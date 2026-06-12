---
title: "I want to make my mount my /home to a new folder"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Majin Zero on 2008-03-28
but I can't umount my current home, it keeps saying it's busy...

---

### Post by DBrocks on 2008-03-28
Lol of course /home is always busy! What do you need to move it for?

---

### Post by Majin Zero on 2008-03-28
I have my /home on a second HDD, and I wanna remove that HDD

---

### Post by DBrocks on 2008-03-28
so, you want to change the HDD where your /home is on correct?

---

### Post by Majin Zero on 2008-03-28
yes, right now

sda1 is my / and all other folders

sdb1 is my /home, and nothing else.

I need to remove my sdb1 disk from the computer I'm on

so I made a new folder with all the home stuff I need on sda1

it's /nexthome

I just need to mount /nexthome as home

but /home is busy and won't let me.

---

### Post by cerealtx on 2008-03-28
just alittle confused, but linux is installed on your removable, so u just want the info, not the functionallity of the home dir right?

---

### Post by DBrocks on 2008-03-28
Have you moved everythin out of /home on sdb1 to /nexthome on sda1? If so, you can open account manager. 
Then: **Users** [IMG]http://uw713doc.sco.com/en/UG_admin/graphics/rarr.gif[/IMG] **Modify.** Use the **Change Home Directory**, and select /nexthome/USERFORYOURNEWHOMEDIR

Good luck!

~Dan

---

### Post by Duck2006 on 2008-03-28
You will have to do it from a live cd, not from the drive you want to move to partition from.

---

### Post by DBrocks on 2008-03-28
> **cerealtx said:**
> just alittle confused, but linux is installed on your removable, so u just want the info, not the functionallity of the home dir right?

No he as linux installed on his SDA1. You NEED the functionality of the home dir. I've learned that the hard way. If you don't have a home dir set, and you reboot, you will get an error, and it will not allow you to continue untill you set a legit home dir. He wants the info, and the functionality of the home dir. Does that explain it? If not feel free to ask! :guitar:

---

### Post by DBrocks on 2008-03-28
> **Duck2006 said:**
> You will have to do it from a live cd, not from the drive you want to move to partition from. Its not really moving a partition per se. You are just movin a directory, and then setting that as your home dir. (I assume you know how to copy a dir :lolflag:) Then, you can use account manager to set a new home directory. If I'm wrong, don't hesitate to correct me. :guitar:

---

### Post by Duck2006 on 2008-03-28
> **DBrocks said:**
> Its not really moving a partition per se. You are just movin a directory, and then setting that as your home dir. (I assume you know how to copy a dir :lolflag:) Then, you can use account manager to set a new home directory. If I'm wrong, don't hesitate to correct me. :guitar:

You have to edit your fstab to tell it that you have a new home folder and remove the old one from there. You have to do that from a live cd.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by DBrocks on 2008-03-28
> **Duck2006 said:**
> You have to edit your fstab to tell it that you have a new home folder and remove the old one from there. You have to do that from a live cd.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Thats correct. Thanks for pointing that out.

---

### Post by Majin Zero on 2008-03-28
ok, I changed my /home with the user settings thing; shut down; removed the spare HDD, rebooted, and I get an error.

The only way I can get it up to a GUI is failsafe mode and startx.

but then, I have no network conectivity.

I'm online with a second computer.

How do I edit that file, from failsafe mode?( any other way of booting doesn't load and makes the comp reboot)

---

### Post by Majin Zero on 2008-03-28
for the record, I have all the files I need saved in a safe place on my HDD, I just need a working home made.

---

### Post by DBrocks on 2008-03-28
> **Majin Zero said:**
> ok, I changed my /home with the user settings thing; shut down; removed the spare HDD, rebooted, and I get an error.

The only way I can get it up to a GUI is failsafe mode and startx.

but then, I have no network conectivity.

I'm online with a second computer.

How do I edit that file, from failsafe mode?( any other way of booting doesn't load and makes the comp reboot)

What is the error?

---

### Post by Majin Zero on 2008-03-28
when I boot up I get this:

efsck: cannot continue, aborting

fsk died with exit status 8

*file sytem check failed

Please repair the file system manually
control-D will terminate this shell and resume boot.

If I do ctrl+D it boots and when I go to log in I get this:

User's $HOME.dmrc file being ignored. File should be owned by user and give 644 permisions. User's $HOME directory must be owned by user and not writable by other users.

and there's an OK button, I click OK, and get this:

This session only lasted 10 seconds. If you have not logged out yourself, there may be an installation problem. Try using failsafe mode to see if you can fix this problem.

There is an OK button, and clicking it brings me back to the log in screen.

---

### Post by DBrocks on 2008-03-28
Try putting the spare HDD back in, and see what happens then.

---

### Post by Majin Zero on 2008-03-28
I can not put the spare HDD back in.

---

