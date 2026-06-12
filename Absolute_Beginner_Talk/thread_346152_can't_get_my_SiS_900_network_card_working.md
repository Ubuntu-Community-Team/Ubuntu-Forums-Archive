---
title: "can't get my SiS 900 network card working"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by noob@linux on 2007-01-25
Hi all,

Please can anyone point me in the right direction, i have an old computer in my school and i have installed Ubuntu 6.10 on to it and i want to connect it to our school network, initially to get the computer up and running, but potentially to change it to a server when comfortable with the package.
I have a SiS-900 based Ethernet LAN card thats built onto my Motherboard but it doesn't seem to detect it at all. 
I think i have downloaded a driver for this but it requires me to set it up ... well, i'll copy a bit from the read me

Now enter the following commands at the UNIX prompt. Remember, UNIX
       is case sensitive.

       # mkdir /temp
       # mcopy a:sis900.c /temp

How do i get to this promt etc and what do i do?

I would appriciate any input to this matter, 

keep up the good work all


Aidy

---

### Post by mikewhatever on 2007-01-25
Applications-->Accessories-->Terminal would get you to the prompt, and terminal is the name in ubuntu. You may also want to add an icon for the terminal/prompt to the panel. Right click on the word Terminal in the drop down menu, and choose Add to Panel.

---

### Post by noob@linux on 2007-01-26
Thanks
well, a bit further anyway, had a play with the terminal window and got a bit into it before i got stuck. I don't have mtools so couldn't use the mcopy so tried it with cp command.

Here are the instructions for my ethernet driver
1. Now enter the following commands at the UNIX prompt. Remember, UNIX
       is case sensitive.

       # mkdir /temp
       # mcopy a:sis900.c /temp

	 Note: a. copies from DOS disk to current working directory.
	       b. mcopy is mtools if you don't have mtools, you can
		  mount -t /dev/fd0 and use cp command

       # mcopy a:trans /temp
       # cd /temp
       # chmod 777 *			 (add all right to all file)

    2. run trans file to complie and copy driver to linux source code:
       /temp/trans

    3. Run netconfig to set you network parameter (like ip, gateway), This
       will create '/etc/rc.d/inet1' and 'inet2' files.

    4. you must modify /etc/rc.d/rc.inet1 to insmod driver. This file will
       run at boot time. add a line in rc.inet1:

       # cd /etc/rc.d
       # vi rc.inet1
       # insmod /your driver'path/sis900.o

	   ex: insmod /usr/src/linux/modules/sis900.o
	       (must before bind protocal)

       # shutdown -h now

       (then your driver will work every time you boot.)


I can't seem to copy from my floppy disk the files as asked, i keep getting 'No such file or directory'. Not sure if i'm doing it right.

Thanks all

---

### Post by HereInOz on 2007-01-26
Not sure but the use of a:sis900.c as the source for the copy seems wrong.  Drive letters do not get used with the cp command (I think).

The easiest way to mount the floppy is to click on Places > Computer then right click on the floppy drive icon and select Mount Volume.  If it is already mounted, then the option will be to Unmount Volume.

I also reckon the copy command should be something like:

cp /media/floppy0/sis900.c /temp

Could be wrong but give it a go and see what happens.

---

### Post by noob@linux on 2007-01-26
Thank you,

Have copied the two files accross, and have run the TRANS file as in step two.
Step 3 says to run netconfig but i'm uncertain as to what netconfig is, i have all the details of my ip address, subnet mask etc to put in but im not sure where.

Thanks

---

