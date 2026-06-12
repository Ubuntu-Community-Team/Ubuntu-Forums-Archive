---
title: "How to log in Ubuntu!"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by beni on 2006-07-07
I've just installed Ubuntu. I got through installation without any difficulty. However, I noticed that the installation did not give me any choice to set my username but password only. As a result, I then was sitting in front of the log in screen with no clue what I should type for user name because I only have the password. I tried all "root", "ubuntu", "user", "guest" but they all were in vain.
Please help me. I'm really eager to try out Ubuntu for the first time of my life.

---

### Post by T700 on 2006-07-07
All the times I've installed it, it has asked me for a user name.  Try your first name (lower case letters).  This isn't the Live CD, is it?

Paul

---

### Post by tseliot on 2006-07-07
Boot in Recovery mode (select it from the GRUB menu almost as soon as you turn on your computer)

you will boot to the command line.


try this:
```
cd /home
```
```
ls
```

the ls command will show you a list of folders one of which has the same name as your username.

Please post the output of "ls" here and we'll help you.

---

### Post by beni on 2006-07-07
Thanks guys. I ran the recovery mode and found out that the user name is OEM. I logged in by that and I got through! But is there any way I can find the password for "root" mode?
Those troubles are probably because I just downloaded the CD. Maybe I should try the DVD version.

---

### Post by Katryx on 2006-07-07
> **beni said:**
> But is there any way I can find the password for "root" mode?
Ubuntu doesn't have a root user.

---

### Post by tseliot on 2006-07-07
> **beni said:**
> Thanks guys. I ran the recovery mode and found out that the user name is OEM. I logged in by that and I got through! But is there any way I can find the password for "root" mode?
Those troubles are probably because I just downloaded the CD. Maybe I should try the DVD version.
There's no need to download the DVD version.

You might have found a BUG. It never happened to me.

The root account is not set up in Ubuntu by default.

If you need (temporarily) root priviledges you have to use "sudo".

For example if you want to use "apt-get" you can do:
**sudo** apt-get (etc.)

---

### Post by Albi on 2006-07-07
Hi, is this ubuntu or xubuntu?
If it's xubuntu, you have to follow this instead of the alternate cd, as it is bugged:
[http://psychocats.net/ubuntu/xubuntu.php](http://psychocats.net/ubuntu/xubuntu.php)

Or even if it isn't, you could just replace xubuntu-desktop with ubuntu-desktop.  AFAIK, there's no way to fix this, so you have to reinstall.

Edit: Don't do step 8, and you need the server CD

---

### Post by PriceChild on 2006-07-07
You may have acciadently done an "oem" install.

Try using the username "oem" together with your password and see if that works.

---

### Post by beni on 2006-07-09
Thank you all for replying.
When I installed Ubuntu, there were two choices: Install in text mode and in OEM mode. I thought OEM mode should look better then the "text" mode so I chose it (so can somebody please explain to me what's OEM any way?, sth like original equipment manufacturer?). Anyway, I got the DVD now and already installed it.
But my current issue now is that it takes too much time to start Ubuntu. As I saw, while loading, it got stuck for awhile at the step "check all files system...". It then showed the black and white screen saying:
check all files system...
dosfsck 2.11, 12 Mar 2006 FAT32, LF2
/dev/sda/: 1821 files, 8679301/1020127 clusters
dosfsck 2.11, 12 Mar 2006 FAT32, LF2

and I have to wait for very long until the log in screen showed up.
So is there any way to improve this? You may want to know that my hard drive's capacity is 120 GB. I have several patitions:
4GB -> backup, driver
46GB -> NTFS, windows
9GB -> linux
59GB -> NTFS

---

### Post by Apple 101 on 2006-07-09
Do you have a swap partition at all?  What is your computer's RAM size?

---

### Post by beni on 2006-07-09
9GB is the extended patition, containing 1GB for swap and 8GB ext3. I have 2GB RAM.

---

### Post by SkyNet2029 on 2006-07-09
Having a photographic memory, and needing to umm, exercise it as much as possible, whenever I install an OS that doesn't automatically prompt for a <root> password, I take the first opportunity to enable one. In Kubuntu (Ubuntu also, AFAIK) you can do so like this:

```
$ sudo passwd root 
``` 

the result should be like this:

```
machine@NTAuth:~$ sudo passwd root
Password:
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
```

that way you will have an <root> password.
I am not entirely sure that the security model of K/U/Xubuntu is affected by this, but it does allow for one more password (and also one more obstacle) on your system's front door.

---

### Post by Crosbie on 2006-07-09
> **beni said:**
> Thank you all for replying.
But my current issue now is that it takes too much time to start Ubuntu. As I saw, while loading, it got stuck for awhile at the step "check all files system...". It then showed the black and white screen saying:
check all files system...
dosfsck 2.11, 12 Mar 2006 FAT32, LF2
/dev/sda/: 1821 files, 8679301/1020127 clusters
dosfsck 2.11, 12 Mar 2006 FAT32, LF2

and I have to wait for very long until the log in screen showed up.
So is there any way to improve this? You may want to know that my hard drive's capacity is 120 GB. I have several patitions:
4GB -> backup, driver
46GB -> NTFS, windows
9GB -> linux
59GB -> NTFS

I had this issue.  I decided I didn't want Ubuntu checking my Windows filesystems with 'dosfsck' (since it was always finding the same errors and not choosing to fix them, causing similar ugly screens/wasted time as in your case), so I disabled this.  If I remember correctly I used the wonderfully-named 'bum' (=BootUp Manager).  For me it's in System/Administration from the top menu bar.  You may have to install it via Synaptic first.

Alternatively, try Googling or searching the forums for ('disable') 'dosfsck' or something, and you might find clearer directions - that's what I did. :)

---

### Post by beni on 2006-07-09
Thank SkyNet2029 and Crosbie, your answers are really helpful.
@Crosbie: I installed the "bum". When I ran it, it just asked for root password, "Starting..." for awhile but never show up. Fortunately, I searched and found a way to change the dosfsck by editing a file in the /etc. Thanks a lot though.
I have another question (I'm a real newbie :() Is there anyway to try Kubuntu without downloading the CD/DVD and installing again? I installed lots of packages through the Synpatic Package Manager including all KDE packages. However, after I rebooted, I got the Edubuntu and I didn't know how to switch to Kubuntu.

---

### Post by cyberlite on 2006-07-09
Hey the anwser is simple install the [COLOR="Red"][SIZE="2"]text[/SIZE][/SIZE][/COLOR] version. Then it will ask you for user name and the the password. I also had the problem.

---

### Post by beni on 2006-07-09
@cyberlite: is that the way to set up Kubuntu? Can you please tell me more about "install the text[/size] version". Sorry for asking too much, I still have to learn a lot about Ubuntu.

---

### Post by cyberlite on 2006-07-09
Beni 

I'm talking about ubunto.:)  Here is how to do it step by step.

Download & Burn a cd with ubuntu 6.06 iso, then when you put it in the cd, the system should boot from cd.
In the menu it will give you options like install as test or oem etc.
those test, the os will ask you for a user name and computer name, password etc. thats all. and ofcourse to format.

---

