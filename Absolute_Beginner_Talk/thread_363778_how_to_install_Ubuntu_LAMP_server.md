---
title: "how to install Ubuntu LAMP server?"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by ColmOsiris on 2007-02-17
I've been using Macs for many years, and now I've got a PC to install Linux on.

I got a Ubuntu install ISO from [www.ubuntu.com](www.ubuntu.com), and copied it to a CD.

It installed fine, but didn't give me the LAMP server option.

I went back to [www.ubunto.com](www.ubunto.com), and the 'desktop' and 'server' links seem to both go to the same page ([http://www.ubuntu.com/download)](http://www.ubuntu.com/download)).

The install options I get are:

* Start or install Ubuntu
* Start Ubuntu in safe graphics mode
* Check CD for defects
* Memory test
* Boot from first hard disk

Nothing about a LAMP server. :-(

(Pressing F6 gives me this:

"Boot Options ._size=1048576 root=/dev/ram rw quiet splash --|"

What do I do, please?

---

### Post by TeraDyne on 2007-02-17
Download the Server Install CD. Most mirrors have it for Edgy under the "Other Installation Options" option for the download. For example, go to: [http://ftp-mirror.internap.com/pub/ubuntu-releases/edgy/](http://ftp-mirror.internap.com/pub/ubuntu-releases/edgy/)
and look at the list. There will be a Server Install CD section there.

You could also just install Ubuntu and pick all the packages out yourself via Synaptic.

---

### Post by Muzik83 on 2007-02-17
LAMP refers only to whats running on the server, so you "can" use ubuntu desktop as a server (which is nice if you are going to use it for a workstation as well)

Since you already have the Linux portion of the LAMP, you just need the AMP.

In System, Administration, Synaptic Package Manger, search for apache2, mysql-server and php5

You will also need libapache2-mod-php5 and php5-mysql

Note in Synaptic to install stuff you will need to click on the box which is left of the name and choose mark for installation.  It took me a while to figure out why right click wasn't working in Synaptic ;)

-sean

---

### Post by ColmOsiris on 2007-02-17
Thanks TeraDyne and Muzik83.

I decided to go down the Synaptic route, as apparently the Ubuntu server installation doesn't give me a GUI, and I'm not ready for that yet!

Anyway, I selected all the things you mentioned, Sean, and clicked 'apply', and then it told me that some of the things I need have to be downloaded. That's a good trick, since the machine isn't yet online!

Nor can it be, as my router only has 1 port, and I need that for my Netgear wireless access point, for the Mac (*). I do have a SafeCom USB wireless adaptor which claims to have a Linux driver, but I haven't the first idea how to install that. And anyway, I'm told if the driver isn't installed at system installation time, it won't work!

If Synaptic had told me *which* things I needed to download, I could probably have done it on my Mac and transferred them via CD, but unfortunately it didn't. What can I do now?

Thanks again.

(*) I can't move the router, because it's also being used by a wireless client in a boat on the canal, and she'd lose her connection if I did.

---

### Post by TeraDyne on 2007-02-17
Here's an idea, though I'm not sure it would work.

Maybe you could use the apt-cdrom command along with the Ubuntu Server Install CD to add the CD as a repository, and then grab everything you need off of that? Anyone know if that would work?

---

### Post by ColmOsiris on 2007-02-17
Thanks, but I'm afraid I don't understand that. Can you explain it in simple terms please? I'm not even sure how to get to the command line on my new machine, let alone of the relevant commands!

---

### Post by TeraDyne on 2007-02-17
For a command line, you can either open a terminal window in Applications > System > Terminal or somewere in that area, or you can hit CTRL + ALT + any one of F1-F6 to get to another terminal, though you'll have to login there.

Then, to add the cdrom, the command is:

```
sudo apt-cdrom add
```

I'll ask for the disk, so just insert it and hit enter, and it'll go from there. That should be it.

---

### Post by ColmOsiris on 2007-02-17
Thanks, I've done that. But now, in Synaptic, I did a search for 'apache2', 'mysql-server',  'php5', 'libapache2-mod-php5' and 'php5-mysql', and none of them was found!

---

### Post by TeraDyne on 2007-02-17
Ok, that's odd. Try running

```
sudo apt-get update
```

and see if there's an error.

---

### Post by ColmOsiris on 2007-02-18
I did that, and then tried Synaptic again. This time the packages and files were there, but when I clicked 'apply', I got loads of error messages. They looked like this:

> W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/a/apache/libapr0_2.0.55-4ubuntu4_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/a/apache/libapr0_2.0.55-4ubuntu4_i386.deb)
   Temporary failure resolving 'archive.ubuntu.com'

Perhaps I do need to get the machine online first after all, before I do anything else? In which case, I guess it should be a new thread.

---

