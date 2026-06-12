---
title: "[SOLVED] absolutely new to Ubuntu, first question..."
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by rickhurl on 2008-03-01
Hello,

After being very sick of Windows (for several reasons) I've decided to go with Ubuntu.  This is really very new to me and is pretty difficult right now.

I've downloaded an iso, but I can't figure out how to get it to install for me.  I need absolute step be step instructions on how to do this, where to go within Ubuntu, which program(s) to use etc...  I'm talking before square one.

Thanks everyone,

The iso is Soldier of Fortune
[COLOR="DarkOliveGreen"]
INSTALLATION
----------------

Mount the Soldier of Fortune CD and change the current directory to
where it is mounted. Type 'sh setup.sh' to run the install script.

e.g.  Log in as root:
  $ mount /mnt/cdrom
  $ cd /mnt/cdrom
  $ sh setup.sh[/COLOR]

But this does not seem to work for me when I use cvs...

---

### Post by taurus on 2008-03-01
Burn:  [https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28iso%29)

Install:  [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

p.s.  Have you already installed Ubuntu on your machine?

---

### Post by rickhurl on 2008-03-01
I've already installed Ubuntu, have my geforce 7900 nvidia installed, installed nvclock---what a nightmare for me---and everything else is working pretty well.  I just have no idea what to do when I download a program, how to get it to work, install, or anything...thanks for the link

---

### Post by taurus on 2008-03-01
Then you need this link, [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/).

---

### Post by boombox1387 on 2008-03-01
Welcome to Ubuntu!  I'm pretty new to Linux/Ubuntu myself, but I'll give this a shot.

Step 1: Download and install Gmount-iso
The .iso file is a disk image that can be burned to a CD or mounted as a virtual CD.  Ubuntu may have built-in support for mounting .iso images, but I don't remember and I'm not at my computer to check.  Either way, I would recommend using a program called Gmount-iso instead.  To install it, open terminal and type:

```
sudo apt-get install gmountiso
```

Step 2: Mount the .iso
Installing the program this way should add Gmount-iso to the "Applications > System Tools" menu.  Open the program and in the top line, browse to the .iso file.  In the second blank, set the mount point.  I'd recommend typing /media/iso  (By default Ubuntu creates mount points for hard drives, CDs, and USB sticks in the /media folder.)  I forget how the program responds if the directory doesn't exist.  If it complains, you can create the new folder by going back to terminal and typing:

```
sudo mkdir /media/iso
```

In Gmount-iso, click the Mount button and it will ask for your password.  Once you type that, the .iso should be mounted.

Step 3: Install
In terminal, navigate to the mounted iso:
```
cd /media/iso
```
And follow the Soldier of Fortune instructions:
```
sudo sh setup.sh
```

Hope this helps.  These websites are also useful:
[for more about Gmount-iso]("http://www.ubuntugeek.com/easy-way-of-mountunmount-iso-images-in-ubuntu.html")
[for installing things in Ubuntu]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by rickhurl on 2008-03-01
everything works right unitl the end code, I get 

"setup.sh: 9: function: not found
x86

???

any ideas?

Thanks for the help too, I appreciate it very much!

---

### Post by boombox1387 on 2008-03-01
Do you know what version of Ubuntu you're running?  Is it the 64-bit operating system?  From the "x86" part of the error, it sounds like it's trying to install a 32-bit version of the game on a 64-bit OS (or possibly vice versa).  If they make a 64-bit version of the game for Linux, that's probably what you want.

I could be completely wrong, but this is my best guess.

---

### Post by boombox1387 on 2008-03-01
After reading [this thread]("http://ubuntuforums.org/showthread.php?p=4419114") I changed my mind.  instead of trying "sudo sh setup.sh" in the last step, try this instead:

```
sudo apt-get install ksh
sudo ksh setup.sh
```

Hope this works.

---

### Post by rickhurl on 2008-03-01
Thank you so much, this works great.  I have a lot to figure out.

Thanks again!

---

