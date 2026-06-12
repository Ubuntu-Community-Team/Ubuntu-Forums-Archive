---
title: "Foxit PDF Reader in Linux?"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by QuITh on 2007-09-01
Hi all,
I use Foxit PDF Reader to read PDF files under WinXP, I can create ellipse markup create line markup, etc; use Highlight Annotation Tools, Note Tools, etc.
Foxit PDF Reader also supports _[Linux]("http://foxitsoftware.com/pdf/desklinux/")_, but Foxit Reader for desktop Linux has just been tested on Fedora 4 and SuSE Linux 10.0.
Now I am using Ubuntu GNU/Linux, any suggestions?

---

### Post by avik on 2007-09-01
Try it.  It doesn't work for me, but then again I'm using 64bit.  Maybe you'll have more luck.

---

### Post by bone2006 on 2007-09-01
does it have a rpm file? If so use alien

install Alien from the synaptic package manager.  Then download the Fedora/Red hate release.  Open up a terminal and type in alien and the name of your rpm file.  It will create a deb file for you.  Run the file and hopefully that will work out for you.

If it's creating PDF Files doesn't openoffice do a decent job and then you can just click export to PDF.  Ubuntu has a default pdf reader that I've been happy with as well.

---

### Post by QuITh on 2007-09-01
> **bone2006 said:**
> does it have a rpm file? 
No, it doesn't. 
> Name: ReaderLinux
Type: executable
MIME type: application/x-executable

> If it's creating PDF Files doesn't openoffice do a decent job and then you can just click export to PDF.  Ubuntu has a default pdf reader that I've been happy with as well.
I use latex to create dvi files, and then convert it to ps or pdf files if I'd like to, :)

---

### Post by mali2297 on 2007-09-01
Open a terminal, *cd* to the directory where you have downloaded the file and type:
```

tar -xvzf FoxitReaderLinux.tar.gz
./ReaderLinux

```
Alternatively, you can double click the icon in the file browser.

However, although the program started for me, it crashed as soon as I tried to open a pdf file. But try it yourself, you might be luckier.

---

### Post by QuITh on 2007-09-01
> v@FlyInDance:~$ cd Desktop
v@FlyInDance:~/Desktop$ tar -xvzf FoxitReaderLinux.tar.gz
ReaderLinux
v@FlyInDance:~/Desktop$ ./ReaderLinux
X Error: BadDevice, invalid or uninitialized input device 169
  Extension:    145 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Extension:    145 (XInputExtension)
  Minor opcode: 3 (X_OpenDevice)
  Resource id:  0x0
Failed to open device
The same things happen to me, :mad:

---

### Post by schorsch on 2007-09-01
Foxit crashes on my computer too if I want to open a PDF file. But the error message you posted regarding the "X Error" has nothing to do with it. To solve the "X Error" problem please take look [here]("http://ubuntuforums.org/showthread.php?t=537976")

---

### Post by QuITh on 2007-09-01
@schorsch: Nice link, My OS is Ubuntu 7.04 Feisty Fawn.

---

### Post by schorsch on 2007-09-01
Well the problem is solved by the method mentioned there anyway ....

---

### Post by QuITh on 2007-09-01
Try now!

---

### Post by QuITh on 2007-09-01
_[FuturePilot]("http://ubuntuforums.org/showthread.php?t=537976")_ 's method doesn't seem to work for me! I cannot start X after reboot. Maybe that just works with Kubuntu users.

---

### Post by schorsch on 2007-09-01
Try
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
on the command line and then
```
startx
```

---

### Post by QuITh on 2007-09-01
@schorsch: Well, thanks, I got into X now.

---

### Post by schorsch on 2007-09-01
Sorry, I should have told you to backup the file /etc/X11/xorg.conf before editing .... ;-)

---

### Post by QuITh on 2007-09-01
> **schorsch said:**
> Sorry, I should have told you to backup the file /etc/X11/xorg.conf before editing .... ;-)
Just some "Delete" time.[-(
I delete the "#"s one-by-one.

---

### Post by bogolisk on 2007-09-01
I've run Foxit Reader for Linux without problem in gnome. The issue is the linux version doesn't let you do things like filling form and adding text like the windows version!:(

Btw, the old 1.5 version does run fine under wine. But with wine, YMMV.

---

### Post by QuITh on 2007-09-01
> **bogolisk said:**
> I've run Foxit Reader for Linux without problem in gnome.
Hey bogolisk, can you tell me how?
> **bogolisk said:**
> The issue is the linux version doesn't let you do things like filling form and adding text like the windows version!
Upset!

---

### Post by bogolisk on 2007-09-01
> **QuITh said:**
> Hey bogolisk, can you tell me how?

Upset!

Sorry, I'll take back my comments. I've run it successfully under gnome on RHEL4WS not on Ubuntu!:(

---

### Post by schorsch on 2007-09-01
Perhaps you can use pdfedit instead. It is available in the repos and just yesterday I helped compiling an actual version .... Take a look [here]("http://ubuntuforums.org/showthread.php?t=538338") ;-)

---

### Post by QuITh on 2007-09-01
> **schorsch said:**
> Perhaps you can use pdfedit instead. It is available in the repos and just yesterday I helped compiling an actual version .... Take a look [here]("http://ubuntuforums.org/showthread.php?t=538338") ;-)
Nice thing, schorsch. I had apt-get installed it. Oh BTW, how about Adobe? I've never use it under WinXP.

---

### Post by schorsch on 2007-09-02
Sorry, I never used (and bought!) any Adobe apps...or are you just looking for the free reader program that is .... well, really large?

---

