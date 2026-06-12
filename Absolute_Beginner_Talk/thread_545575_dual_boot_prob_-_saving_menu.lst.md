---
title: "dual boot prob - saving menu.lst"
date: 2007-09-07
forum: Absolute Beginner Talk
---

### Post by wbar on 2007-09-07
Can't save menu.lst!!

Hey guys, having a trouble with the dual boot. I was running vista home premium before I installed ubuntu standard i386 edition on a separate partition. From what I understand, I need to go to boot/grub/ and open the menu.lst, add a thingy for vista and save it. I added this right after the ## ## END DEBIAN AUTOMATIC KERNELS LIST ## thing:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title        Microsoft Windows Vista Home Premium
root        (hd0,1)
savedefault
makeactive
chainloader    +1
```

All I changed from the original, which someone on a different site gave me, was the title and root. Wasn't sure if I was supposed to change the # on /dev/hda1. But anyway, I went to save, and it was grayed out, so I went to save as, clicked save, it said that file was write-only, would you like to try to replace it, I clicked replace, then I get an error saying something like "you do not have the permissions neccessary to save the file." Uh, why not? I am the only user on the computer, so I should have full administrative rights. I thought I heard somewhere that in order to edit it, I need to load it from the command line. Is this true?

---

### Post by eapache on 2007-09-07
even though you run the admin account, you need to use sudo (super-user do) to edit system files. Type```
gksudo gedit /boot/grub/menu.lst
```in the command line and enter your password.

explanation: gksudo is sudo for graphical apps. gedit is short for gnome-edit, the text-editor, and /boot/grub/menu.lst is the path to the file.

---

### Post by Ink-Jet on 2007-09-07
In a command-line, type

```
sudo gedit /boot/grub/menu.lst
```

This loads the boot menu in gedit, with super user privileges, menaing you can edit it completely.

---

### Post by eapache on 2007-09-07
Ink-jet: normal sudo causes problems with graphical apps. use gksudo instead.

---

### Post by DBStevens on 2007-09-07
You have to be the proper user and that proper user is root.

Just because you are the only user that doesn't make you root and it doesn't mean that there aren't other users defined on the system.  There most likely are several other defined users.

From a terminal enter:

sudo nautilus

Then you can use normal point and click to select the file and editor to edit menu.lst

Good luck.

---

### Post by eapache on 2007-09-07
DBStevens: please see my other post in this thread. nautilus is a graphical app, so gksudo most be used in place of sudo

---

### Post by DBStevens on 2007-09-07
Oh, exactly why must gksudo be used ?

---

### Post by eapache on 2007-09-07
DBStevens: Sorry if I sounded a bit short in my previous, but using sudo on a graphical app can break your system. gksudo tells it to load the program with graphical hooks despite the fact that it was run in the command-line.

---

### Post by DBStevens on 2007-09-07
You know in many years of using Linux I've never run into a single problem using sudo.  I still want to know what the precise issue is, maybe I just haven't run into it.  I have done literally thousands of sudo calls to graphical applications under many window managers.

---

### Post by eapache on 2007-09-07
There is a good explanation here: [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

### Post by philinux on 2007-09-07
Never used gksudo just sudo, never had a problem. Who is going to run firefox from the terminal?

---

### Post by DBStevens on 2007-09-07
Cute bit of information, the remark about sudo kate is incorrect.

I also believe that the example with the browser would turn out far differently if sudo was used with the proper options.

One really should look at all of the options and properly apply them.  It always has been a case of which option one needs to use.

Failure to choose correctly can result in unintended consequences.

---

