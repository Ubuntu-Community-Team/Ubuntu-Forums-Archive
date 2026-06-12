---
title: "Error message on start up"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by chris.olsen on 2006-10-29
This should be easy for something with a little more experience than I have

This is a message that pops up on just before the login screen appears
-------
Users $Home/.drme is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions. Users $home dir must be owned by the user and not writable by other users.
-------

I can't find the hidden file that is referred to.  Currently in the Home folder there is my folder "chris" and the oem folder for the initial user that was created for the initial boot.  The oem folder is currently empty except for one hidden file -> .cpan

Thanks for the help.

---

### Post by chris.olsen on 2006-10-29
Correction:

It is just after I login that the message appears

Here are the file details
-rwxrwxrwx  1 chris chris    26 2006-10-28 03:21 .dmrc

---

### Post by bodhi.zazen on 2006-10-29
LOL :lol:

The file is in /home/chris not /home.

In a terminal try:```
chmod 644 ~/.drme
```

If you still get errors post the optput of:

ls -l /home | grep chris

and

ls -la /home/chris | grep .drme

---

### Post by bsussman on 2006-10-29
> **chris.olsen said:**
> This should be easy for something with a little more experience than I have

This is a message that pops up on just before the login screen appears
-------
Users $Home/.drme is being ignored. 

I think it is .dmrc that is being mentioned?  This has been the subject of numerous posts...

after logging in and confirming whether I am correct, if I am, open a terminal and type:

```
chris@yersysname:~$ chmod 644 .dmrc
```and test it.

If I am not correct, do not change the file unless somebody can document what it is for.  Just come to New Hampshire and slap me...:mrgreen:

---

### Post by chris.olsen on 2006-10-29
Just before you posted I had changed the permissions of the file to 644 and got the same message.

here is the file specs now. la -la
-rw-r--r--  1 chris chris    26 2006-10-29 08:56 .dmrc

-------
chris@ubuntu:~$ ls -l /home | grep chris
drwxrwxrwx 33 chris chris 4096 2006-10-29 09:04 chris
-------
chris@ubuntu:~$ ls -la /home/chris | grep .dmrc
-rw-r--r--  1 chris chris    26 2006-10-29 08:56 .dmrc


I have also found some other posts on this issue on the forum.  I am sure sure if it would just be easier to create another user and move all my personal files to that dir...?

Thanks for the quick help :)

---

### Post by bsussman on 2006-10-29
> **chris.olsen said:**
> Just before you posted I had changed the permissions of the file to 644 and got the same message.

here is the file specs now. la -la
-rw-r--r--  1 chris chris    26 2006-10-29 08:56 .dmrc

-------
chris@ubuntu:~$ ls -l /home | grep chris
drwxrwxrwx 33 chris chris 4096 2006-10-29 09:04 chris
-------
chris@ubuntu:~$ ls -la /home/chris | grep .dmrc
-rw-r--r--  1 chris chris    26 2006-10-29 08:56 .dmrc


hmm - worked for me...
> 

I have also found some other posts on this issue on the forum.  I am sure sure if it would just be easier to create another user and move all my personal files to that dir...?
certainly not hard to try it...
> 

Thanks for the quick help :)Lucky you got it - we have had 5 high wind power outages since this morning!  ](*,)

---

