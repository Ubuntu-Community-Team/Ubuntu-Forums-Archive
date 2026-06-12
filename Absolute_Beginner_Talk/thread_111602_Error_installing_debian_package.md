---
title: "Error installing debian package"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by Raymosexual on 2006-01-02
Ok, I'm totally new to linux, but I got my box up and running with Ubuntu 5.10.
I want to install gtkpod for use w/ my 4G ipod.  When I tried installing it from the package manager, it informed me that i needed libid3tag0 (>=0.15.1b)
I downloaded the debian package and from the terminal i tried

apt-get install libid3tag0_0.15.1b-7.i386

and i get the error:

E: Could not open lock file /var/lib/apt/lists/lock - open (13 permission denied)
E: Unable to lock the list directory

I tried googling for answers w/ no luck. Can anybody help me?

---

### Post by Jukey on 2006-01-02
maybe try sudo apt-get.
i'm new too but try that

---

### Post by kingsidy on 2006-01-02
usually when you get a permission error that means that you are not using sudo so try it again as a sudo

---

### Post by Raymosexual on 2006-01-02
Ok so I tried it with sudo and now I'm getting another error:

E: Could not lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I checked my processes but I'm not really sure what I'm looking for.

---

### Post by cwaldbieser on 2006-01-02
[QUOTE=Raymosexual]Ok so I tried it with sudo and now I'm getting another error:

E: Could not lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

I checked my processes but I'm not really sure what I'm looking for.[/QUOTE]
Normally it means you have another copy of apt-get, synaptic, or aptitude open.

---

### Post by Raymosexual on 2006-01-02
Ok, now i feel really stupid. Synaptic was open and I closed it but now i get this:

sudo apt-get install libid3tag0_0.15.1b-7_i386
Reading package lists...Done
Building dependency tree...Done
E: Couldn't find package libid3tag0_0.15.1b-7_i386

I'm at root@ubuntu:~/Desktop$ when i issue the command b/c thats where the package is.  I also tried it with the .deb extension even though I'm pretty sure you're not supposed to put that. I triple checked for typos, too.

---

### Post by Jukey on 2006-01-02
did you check for capps? linux is case sensitive.

---

### Post by Raymosexual on 2006-01-02
No such luck.  There's not even any capital letters.

---

### Post by Perfect Storm on 2006-01-02
Did you have enable the stuff in your sourcelist?

---

### Post by Raymosexual on 2006-01-02
Sorry I don't understand. Where is the sourcelist?

---

### Post by harisund on 2006-01-02
A couple of things .. 

1. apt-get searches from a centralized repository of software / libraries. Now what this means is that there is a big machine out there somewhere which holds all the libaries and software binaries. You say apt-get install and it automatically downloads the required software package, and also downloads all the required libraries. 
2. If it says it needs a library, that means the libary is not found in that repository. So you need to add extra repositories. Do search in the forums for how to do that. 
3. You generally do not download a single .deb file and try to install it. It may depend on some other library, and if you dont have that library it is going to complain again. The only reason you would download a .deb file is when the software has been packaged for debian and not available in any repository yet. And generally you don't download individual libraries. 
4. If you do want to install a .deb file you downloaded, you don't use the apt-get command. Instead you do
sudo dpkg -i name_of_deb_file.deb

Hope it works !

---

### Post by Lord Illidan on 2006-01-02
I think you should read this : [http://help.ubuntu.com/starterguide/C/faqguide-all.html](http://help.ubuntu.com/starterguide/C/faqguide-all.html)

It should give you a lot of help on what to do... otherwise you are going to end up with a sour first experience of Ubuntu.

---

### Post by Perfect Storm on 2006-01-02
First, you said you downloaded a debian package (.deb). To install it
```

cd /where/the/package/is
sudo dpkg -i XXXXXXXX.deb

```

But the package you seek is in your sourcelist if you enable some lines which are disable.

To do so 

```

sudo gedit /etc/apt/sources.list

```

Here you'll see some lines which have 1 **#** infront of it. remove the #.
Here an example:

> 
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe


save it

now
```

sudo apt-get update
sudo apt-get install libid3tag0

```

---

### Post by Raymosexual on 2006-01-02
Muchos Gracias.  I was able to install the debian package using dpkg and then install gtkpod using apt-get. Again, Thankyou

---

