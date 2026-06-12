---
title: "No sound??? Thinkpad R61i"
date: 2007-10-16
forum: Absolute Beginner Talk
---

### Post by obesus_puer on 2007-10-16
So I successfully completed my very first Ubuntu install. I installed Gutsy 64bit. Everything appears to have installed except for one small problem. My sound does not work! After installation I was greated with a little tune. After that no sound at all. When i start up sound is muted. I unmute it but i still am unable to get sound. Please help!

---

### Post by obesus_puer on 2007-10-16
bump

---

### Post by obesus_puer on 2007-10-16
please help ='(

---

### Post by benuski on 2007-10-16
I have a T61, and I had to compile my own alsa.  Go [here]("http://www.alsa-project.org/main/index.php/Main_Page") and download alsa-driver and alsa-lib and then [install from source]("http://www.psychocats.net/ubuntu/installingsoftware#source").  

Or, you could wait until alsa 1.0.15 hits the repositories, but who knows when that will be.

---

### Post by obesus_puer on 2007-10-16
k ill try

edit... actually i have no idea how to do that.

---

### Post by obesus_puer on 2007-10-17
i dont understand what i should be doing. I just get compile errors. Maybe I should just go back to windows =(

---

### Post by obesus_puer on 2007-10-17
haha! it randomly started working. Guess i just had to threaten it a little with windows.

---

### Post by Hydrargyri on 2007-10-20
Hello!

I just recently upgraded to Gutsy, and I am also having a similar problem. The volume control says that it cannot detect any sound device or something. I tried to follow the above instructions. I successfully installed the library, but when I tried the driver:

```
checking for kernel linux/version.h... no
The file /usr/src/linux/include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).

```

I ended up with that output after typing the ./configure command.

I would really like to have sound work. I'm using the onboard sound plug. Here's my motherboard:

[http://www.giga-byte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2281&ProductName=GA-M51GM-S2G](http://www.giga-byte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2281&ProductName=GA-M51GM-S2G)

(As a note, the sound worked fine in Fiesty)

Thank you!

Edit: I realize now that this thread is on a specific laptop, while my computer is a desktop. Sorry for any confusion.

---

### Post by Lorenz on 2007-10-20
I do have the problem sometimes with my T60.
One thing you should always check first is, if your playback is somehow muted.
System -> Preferences -> Sound
There you can also check if the settings work.

---

### Post by Hydrargyri on 2007-10-20
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

That is the output I get when I try the playback test. There is no audio output to select. :(

I've definitely checked -- a few other people have reported the problem. I believe this is a very similar, if not the, bug in question:
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/117246)

---

