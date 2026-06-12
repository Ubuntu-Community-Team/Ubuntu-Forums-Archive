---
title: "Make Fedora 15 USB"
date: 2011-09-09
forum: Any Other OS
---

### Post by doppel.ganger on 2011-09-09
How would I make a Fedora 15 USB stick in Ubuntu 11.10 Beta 1? Is it even possible?

-DG

---

### Post by wojox on 2011-09-09
unetbootin will let you do it. DD command as well. Unless your looking for persistence.

---

### Post by doppel.ganger on 2011-09-09
What do you mean, looking for persistence?

---

### Post by P05TMAN on 2011-09-09
You could always go the easy route an d check out pendrivelinux.com. I think there is a linux download for that program.

---

### Post by wojox on 2011-09-09
Do you want a flash drive you can save random files on and the next time you load it they will be there?

---

### Post by P05TMAN on 2011-09-09
> **doppel.ganger said:**
> What do you mean, looking for persistence?

Persistence allows you to save changes to the live usb without actually having installed Linux to hard disk, if I'm not mistaken

---

### Post by haqking on 2011-09-09
see here [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

probably can be modified to suit Fedora, if not will explain peristence etc.

---

### Post by doppel.ganger on 2011-09-09
As long as I can run it live and install it. I guess that's persistence.

---

### Post by wojox on 2011-09-09
> **doppel.ganger said:**
> As long as I can run it live and install it. I guess that's persistence.

Sure if you want to run it live then dd or unetbootin will do it.

---

### Post by doppel.ganger on 2011-09-09
What's dd?

---

### Post by wojox on 2011-09-09
> **doppel.ganger said:**
> What's dd?

Only one of the most awesome commands ever created. [DD command]("http://en.wikipedia.org/wiki/Dd_(Unix)")

---

### Post by doppel.ganger on 2011-09-09
How would I use it to install Fedora installer + Live to a stick?

---

### Post by wojox on 2011-09-09
> **doppel.ganger said:**
> How would I use it to install Fedora installer + Live to a stick?

You should probably download unetbootin from the repo's and use it. 
DD can be a little tricky (and dangerous).

Don't you have the Fedora-15 iso?

---

### Post by haqking on 2011-09-09
everything you need is here [http://fedoraproject.org/wiki/How_to_create_and_use_Live_USB](http://fedoraproject.org/wiki/How_to_create_and_use_Live_USB)

it is if you are on Fedora, but you can still use unetbootin in ubuntu

---

### Post by 2F4U on 2011-09-10
I never had a problem putting a Fedora liveCD with dd on a USB stick. However, you need a running Linux to be able to use dd. 

[http://fedoraproject.org/wiki/How_to_create_and_use_Live_USB#Using_dd_for_a_direct_copy](http://fedoraproject.org/wiki/How_to_create_and_use_Live_USB#Using_dd_for_a_direct_copy)

From a Windows machine, I used to use Fedora liveusb-creator

[https://fedorahosted.org/liveusb-creator/](https://fedorahosted.org/liveusb-creator/)

---

### Post by lisati on 2011-09-10
*Thread moved to **Other OS/Distro Talk**.*

---

### Post by pierreyy on 2011-09-10
hey!

 there is an .exe program called yumi if you have wine itll run it fine... you download the .iso file from wherever and you use the program to make your usb bootable... good luck!

---

### Post by doppel.ganger on 2011-09-10
Do I need to first ```
thomas@Thomas-Dell-DE051:~$ cd ~/Downloads/Fedora-15-i686-Live-KDE
thomas@Thomas-Dell-DE051:~/Downloads/Fedora-15-i686-Live-KDE$ isohybrid Fedora-15-i686-Live-KDE.iso
thomas@Thomas-Dell-DE051:~/Downloads/Fedora-15-i686-Live-KDE$
```
Then do dd?

---

### Post by doppel.ganger on 2011-09-10
Cuz I already did :)

I downloaded Fedora-15-i686-Live-KDE.iso if that helps.

---

### Post by haqking on 2011-09-10
> **doppel.ganger said:**
> Do I need to first ```
thomas@Thomas-Dell-DE051:~$ cd ~/Downloads/Fedora-15-i686-Live-KDE
thomas@Thomas-Dell-DE051:~/Downloads/Fedora-15-i686-Live-KDE$ isohybrid Fedora-15-i686-Live-KDE.iso
thomas@Thomas-Dell-DE051:~/Downloads/Fedora-15-i686-Live-KDE$
```Then do dd?


There is a step-by-step tutorial link in my post #14 above

---

### Post by doppel.ganger on 2011-09-10
```
thomas@Thomas-Dell-DE051:~$ cd ~/Downloads/Fedora-15-i686-Live-KDE
thomas@Thomas-Dell-DE051:~/Downloads/Fedora-15-i686-Live-KDE$ isohybrid Fedora-15-i686-Live-KDE.iso
thomas@Thomas-Dell-DE051:~/Downloads/Fedora-15-i686-Live-KDE$ sudo dd if=Fedora-15-i686-Live-KDE.iso of=/dev/sdb1 bs=8M
[sudo] password for thomas: 
86+1 records in
86+1 records out
725614592 bytes (726 MB) copied, 115.253 s, 6.3 MB/s
thomas@Thomas-Dell-DE051:~/Downloads/Fedora-15-i686-Live-KDE$
```
Hoping this works...

---

### Post by doppel.ganger on 2011-09-10
BTW, what does that last part, bs=8m mean?

---

### Post by haqking on 2011-09-10
[QUOTE=doppel.ganger;11237233]BTW, what does that last part, bs=8m mean?[/QUOT

bs = bytes

see

man dd

---

### Post by doppel.ganger on 2011-09-10
Uh oh... What'd I do?

---

### Post by cpatrick08 on 2011-09-10
> **doppel.ganger said:**
> Uh oh... What'd I do?
just use unetbootin much simpler and it will fix your problem

---

### Post by doppel.ganger on 2011-09-10
Downloaded Unetbootin. Hoping this will work... Downloaded from the Pendrive Linux website through the terminal commands...

---

### Post by doppel.ganger on 2011-09-10
Aaarrrggghhh!!!

---

### Post by haqking on 2011-09-10
> **doppel.ganger said:**
> Aaarrrggghhh!!!


hate to refer to this for the third time now but are you following the instructions here:

[http://fedoraproject.org/wiki/How_to_create_and_use_Live_USB](http://fedoraproject.org/wiki/How_to_create_and_use_Live_USB)

if so where are you getting stuck ?

---

### Post by doppel.ganger on 2011-09-10
The LiveUSB creator is for Fedora only!
"Download the LiveUSB Creator program from [http://fedorahosted.org/liveusb-creator](http://fedorahosted.org/liveusb-creator) if you're on Windows, or install on your ***Linux system using PackageKit or yum***."

---

### Post by haqking on 2011-09-10
> **doppel.ganger said:**
> The LiveUSB creator is for Fedora only!
"Download the LiveUSB Creator program from [http://fedorahosted.org/liveusb-creator](http://fedorahosted.org/liveusb-creator) if you're on Windows, or install on your ***Linux system using PackageKit or yum***."


modify to suit.

[http://coffeecode.net/archives/223-Using-Fedoras-liveusb-creator-on-Ubuntu-Lucid-Lynx.html](http://coffeecode.net/archives/223-Using-Fedoras-liveusb-creator-on-Ubuntu-Lucid-Lynx.html)

same steps for install apply, it is just the USB creator

---

### Post by doppel.ganger on 2011-09-10
I am really sorry, but that stuff the link said is WAY over my head. :(

---

### Post by haqking on 2011-09-10
> **doppel.ganger said:**
> I am really sorry, but that stuff the link said is WAY over my head. :(


OK options as you are having issues.

Install virtual box and run fedora in that.

Create a fedora live CD and boot to that.

Install fedora in a Vm in vbox then use that to create the fedora live USB with links i provided earlier.

Install windows in a VM and use the live USB creator from Fedora to do it that way.

lots of options if you are having difficulties.

After all it is a fedora project.

---

### Post by doppel.ganger on 2011-09-10
Would it be easier to make a Fedora CD instead of a USB?

---

### Post by haqking on 2011-09-10
> **doppel.ganger said:**
> Would it be easier to make a Fedora CD instead of a USB?


yeah just download the .iso and burn it.

[http://fedoraproject.org/wiki/FedoraLiveCD](http://fedoraproject.org/wiki/FedoraLiveCD)

infact you already have the .iso dont you so just burn it to CD/DVD

---

### Post by wojox on 2011-09-10
> **doppel.ganger said:**
> Would it be easier to make a Fedora CD instead of a USB?

Looks like your .iso might be bad. Did you [Verify it?]("https://fedoraproject.org/en/verify")

---

### Post by Blasphemist on 2011-09-10
> **wojox said:**
> Looks like your .iso might be bad. Did you [Verify it?]("https://fedoraproject.org/en/verify")

I agree with wojox. It appears that your iso is bad. Just yesterday for a project I'm working on, I downloaded the Fedora 15 iso and used unetbootin to install it to a usb. I used it today and had no issues at all.

---

### Post by doppel.ganger on 2011-09-11
Lately, the same thing has been happening with every rpm based os that I've tried. I boot it up after a "successful" install and I just get a blank screen.

---

