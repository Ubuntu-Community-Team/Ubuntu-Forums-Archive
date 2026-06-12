---
title: "Driver Install"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by roodscreen on 2007-02-05
I have been working on this for over an hour and keep getting more and more confused. 

When I go to adjust the screen resolution I only get the option of 640x480. I think I know why I am 'stuck'. It seems to me that I need to install the correct video drivers. 

A couple of issues, however. First, I am not sure how to find and install drivers in Ubuntu nor am I sure the exact drivers I need. I installed it on a Dell Dimension 3000 with a 15 inch LCD screen (157FPb). I am pretty sure it is not an nVidia graphics card (chip set?) but I did not write down the name of the graphics card before doing a complete install of Linux (so I have no Windows partition). 

1) So, am I correct in assuming that I need to install drivers so I can get a resolution other than 640x480?
2) Where can I find info on how to install drivers into Ubuntu? I have been reading the FAQs and Googling a lot, but I keep getting more confused.

Help me, Obi Wan, you're my only hope!!!

Michael

---

### Post by divague on 2007-02-05
Open a terminal and put

more /etc/X11/xorg.conf

look in the device section there should be your graphic card name.

For drivers and installation guides you can find them here in the forum.

---

### Post by roodscreen on 2007-02-05
Thanks, just a note since I am an uber-n00b - it took me a while to figure out where the terminal was and it took me even longer to realize that there was a space after the more statement.

Thanks for your help.

---

### Post by Spr0k3t on 2007-02-05
If you still need help, type this into a terminal

```
$ lspci | grep VGA
```

If your device shows up as Unknown, you may need to update your PCIID information.

```
$ sudo apt-get update-pciid
```

(doing this from memory, so I may not have that entirely correct.

---

### Post by roodscreen on 2007-02-05
> $ lspci | grep VGA

Okay, I've used the above code in terminal and the

> more /etc/X11/xorg.conf

Both tell me I have the Intel 82865G chipset with the i810 driver (I hope I said that right). I am feeling a bit crippled though: First, I am at the family computer that I am trying to fix the resolution on. It is currently operating at 640x480 - which is like trying to read a tech manual at the bottom of a pool. Second, due to the cold weather, my kids and friends are home from school and are singing Karakoe 2 feet from my ears, third, I have no idea what I am doing.

I have searched the forums for info on how to install drivers. Could someone point me to a step-by-step on what to do? Also, I haven't been able to locate the appropriate driver. I have been Googling away but am not sure if I should be searching on the term '82865G' or 'i810'.

I have also had all of 3hrs of sleep. So...

Have mercy on a poor n00bs soul!

---

### Post by divague on 2007-02-05
Hi, i've found this guide to fix the screen resolution, hope it helps

[http://easylinux.info/wiki/Ubuntu:Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://easylinux.info/wiki/Ubuntu:Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29)

---

### Post by roodscreen on 2007-02-05
I went to the [site ](http://easylinux.info/wiki/Ubuntu:Edgy#How_to_Correct_the_Graphics_Resolution_.28Intel.29) as you suggested.

This seems to deal with what I am trying to accomplish. It gave the following instructions:

>     * Install the resolution altering tool: 

sudo apt-get install 915resolution



When I do so, I receive the following:

> Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package 915resolution


So, I am assuming that there is a file that needs to be installed first, but I am not sure where to get the file. 

Am I doing this right? What do I do next?

---

### Post by divague on 2007-02-05
I think you need to enable the extra repositories

[http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)

---

### Post by roodscreen on 2007-02-06
Thanks so much for your help. I was able to get the resolution issue resolved. I am still not quite sure which of the things I did was the exact solution, but I am up and running.

I am starting to find my way around the interface and like it quite a bit. There is still a lot of learning involved, but it is no where near as nasty as I thought. 

I still expect some bumps and bruises along the way, but I must say that I am experiencing a bit of a rush, being out from under the M$ yolk. I will continue to work with Ubuntu on the family computer until I feel gutsy enough to convert my mission critical computer over.

I just wanted to say thanks for the help. Ubuntu has a kick-*** community. I look forward to being knowledgeable enough to be of assistance to others. It's something to work towards.

Michael

---

