---
title: "LiveCD to tmp replace dead HDD"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by TuxIsCute on 2006-12-27
Okay.  I suffered through an HDD crash on my laptop as well as some loss in RAM.  I still require the laptop, however, for limited use at work.  Because of the loss in RAM, I think it's worth mentioning, I'm limited to Hoary (thank GOD I found the LiveCD in my closet).  So I wanted to use a copy of Ubuntu's LiveCD in conjunction with an USB 1 Gig flash drive.  I figured I'd store the packages I needed to use on the flash drive and install them when it was required I use them.  That worked fine until I ran into a problem with requiring a file.

I know how to dpkg -i <DIR.deb> and how to use the ln command to create symbolic links to programs and files, but this isn't a solution to my problem.  I have to use a file which I have stored on the USB flash drive.  It has to be in the same folder as the program.  Under normal circumstances, this would not be a problem, but the LiveCD wont allow the copying of files to and from the base folder of the program.  So I thought I'd link to it.  The ln command creates the link to the correct folder, but it is unusable and disappears if clicked.

I then tried to dpkg the file to the flash drive itself by using the following sequence of commands:

```
# mkdir /media/usbdrive/linux/tmp
# cd ./tmp
# dpkg -X <dir.deb> ./
```

But I can't use the program from there.  So I was wondering simply: Is there a way I can install the programs onto my flash drive and use them in the Ubuntu Linux LiveCD Environment?  Possibly even not having to use the dpkg command on them every time (although I could still do this with little inconvenience).

Any help offered will, of course, be helpful.

-Tux Is Cute-

EDIT: Is there possibly a way I can edit the DEB file so that it includes and installs the file I need when I use the dpkg -i <DIR.deb> method of program installation?  Would it be as easy as simply adding the new file to the DATA tarball within the DEB file?

---

