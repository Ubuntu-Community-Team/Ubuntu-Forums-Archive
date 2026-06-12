---
title: "Ubuntu and sony vaio"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by bprof on 2007-05-27
Hi,

I have tried to use ubuntu 7.04 on sony vaio vgn-fz150e but so far I was unable to make run, it failed at first in detecting the display adapter and once it said failed and gave me a prompt with almost all commands are not recognized.

Can any one please help me know what is the problem? Is there compatability issues between ubuntu and sony?

thank you,

---

### Post by coffeecat on 2007-05-27
> **bprof said:**
> Is there compatability issues between ubuntu and sony?

Not specifically with Sony. I'm posting from my 2-year old Sony Vaio VGN-FS215B and I have no significant issues with it.

But I notice from Sony's [Specification Sheet]("http://news.sel.sony.com/documents/consumer/computer_peripheral/notebooks/VGN-FZ150EBC_SpecSheet.pdf") (WARNING for those on dial-up - pdf file) for your machine that it's a pretty-much up-to-the-minute set of hardware.

<envy_mode> Mmmm. </envy_mode> :wink:

The display adapter is a:

> Processor: Mobile Intel® Graphics Media
Accelerator X3100
Video RAM: 358MB Total Available Graphics
Memory
Chipset: Intel® 965GMI have no experience of that one but I would have thought that an Intel chipset would be OK. Can anyone else comment?

If you are getting different errors at different times - it's not quite clear, but that's what you seem to be saying - it might be the install CD that's the problem. Did you download the iso? Did you check the md5sum? What speed did you burn at? Usual advice is to burn at low speed. I usually burn at 4x. It takes ages but saves time in the long run by reducing the possibility of bad burns.

---

### Post by spartan777 on 2007-05-27
apparently they do have support for the x3100, which is really the gm965. according to [http://www.intellinuxgraphics.org/documentation.html](http://www.intellinuxgraphics.org/documentation.html) :

"Question: What is the difference between the GM965 and X3100?
Answer
The Mobile Intel® GM965 Express Chipset is the whole piece of silicon, including PCI Express, memory, and CPU interfaces along with the graphics accelerator. The Mobile Intel® Graphics Media Accelerator X3100 is just that part of the GM965 which is used for graphics."

but the problem is that they added support for the x3100 *after* fiesty was released:(. so this guy is having the same issue you have. he installed ubuntu using the alternate cd;

[http://ubuntuforums.org/showthread.php?t=452697](http://ubuntuforums.org/showthread.php?t=452697)

sorry, i couldn't really help from here. i'm sure a little googling will help. other people are bound to have the same issue.

btw...  coffeecat, what's the quick way to check md5's? is there a good script for gnome? there's something like that I used in windows, but i can't find anything like it for gnome/ubuntu.

---

### Post by coffeecat on 2007-05-27
> **spartan777 said:**
> btw...  coffeecat, what's the quick way to check md5's? 

Oh dear. I posted an answer an hour ago. At least I thought I did. I must be getting a dose of pebkac. :(

Anyway...

Method 1

From a terminal, do 'md5sum filename.iso'. Compare the output with the md5sum you can find on the repo server. Alternatively, select the iso file in K3b. It will do a md5sum for you. Again compare the long string. Some people think that the big tick K3b gives means that it has OK'd the file. I don't think this is so. I think it has just calculated the md5sum.

Method 2

In firefox find the md5sum page on the repo server for the iso you have downloaded. It may have just one sum or several, depending on the distro. Do a 'save page as' to the same location as the .iso file. From a terminal, cd into where the iso and md5sum files are and do:

md5sum -c name_of_md5sum_file

You'll get errors for the iso files you haven't got - don't worry about that - and, hopefully, an OK for the one you are checking.

And, hopefully, I'll press the right button this time. :?

---

### Post by bprof on 2007-05-27
Thank you coffeecat and spartan777 for the input.

> If you are getting different errors at different times - it's not quite clear, but that's what you seem to be saying - it might be the install CD that's the problem. Did you download the iso? Did you check the md5sum? What speed did you burn at? Usual advice is to burn at low speed. I usually burn at 4x. It takes ages but saves time in the long run by reducing the possibility of bad burns.

I installed Ubuntu on two other machines with no problems at all. MD5SUM is correct, burning was at low speed, so I doubt its the CD. Probably the laptop is really very new!

Thanks again guys for your help!

---

