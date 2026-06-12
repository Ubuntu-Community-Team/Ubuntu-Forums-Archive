---
title: "Driver for pinter Brother MFC-3240C"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by eys on 2007-02-17
Hello,
I got problem to install Driver for Brother MFC-3240C. I've downloded files from Brother Site and installed pakage, but still can't get printer work. Any ideas.
Thank you

---

### Post by Tilex on 2007-02-17
There are drivers included in Ubuntu for the Brother MFC-3000 family.  I don't know if that will enable all the features on your particular model but you might want to give it a try.

In order to install a printer in Ubuntu, go your System Preferences, click on the Printer icon, click on "Add a printer", then choose how it's connected to your computer, then you will be given a table with all the manufacturers and their drivers.  Choose Brother/MFC-3000 and intall.  Try to make a test page and see if it looks good.

---

### Post by freebird54 on 2007-02-17
Before messing with the drivers and settings that you already have, try setting your parallel port (LPT1) to normal mode, rather ECP or EPP or both...

There seems to be a communication problem with a 'non-normal' port setting.

Port settings are available in your computer BIOS - at first boot-up press (del) or F12 or whatever you see flashed on the screen first...

Hope this helps

freebird54

---

### Post by phi1ip on 2007-04-28
I get the printer detected correctly on the USB port. but cannot get the printer to come up in the list. tried installing it as 3000 series but did not work.

So how do i get the 3240c driver installed? the brother site seems to be geared to debian users only.

I am being a Ubuntu evangelist, have installed it on my fathers work PC and it is critical the printer works.....  i need some tips urgent......

Phil

---

### Post by Najand on 2007-04-28
Here is the driver you were looking for.

---

### Post by phi1ip on 2007-04-28
thanks, do you know which directory it needs to be put?

I got an error message below when i tried to "install driver" from the install printer wizard. I assume it needs to be put somewhere. no?

Missing PPD-Adobe-4.x header at 1:'/home/phil/Desktop/brmf3240.ppd'

---

### Post by phi1ip on 2007-04-28
I think i need to install the driver before starting the install printer process(my error message in previous post)

Najand: Is there a procedure to install this driver?i have downloaded the file and extracted it to the desktop  directory.
thanks so far.....

---

### Post by Najand on 2007-04-28
Use firefox; go to [localhost:631]("localhost:631") and try to install the printer there.

---

### Post by phi1ip on 2007-04-28
Hi, i go through the stuff(CUPS administration), go through three or 4 screens, select the driver then get a box pop up 

"enter username and password for cups. enter my current username and password that is administrator privilages in UBUNTU. 

Then get permission denied.

?

---

### Post by Najand on 2007-04-28
It needs the "root" password. you can skip that part by opening firefox as a root:
PUSH ALT+F2 and type: gksu firefox

---

### Post by Najand on 2007-04-28
In case the driver I sent you doesn't work, use the Linux driver by Brother:
[http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de](http://solutions.brother.com/linux/sol/printer/linux/cups_drivers.html#de)

---

### Post by phi1ip on 2007-04-28
It is still asking for the CUPS username and password

would "sudo firefox" not do?

---

### Post by Najand on 2007-04-28
Have you made a root password?
If not make it using "sudo passwd root" in terminal;

---

### Post by phi1ip on 2007-04-28
just created root user.

i assume the login is 'root' and not 'su' yes?

still getting permission denied to run scripts

Unable to copy interface script - Permission denied!

---

### Post by phi1ip on 2007-04-28
All i can think of is, the ppd file downloaded is owned by a user with administrator privileges. but the cups was asking for root user and password. wonder if this screws it up...

Has anybody had success with this method?

I tried the way at the brother website, but this seemed to be for debian users. it was not clear cut for ubuntu users. am i wrong?

has anyone had success with this printer under ubuntu? out of time today....

---

### Post by phi1ip on 2007-04-28
Just Curious, 

Is there just one person here that has gotten this printer to work in Ubuntu?

If so, how?

Phil

---

### Post by ajmoncrief on 2007-07-31
I dont know if you solved this or not, but I followed (and have been following) the guide seen here [http://ubuntuforums.org/showpost.php?p=587083&postcount=1](http://ubuntuforums.org/showpost.php?p=587083&postcount=1) which is for a different brother mfc printer, but it works everytime for me.  Of course you will need to swap out mfc3240c for whatever he refers to for his printer.  Good luck.  FYI- just a tip, when you are trying to get a piece of hardware working, search first for your specific model (ie ubuntu brother mfc 3240c) if that doesn't turn up anything then broaden it and look for similarities (ie ubuntu brother mfc).

---

