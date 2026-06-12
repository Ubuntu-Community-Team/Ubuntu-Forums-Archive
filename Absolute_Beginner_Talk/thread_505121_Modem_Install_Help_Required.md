---
title: "Modem Install Help Required"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by victor9098 on 2007-07-19
Hello All,

Right, to bring you up to speed. I ran the Live CD, saw what did not work (both my dial-up & USB Modem) but I found a fix for the USB problem. So installed Ubuntu...BUT once I was ready to go I realised I had not a clue how to input the fix!!!! ](*,)

So I am basically looking for an idiots guide to walk me through what to do. Here is the website that lists the fix: [http://oozie.fm.interia.pl/pro/huawei-e220/](http://oozie.fm.interia.pl/pro/huawei-e220/), I downloaded the file, placed it on my external HD and then thought a simple click would launch it and then onto the web. 

Any guidance would be greatly appreciated...so close yet so far away! #-o

---

### Post by kidcharles on 2007-07-19
Looking at that website, it seems they have the commands you need to perform in blue boxes to the left of each item.

```
$ tar xjvf huawei.tar.bz2
$ cd huawei
$ su
# make info
```

Do you know how to open a shell to type in commands?

Under the 'Applications' menu choose Accessories->Terminal

Then you can type in the commands that are listed.

Make sure this file is in your home folder before you do this.

I would change them up a bit for Ubuntu:

```

$ tar xjvf huawei.tar.bz2
$ cd huawei
$ sudo make info

```

'su' and 'sudo' are ways to do things that require administrator level permissions.

---

### Post by victor9098 on 2007-07-19
To update my previous post,

Ubuntu does detect the modem, it was listed in the Hardware anyway. So my problem is getting the default settings into  wvdial!? 

Is this when I start my crash course with the terminal?

---

### Post by kidcharles on 2007-07-19
It looks like wvdial  (like most programs) is configured by editing a file in the /etc directory, in this case /etc/wvdial.conf. Sometimes these configuration files have a bunch of useful things in them, you might want to look at this file using 'gedit' or a different text viewer/editor.

---

### Post by kidcharles on 2007-07-19
My wvdial.conf file has this in it:

```

[Dialer Defaults]
Phone =
Username =
Password =
New PPPD = yes

```

I think your first move might be to fill in the blanks.

---

### Post by kidcharles on 2007-07-19
If you type in:

```

$ man wvdial.conf

```

in a terminal that will bring up the man(ual) page for the configuration file, that may be of use.

---

### Post by victor9098 on 2007-07-19
Ok, found a guide [http://ubuntuforums.org/showthread.php?t=302464](http://ubuntuforums.org/showthread.php?t=302464)

But...when I create the config file with a text editor where do I save it to?

---

### Post by kidcharles on 2007-07-19
You should save it as 'wvdial.conf' in the /etc directory. In order to do this you have to have root permissions. The easiest way to do this is to type:

```

$ sudo gedit

```

at the terminal prompt, which will open the gedit text editor with root permissions, then you can edit the file and save it to the /etc directory with no problem.

---

### Post by victor9098 on 2007-07-19
I have so much to learn!

10 years on Windows, there was always going to be a steep learning curve.

Anything else you think before I try the install again?

---

### Post by kidcharles on 2007-07-19
Give it a shot with your new config file.

---

### Post by victor9098 on 2007-07-20
If you do not mind I will send you an IM just to let you know if I passed this first test!

Thank you for all the help.

---

### Post by Bartender on 2007-07-20
victor -
Take a look [here]("http://ubuntuforums.org/showthread.php?t=480717") if you haven't already seen it.  I aimed this at the beginner, including the steps to get thru wvdial.

---

