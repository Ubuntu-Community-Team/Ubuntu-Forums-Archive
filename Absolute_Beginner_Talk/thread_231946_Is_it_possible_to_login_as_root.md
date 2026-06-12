---
title: "Is it possible to login as root?"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by jordi_rc on 2006-08-08
Hello all.

Is it possible to login as root in Xubuntu and make all that is posible as root in graphic mode? Or is it mandatory to make it all from the command line?

If it is mandatory to do it from command line, do you have a  list of the most used commands and syntaxis so I can print it in paper?

Thanks.

Jordi

---

### Post by scxtt on 2006-08-08
yes, it's possible ... but unless you want to change some GUI options for the root user (that doesn't exist unless you explicitly create it), a simple kdesu/gksudo will allow you to run GUI programs as "root" within your non-root login ...

**$:> kdesu kcontrol** is an example ...

---

### Post by louis_nichols on 2006-08-08
it is possible to login as root. [Here]("https://help.ubuntu.com/5.10/ubuntu/faq/C/fg-users-administration.html#id2532843") is how. Just take care what you'll be doing.

You should try getting used to login as a regular user, and use root privileges only when needed, though. I was also logging as root when I started using Linux, but then I messed my system a couple of times and learned there is a reason why Linux users recommend this.

---

### Post by mlind on 2006-08-08
Usually this article gets posted next
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jordi_rc on 2006-08-08
Thanks very much for so clear answers, and specially for giving me that links that explain the procedure.

I will contribute giving this link:
[http://www.perpetualpc.net/srtd_commands_rev.html](http://www.perpetualpc.net/srtd_commands_rev.html)

Seems it's a complete dictionary of commands. I suppose they work in ubuntu, isn't it?

Jordi.

---

### Post by steve.horsley on 2006-08-08
Most will (I didn't look closely). Pressing tab twice will get you a list. The size of the list depends on how much rubbish you have instsalled. I currently have 1919 possibilities, most of which I have no idea what they do.

---

### Post by jordi_rc on 2006-08-08
Thanks!!
:D 
I loose fear to the shell and got xampp running on localhost and my website hosted and works ok.

I will have to wait one month until my modem arrives and I can make my site appear in the www, anyway.

I should be masochist or a nostalgic but I like a bit this command line after all, it's not so terrible as I thought.
By the way, the shell in Xubuntu is nice looking, it is called "Terminal". Don't know if in Ubuntu or Kubuntu is the same. I saw that in Debian was very cold and horrible.
I use an Odilon Redon picture as background.

Jordi

---

### Post by aysiu on 2006-08-08
Alt-F2 ```
gksudo thunar
``` More details here: [http://www.psychocats.net/ubuntu/permissions](http://www.psychocats.net/ubuntu/permissions)

---

### Post by jordi_rc on 2006-08-08
Oooh!!

I can't believe! With "gksudo thunar" I can do all things in desktop as root! Then I close the window and become user again.

aysiu nice help!

Jordi

---

### Post by jordi_rc on 2006-08-09
Just a question, aysiu...

Does this method "gksudo thunar" have some dissavantage from a security point of view apart from smashing the system doing something I musn't ex.gr. deleting a file or something?

Thanks.

Jordi

---

### Post by mlind on 2006-08-09
> **jordi_rc said:**
> Just a question, aysiu...

Does this method "gksudo thunar" have some dissavantage from a security point of view apart from smashing the system doing something I musn't ex.gr. deleting a file or something?

Thanks.

Jordi

If your using root privileges while modifying (new) files on you $HOME folder, you'll be accidently giving files root-only permissions. That's probably not what you want.

And if you're launching applicantions using thunar (is it possible?) those applications are probably launched using root privileges aswell.

---

### Post by aysiu on 2006-08-09
The Thunar window that you have open with the *gksudo thunar* command can do *anything* to your system. It can delete any file and screw up everything.

Anything else besides that window (your desktop, other programs, your panel) are just your regular user privileges.

---

### Post by jordi_rc on 2006-08-09
Thank Mlind and Aysiu.

So I suppose I must be very carefull when acting as root, and don't do stupid things.

I created a direct access to root login in my desktop and another access to my home directory.

Thanks for your help, with all this I gain a lot of time.

Jordi.:rolleyes: :rolleyes:

---

