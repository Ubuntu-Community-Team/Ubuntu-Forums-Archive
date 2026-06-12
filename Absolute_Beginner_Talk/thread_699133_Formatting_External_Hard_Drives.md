---
title: "Formatting External Hard Drives"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-02-17
I need a lil help here, not as easy as it sounds.

I use an external hard drive, as do most people - great.

So somebody got sat down at my computer on the one day it wasn't locked and got to some files they shouldn't have (had information that could cause id theft if got out, along with other things), while I agree this shouldn't be on my computer, that's not my real concern.  Nothing was taken/damaged, so I'm not in a worry there.

Though this has made me re-think security here.  So I decided I need to find a way to lock up folders, then I can dump crap in there and they're safe - even on the off chance I leave my computer and don't lock it on the way out.  My sudo PW was safe since that's only upstairs.

Right, so I decide that I'll make a bash script to chance the permissions - though while talking it over with a linux friend of mine, he brought up a good point, any owner can change file permissions without being sudo, I was not aware of this, I thought sudo had to be implemented before using the chmod command.  He offered the idea of making a different userand chown'ing along with chmod'ing them - then make the user have no ability to log-in, so I basically lock them under a different user with no permissions to the outside (me) world.

Right, so I made a script that would lock and another script with lines that would unlock.

It worked fine - on my local system.

Then I got to my external, which is NTFS - the lock did not work at all - obviously a slight problem in my planning.

So, what the f8ck do I do now?

I know with windows you can format the drives from FAT32 to NTFS WITHOUT erasing any information, you just have to enter the line the right way in the command prompt - though is there any way to convert the NTFS system they use now to the EXT3 system so I can change the permissions and ownership of them - but doing it WITHOUT damaging/the data onboard?

I'm guessing not, though since it was possible to change from FAT32 to NTFS without losing any data, I'm trying not to give up hope :(.

If I can't do that - does anybody else have any ideas i can use?

There's no worries of people doing this remotely, my sudo pw is safe - but I'm talking local.

Usually I lock my computer when I leave - but I still don't feel safe since this last incident, so does anybody have any ideas?

PS:
If I can convert it to EXT3 - what would happen if you tried to read it from a mac or XP?  I know XP won't read it - but I'm pretty sure you can install a program that'll let it read EXT3 file format - but what about writing it - and so on - if I am able to do that - does that make it an exclusive linux only drive?

---

### Post by yabbadabbadont on 2008-02-17
You might consider installing TrueCrypt and using it.  It is available for both Windows and Linux, and I believe that the two are compatible.

---

### Post by Sinkingships7 on 2008-02-17
i have to admit, i don't have a direct solution to your problem, but rather an alternative.

have you tried using truecrypt?

it will create a virtual image, which you create it's size and a password for it, and mount it using truecrypt. truecrypt mounts it as a virtual hard drive, so when you go to computer, it will show as a different hard drive. you then store your data onto that virtual hard drive and it's encrypted as it's sent through. when you're done storing sensitive/personal data, just unmount the image.

the ONLY way to get into one of these images is if someone mounted it with truecrypt, which they can't do unless they have the password you created for the image.

other than that, it's only shows as a file, of which no other program can touch or manipulate in any way. uncrackable, as there's no proof that it's anything other than an unreadable file.

just an idea.

---

### Post by Syndacate on 2008-02-22
> **Sinkingships7 said:**
> i have to admit, i don't have a direct solution to your problem, but rather an alternative.

have you tried using truecrypt?

it will create a virtual image, which you create it's size and a password for it, and mount it using truecrypt. truecrypt mounts it as a virtual hard drive, so when you go to computer, it will show as a different hard drive. you then store your data onto that virtual hard drive and it's encrypted as it's sent through. when you're done storing sensitive/personal data, just unmount the image.

the ONLY way to get into one of these images is if someone mounted it with truecrypt, which they can't do unless they have the password you created for the image.

other than that, it's only shows as a file, of which no other program can touch or manipulate in any way. uncrackable, as there's no proof that it's anything other than an unreadable file.

just an idea.

Yeah but wont the regular hard drive still show up in /media ?

---

### Post by Syndacate on 2008-02-23
*bump?

---

### Post by Syndacate on 2008-02-24
> **Sinkingships7 said:**
> i have to admit, i don't have a direct solution to your problem, but rather an alternative.

have you tried using truecrypt?

it will create a virtual image, which you create it's size and a password for it, and mount it using truecrypt. truecrypt mounts it as a virtual hard drive, so when you go to computer, it will show as a different hard drive. you then store your data onto that virtual hard drive and it's encrypted as it's sent through. when you're done storing sensitive/personal data, just unmount the image.

the ONLY way to get into one of these images is if someone mounted it with truecrypt, which they can't do unless they have the password you created for the image.

other than that, it's only shows as a file, of which no other program can touch or manipulate in any way. uncrackable, as there's no proof that it's anything other than an unreadable file.

just an idea.

It might be decent - I couldn't even get it to work so I wouldn't know.

Though that aside, you need to erase everything to encrypt a whole volume, which rather defeats the purpose unless I was to temporarily transfer everything to a different drive - which I might be able to do - but I can't even get the stupid thing to work right on a test system.  Of course it doesn't help that I know nothing about encryption or how this thing works.

Gah.

Any other suggestions?

---

### Post by Syndacate on 2008-02-28
Blah, last call, anybody? :(

---

