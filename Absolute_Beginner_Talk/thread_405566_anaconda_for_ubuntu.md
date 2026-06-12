---
title: "anaconda for ubuntu"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by guguma on 2007-04-09
Hello and good days,

I have ubuntu 6.10 installed on my pc and it is running well. But I also need to install scientific linux 4.4 on my pc. I have downloaded the 5 cd iso images of that distribution and it also comes with a file called make.dvdiso.sh. The thing is when I do 

bash make.dvdiso.sh ....................

I get a message telling me that I need the following RPMs

anaconda-runtime mkisofs.

The thing is I cannot find a way to install this runtime. How could I do this. Or is there a nother method for making this .sh file run without these. (maybe if I can modify the file itself :))

I can post the contents of the file too if needed.

Thanks in advance.

---

### Post by Famicommie on 2007-04-10
If it came with the .iso files, then all you should have to do is use a program like GnomeBaker or k3b to write the images to DVDs. mkisofs is just a commandline CD burner if I remember properly

---

### Post by msak007 on 2007-04-10
> **Famicommie said:**
> If it came with the .iso files, then all you should have to do is use a program like GnomeBaker or k3b to write the images to DVDs. mkisofs is just a commandline CD burner if I remember properly
He downloaded 5 CD size ISOs, the script is probably to combine them and make 1 big DVD size ISO. It wouldn't work just burning the images to the DVD because they're still separate.

Unfortunately I couldn't find any .deb packages for anaconda-runtime and only found RPMs because Anaconda is the Red Hat installer (and would serve no purpose in Deibian / Ubuntu). It may be your only route, but you may have to get one of the RPMs from [here]("http://rpmfind.net/linux/rpm2html/search.php?query=anaconda-runtime") and use alien to install them.

---

