---
title: "[SOLVED] How do I install this package?"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by pHreaksYcle on 2008-03-23
I need to install network-manager 0.6.6-0ubuntu1 because of issues with my wireless card. The only place I could find it is at this [link]("https://bugs.launchpad.net/ubuntu/+source/network-manager/0.6.6-0ubuntu1"). It is source, and I have no idea how to install from source. Anyone who has exact instructions would be appreciated greatly.

Also, what is the consequences of not completing an installation from source? For example, if I only did a few steps, became confused, then decided to stop, would there be issues there? I would just work with it and see what I could mess with to get it installed, but I don't want to mess it up and have to reinstall or something.

Thanks!

---

### Post by pHreaksYcle on 2008-03-23
I tried a workaround of installing another wireless manager instead of downgrading the default one but that did not work either. If someone could tell me how to install from source so I don't feel uncomfortable doing it, it would be greatly appreciated, and would also keep another person on Linux because my friend is about to reinstall Windows because of this wireless issue...it always comes back to the wireless...

---

### Post by kevdog on 2008-03-23
Is there a README or INSTALL file in the list of files.

It might be
./configure --path=/usr
make
sudo make install

That is the usual however the README or INSTALL file will help you.
BTW you need the build-essential and linux header files installed in order to compile from source

---

### Post by pHreaksYcle on 2008-03-23
Thank you very much sir. A response makes me quite pleased!! 

I have looked at the INSTALL file and when I tried to follow the instructions, it worked for the first step, ./configure or whatever it is, but the ones that followed didn't do a damn thing, it said couldn't find path STOP or something like that.

I will get the files and attach the INSTALL text file so you may possibly translate it for me. =)

EDIT: Could you tell me what the two bottom files are[here?]("http://https://bugs.launchpad.net/ubuntu/+source/network-manager/0.6.6-0ubuntu1")

I know I need the first one but what are the other two??
Thanks so much.

EDIT: > BTW you need the build-essential and linux header files installed in order to compile from source Sorry for being so n00b but what exactly are these and how do I get/use them?

---

### Post by sumguy231 on 2008-03-23
As long as you're following the instructions in the INSTALL file, then what you should post here to help others figure out what's going wrong is what error output you get when you try to follow those instructions. I bet there is probably a better way to fix your problem, but I don't know enough about it to say for sure.

As you requested, the .diff.gz is a compressed file which describes the differences in source code from the last version (for patching) and the .dsc file is a Debian source package.

---

### Post by pHreaksYcle on 2008-03-23
Thank you sum! Now I know I do not need those and I can concentrate on one thing.

One more thing before I leap in and try to get some error codes for diagnostics: **_is it okay to install the older network-manager from source over the top of the newer one or do I have to remove it?_**

I added the INSTALL file as an attachment for ease of assistance.

---

### Post by pHreaksYcle on 2008-03-23
Well, I jumped on in. I cd'ed to the correct directory and did
```
./configure
```
and it gave me ```
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
```

config.log is attached, it's huge and I can't make anything of it.

Is there anything even wrong, can I continue on with "make"?
Awaiting instruction from the pros...thanks again guys.

---

### Post by JoshuaRL on 2008-03-23
Try [this page here.](http://packages.ubuntu.com/search?keywords=network-manager+&searchon=names&suite=hardy&section=all)  Its the official package site for Ubuntu, and the package you need.

Since you're running the Hardy beta and this is from Hardy, have you tried:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install network-manager

```

That might work.  If it says it's already installed, try:
```

sudo apt-get install -reinstall network-manager

```

---

### Post by pHreaksYcle on 2008-03-23
Thank you for your ideas kind sir, but none of the commands came to anything, but I did follow your link. [http://packages.ubuntu.com/hardy/network-manager-gnome](http://packages.ubuntu.com/hardy/network-manager-gnome) looks like what I need but has the -gnome at the end. What is the difference, do you know? Thank you once again!

---

### Post by JoshuaRL on 2008-03-23
Are you using regular Ubuntu or Kubuntu/Xubuntu.  If Ubuntu, then you should be fine.

---

### Post by pHreaksYcle on 2008-03-23
Damn, looks like I lost all you guys...hopefully someone can pick up from here with assistance? I would be greatly obliged.

EDIT: Just saw your last post thx im going to try that package with the -gnome be right back to report.

EDIT: I downloaded it, changed location to it, and ./configure gives the same thing as last time. I will attach the config.log file just in case it is different than the last one.

This is really annoying and I thank you for stickin with me so far

---

### Post by JoshuaRL on 2008-03-23
Well, that package should be a .deb file.  So you wouldn't need to compile at all, just double click and run.  It's the Debian-based-Linux version of an .exe, except so much cooler.

:)

---

### Post by pHreaksYcle on 2008-03-23
Could you post the exact download link you are speaking of? Because the one I ended up using gave me a tar file...I feel so n00b.

---

### Post by smartboyathome on 2008-03-23
I can't find the link to the deb package, but here is my copy. :)

---

### Post by JoshuaRL on 2008-03-23
No problem man.

[http://packages.ubuntu.com/hardy/network-manager](http://packages.ubuntu.com/hardy/network-manager)

Go there to the bottom, click the type of processor architecture you have, click a mirror, and download.  It should give you a choice to open with a DEB manager, you can go ahead and do that.

---

### Post by pHreaksYcle on 2008-03-23
THANK YOU SO VERY MUCH! smartboy's copy was the magic key, thank you to all who helped, forum thanks will be applied. My friend will now be using Linux full time, this was worth it. Thanks again!!!!!


:guitar:

---

