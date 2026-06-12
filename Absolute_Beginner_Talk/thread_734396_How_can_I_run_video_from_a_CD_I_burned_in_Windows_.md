---
title: "How can I run video from a CD I burned in Windows in Ubuntu?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by quddusaliquddus on 2008-03-24
Hi all :),
           Basically I burned some video files in Vista using ImgBurn to a CD. Now when I insert the CD while logged into Ubuntu i get the following error:

Cannot mount volume.invalid mount option when attempting to mount volume "udf Volume"

Any help is much appreciated. Thanks :D

Regards

Q

---

### Post by stchman on 2008-03-24
> **quddusaliquddus said:**
> Hi all :),
           Basically I burned some video files in Vista using ImgBurn to a CD. Now when I insert the CD while logged into Ubuntu i get the following error:

Cannot mount volume.invalid mount option when attempting to mount volume "udf Volume"

Any help is much appreciated. Thanks :D

Regards

Q

I have had this problem before.  I make sure and burn all my CDs using ISO Level 2 with an ISO9660 character set and Joliet as the secondary volume in Windows.  Remember Windows likes to be non-standard or make their own standards.

I have had to go back and re-do CDs that did not meet this criteria to read them in Ubuntu.  I now make all my burn copies using K3b and all is well.

---

### Post by quddusaliquddus on 2008-03-24
thanks for the info

---

### Post by quddusaliquddus on 2008-03-25
So - is there no way i can run these CDs ive burned other than in windows?

---

### Post by hyper_ch on 2008-03-25
you could write a program that converts them to a standard .iso file and then you could mount that .iso in linux.

---

### Post by quddusaliquddus on 2008-03-25
sorry about this. I have a bad memory u c. It isnt an ISO file but some videos and dragged and dropeed into a CD to burn it in windows. 

I appreciate u helping me out.

---

### Post by stchman on 2008-03-25
> **quddusaliquddus said:**
> So - is there no way i can run these CDs ive burned other than in windows?

I actually had to go back to a Windows machine and copy the disc using the parameters I stated above.  If the file system is incompatible that is it.

---

### Post by quddusaliquddus on 2008-03-25
thanks for the help. I just found that someone on another forum ran his cd rom by using Wine and ISOBUSTER. So thinking along the same lines i installed wine and ran media player classic using it. When i open the CDROM directory using media player classic no files show up. Is there a a work around for this? Or is there a better windows mdia player i could use in conjucntion with  wine?

---

### Post by quddusaliquddus on 2008-03-25
please someone help me. ive spent this whole dayand yesterday evening  trying to fix this.

---

### Post by northern lights on 2008-03-25
Man, raw CD's aren't as spendy as in the '90s - reburn.

Wine will just keep pissing you off...

---

### Post by quddusaliquddus on 2008-03-25
Believe me when I say I'd reburn if i still had the files.

---

### Post by northern lights on 2008-03-25
mkey, that explains it. No buddy with a windows machine? No windows machine at school/work?

---

### Post by Therion on 2008-03-25
I'm confused...  

Do you have an .iso, or do you have a data CD you copied files to?

---

### Post by quddusaliquddus on 2008-03-25
I dont have an ISO. I just copied video files directly into the CD by dragging anf dropping in Wiondows Vista.

---

### Post by Therion on 2008-03-25
kk... That's what I thought.  And the files are in what format?  

I'm guessing they're not .avi files, or we wouldn't even be having this "conversation".

---

### Post by quddusaliquddus on 2008-03-25
Im afraid they are avi files. Why wouldnt we be having this conversation? Im hoping theres some very easy way to run them. pleaaaase let it be that!!!!

---

### Post by stchman on 2008-03-25
> **quddusaliquddus said:**
> I dont have an ISO. I just copied video files directly into the CD by dragging anf dropping in Wiondows Vista.

Take the CD to a Windows XP or Vista machine and copy the files off it.  Use a flash drive to transfer over to your Ubuntu machine.  Once that is done re-burn using K3b.  I know you know someone with a Windows machine.

---

