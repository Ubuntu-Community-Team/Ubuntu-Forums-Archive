---
title: "How do i install NVIDiA drivers?"
date: 2006-07-24
forum: Absolute Beginner Talk
---

### Post by mbrang00 on 2006-07-24
I had an issue issue after i installed ubuntu that caused the screen to fill with garbage at the login screen and would not go away. I posed a question and got help... see link

[http://www.ubuntuforums.org/showthread.php?t=222330](http://www.ubuntuforums.org/showthread.php?t=222330)


after configuring the video settings to vesa, i fiugured id try to download the latest driver pack from nvidia.

Got it its on the desktop, but i dont know how to install it.
the instructions on the page say to type the following

```
sh NVIDIA-Linux-x86-1.0-8762-pkg1.run
```

im told

```
no such file or directory
```

I know the part after sh is the file name... it matches
when i double click on it i get an error:
blah blah...could not open file....blah blah....gedit has not been able to detect the character coding....blah blah blah



i tried sudo also, no joy

What must i do to install this package...

---

### Post by mbrang00 on 2006-07-24
installing.....
i had to go to the directory of where it was/


```
sudo sh /home/michael/Desktop/filename.run.whatever.it.was
```

---

### Post by mbrang00 on 2006-07-24
I dont understand

I got the package to start the install but then it tells me:

Error: you apper to be running an x server; please exit x beroe installing. For further details,  please see the section installing the nvidea driver in the readme available on the linux driver douwlad page at [www.nvidia.com](www.nvidia.com)

in other word it just told me to eat it.



What does that mean and how do i exit x?

---

### Post by Kold on 2006-07-25
Try this topic: [http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

---

### Post by testube_babies on 2006-07-25
Is your problem like this? [http://www.ubuntuforums.org/showthread.php?t=161277](http://www.ubuntuforums.org/showthread.php?t=161277)

---

### Post by Dr. Nick on 2006-07-25
I second Kold's posted link. You can use the .run file from nvidia but you will have to reinstall the drivers each time a new kernel is released, by using stuff in the repos it will all be done automatically on a update

---

