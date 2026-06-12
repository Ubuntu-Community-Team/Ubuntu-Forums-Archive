---
title: "Fubar Recovery [Resolved]"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by newbsaucer on 2007-02-13
Alright, so I managed to fubar my distro up pretty good and I have no idea on how to recover from this. I assumed that eventually I would learn this, as everyone should for every system eventually, so how do I recover from an apparent crash or fubar situation?

Let me explain what happened:

During the process of trying to install my new nvidia drivers and up the max resolution to 1900X1200 and 1600X1200 (since I have a widescreen) I was messing with the xorg.conf file. I did make a backup of it using a command I saw somewhere on the forums to make a backup. However I have no idea how to go into a sort of "safe" mode so that I can replace the modified file with the backup copy and reboot from there.

Some of the alterations I made were to actually add the resolutions manually to the list of available resolutions and to add the Model of my monitor to the monitor type. The only other thing I did was change wherever it said "nv" to "nvidia" as some posts suggested here. I am nt exactly desperate because I do have ubuntu on its own drive and dual boot using grub into either xp or ubuntu. So I have been using my xp to work and play. I want to move to ubuntu however and I just need to learn this stuff so that can be a reality. 

Now, I have quite a few things swimming in my head regarding this OS and its uses and functionality. I won't go into them in this thread because I just want to know how to recover from this type of problem and any others. I will say this, however, ubuntu seems very easy to use in the beginning, however "Aunt Tilly" still won't know wtf to do with alot of this stuff. Does anyone know when doing simple operations like installing drivers and software will be a little easier? Are there any projects out there that are working towards this? Are they using intelligent and experienced people to design the GUI interfaces? These seem like serious obstacles to getting Joe Average User to switch from WinXXX to Linux in any form. 

