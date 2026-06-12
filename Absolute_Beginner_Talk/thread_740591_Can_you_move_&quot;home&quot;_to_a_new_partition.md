---
title: "Can you move &quot;home&quot; to a new partition ?"
date: 2008-03-30
forum: Absolute Beginner Talk
---

### Post by aborigine on 2008-03-30
I used gparted to take space away from windows and [LIST=1]
[*]give more space to Linux programmes
[*]create a partition to put my own data on
[/LIST]
I did this _after _installing Ubuntu (I know I probably shouldn't have)
Can I simply drag and drop the home directory onto the new partition in Nautilus, or should I do some nifty command-line stuff in the console- if so what ? (bearing in mind that to any of that I have to sit there with a book on my knee, thumbing through the pages!)

---

### Post by y-lee on 2008-03-30
Yes, see [moving home]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") for the details.

---

### Post by nsche on 2008-03-30
I'd suggest you should do some command line stuff.

I assume what you have is /home as a directory on the root partition and now an additional partition which you want to mount as /home.

If that is so I would do the following:
sudo vi /etc/fstab (or use gedit or whatever you like)
add a line like this
/dev/sdaN /home               ext3    defaults,errors=remount-ro 0       1
where you substitute the proper device name for /dev/sdaN.  You should know the name from your partitioning.
save the file.
sudo mv /home /home1
sudo mkdir /home

sudo (cd /home1 ; tar cf - .) |(cd /home ; tar xf -)
(not sure if a second sudo is needed after the pipe..  check it out

that will copy the files....

when done reboot.  When you are satisfied things are ok you can sudo rm -rf /home1

Check each of these steps out in your book and do not do it until you are sure you understand what is being done!

---

