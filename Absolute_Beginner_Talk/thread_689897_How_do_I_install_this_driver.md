---
title: "How do I install this driver?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by Beornz on 2008-02-06
Hi, this is my first time using Ubuntu/Linux.  I did a search on the forum and I didn't see anything that helped me out so I figured I'll start my very first thread with a question.  How do I install a driver that I downloaded from nvidia?  It seems that my graphic card (Geforce 8800 GT) is not working, especially with Compizfusion.  So, I cannot enable any advance desktop effect.

The file is "NVIDIA-Linux-x86-169.09-pkg1.run" and it's on my desktop.  Now... how do I install it?

Thanks~

P.S.

I have a five buttons mouse, anything I can get to use my default feature of the mouse to move forward and backward in firefox?  Thanks again :-D

---

### Post by Jimmyfj on 2008-02-06
Instead of installing the driver from a downloaded file you can install it via the Ristricted Drivers Manager. Go to System/Administration/Hardware Drivers and let the manager install it for you.

---

### Post by Beornz on 2008-02-06
I get this message:

"Your hardware does not need any restricted drivers."

I forgot to mention that I'm on Gusty 7.10.

---

### Post by y-lee on 2008-02-06
> **Jimmyfj said:**
> Instead of installing the driver from a downloaded file you can install it via the Ristricted Drivers Manager. Go to System/Administration/Hardware Drivers and let the manager install it for you.

Jimmyfj is probably right that is the best and easiest way to to do it :)

but  **sh NVIDIA-Linux-x86-169.09-pkg1.run** should install the driver if for some reason you decide you must.

---

### Post by Beornz on 2008-02-06
I tried the "sh NVIDIA-Linux-x86-169.09-pkg1.run" option but I get this message:

"sh: Can't open NVIDIA-Linux-x86-169.09-pkg1.run"

Spelling is correct.  I'm not sure what I am doing wrong...

---

### Post by y-lee on 2008-02-06
check the files permissions. You probably need execute permission.

---

### Post by Beornz on 2008-02-06
Not sure what you mean but I decided to post a few screenshots.

[IMG]http://img.photobucket.com/albums/v195/BigBear/Screenshot.png[/IMG]

[IMG]http://img.photobucket.com/albums/v195/BigBear/not.png[/IMG]

[IMG]http://img.photobucket.com/albums/v195/BigBear/error.png[/IMG]

[IMG]http://img.photobucket.com/albums/v195/BigBear/none.png[/IMG]

-----------------------------------------------------

I hope you can read it. >_>;;

---

### Post by Whiffle on 2008-02-06
As far as I know, the restricted drivers manager doesn't have the drivers for the newest cards yet, so you're stuck with other means. (might try searching for envy before you try my way...)

This is how I do it. The nvidia installer won't let you install it if X is running, so...

First, 
```

sudo apt-get install build-essential

```

then close everything you have running, and logout.

Then do:

Ctrl+alt +f2

Login there to the text console, and run:

```

sudo /etc/init.d/gdm stop

```

then,

```

sudo chmod +x NVIDIA..blahblah.run
sudo sh NVIDIA...blahbloahblah.run

```

It will run, ask a couple of questions, compile a kernel module, update your xorg file, and you should be good to go.  When its done,
```

sudo /etc/init.d/gdm start

```
should get you back to your login.  If all goes well, it will run.  If not, it won't.  If it doesn't, do:
```

sudo nano -w /etc/X11/xorg.conf

```

and go down to where it says 
```

Driver "nvidia"

```

and change nvidia to nv .   Hit F3 to save, ctrl X to exit, and then try starting gdm again. 

*crosses fingers*

EDIT: If you ever change kernels (or update them), you will need to redo this process.

---

### Post by Beornz on 2008-02-06
For some odd reason, when I do **sudo chmod +x NVIDIA-Linux-x86-169.09-pkg1.run**, it read "No such file or directory."  I even renamed the file to **nvidia.run** (to shorten the name) to make sure spelling is exact.  Anyone know why?

---

### Post by Beornz on 2008-02-06
Problem solved.

No one mention "Make sure you **cd Desktop** before you try **sh NVIDIA***"

