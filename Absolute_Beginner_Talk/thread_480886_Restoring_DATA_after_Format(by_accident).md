---
title: "Restoring DATA after Format(by accident)"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-06-21
Does anybody know how to retrieve Data, such as "MY Documents" and such from an NTFS partition after Vista formatted it when it was not supposed to!
I tried those "RestoreMyFiles" type of software but only got scrap!

---

### Post by odiseo77 on 2007-06-21
Well, I think it depends of which kind of formatting did windows to your HD... if you simply lost your partition table, then you can boot with some ubuntu live cd (or any other linux live cd), download gpart for linux from [here]("http://www.stud.uni-hannover.de/user/76201/gpart/#download"), make it executable with ***chmod +x gpart.linux*** and then run it with ***sudo ./gpart.linux /dev/YOUR_DRIVE*** and it will hopefully detect any lost partition on your HD. Now,if you unluckily really formatted your HD, then I have no idea how to recover your data (I'm afraid it could not be recovered).

Regards and good luck!

---

### Post by Hobo Joe on 2007-06-21
> Now,if you unluckily really formatted your HD, then I have no idea how to recover your data (I'm afraid it could not be recovered).

I'm not so sure about that. While I don't know of any programs that could fix it, I'm pretty sure that all the data is left on the hard drive, and it's just 'hidden', so to speak, 

I'm no expert on this stuff, but I've heard things like that from several sources.

---

### Post by odiseo77 on 2007-06-21
> **Hobo Joe said:**
> I'm no expert on this stuff, but I've heard things like that from several sources.

Yeah, me neither, I've just dealt successfully with broken partition tables, so I might be wrong :) (I mean, the data could still be there in some way)

---

### Post by FleetAdmiral74 on 2007-06-21
if it is absolutely important data, there are buisnisess who will restore it for you for a nominal fee. usually pretty successful.

---

### Post by atria on 2007-06-21
The data is definitely still around as long as they don't get overwritten by another software. I'm not sure how data can be recovered from a nonexisting NTFS partition in Linux, but it is possible in Windows. I did it quite some time ago with some recovery software, cant remember its name though :(

Just posting to let you know that theres hope for it ;)

---

### Post by Mazen on 2007-06-22
> **FleetAdmiral74 said:**
> if it is absolutely important data, there are buisnisess who will restore it for you for a nominal fee. usually pretty successful.
do you know the name of any of those businesses?!!!!
And i know there is hope if i have any contacts inside the FBI!!!lol

---

### Post by jlambeth1 on 2007-06-22
I once used a program for XP called Getdataback to retrieve pictures from a dead hard drive for a friend.  Maybe worth a try?

---

### Post by tjschia on 2007-06-22
I am new here as you can see by the number of posts but I am a IT Consultant learning about Linux.  My solution involves using windows because that is what I am familiar with, sorry I know this is a Linux but just wanted to help you out.

First off, stop using the Hard Drive.  What I have done in the past for people is put their HD in an external enclosure (or you could just put it in another system, but do not boot to it), once the computer comes up you can use a Fast File Undelete on the &#8220;formatted&#8221; HD and pending if Vista wrote over the part of the HD that had your data your files should come up.  If Fast File Undelete does not work I have also used Get Data Back too and had success.

Those business charge lots and lots of money and pending how important the data is they are not worth it for personal computers, in my experience.

Hope this helps,

   TJSChia

---

### Post by Mazen on 2007-06-22
Thanks alot, and actually i forgot to mention that it's ok if the solution is from windows, and the other thing is that i did u the partition again!!!
anyways i will try Fast File Undelete out and get back to u! thanks again

---

### Post by Mazen on 2007-06-22
> **jlambeth1 said:**
> I once used a program for XP called Getdataback to retrieve pictures from a dead hard drive for a friend.  Maybe worth a try?
i tried this one, but it's not detecting my "physical" or "logical" drives!!! i didn't give it much attention cuz it was late night!! i'll try it again tonight and see along with Fast File Undelete.
Cheers

---

### Post by WorldTripping on 2007-06-22
I also used 'GetDataBack' a few years back to successfully recover a formatted HD.

This is the URL [http://www.runtime.org/]("http://www.runtime.org/")

If I remember there is a version for both fat32 and NTFS filesystems.

Only thing was the trial version will make you rename the files one by one on recovery.

The paid for version will recover both file and original filename.

Happy file hunting.

---

