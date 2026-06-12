---
title: "Locked out of Root"
date: 2014-05-27
forum: Any Other OS
---

### Post by codingman on 2014-05-27
I just can't get root access! I have dumbly placed a password within the confines of root during graphical network installation of Debian.

Yes, I've tried opening a terminal and using sudo -i and su - . su doesn't work at all, and sudo -i tells me that codingman is not in the sudoers file, oh, and that this will be reported.

So the next thing anyone should know is that I tried visudo, as ritual after nearly any distributions installation. However, I could obviously not access the command because I wasn't root.

So, all I can say is: HELP!

---

### Post by codingman on 2014-05-27
All attempts to become root have failed one by one, and I really need help getting this fixed.

---

### Post by steeldriver on 2014-05-27
What exactly do you mean by "placed a password within the confines of root" - are you saying you've set a root password and forgotten it? Can you boot to single-user mode at all?

What attempts have you tried and how have they failed exactly?

---

### Post by codingman on 2014-05-27
No, I remember the password fully, however, when I attempt to use it while trying:
```
su -
```
or
```
sudo -i
```
it gives me errors.

For su , it gives me an authentication error.
And with sudo, it tells me that my username is not in the sudoers file, meaning that I have to use visudo to change that, and I cannot access visudo because I have no methods of becoming root, even temporarily by running:
```
sudo visudo
```
When I boot into recovery mode, it just brings me to my normal desktop, and I don't have any recovery tools as I normally would with Ubuntu or other distributions. I'm quite sure that this can be fixed, however. 

Yes, I can boot to single-user mode, if by that you mean to the Gnome 3 desktop through GDM. I have also tried going to System Settings within the desktop and attempted to unlock the user settings area in order to set my normal user to Administrator instead of a Standard user. This also tells me that there was an authentication error.

Funnily enough, when I go to a TTY, (hence, Ctrl-Alt-F1 or similar), it tells me that I have mail when I log in as a normal user, as though I was an administrator or was in an account with root privilidges.

I will gladly give more information if necessary.

---

### Post by steeldriver on 2014-05-27
No, by single-user mode I mean a root CLI (like Ubuntu's recovery mode). No GUI.

What authentication error exactly? if it's a 'authentication **token manipulation** error' that usually means the filesystem is read-only

Can you log in as root (using the root password that you set) in the Ctrl-Alt-F1 virtual terminal?

---

### Post by codingman on 2014-05-27
How can I get something like the Ubuntu recovery mode?

Do you mean like in su -? It only says, su: Authentication error. Which I have experienced whenever using su in a Debian-based distribution.

And no, I cannot log in as root in the virtual terminal.

---

### Post by deadflowr on 2014-05-27
Do you have a livecd around?
If so, then try this
[https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery)
but instead of changing the password, add your user to the sudoers group.
In Ubuntu it would simply be 
```
adduser you sudo
```
but in debian it's probably
```
adduser you admin
```
run sudo visudo, first, and look at which groups are listed in the sudoers file.
After you add the user, run a qick id to confirm they were added.
```
id you
```
which will list all the groups your user is in.
If all is well exit the chroot exit the live session and reboot.
See if that helps.

For the record, debian should have a recovery mode. Just like Ubuntu.
But I don't know what's wrong on that front.

---

### Post by codingman on 2014-05-27
As for the live CD, I doubt it, but I will go check.

I know on other Debian derivatives the recovery mode works perfectly fine, like in LinuxBBQ, CrunchBang, etc. But I am unsure as to why I am unable to get a useful recovery session by choosing the recovery mode when turning on the machine in GRUB. Hopefully this is only a minor bug and will soon be fixed.

---

### Post by deadflowr on 2014-05-27
Is it a single boot system?
(Meaning are there other linux systems on the machine)
If you dual-boot, you can chroot from another system.

---

### Post by codingman on 2014-05-27
No, it is single boot.

---

### Post by codingman on 2014-05-27
This is quite ridiculous. How is one supposed to install Debian without a high level of hassle when attempting to use the root account?

No, I appear not to have any Ubuntu disks on hand, but if I simply want to have a recovery tool, what should I burn?

---

### Post by deadflowr on 2014-05-27
> **codingman said:**
> This is quite ridiculous. How is one supposed to install Debian without a high level of hassle when attempting to use the root account?

No, I appear not to have any Ubuntu disks on hand, but if I simply want to have a recovery tool, what should I burn?

Puppy is simple enough and small enough to do a quick burn.
Boot repair has a live cd version
[http://sourceforge.net/p/boot-repair-cd/home/Home/](http://sourceforge.net/p/boot-repair-cd/home/Home/)
though i doubt it'll fix the actual problem with the the recovery mode though.

---

### Post by codingman on 2014-05-27
So, basically, what this incident is telling me, is that I need to have a  live CD in order to properly use the root account, very nice....

So should I burn Puppy and boot into it as a live CD? Then what?

---

### Post by deadflowr on 2014-05-27
I don't know if a liveCD is the only way, but since the recovery mode seems to be busted, it's a viable alternative.

simply put, puppy boots into a live session.
It runs as root so no need to worry about that.
You'll need to know your partition of the debian install
I think puppy has fdisk, or maybe parted, which will list the partitioning scheme.
But typically, when all it right
you would run
```
mount /dev/sda1 /mnt
```
this will mount the debian partition on the /mnt directory.
then
```
chroot /mnt
```
this will give you the ability to manipulate the passwords on the debian system.
then when done simply type
```
exit
```
then 
```
umount /mnt
```
You shouldn't need to do more than that.
(other the making the changes)

If all you want to do is change the root password then run
```
passwd root
```
Which should let you change the existing password to something new.
Without questions, or a need to input the old password.
I hope this helps.

---

### Post by steeldriver on 2014-05-27
Can you give a bit more background to how you got in this situation? The only Debian-ish system I'm currently running is LMDE (Linux Mint Debian Edition) but iirc I was prompted to set a root password at install time and did so. I can use 'su' on this box. If I enter the *wrong* password I get

```

$ su -
Password: 
su: Authentication failure

```

If you set a root password but can't remember it (or keyboard / language settings prevent you from entering it) AND you don't have any valid sudoers then yes I think the only remedy is what deadflowr suggests (or if you absolutely can't chroot, I guess the fallback position would be to add a sudo from the liveCD user using something like visudo -f /mnt/etc/sudoers)

---

### Post by codingman on 2014-05-27
I will try what you said deadflowr, thanks for the help!

As for su, it gives me the exact same error when using the password that I entered during installation.

---

### Post by codingman on 2014-05-27
Thank you all for your help today, I was successfully able to use a Live CD to recover my system!

---

### Post by CharlesA on 2014-05-28
FWIW, I've got Debian running on 6 or 7 different systems and I've had run into the problem you describe. I use su root instead of sudo though.

---