Thanks for the help.  Even though I'm a complete noob, don't forget the small details! :)

---

### Post by turbo_dsm on 2008-02-07
> **Beornz said:**
> Problem solved.

No one mention "Make sure you **cd Desktop** before you try **sh NVIDIA***"

Thanks for the help.  Even though I'm a complete noob, don't forget the small details! :)

what do you mean cd Desktop?

---

### Post by Beornz on 2008-02-07
> **Whiffle said:**
> As far as I know, the restricted drivers manager doesn't have the drivers for the newest cards yet, so you're stuck with other means. (might try searching for envy before you try my way...)

This is how I do it. The nvidia installer won't let you install it if X is running, so...

First, 
```

sudo apt-get install build-essential

```

then close everything you have running, and logout.

Then do:

Ctrl+alt +f2

Login there to the text console, and run:

```

sudo /etc/init.d/gdm stop

```

then,



This is where I used **cd Desktop** since I downloaded NVIDIA.run to my desktop.  Which the next step for me is:

```

cd Desktop

```

Once I did this, I was able to follow the rest of the step as quoted.

> **Whiffle said:**
> 

```

sudo chmod +x NVIDIA..blahblah.run
sudo sh NVIDIA...blahbloahblah.run

```

It will run, ask a couple of questions, compile a kernel module, update your xorg file, and you should be good to go.  When its done,
```

sudo /etc/init.d/gdm start

```
should get you back to your login.  If all goes well, it will run.  If not, it won't.  If it doesn't, do:
```

sudo nano -w /etc/X11/xorg.conf

```

and go down to where it says 
```

Driver "nvidia"

```

and change nvidia to nv .   Hit F3 to save, ctrl X to exit, and then try starting gdm again. 

*crosses fingers*


And.... it worked!  Good luck for whoever has the same problem as me!

---

### Post by turbo_dsm on 2008-02-07
i have the same problem and when i do cdDesktop it does a bunhc of little tasks then at the end asks me to insert a cd into the cd drive :(

---

### Post by Whiffle on 2008-02-07
Just as a note, if you do it the way I said above, the nvidia driver will need to be reinstalled when your kernel gets upgraded.  So watch those kernel upgrades and keep a copy of the driver on your hard drive somewhere.  Glad it worked out.

turbo_dsm, where did you save the nvidai driver?

---

### Post by turbo_dsm on 2008-02-09
on the desktop

---

### Post by ayenack on 2008-02-09
You have to be in the correct directory for it to run.

If this was desktop it'd be something like this.

**cd /home/ayenack/Desktop** (where ayenack is your user name)

Then you would type this.

**sudo sh NVIDIA-Linux-x86-169.09-pkg1.run**

Much better to use restricted drivers manager from system menu if possible.

One last thing please make a backup of your xorg.conf like this.

**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup**

If everything goes wrong and you end up at the command line do this to restore your previous xorg.con and the GUI.

**sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf**

Making sure to use capitol "X" in all instances of "X11"

---

### Post by turbo_dsm on 2008-02-09
after i type in sudo apt-get install build-essential
it tells me to hit Y or N and i hit Y and then it tells me to insert drive into cd rom. do i do this or just go right to hitting ctrl+alt+f2

---

### Post by ayenack on 2008-02-09
It's asking you to insert the Ubuntu CD/DVD ROM that you installed Ubuntu with so put that into you CD/DVD drive and type the commands again. If you do not have it and the install stalls you'll need to edit /etc/apt/sources.list and comment out the deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted. To do this follow these instructions.

Make a backup of sources.list like this.

In Terminal.

**sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup** (cp stands for copy and all that's happening here is that the file is being copied and renamed)

If you need to restore your sources.list to how it was do this in Terminal.

**sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list** (Only do this if you want to restore your sources.list)

Now do this to install build-essential.

**gksu gedit /etc/apt/sources.list** (this will open up a file called sources.list)

Edit the file by commenting "#" out Gusty Gibbon cdrom entry as shown.

**#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted** (Commenting it out will stop it from being used when you install programs and means they will be downloaded from the internet.)

Save the file. and do this. In Terminal.

**sudo apt-get update**
**sudo apt-get install build-essential**

But don't know why you don't just follow my previous post.

---

