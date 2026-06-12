---
title: "&quot;xxx&quot; is not a valid disk image..."
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by Bakhman on 2008-03-03
I'm trying to burn a 4.5GB image that I acquired online, by using the simple "write to disc" feature as well as a couple other programs, and they each give me this same error message. That it's not a valid ISO file. I did this on a Windows OS earlier and there was no problem... is this a common problem and do I need to convert it in some way? Another more specific message was:

"CD-ROM is NOT in ISO 9660 format"

:confused:

---

### Post by hhhhhx on 2008-03-03
have you tried k3b?

---

### Post by rahimveron on 2008-03-04
Me too having the same problem even with K3B & Brasero :(

---

### Post by Bakhman on 2008-03-06
> **xhhux said:**
> have you tried k3b?

Uhh what is that, and how do I get it? Is it a program, update, ...?

---

### Post by taurus on 2008-03-06
k3b is an app to burn CD/DVD.  You can install it either from synaptic or apt-get.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install k3b
```
It should be in Applications -> Sound & Video.  What is the extension of your image file?

---

### Post by Bakhman on 2008-03-06
I got the program, but it treats it as if its a CD. i.e. it says "4.4GB exceeds by 3.7GB" meaning it expects it to be 700MB! When using the DVD quickstart, it says it's not a valid 9660 image, but I told it to "burn it anyway", and now it's in the process... I'll let ya know how it goes?

---

### Post by Sf4tt on 2008-03-13
Hi all!

I'm an italian ubuntu user and while i was searching about this error i have found this post.

Anyhow i have solve this problem simply changing the permissions of the file at issue.

So you can type 

```

gksu nautilus

```

Now type your password and you are in a super-user graphic mode.

Search the .iso file, right-click -> Preferences - > Permissions

In this window set the acces for all (User, group and others) to "Read and write". 
Select "Allow to execute the file as a program"

Well done, click ok and close the super-user graphic window.

Now if you have exactly follow these points you should can write your iso...

I hope this post is helpful and i apologize for my bad english :)

EDIT:
I wrote this post because i had notice the same problem with K3b advised in this thread.

---

