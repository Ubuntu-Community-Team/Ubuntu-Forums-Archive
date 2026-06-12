---
title: "Help (please) a little confused"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by Mark Haysom on 2007-05-16
I have moved over to ubuntu and so far have not regretted it at all, in fact all the family are happy too!
However I keep coming up against a problem that must be easy to fix but I can't work it out as yet. I have downloaded a couple of programs that work in the login I used to setup the system but fail to work in other user's desktops even though you can see the programs in the drop downs.

To date this effects Picasa and Camorama.

Picasa reports chmod 666 /dev/nvidia0 /dev/nvidiactl needsto be done. I have carreid out this using sudo and Yes it works, until I reboot then I havw to carry out the same instruction again.

Camorama also seems to be the same, works in the set up account but reports /dev/video0 as an error in any other user account.

So I guess i must have missed something here in setting up programs and there respective permissions, can anyone please shed some light on this as it would really help convert the family once and for all.

I am using fiesty fawn by the way.

Any help would be appreciated and sorry if its a stupid question, we all have to learn I guess :-)

Cheers...

---

### Post by ubnewbie2 on 2007-05-16
Not an expert, but I believe you could put this comand in  /etc/rc.local

i.e.

sudo gedit /etc/rc.local

and add the line near the end before the exit.  As i understand it, rc.local get's executed last thing as the computer starts up (to any run level) so the change in permissions will effectively be permanent.

---

### Post by 3rr0r on 2007-05-16
I think when you install a program, it only installs it for that user.  Windows has this as well, where you can limit what programs are installed for all users vs only some.  Given that, this idea might make more sense to you.  Now, to go about setting the permissions so that everyone has it... i'm not sure.  I know it involves chown (its the command to modify the owernership of a file)

---

### Post by Mark Haysom on 2007-05-16
Thanks ubnewbie2 and 3rr0r, that has fixed Picasa, all accounts now work, appreciated.

Still stuck on Camorama really, because I do not know what steps to take to fix it in the first instance.

Thank you...

---

### Post by 3rr0r on 2007-05-16
You could try installing canorama on each user that wants it.  Then pay attention to see what it does so that they can use it too!

---

### Post by Mark Haysom on 2007-05-16
Sounds like a good plan; however how do I go about installing camorama on each user without using the set up account, it does not appear to let me!

---

### Post by ubnewbie2 on 2007-05-16
Did the install create a group  to control access?  If it did, adding each user to the group should give them the necessary permissions, without having to own the files.

---

### Post by Mark Haysom on 2007-05-18
Its all now resolved, so a big thank you to all that shared and guided.

For Camorama it was a permission issuse. Using "sudo adduser XXX video" did the trick for me, XXX being the required user name and video being the group.

One final point I was unable to carry out these changes in the Desktop environment mainly due to not being able to access the group called video. The terminal approach however worked fine.

---

