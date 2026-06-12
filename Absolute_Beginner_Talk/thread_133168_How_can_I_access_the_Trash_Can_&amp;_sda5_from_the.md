---
title: "How can I access the Trash Can &amp; sda5 from the Terminal"
date: 2006-02-19
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-19
Hello all !

I have 2 questions:

1. I have some locked files in the Trash which I can not delete.

    These files are locked, and therefore I have to do it from the "root".

    What is the path to enter the Trash can folder from root?

2. Some other files are in sda5 Partition - which (even though I have "mount -a"),
    I can see the files but can NOT move to Trash can.

    What is the path to enter the /sda5 Partition folder from root?

Thanks.

---

### Post by mushroom on 2006-02-19
1. trash is located in /home/yourusername/.Trash

2. Have you mounted sda5 read-write?

---

### Post by dvarsam on 2006-02-19
I went to /home/dimitris/.Trash, did the following:

[email]root@house:/home/dimitris/.Tras[/email]h# ls -a
.  ..
[email]root@house:/home/dimitris/.Tras[/email]h# ls -a
.  ..
[email]root@house:/home/dimitris/.Tras[/email]h#

How is it possible that the above ".Trash" is empty, but if I open the Trash Window from the Desktop, I see some locked folders which I can not delete?

Is there another trash can? - Possible instead of a "user" trash can, a "root" trash can?

Please Help...

I just performed a clean install - how is this possible?

---

### Post by Stinger on 2006-02-19
```
sudo nautilus
```

Then navigate to your home directory , remember your in the "root" directory now (sudo).
When you are in your own home directory click on show hidden files navigate to the ".trash" folder and delete the files and folders you need to remove.

BTW. every user has his own trash can , even root ! but the one you are refering to seems to be your own.

---

### Post by dvarsam on 2006-02-19
[QUOTE=Stinger]

BTW. every user has his own trash can , even root ! but the one you are refering to seems to be your own.[/QUOTE]

I have to correct you on this:

In fact, _EVERY_ USER Account & _EVERY_ Partition has one Trash can.

I JUST realized this !!!

Actually the stuff that I was seeing inside my Trash window, were stuff from NOT the Ubuntu Partition, but in fact, stuff from a Different Partition's "Trash" can.

It is kind of awkward to have 1 Trash can inside_ EVERY_ Partition.

A Trash Can for EVERY User is understandable.

...But a Trash can for _EVERY_ Partition _as_ _well_, is TOO much!

This way, I may find things in my System's Trash can, thinking that it is stuff from my User's Trash Can, & the trash might belong to a diff Trash can, in a different Partition...

And in order to find at which Partition's Trash can, I am looking into,,,,

... is  as if I am looking to find one needle in a stack of hay....

I have 4 Hard Drives & numerous partitions, what is this?

This is WAAAYYYY too complicated...

Come on programming guys - you NEED to simplify this...

Thanks, anyway.

---

### Post by Stinger on 2006-02-19
Maybe not so complicated when you think about it ?

Example , if I trashed a large file on a different partition or drive , and I only had  a trash can on my own partition , you would have to move this large file to your own partitions trash can.
With a trash can on each partition you don't , makes it easier to restore a file too.
I've seen this behavioure in windows too.
Furthermore I would think that the files that you trash on partition or drive X would only be visible to yourself and no other users (exept root) but I can't tell for sure , I only have one 20GB drive and only Ubuntu installed.
:-k

---

