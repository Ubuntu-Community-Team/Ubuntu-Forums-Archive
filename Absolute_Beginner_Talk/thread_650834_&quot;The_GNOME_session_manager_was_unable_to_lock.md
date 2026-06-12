---
title: "&quot;The GNOME session manager was unable to lock the file&quot;... error message"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by Watchtow3r on 2007-12-26
I've been trying to get the sound working in my HP dv2000 laptop. Supposedly this is a common problem with HP's, and so I was following [this]("http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/") guide. Everything seemed to work fine, but when I restarted Ubuntu, it loaded fine, but then it wouldn't log in and I got this error message: 

The GNOME session manager was unable to lock the file 'home/ubuntu/.ICEauthority'. Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwritable, you could try logging in via the failsafe session and ensuring that it is.

What can I do here? Thank you.

---

### Post by jas0 on 2007-12-26
I assume that somewhere along the way you have in some way modified a permission or ownership of something somewhere in your home folder. I am by no means an expert, but here is what I would do:

Boot into the Ubuntu recovery console (press escape repeatedly at boot time and select the kernel with recovery in the name) and type the following:

```
sudo chmod 755 /home
sudo chown your_username /home/your_users_home_folder/.dmrc
sudo chmod 644 /home/your_users_home_folder/.dmrc
sudo chown your_username /home/your_users_home_folder
sudo chmod 755 /home/your_users_home_folder
```

*Note: replace your_usename with your username on the system (I assume it's ubuntu) and your_users_home_folder with the home folder name (usually the same as the former)

**_Before you do any of this, wait for a few other replies to this thread. I may be misunderstanding the situation._**

Good luck!

---

### Post by Watchtow3r on 2007-12-26
thanks. I'm going to wait and see what some other people say before trying this.

---

### Post by Watchtow3r on 2007-12-27
On my computer, pressing escape at boot time loads the change boot order menu. I tried doing it in Safe Graphics Mode, but nothing happened. How can I load that recovery console?

Edit: also please note that I am running Ubuntu from a USB drive, so when I start my computer a menu pops up that says:

Start Ubuntu in USB persistent Mode(saves changes)   <<<(usually the one I select)
Start Ubuntu in Live Mode
Start Ubuntu in Safe Graphics Mode
Install with Driver Update CD
...and other options (it looks a lot like the menu when I use the Live CD.

I am not sure how to access the recovery console from my computer. Can somebody help me out?

---

### Post by Watchtow3r on 2007-12-27
can someone help me please?

---

### Post by Watchtow3r on 2007-12-27
bump

---

### Post by jas0 on 2007-12-27
What file system are you running on your USB drive? You may want to fsck the filesystem first if it's ext2. This all could in theory be sector corruption.

---

### Post by Watchtow3r on 2007-12-27
I think FAT 6. I used the standard installation from pendrivelinux listed [here]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/").

---

### Post by jacob21 on 2007-12-27
I did changed my permission somewhere in my home folder.  Anyway the code you supplied worked, thanks.  But when I logged in I couldn't access the folders on my desktop, I can't delete them or move them.

---

### Post by Watchtow3r on 2007-12-27
> **jas0 said:**
> What file system are you running on your USB drive? You may want to fsck the filesystem first if it's ext2. This all could in theory be sector corruption.

i don't think I have any corruption. I just need help accessing the recovery console.

---

### Post by silentsniper on 2008-01-24
well. i have the same problem... on my secondary acc. i cant get in either so i logged in and verified myself as root on the main account and chmod -ed the permissions to rw-r-r
and then that didnt work so i tried other permissions leaving out execute because it says "cannot execute the binary file" so..... i chmod-ed the file /home/robert/.ICEauthority and then i used "ls -l /home/robert/.ICEauthority" without the "" and it showed exactly the right permissions that i applied so i logged out and still couldnt log in as "robert" so.... i went into failsafe and looked at my permissions for the account that has the error and they didnt save!! and i was verified as root. well..... i cant figure out why the permissions changes to the .ICEauthority dont save when i am verified as root.... help please!!

---

### Post by rggavubt on 2008-03-01
I just installed Ubuntu on my 4GB USB dongle and I'm getting the same exact error message.  I have a Lenovo R61i laptop.  I booted up the first time after I installed Ubuntu using the PendriveLinux.com instructions using the persistent mode so I could save the changes I made??     I had no problems on the first boot.  The second boot I got the error message.  I would also like to set a user name and password on the USB dongle?? Any help appreciated.

---

### Post by phil13 on 2008-03-12
I also have this problem, I seem to be unable to login in failsafe mode-same error occurs. I installed this to my 4GB usb drive yesterday and it's booted several times succesfully. I followed the instructions at pendrivelinux to install.

Thanks

---

### Post by Hockey_Man on 2008-04-01
I am having the same issue is there a valid fix for this problem? I have tried a few things and this error keeps pooping up.
Thanks

---

### Post by bobsp on 2008-04-08
I was having the same problem with .ICEauthority not being able to be locked when starting ubuntu in persistent mode, having followed the instructions on [www.pendrivelinux.com](www.pendrivelinux.com).  I tried several things, including trying to change the ownership of the file, its read/write permissions - even tried deleting the file to see if a new one would be created at login.  None of this worked.

I finally had success by re-formatting the USB stick (I'm using a 4 GB one), and repeating the pendrivelinux instructions, but instead of using the "sudo su" command at the start, I prefixed each subsequent command with "sudo".

Someone correct me if I'm wrong, but I think this does the installation with "ubuntu" as the owner of the files, with root permissions, whereas the "sudo su" command will install with root as the owner, which causes the .ICEauthority ownership issues.

---

