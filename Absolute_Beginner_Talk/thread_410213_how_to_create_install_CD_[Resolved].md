---
title: "how to create install CD? [Resolved]"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by tstockma on 2007-04-15
It's been too long (8 yrs?) since I created a bootable install CD, and I've forgotten this stuff...

I'm using BurnAtOnce, I have the ISO for Dapper Drake downloaded.

Looking at other posts & sites, I eventually decided all I had to do was burn the ISO file to a CD, despite my misgivings I tried it...no luck, it's not bootable.  So here's the questions:

Do I write the ISO file, or unpack it and write its contents to the CD?  I've unpacked it to a directory on HD, so I see a bunch of folders & files.

In BurnAtOnce, don't I have to do something more than just write the CD before it becomes a boot CD?  Here's what I'm doing to get at boot-options in BurnAtOnce...

  Mastering > Data-CD 
  ISO Settings
  check Bootable Image

...and options that open up when I check that "Bootable Image" option include checkboxes for "No Emulation", "Load Size", "Boot Info Table", and a browse-to button to select the Boot Image file.

But now I don't know what file to "point to" for Boot Image.

Any help appreciated!  Do I leave those additional options unchecked, and is all I now need to do is, point to the correct Boot Image file?  Which file is that?  Thanks!

---

### Post by aysiu on 2007-04-15
Don't upack. Don't burn as data. Burn it as a disk image. More info here:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by ibanezix on 2007-04-15
Your point of error is that you are burning a cd which contains the .iso as a data file, you are not actually creating a disk that is an image of the iso. I had a look at BurnAtOnce, the options you are referring to are most probalby options for creating an iso image from an existing disk.

Start from scratch: Launch BurnAtOnce, go to File -> Load New Image and find the image that you want to burn. Do NOT mess with any options just hit the Write button. 

You will end up with a bootable CD. To check it out insert it in your drive while in Windows. It should autostart and display you some options to install some free software on Windows, like in the post aysiu linked.

---

### Post by tstockma on 2007-04-15
Thanks for both pots!  Aysiu, that link leads me to good info...Ibanezix, your comment nailed it for me.  CD created, now on to te next problem...thanks again!

---

