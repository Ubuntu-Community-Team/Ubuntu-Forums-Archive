---
title: "Software for Ubuntu"
date: 2005-10-21
forum: Absolute Beginner Talk
---

### Post by HJThis on 2005-10-21
Hello,To all

First time here & have to say great looking site

i would like to ask when you install software on this
Ubuntu is it the same as Suse it's what i have been
using.

what i am asking is can i install the same software
say like f-prot & rootkit's & do i stell use md5sum
to check on my downloads.

& as far as installing software it would be just about
the same as in Suse yes

Thank you

---

### Post by HJThis on 2005-10-21
Hey,To all

Opps sorry about that i should tell you what i
installed & on what.

Ubuntu 5.10 & i installed on a Dell laptop

Thank you

---

### Post by Kapre on 2005-10-21
[QUOTE=HJThis]Hey,To all

Opps sorry about that i should tell you what i
installed & on what.

Ubuntu 5.10 & i installed on a Dell laptop

Thank you[/QUOTE]

HJThis - apps that are available that you can install are in the repos (which are recommended by Ubuntu - other than the ones that are in the universe-multiverse). Make sure you update your sources.list (see my signature USE ME). Go to System---Synaptic--, there you'll see all the apps/prgs that you can install. You can also go to a terminal --Application---Accessories---Terminal and type "sudo apt-get install 'nameof app'" (without the quotes).

K

---

### Post by GreyFox503 on 2005-10-21
I haven't used SuSE, but it's an RPM based distribution.

The best way to install software is to use Synaptic Package Manager.  Just search for what you want, check the box next to it, and hit apply.

If you find software that's not in the repositories, the next best thing is to find a *.deb of the application.  That's like RPMs, but for Debian-based distros.

```
sudo dpkg -i coolprogram.deb
``` 
Will install coolprogram on your computer.

And lastly, if all you have is the source, then installing it would be the same as it was on SuSE I would guess. :)

---

### Post by HJThis on 2005-10-21
Hi,Kapre

Ok got you thanks for the info & link will be a big help.

@GreyFox503

Thank you as well i was thinking they where all
the same thing. so it looks like i will be doing a
lot of reading, up on this Ubuntu.

but from what i have seen i'm at the right place
to ask for help keep up the great work.

Thank you :)

---

