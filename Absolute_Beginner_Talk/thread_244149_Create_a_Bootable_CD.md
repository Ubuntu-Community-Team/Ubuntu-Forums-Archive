---
title: "Create a Bootable CD"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by Eykonic on 2006-08-26
How do I create a bootable CD? Is it possible to choose different Operating systems to boot into? Is only an ISO file type bootable?

Next step would be to load software on CD with a menu system to run the stuff. Are there any tools to do this without programming? 

Am I getting a bit ahead of myself?:rolleyes:

---

### Post by aysiu on 2006-08-26
Have you installed Ubuntu? Are you trying to install Ubuntu?

---

### Post by Eykonic on 2006-08-26
I have a good install of 6.06 and download of Automatix.

---

### Post by aysiu on 2006-08-26
So you want to choose different operating systems to boot into...? Do you mean like dual-booting? Or just trying out other Linux distro live CDs?

---

### Post by Eykonic on 2006-08-26
Not dual booting. Burning a new bootable CD with an operating system installed.

---

### Post by aysiu on 2006-08-26
> **Eykonic said:**
> Not dual booting. Burning a new bootable CD with an operating system installed.
Yes, they will be of the ISO format. An ISO is a disk image, and it's the best way to have a downloadable and burnable CD--much better than saying, "Here are a bunch of folders and files. Put them together."

Several Linux distributions have live CDs that you can boot up--Mepis and PCLinuxOS are two I'd recommend.

---

### Post by Eykonic on 2006-08-26
OK. Now how to burn an operating system to a CD?

---

### Post by aysiu on 2006-08-26
Can you be more specific? What operating system are you talking about?

If it's an ISO, just burn it as a disk image.

---

### Post by Eykonic on 2006-08-26
I had to do quite a bit of research to figure out how to burn Blag properly. Most Linux CDs come with an .ISO extension, which means they are disk images, not files. It's kind of like the difference between handing someone a Word document of an article as opposed to a photocopy of the article. Both have the same article contained within, but the Word document contains the actual words, which you can edit and remove at will; the photocopy appears to contain words, but it's really just an image of those words--you cannot add and remove words. A disk image is a single file--about 700 MB in size--that is an image of the CD, not a collection of the files in the CD. If you burn the .ISO as data, you'll get a CD with one big file on it. If you burn the .ISO as a disk image, you'll get all the files contained within. (If this paragraph confuses the hell out of you, then you're getting closer to the real reason Linux isn't more widely used on the desktop.)

Ok. I need to download an .ISO file, say of a Linux OS. What application will burn the .ISO data to a CD to make it bootable?

---

### Post by aysiu on 2006-08-26
If you're using Ubuntu, just right-click the ISO and select *write to disc*.

If you're using Kubuntu, launch up K3B and select *burn CD image*.

---

### Post by Eykonic on 2006-08-26
Ok so k3b will do it. That answers the 1st part of my question.

---

### Post by Eykonic on 2006-08-26
Ok so K3B will burn an .ISO CD. That was the 1st part of my question.

---

### Post by aysiu on 2006-08-26
You want this option.

---

### Post by corax on 2007-03-15
Hi !

I read through this thread and i didn't find the answere for my question :

How can you create a bootable CD ? :-)

No! I don't want to burn .iso file (at least not an .iso file made by someone ). I'd like make a CD with files and I like to make bootable OS on it for example DOS... (to make Ghost backup/restore on an M$ machine)...

Can I do something like in nero ? (download a bootable DOS floppy image and show the program to write this to boot section)

Or any other method ?

Thanks :-)

---

