---
title: "Partimage Compression"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2007-01-01
I recently used partimage to image a great setup in my opinion. The setup was 15gb big, but the 
image came out to 2gb. Did something go wrong? I find it a little hard to believe it could possibly 
compress that much. I did choose the slowest and smallest file size, but still that's crazy!

---

### Post by pseudonym on 2007-01-01
Is it the size of the *partition* that is 15GB, or the size of the *data on the partition*? Remember, partimage compresses only the used portion of a partition.

You have the option with partimage to use bzip compression instead of the usual gzip, but I don't think it could ever be [*that* good]("http://jeremy.zawodny.com/blog/archives/000953.html").

---

### Post by shanepardue on 2007-01-01
Yeah, I'm aware it compresses only the used portion. It's almost 20gb of used space and the image file is 2.1gb. It gave no error messages or anything. Also, I did specify that it only make one image file so I know it's not one of many files.

---

### Post by pseudonym on 2007-01-01
Mind you, I could have been wrong above :) As an example I just checked my bzip2ed kernel from kernel.org. It's 40mb in size and unpacks to about 440mb. That's about the same ratio as what you've got, but it is of course a much smaller piece of data.

I just had a look at the [partimage forums]("http://www.partimage.org/forums/") and couldn't find anybody with the same type of question as yours. But if you're worried, you could delete your image file and start over, only this time using gzip compression. That's what i use in partimage and I've never had a problem.

---

### Post by shanepardue on 2007-01-01
I just noticed that the partimage disk check shows "large file support - no". That may be causing this although I'm not sure if I have any files that big within my software partition (the partition I'm imaging).

---

### Post by Frank Golden on 2007-01-01
> **shanepardue said:**
> I just noticed that the partimage disk check shows "large file support - no". That may be causing this although I'm not sure if I have any files that big within my software partition (the partition I'm imaging).
Where are you saving to? Is it a Fat32 volume? If it is are you are aware of the 4GB file size limit with Fat32?

At any by default partimage will split up any large image into multiple 2GB images
unless you change that parameter. See the bottom of page where you select your compression.
This is what happens if you try to image a 4GB or bigger file to a Fat32 partition.
If you set the number to 3900MB it will produce fewer sub images.

In my experience I use my linux shared partition (on the same drive) which is Fat32
to store my images. It is the fastest method of using partimage both to save and restore.
Your image will appear as xx.000, xx.001, xx.002 etc. When restoring partimage will seamlessly access each file in sequence automatically. If you are saving to a ext3
partition, which has no such file limitation, then set the file size number to something larger than your actual uncompressed used space.

---

### Post by shanepardue on 2007-01-01
It's to an ext3 filesystem and it is saying no large file support. I've changed the option of splitting 
up files to make it one file. I said to split up if out of space. It imaged perfectly, but suspiciously 
small. My biggest concern now is why it said no large file support when both partitions involved are
 ext3.

---

### Post by Frank Golden on 2007-01-01
> **shanepardue said:**
> It's to an ext3 filesystem and it is saying no large file support. I've changed the option of splitting 
up files to make it one file. I said to split up if out of space. It imaged perfectly, but suspiciously 
small. My biggest concern now is why it said no large file support when both partitions involved are
 ext3.
I agree that a 10:1 reduction if size for a lossless compression (as it must be) is suspect.
I have not had luck using the option of splitting up if out of space. 
I just leave it on the second option and adjust the size accordingly.
That is I leave the check mark on the second box and set the number to 3900MB.
That way if the file turns out to be 4GB or bigger it will automaticall split.
Bear in mind I use a Fat32 storage partition. I have no experience with file compression in partimage. I will however make an image of my Ubuntu install using the most compression
and see if my results are similar to yours (10:1). If they are I will attempt a restore.
Will keep you posted. BTW my Ubuntu install is only 3.5GB before compression.
I try to keep all my Linux distros under 4GB.

---

### Post by shanepardue on 2007-01-01
Alright! I look forward to your results. My partition is big because I have my windows virtual machine in with this as well..(job requires a little micro$oft) Thanks for your help!!

---

### Post by Frank Golden on 2007-01-01
> **shanepardue said:**
> Alright! I look forward to your results. My partition is big because I have my windows virtual machine in with this as well..(job requires a little micro$oft) Thanks for your help!!
Wow you sure know how to complicate things.:D  Anyway I created an image of my 3.61GB Ubuntu
install first using gzip compression the process took 6 minutes and resulted in a 1.3GB image.
This looks to be about 3:1 compression. I next restored using the gzip image with no problems.

I then made another image using bzip2 compression (ignoring the warning message about not being able to restore the MBR due to a known bug). This time the resulting process took 10 minutes or so.
3.61GB compressed to 1.2GB, again only about 3:1 compression. Again restore was uneventful
despite the warning about the MBR.

Judging from my experiences as outlined above I doubt that what you are seeing (the 10:1 compression ratio)
is valid. I suspect that the process is creating multiple image files or is not completing. 
Try using the second option and set the size of the image to 20GB.

I would not try using the image file (the ~2GB one) to restore.

A question does your (vmware?) require XP installed when you make your image?
Could you not uninstall it temporarilly?


BTW, thanks to your post I now know how well compression works and how much space it saves.
I will be using compression from now on to save space.
Thanks!

---

### Post by shanepardue on 2007-01-04
No, thank you! You've been of great help! I appreciate it!

---

