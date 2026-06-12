---
title: "new user with some quetions"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by MaaSTaaR on 2005-12-22
Hello ...

i installed ubuntu and i have some question .

1: i want install my modem drivers and it's requiest KERNEL DIR , where i can find kernel dir ?
2: i don't found connection tools ?
3: how i can control in Gurb or install LILO as alternative

finally , thank you very much :)

---

### Post by futz on 2005-12-22
[QUOTE=MaaSTaaR]1: i want install my modem drivers and it's requiest KERNEL DIR , where i can find kernel dir ?[/quote]
Not sure about that one.

> 2: i don't found connection tools ?
Top panel/System/Administration/Networking? If that's what you mean by connection tools.

> 3: how i can control in Gurb or install LILO as alternative
Grub is much easier to deal with than lilo, in my opinion. The config file can be found at /boot/grub/menu.lst

You must have root privileges to edit it, so 'sudo gedit /boot/grub/menu.lst' will get you editing. You would be very wise to make a backup of the file before making any changes. Be careful what you change, obviously, as you can make your system unbootable with this file. 

For info on grub, read the info and/or man pages for it ('info grub' and 'man grub') and google for many articles on how to set it up. 

If you have a specific question, I wouldn't call myself an expert on grub but I understand it well enough to get around in it. I've installed and reinstalled and edited it enough times, since I have two multi-boot systems that have changed many times. Post your menu.lst file with any questions.

---

### Post by Sutekh on 2005-12-22
If you want to install modem drivers, it probably wants to know where the kernel source for you kernel is.

It will be under the folder; /usr/src/  but you'll have to install it first.

Install the build-essential package (make and other tools for compiling)
```
sudo apt-get install build-essential
```
To download your kernel headers you will need to determine your kernel version; at a command line type
```

uname -r

```
You will get something like **2.6.12-10-386**. You would need to then download the kernel headers using
```

sudo apt-get install linux-headers-**2.6.12-10-386**

```
Of course if your kernel version is different, just adjust that code.
To download the kernel source you'll need to 
```

sudo apt-get install linux-source-**2.6.12**

```
Forget the -10-386 part.

Then you can continue to install them.
Here is a good link for installing software.
[http://www.psychocats.net/linux/installingsoftware.php]("http://www.psychocats.net/linux/installingsoftware.php")

---

### Post by MaaSTaaR on 2005-12-23
Hello ...

futz :
thanks man , i will read man gurb :)

Sutekh :
thanks Sutekh , the problem is i can use apt-get command becuase i am still don't have internet in Linux , where i can find these files in the sites without use apt-get command ?

---

### Post by Sutekh on 2005-12-23
Sorry!  I completely overlooked the fact you were compiling *modem* drivers. :mad: 

Alright, behold the [Ubuntu Package Archive]("http://packages.ubuntu.com/").

Here are some links

[build-essential]("http://packages.ubuntu.com/breezy/devel/build-essential")

[linux-headers-2.6.12-10-386]("http://packages.ubuntu.com/breezy/devel/linux-headers-2.6.12-10-386")
(make sure that's correct for you, remember uname -r)

[linux-source-2.6.12]("http://packages.ubuntu.com/breezy/devel/linux-source-2.6.12")
(You may not need this one)

Now just download these packages and copy them to /var/cache/apt/archives
I think apt-get should be able to install these, even though you don't have internet.  

If not, then you can install them manually.
```
sudo dpkg -i <packagename>
```

Please note that on each of those package pages, there are dependencies.  Make sure that you have them installed or you will have to download them too.  It could become quite complex, which is why apt-get in so darn good.

I'm not sure how you check whether you have the corerct dependencies installed, other than to just check each one manually in Synaptic.  Hopefully someone can shed some light on this.

Hope that's understandable...
Best of Luck

---

