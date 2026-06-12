---
title: "newb qs: hosts file &amp; gedit"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by guysmiley on 2006-03-19
Hey all,

Thanks for your guidance thus far...  I feel like such a newb asking stuff like this...

So, I named my linux box via Administration -> Networking and gave it a host name.  I was messing around later and deleted it.  Now I can't get the Networking gui back and I'm prompted with a window on boot to edit etc/hosts.  Great, I just don't know the code to place in the hosts file (I originally called the machine 'gonzo').

G-edit:  I can't seem to edit the hosts file in g-edit.  I can highlight but not edit...!?!? Once I know what to put in the hosts file, how do I edit the thing?

tia,
gs

---

### Post by dermotti on 2006-03-19
You cant edit it because you dont have the rights. Open up a console and do

sudo gedit <file_you_want_to_edit>

---

### Post by guysmiley on 2006-03-19
Thanks,

Any idea what line I need to add to the hosts file to indicate my "Host Name"?

---

### Post by dermotti on 2006-03-19
Which file is it you are trying to edit exactly? I can cut n paste mine in here...

---

### Post by guysmiley on 2006-03-19
Hey,

Thanks for the help...

I need etc/hosts   Specifically, I'm looking for a field that indicates something like 'host name'.

Thanks a heap!

gs

---

### Post by dermotti on 2006-03-19
sudo gedit /etc/hostname


your hostname should be hte only thing in the file on line one.

---

### Post by guysmiley on 2006-03-19
Can you provide me sample syntax (i.e. hostname: *hostname*)?

thanks again,
gs

---

### Post by steve.horsley on 2006-03-19
The hosts file takes the format of an IP address, and a list of names for it. I suggest you add a line like this:
> 127.0.0.1       localhost StevePC
replacing StevePC with whatever your hostname is.

---

### Post by guysmiley on 2006-03-19
Thanks, Steve.

I'll give it a go...

btw, is there a quick way in this forum to access your last post other than Search -> Find All your threads...?  I'm used to SMF and vBulletin dosen't seem to have this quick feature.


gs

---

### Post by gbinal on 2006-05-14
Thank you in advance for the patience of answering these questions, but I have been working down the same train, but cannot edit either file /etc/hosts or /etc/hostname.  Permission denied.  This is the case even when logging into a safe session (failsafe gnome or failsafe terminal).  Any ideas?  

Peace and thank you again for your time and help.  

Gray B.

---

### Post by gbinal on 2006-05-19
I realized my error.  I was trying to follow through on your instructions via the two failsaife logins, instead of booting in recovery mode (for those ignorant like me, when you first turn on your comp, you have a 3 second or so countdown to get to the menu, that's where you have the chance to make the proper changes).  

thanks a bunch for the help, fellers.

---

### Post by macdo on 2006-05-19
[QUOTE=guysmiley]
btw, is there a quick way in this forum to access your last post other than Search -> Find All your threads...?  I'm used to SMF and vBulletin dosen't seem to have this quick feature.
gs[/QUOTE]

You can subscribe to threads that you're interested in: either with the "thread tools" button, above the thread, or by choosing the appropriate item in the drop-down box on the reply page (underneath the typing area).

---

