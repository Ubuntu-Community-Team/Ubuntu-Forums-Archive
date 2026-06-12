---
title: "update trouble"
date: 2007-07-25
forum: Absolute Beginner Talk
---

### Post by unawokendreamer on 2007-07-25
I wasn't sure what to call my prob, but i hope the subject line isn't misleading.

It says I have ten updates available. Cool. I click the icon, enter in my password, and then it tells me that there can be only one software manager running at once and to please close the other application, e.g. 'aptitude' or 'Synaptic' first.

I really would love to do this, however, I'm not finding any other program open. Is there something in the terminal I can put in to search for said running programs or what?

---

### Post by sad_iq on 2007-07-25
Try ```
sudo killall synaptic
``` or ```
sudo killall aptitude
``` See if it works!!! If not a reboot(the last resort) will clear that!!!

---

### Post by overdrank on 2007-07-25
> **unawokendreamer said:**
> I wasn't sure what to call my prob, but i hope the subject line isn't misleading.

It says I have ten updates available. Cool. I click the icon, enter in my password, and then it tells me that there can be only one software manager running at once and to please close the other application, e.g. 'aptitude' or 'Synaptic' first.

I really would love to do this, however, I'm not finding any other program open. Is there something in the terminal I can put in to search for said running programs or what?

Hi and welcome have you tried to update via the terminal? If not you can use the commands
```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

```

Enter the commands one at a time and post back if any errors are returned.

---

### Post by unawokendreamer on 2007-07-25
> **overdrank said:**
> Hi and welcome have you tried to update via the terminal? If not you can use the commands
```
sudo apt-get update

sudo apt-get upgrade

sudo apt-get dist-upgrade

```

Enter the commands one at a time and post back if any errors are returned.

tried that... got this message:

W: GPG error: [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

any ideas?

---

### Post by overdrank on 2007-07-25
> **unawokendreamer said:**
> tried that... got this message:

W: GPG error: [http://mirror3.ubuntulinux.nl](http://mirror3.ubuntulinux.nl) dapper-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

any ideas?

Hi yea it appears there is a bad source in your repos and you can use the command 
```
sudo dpkg --configure -a
```
And then followed with the update commands again. If the same error appears we will edit your source list.

---

### Post by sad_iq on 2007-07-25
> **unawokendreamer said:**
> tried that... got this message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
any ideas?
 Type ```
sudo dpkg --configure -a
```
I'll look for the signature thing and edit this if no one responds!!!

---

### Post by Seisen on 2007-07-25
Here 

```
wget http://mirror.ubuntulinux.nl/dists/dapper-seveas/1135D466.gpg -O- | sudo apt-key add -
```

---

### Post by unawokendreamer on 2007-07-25
Wow thanks for that... Honestly not sure if there's forum rules here regarding swearing, but **** those Windows kids that were tell me how mean the ubuntu forum was!

You guys were generally nice and helped out a lot. Thanks so much. I wasn't really sure what to do, and it had been a while since I had worked in the terminal and stuff. Thanks again. You guys were great.

---

### Post by overdrank on 2007-07-25
> **unawokendreamer said:**
> Wow thanks for that... Honestly not sure if there's forum rules here regarding swearing, but **** those Windows kids that were tell me how mean the ubuntu forum was!

You guys were generally nice and helped out a lot. Thanks so much. I wasn't really sure what to do, and it had been a while since I had worked in the terminal and stuff. Thanks again. You guys were great.

Good luck and all of us aren't mean :-x

---

