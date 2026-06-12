---
title: "[SOLVED] Installing video card driver"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by jrharvey on 2007-09-27
Ok This might a super noob question but I have no idea how to install my nvidia geforce 8500 gt driver in ubuntu feisty fawn.

---

### Post by overdrank on 2007-09-27
> **jrharvey said:**
> Ok This might a super noob question but I have no idea how to install my nvidia geforce 8500 gt driver in ubuntu feisty fawn.

Hi and welcome, you can look under system, administration, restricted driver manager. Also if you like you can try envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Good luck!

---

### Post by skymera on 2007-09-27
ok where have you started?

wen u boot you will be dumped in console...blah blah blah

do

sudo dpkg-reconfigure xserver-xorg

select driver NV
select where your card is etc etc

restart then use restricted driver manager to get the right one :)

ok scrap that.
seems i had a dodgy version.

redownloaded and works fine.

---

### Post by overdrank on 2007-09-27
> **skymera said:**
> ok where have you started?

wen u boot you will be dumped in console...blah blah blah

do

sudo dpkg-reconfigure xserver-xorg

select driver NV
select where your card is etc etc

restart then use restricted driver manager to get the right one :)

i wouldnt use envy, its ****

I would appreciate if you did not  describe Envy that way. You could be a bit more polite like "envy did not work for me" :(

Thanks Skymera

---

### Post by jrharvey on 2007-09-27
Ok guys dont start a fight. I got to the configure x-server and selected nv. I dont know what you mean by the location. Its a pci express card

---

### Post by overdrank on 2007-09-27
> **jrharvey said:**
> Ok guys dont start a fight. I got to the configure x-server and selected nv. I dont know what you mean by the location. Its a pci express card

Hi during the configuration it will ask you the location of the card if it did not then that is fine. Good luck! :guitar:

---

### Post by jrharvey on 2007-09-27
OMG there are sooooo many questions. why does it need to know what kind of keyboard i have. geeeeese

---

### Post by jrharvey on 2007-09-27
Ok there are tooo many questions that I dont know the answer to so i aborted. Is there an easier way such as synaptic package manager. There is nothing in my restricted drivers which is weird because there use to be an nvidia option but not any more.

---

### Post by overdrank on 2007-09-27
> **jrharvey said:**
> Ok there are tooo many questions that I dont know the answer to so i aborted. Is there an easier way such as synaptic package manager. There is nothing in my restricted drivers which is weird because there use to be an nvidia option but not any more.

Hi when you started the xorg configure then you probably removed the restricted driver. Search in synaptic manager for the nvidia driver. Hope this help and all the questions you did not have to answer you could have left the default answer given. :(

Hi and here is a search to help your with your issue
[http://ubuntuforums.org/search.php?searchid=27856999](http://ubuntuforums.org/search.php?searchid=27856999)

---

### Post by r4ik on 2007-09-27
> **overdrank said:**
> I would appreciate if you did not  describe Envy that way. You could be a bit more polite like "envy did not work for me" :(

The quote needs no further comment.

---

### Post by jrharvey on 2007-09-27
Ok so I got envy and it worked like a charm. Im not sure why that guy didnt like it. Oh well. the only problem i have now is my screen resolution. i can set up my dual monitors and correct resolutions in the nvidia setup but every time i restart i have to redo it all. Its not a huge deal and I know that gutsy gibbon will fix alot of this. Its awsome that it automatically supports dual monitors :)

---

### Post by CaptainInsaneO on 2007-09-27
Run nvidia settings as root (instead of user-level) and your settings will stick.

So in terminal, type```
gksudo nvidia-settings
```

make your configs in there and then reboot and they should stay. :)

---

### Post by overdrank on 2007-09-27
> **jrharvey said:**
> Ok so I got envy and it worked like a charm. Im not sure why that guy didnt like it. Oh well. the only problem i have now is my screen resolution. i can set up my dual monitors and correct resolutions in the nvidia setup but every time i restart i have to redo it all. Its not a huge deal and I know that gutsy gibbon will fix alot of this. Its awsome that it automatically supports dual monitors :)

Hi and I am glad it worked. I agree with *CaptainInsaneO* and good luck. Please mark this thread as solved if all works well. 
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

