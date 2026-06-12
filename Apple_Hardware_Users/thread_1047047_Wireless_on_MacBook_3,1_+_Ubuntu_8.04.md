---
title: "Wireless on MacBook 3,1 + Ubuntu 8.04"
date: 2009-01-22
forum: Apple Hardware Users
---

### Post by -nat- on 2009-01-22
Hi, I'm new around here (and fairly new to Linux/Ubuntu).

I've just installed Ubuntu 8.04 on my Macbook (3,1) and I want to get wireless internet working. There is no wireless option under the internet Preferences (or whatever it's called), so I'm not sure how to get it working. :(

I know there are solutions on the wiki, but they make no sense to me or I can't get them to work. 
(mainly because [they]("https://help.ubuntu.com/community/Macbook8.04?highlight=(Macbook)") require an internet connection in Ubuntu to download drivers, is there any way I could download the drivers in OSX then install them in Ubuntu?)

If someone could explain how to get wireless internet working or point me to a guide explaining how to do it, that would be absolutely great!

Please note that I'm new to Ubuntu and using the terminal, but any help will still be appreciated! :-D

---

### Post by cyberdork33 on 2009-01-22
First, I would use Intrepid (8.10) since it has better support for your machine.

Second, I believe that no matter what, you are going to need an internet connection for a moment. Why can you not just plug in the ethernet?

---

### Post by -nat- on 2009-01-22
> **cyberdork33 said:**
> First, I would use Intrepid (8.10) since it has better support for your machine.

Second, I believe that no matter what, you are going to need an internet connection for a moment. Why can you not just plug in the ethernet?

So is there no way I can download the files while in OSX then boot into Ubuntu and install them? because I have no way of connecting via ethernet and I can't get Intrepid because my internet is currently at dial up speed :(

---

### Post by -nat- on 2009-01-22
:mrgreen: Yay! I got it working!
it was quite simple to fix it as well.
I used this tutorial [here]("https://help.ubuntu.com/community/Macbook8.04"), but downloaded the dell R151517.EXE file while in OSX, transfered it to Ubuntu, and installed the ndiswrapper files from the Live CD.

This is what I typed into terminal:

```
mkdir driver
unzip -a home/nat/Desktop/R151517.EXE -d driver/
cd driver/DRIVER/

sudo ndiswrapper -i bcmwl5.inf
sudo ndiswrapper -l
sudo ndiswrapper -m
sudo modprobe ndiswrapper

sudo gedit /etc/modules
```

then I added ndiswrapper at the end of the file that opened (and saved), then rebooted and wireless was working!

---

