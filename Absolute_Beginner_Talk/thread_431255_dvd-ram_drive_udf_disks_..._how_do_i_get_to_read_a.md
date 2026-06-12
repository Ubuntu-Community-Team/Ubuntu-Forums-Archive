---
title: "dvd-ram drive: udf disks ... how do i get to read and write in Ubuntu?"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by mijj on 2007-05-02
I have a dvd-ram drive.   I use udf formatted disks (because that's what my video recorder uses) and i would like to be able to process files produced by my video recorder in Ubuntu rather than Windows. 

I dont know where to start ...

... i blindly searched for "udf" in synaptic and installed "udftools" (the name sounded promising) - but - i dont have a clue what to do.  (no useful looking item in any menu generated - that i can find, anyway.)

Help please.

---

### Post by mijj on 2007-05-02
... UDF 2.0, that is .. if that makes any difference.

---

### Post by Bitbucket on 2007-05-02
look here maybe this can help ya
[http://www.bitwizard.nl/udf/](http://www.bitwizard.nl/udf/)

---

### Post by mijj on 2007-05-03
> 
[_[COLOR="SeaGreen"]The Linux UDF file system driver[/COLOR]_]("http://www.bitwizard.nl/udf/")
To write the UDF filesystem, you need:

    * The UDF-2.0 spec.

dagnabbitl .. looks like UDF on dvdram is nogo for the average person.

---

### Post by psusi on 2007-05-03
You can read the disc when you insert it right?  What is the output of sudo mount?

---

### Post by mijj on 2007-05-04
oops ...   :red face:  :shuffles feet:

it's working.

Originally, I got a red box with a cross when i tried to read the disk contents in Ubuntu.  I assumed Ubuntu wasnt set up to read UDF format disks.

Eventually, I went into windows and it said the format of the disk was "Raw".  ... I thought maybe attempting to write to the disk in Ubuntu messed up the format of the disk.

So .. i formatted the disk as UDF2.0 in Windows and created a directory and a couple of text files.   And went back to Ubuntu.  It turned out i could read them.  I wrote to the disk in Ubuntu and read back in Windows.   Ubuntu could read disks formatted as UDF2.0 by my dvd video recorder too.

So ... erm ... :embarrassed: .. i guess my disk was faulty and i just assumed that there was a prob with Ubuntu.

---

### Post by mijj on 2007-05-04
arghhhhh.... i take back the above post ...

i can format to UDF2.0 in windows and add a directory and files in windows and read them in Ubuntu.

But ....

if i add files in Ubuntu .. the disk becomes "raw" in windows and is unreadable ...
.. tho it's still read/writeable in Ubuntu.

somehow things get messed up between ubuntu and windows.
Ubuntu will read what's created in windows, but windows wont read the disk when it's been altered in Ubuntu.

anyone got any clue how to sort this out?

in Ubuntu, 
it is /media/cdrom0
and shows itself as RAMUDF20 on the desktop

---

