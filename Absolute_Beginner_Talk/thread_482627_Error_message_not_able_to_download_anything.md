---
title: "Error message: not able to download anything"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by superintelligentape on 2007-06-23
Whenever I attempt to download updates through the update manager or any other download I receive this error message:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

---

### Post by BobCFC on 2007-06-23
It's because it crashed during an update.  Go to 

Applications -> Accessories -> Terminal 

and paste 

```
sudo dpkg --configure -a
```

to recover.


Then run the update thingy again.   It should be fine


You can paste into Terminal with middle button or right-click and use the menu

---

### Post by oilchangeguy on 2007-06-23
open a terminal, and type sudo dpkg --configure -a and press enter.

---

### Post by superintelligentape on 2007-06-23
I did that and this error message showed up:
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

And I ran that file in Terminal but all that showed up was a blue screen with something from Sun Microsystems

---

### Post by BobCFC on 2007-06-23
Which did you run Synaptic?  That is the big brother of add/remove

Do the command 

```
sudo apt-get install -f
```

in the terminal it should just be text output.

---

### Post by stalkier on 2007-06-24
I am running into a similar issue. I was uninstalling some software right before the power went out. Here is my error after running sudo command.

dpkg: parse error, in file `/var/lib/dpkg/updates/0022' near line 1:
 field name `server.htm' must be followed by colon

How do I fix this? Thanks for the help. BTW I am still fairly green when it comes to Linux. I have been off and on with Ubuntu for a while. Thanks again.

---

### Post by superintelligentape on 2007-06-24
ok thanks I did that command again and realized there was an OK button I didnt see before...thanks fro all the help and putting in in terms I can understand :)

---

### Post by gloxer54 on 2007-06-24
same type of problem with Synaptic (I'm a very noobie).   I can not install or uninstall without getting this message:

E: msttcorefonts: subprocess post-installation script returned error exit status 1
E: ubuntu-restricted-extras: dependency problems - leaving unconfigured

  I can not find anything out about how to fix this.  Can anyone help?
  I'm at my wit's end
       thanks

---

### Post by BobCFC on 2007-06-24
possibly try this at terminal?  just guesswork not sure

```
sudo dpkg-reconfigure msttcorefonts
```

---

### Post by gloxer54 on 2007-06-25
BobCFC 
 I tried the code : 
sudo dpkg-reconfigure msttcorefonts 
 
 and the result was:
ham@ham-desktop:~$ sudo dpkg-reconfigure msttcorefonts
Password:
/usr/sbin/dpkg-reconfigure: msttcorefonts is broken or not fully installed
ham@ham-desktop:~$ 

 Now since I can not download anything in Synaptic, Add & Remove programs or the terminal, I am really stuck.  :confused: So I figure that that did not work.  I thank you for the attempt, but I still need something that works.
  Anyone? Please?
   Thanks again for listening.

---

### Post by BobCFC on 2007-06-25
Ok have a go a removing manually?

```

sudo apt-get --purge remove msttcorefonts
```

---

### Post by gloxer54 on 2007-06-26

  I did remove it manually with what  BobCFC suggested:

sudo apt-get --purge remove msttcorefonts

and IT Worked!!!  YEAH!!!  Thanks BobCFC.  I now can download and update without any errors.!!
Thanks to all for having this thread.  Now I am now going back to learning the terminal script stuff (bashing?).
  Thanks to all you folks for being here.

---

