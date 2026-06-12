---
title: "Feisty bug!"
date: 2007-03-28
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2007-03-28
Hello,

After installing of Feisty beta I get some packages to update (127 packages). But If I update these packages I mis my screen by running Ubuntu again. It means that I don't get login screen and the monitor shows nothing!
Could you guide me why and what i can do?

Thanks,

---

### Post by easyease on 2007-03-28
no offence but fiesty is hardly the best version of ubuntu for a "linux-newbie" to be using......of course these going to be bugs, you'd be better off using dapper because its the most stable version.

---

### Post by grg3 on 2007-03-28
I can confirm that this is a problem with the latest updates to Feisty Beta. I have just updated my beta install of Kubuntu and Ubuntu on my test machine and X is totally hosed. I cannot even get a command prompt.

I am not complaining! I know that this is a beta. Looks like an opportunity to try the rescue mode on the CD.

Anyone else see this? Any quick workarounds/fixes? I just look at this as a learning experience! 




PS. Even newbies can test betas!

---

### Post by easyease on 2007-03-28
"PS. Even newbies can test betas!"

but they shouldnt be surprised if even the simple things dont work.

---

### Post by easyease on 2007-03-28
so do you get a totally blank screen or does it inform you theres an error?

---

### Post by Tomosaur on 2007-03-28
> **easyease said:**
> "PS. Even newbies can test betas!"

but they shouldnt be surprised if even the simple things dont work.

He/She's not surprised, they're just asking for help.

Anyway, it sounds like X is loading but something's messing up with it (if the screen is just black, then that sounds like what's happening. If you're getting any errors, then let us know what they are).

First port of call is to boot into recovery mode and type:
```

dpkg-reconfigure -phigh xserver-xorg

```

Then reboot (if all goes well). If the problem persists, come back here and we'll see what we can do. Try to give as much information as possible, such as:

Any log files you think are relevant, depending on what you think is failing, for example /var/log/boot or /var/log/gdm/:0.log

Any error messages you get

Kernel version, or anything you've done which you think could have caused a problem.

---

### Post by grg3 on 2007-03-28
Yes. The screen is blank. I usually can reconfigure xserver from the F6 terminal but now I have no screen.

I will pursue this problem this evening after I return from work. any and all suggestions are welcome.:) 

Like I said, I am not worried about this for my own sake. this is a test machine and my main desktop is still running edgy. I just worry about the folks who are attracted by all the news about the Beta and decide to give it a try.

---

### Post by easyease on 2007-03-28
ok so if you can reconfigure x your not as much a newbie as i assumed (my mistake, i apologise).....I too worry about the new linux users not grasping the concept of what "beta" actually means and jumping headfirst into it then getting a very bad impression of what ubuntu is about.
 I was just trying to set this chappy straight on which ubuntu version is the most reliable and make life easier for him/her.

---

### Post by grg3 on 2007-03-28
No offense taken!

I haven't checked any other post yet to see if there was anything up with the updates that came out yesterday that made this happen.

Booted the Alternate CD
Entered Rescue mode
Entered host name
selected root partition on local disk
entered shell
cd /etc/X11
mv xorg.conf xorg.bak
mv xorg.conf.2007xxxxxxx xorg.conf
exit & reboot
No X but at least there is a console!
sudo dpkg-reconfigure xserver-xorg
make sure I select nv instead of nvidia (this morning neither worked)
before rebooting........
sudo apt-get update
sudo apt-get upgrade
after unconfigured packages and new packages are done...reboot
X lives!

That worked for me, hope that helps someone else!:)

---