(BTW: 20 years experience in Windows security, administration, network admin and Desktop support here. Along with ten years of experience with Apple and Macs in geneal. Including mixed client environments and desktop support there as well. So I am not completely clueless. It just seems that, while linux has improved LEAPS and BOUNDS on the user interface and useability since I last tried any distro back in 2000, it still is making things a bit overly complicated when they don't need to be. Some very interesting articles written by some noteable linux gurus have even pointed this out. Installing a video driver should not be a 45 minute to 3 day task depending on skill level.)

Articles cited: [http://www.catb.org/~esr/writings/cups-horror.html]("http://www.catb.org/~esr/writings/cups-horror.html")

---

### Post by Brunellus on 2007-02-13
In general:  you'll want the nvidia-glx package, which is installable from apt or Synaptic.  That's plenty good enough unless you really want to push things.  But nvidia-glx is the safe bet.

No need to make things more difficult than they have to be.

---

### Post by ljpm on 2007-02-13
You can use the cp command to copy the backup file into xorg.conf. You can do this from the command promp.

```
sudo cp "source" "destination"
```

The "source" will be /etc/X11/'the name you gave the back up' 
"destination" will be /etc/X11/xorg.conf

---

### Post by newbsaucer on 2007-02-13
so for me it would be: 

sudo cp /etc/x11/xorg.bak /etc/x11/xorg.conf  
(good thing it is the same path as the path i used to save it in.)

or would it be:

sudo cp "/etc/x11/xorg.bak" "/etc/x11/xorg.conf "

Just want to clarify so I will know for future ref.

---

### Post by Brunellus on 2007-02-13
yup.  that's right.

---

### Post by newbsaucer on 2007-02-13
hahaha ok. So either will work then. Thanks.

---

### Post by Brunellus on 2007-02-13
my bad.  didn't read

leave out the quote marks.

```

cp /foo/bar/baz.bak /foo/bar/baz.conf

```

---

### Post by newbsaucer on 2007-02-13
Gotcha! Thank you Brunellus!

---

### Post by igknighted on 2007-02-13
> **newbsaucer said:**
> Now, I have quite a few things swimming in my head regarding this OS and its uses and functionality. I won't go into them in this thread because I just want to know how to recover from this type of problem and any others. I will say this, however, ubuntu seems very easy to use in the beginning, however "Aunt Tilly" still won't know wtf to do with alot of this stuff. Does anyone know when doing simple operations like installing drivers and software will be a little easier? Are there any projects out there that are working towards this? Are they using intelligent and experienced people to design the GUI interfaces? These seem like serious obstacles to getting Joe Average User to switch from WinXXX to Linux in any form. 

(BTW: 20 years experience in Windows security, administration, network admin and Desktop support here. Along with ten years of experience with Apple and Macs in geneal. Including mixed client environments and desktop support there as well. So I am not completely clueless. It just seems that, while linux has improved LEAPS and BOUNDS on the user interface and useability since I last tried any distro back in 2000, it still is making things a bit overly complicated when they don't need to be. Some very interesting articles written by some noteable linux gurus have even pointed this out. Installing a video driver should not be a 45 minute to 3 day task depending on skill level.)

Articles cited: [http://www.catb.org/~esr/writings/cups-horror.html]("http://www.catb.org/~esr/writings/cups-horror.html")

I will argue till the death that linux method of installing is WAY easier than windows, it is just different.  Once you learn it and it is second nature, you will scratch your head and go, "why the hell doesn't windows do this too!"  As for drivers, almost everything is included in the kernel.  The driver situation will improve when hardware vendors decide that linux is worth supporting and release drivers, or at least specs for their products so linux programmers can code them.  In a sense, its a bit of a catch22, as vendors will support linux when there are more linux users, and users will come to linux when hardware support is better.  It is definitely improving, however.  Please do not try to apply Windows and Mac experiences to linux.  They are so different in how they do things that this often leads to the very question you pose, "why doesn't this work like windows/mac".  Once you take a step back and see the bigger picture about how linux wants to do things, it makes a ton of sense.

---

### Post by newbsaucer on 2007-02-13
Well let's debate this for a bit. Windows driver installation is usually a point and click affair. (provided plug and pray didn't work and install it automagically for you) Mac is drag and drop or click and click. Linux is not exactly that easy. I agree that the linux way is different, but I do have to apply what I know to it because I hear alot of people in the linux community proclaiming that Linux is easier to use than windows or some such. This is just not the case. Is linux a lot easier on the wallet and more dependable in the long run due to its nature and reputation as a more secure environment or a more robust and versatile platform? Yes definitely, but how is anyone going to convince Aunt tilly to switch when her first hurdle will be conquered by someone telling her "Go to the command terminal and type in "sudo gkedit /etc/x11/xorg.conf" or what have you. This is just not the same in terms of ease of use for the AVERAGE user.

To keep things as is you will have to assume a whole lot of things.

You will have to assume that the average user will know:

What a command terminal is

How the file and directory structure for linux works

what to do if they need support (forums and discussion groups as opposed to the customer service rep at the end of a 1800 number)

How to post intelligent questions on the forums or groups so that they can accurately convey what the problem is.


My assertion is just that normal users don't care how it works, just that it does. I am not bashing Linux at all, sorry if that is how you want to take it, I am just saying there is plenty of room for improvement here if being part of the average user's life is going to be a reality. I am all for linux being more of a main stream OS if it means I will have more support from hardware and software providers. But they won't become more involved until Linux has a broader user base and that won't happen until Using linux becomes akin to turning on your computer and stuff just working. No command line involved. (Most of the time) As it stands now, installing and configuring a linux box, even using ubuntu, is a process of not just pointing and clicking, but typing obscure commands ( to the average user the line "sudo gkedit fu/bar/fubar" is voodoo magic talk) into something called "The Terminal".

Anyway, we are all entitled to what we think. I will continue to get this to work and learn linux because I do not want to be part of the Vista revolution. Thanks for your input though.

---

### Post by ljpm on 2007-02-13
> **newbsaucer said:**
> Well let's debate this for a bit. Windows driver installation is usually a point and click affair. (provided plug and pray didn't work and install it automagically for you) Mac is drag and drop or click and click. Linux is not exactly that easy. I agree that the linux way is different, but I do have to apply what I know to it because I hear alot of people in the linux community proclaiming that Linux is easier to use than windows or some such. This is just not the case. Is linux a lot easier on the wallet and more dependable in the long run due to its nature and reputation as a more secure environment or a more robust and versatile platform? Yes definitely, but how is anyone going to convince Aunt Tilly to switch when her first hurdle will be conquered by someone telling her "Go to the command terminal and type in "sudo gkedit /etc/x11/xorg.conf" or what have you. This is just not the same in terms of ease of use for the AVERAGE user.

To keep things as is you will have to assume a whole lot of things.

You will have to assume that the average user will know:

What a command terminal is

How the file and directory structure for linux works

what to do if they need support (forums and discussion groups as opposed to the customer service rep at the end of a 1800 number)

How to post intelligent questions on the forums or groups so that they can accurately convey what the problem is.


My assertion is just that normal users don't care how it works, just that it does. I am not bashing Linux at all, sorry if that is how you want to take it, I am just saying there is plenty of room for improvement here if being part of the average user's life is going to be a reality. I am all for linux being more of a main stream OS if it means I will have more support from hardware and software providers. But they won't become more involved until Linux has a broader user base and that won't happen until Using linux becomes akin to turning on your computer and stuff just working. No command line involved. (Most of the time) As it stands now, installing and configuring a linux box, even using ubuntu, is a process of not just pointing and clicking, but typing obscure commands ( to the average user the line "sudo gkedit fu/bar/fubar" is voodoo magic talk) into something called "The Terminal".

Anyway, we are all entitled to what we think. I will continue to get this to work and learn linux because I do not want to be part of the Vista revolution. Thanks for your input though.


For the most part your arguments are valid. Linux is not for aunt Tilly, especially if aunt Tilly's VCR is still blinking 12:00. Linux is for the computer user who wants to do a little more than email yahoo or msn messenger.

As for the reason most help is given in terminal commands is not because it can't be done with the GUI but because it is easier tell some one to copy and paste the following code. 

What does aunt Tilly do when do when a windows driver stops working or runs into a missing dll error? The steps to fix the problem are no less complex on a Windows machine as they are on a linux machine, they are just different.



As an example, your problem here was a messed up xorg file. 
The solution was entering "sudo cp etc/X11/xorg.bak etc/X11/xorg.conf" at the command promt.

Explain to me what you would have to do if your Windows machine would not boot because of a video driver problem. Can you do it in one line?

---

### Post by igknighted on 2007-02-13
> **ljpm said:**
> For the most part your arguments are valid. Linux is not for aunt Tilly, especially if aunt Tilly's VCR is still blinking 12:00. Linux is for the computer user who wants to do a little more than email yahoo or msn messenger.

As for the reason most help is given in terminal commands is not because it can't be done with the GUI but because it is easier tell some one to copy and paste the following code. 

What does aunt Tilly do when do when a windows driver stops working or runs into a missing dll error? The steps to fix the problem are no less complex on a Windows machine as they are on a linux machine, they are just different.



As an example, your problem here was a messed up xorg file. 
The solution was entering "sudo cp etc/X11/xorg.bak etc/X11/xorg.conf" at the command promt.

Explain to me what you would have to do if your Windows machine would not boot because of a video driver problem. Can you do it in one line?

Why is linux not for aunt tillie?  I think she is the perfect linux user.  She is more likely to follow links to bad sites or open dangerous emails because she doesn't know.  So say she has a pro set up her computer (windows or linux), and all she uses is firefox (or IE) and thunderbird (or outlook express) and maybe the occassional word processor.  Would not linux make more sense?  She wont mess with the settings, the pro would have done that for her.  She would just work away, and one year later windows would be crawling and full of viruses and malware, while linux would be good as new.  Windows is really only better, IMO, for people have have very specific needs (mainly intermediate users).

---

### Post by Brunellus on 2007-02-13
OP's problem has been solved.  Further debate on the merits is useless.  this thread is closed.

---

