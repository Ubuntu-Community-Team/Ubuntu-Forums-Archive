---
title: "libdvdcss (?)"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by Akuma Shiro on 2007-06-23
Every time I try to play a DVD, I get this message "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?"

I am trying to play the first Ghostbusters movie as a test for stuff. I can't seem to find this "libdvdcss" in the add/remove apps foir the synaptic package manager.

Any clues as to where i can find waldo?

---

### Post by apjone on 2007-06-23
Hey, open a terminal and type
```
sudo apt-get install libdvdcss2 
```

that will get ya up and running

---

### Post by skywarp04 on 2007-06-23
That is a correct command for adding the package, but he can't do that until he adds the Medibuntu repository to his sources list.  Go to /etc/apt.  Then use a text editor to open the sources.list file.  Add this to file.

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

After you have added that to the file and then saved type this at the command line.

sudo apt-get update

then

sudo apt-get libdvdcss2

Hope that helps.

---

### Post by skywarp04 on 2007-06-23
Sorry that should be

sudo apt-get install libdvdcss2

---

### Post by apjone on 2007-06-23
> **skywarp04 said:**
> That is a correct command for adding the package, but he can't do that until he adds the Medibuntu repository to his sources list.  Go to /etc/apt.  Then use a text editor to open the sources.list file.  Add this to file.

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

After you have added that to the file and then saved type this at the command line.

sudo apt-get update

then

sudo apt-get libdvdcss2

Hope that helps.

I do not have those source's and have installed libdvdscc without any problems

---

### Post by Akuma Shiro on 2007-06-24
> **skywarp04 said:**
> That is a correct command for adding the package, but he can't do that until he adds the Medibuntu repository to his sources list.  Go to /etc/apt.  Then use a text editor to open the sources.list file.  Add this to file.

deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

After you have added that to the file and then saved type this at the command line.

sudo apt-get update

then

sudo apt-get libdvdcss2

Hope that helps.


Well I tried editing the source.list, but its not letting me save the file after adding the text. And just typing in the commands into the terminal without adding the test to the source.list file didn't work either, it just says 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

---

### Post by Titus A Duxass on 2007-06-24
You have to be sudo when you edit your sources.list

Try sudo nano /etc/apt/sources.list

---

### Post by pyros on 2007-06-24
> **Akuma Shiro said:**
> Well I tried editing the source.list, but its not letting me save the file after adding the text. And just typing in the commands into the terminal without adding the test to the source.list file didn't work either, it just says 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate

Yeah, the problem is that libdvdcss2 is not in the standard ubuntu software repository for legal reasons. The medibuntu repository has the package. There is a great explanation of adding the repositories here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

This only requires copying commands from that page and pasting them into a terminal.

---

### Post by Akuma Shiro on 2007-06-24
Worked like a charm! Thanks to everyone for the info.
I am learning so much about software since I started using Linux.

Now if I can just get my printer to work I will be golden!

:KSThanks again everyone!!!:KS

---

### Post by Caedis on 2007-06-27
> **pyros said:**
> Yeah, the problem is that libdvdcss2 is not in the standard ubuntu software repository for legal reasons. The medibuntu repository has the package. There is a great explanation of adding the repositories here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

This only requires copying commands from that page and pasting them into a terminal.


Best advice to ANY nub Ubuntu users. (like me at the moment) 
It took me like 2 days to figure out how to do all this in Both SuSE and Fedora.  In the same way, using official forums... I can already tell switching to Ubuntu was the best decision I've made as far as OS choices. :KS:KS:KS:KS:KS:KS:KS

---

### Post by be4truth on 2007-07-09
Tried this on Feisty without success.

The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss?

:(

---

### Post by rookshop on 2007-07-09
I just read the Sticky and everything works fine.

---

