---
title: "Locked out of Dapper"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by capasio on 2008-01-09
I am having trouble booting Dapper. There is a corrupt file on dev/hda6  and file check is forced. I finally get a login screen and when I login I get this message. 

"could not set mode 0700 on private per-user gnome configuration directory  '/home/paco/.gnome2-private/': Read-only file system."

Not much experience with this os. I'd appreciate any help I can get.

Thanks Capasio

---

### Post by taurus on 2008-01-09
Boot into recovery mode from GRUB menu and run

```
chmod -R 755 /home/paco/.gnome2-private
shutdown -r now
```
Now, see if you can log in to your account, paco, again.

---

### Post by capasio on 2008-01-09
Taurus, thanks for your reply.  Sorry, but I don't know how to "Boot into recovery mode from GRUB menu and run:"

I can get to a screen (forgive me but truly a beginner) that  has my computer name login and the password which I do and then get 
paco@Bellevue:~$     I loaded your suggested command and receive

chmod: cannot access "755"   etc. no such file or directory.

Where am I? :)

capasio

---

### Post by taurus on 2008-01-09
So you can log into your account.  Then, try something like

```
sudo chown -R paco:paco /home/paco/.gnome2-private
sudo chmod -R 700 /home/paco/.gnome2-private
```

---

### Post by lgambett on 2008-01-09
Sorry to contradict you, friends, but this guy is trapped into a login console launched by fsck. The entire file system is mounted read only, thus is useless to try to chmod the files. 
I suggest our friend to google for "fsck linux recovery", or something similar, and follow the instructions With a little bit of luck the entire file system will be recovered.

---

### Post by capasio on 2008-01-09
Thanks again.  Wherever I am logging in from it's the same.  Both commands return "cannot access - No such file or directory."   Can't fathom what is happening.

capasio

---

### Post by lgambett on 2008-01-09
Give a look there..
[http://forums.contribs.org/index.php?topic=34493](http://forums.contribs.org/index.php?topic=34493)
Is a case similar to yours, IMHO.
Your filesystem is corrupted, linux started  an automatic fsck, that cannot solve the problem. You should run from the command prompt
fsck -y /dev/hdx (change hdx with e.g. hda, hdb). 
Usually Linux systems can recover with little or no damage.

---

### Post by capasio on 2008-01-09
So I ran from the command line  fsck -y /dev/hda  and received this:" permission denied, you must have r/w access to the file system or be root"  

So it looks like Igambett has something. 
Trapped in a login console! I googled  as you suggested, but this is getting highly technical. Is there another way out of this mess?

---

### Post by lgambett on 2008-01-12
sorry for the delay capasio, I hope you solved it by now. If not... try to umount the partition before running fsck, eg
umount /dev/sd*x*
then
fsck -y /dev/sd*x*

---

### Post by lswest on 2008-01-12
also, you'd need to run those commands with sudo, or in the root account.

---

### Post by LinuxGuy1234 on 2008-01-12
Hmm... go root and check the FS by:
1. su - root
2. reboot
3. Press ESC
4. Choose "Ubuntu, kernel 2.6.15-16-386 (recovery mode)" (or something like that)
5. Wait
6. fsck /dev/sda2 (replace sda2 with the correct partition)
7. Press y
8. Wait again
9. When done, use reboot
10. Wait as Ubuntu loads
11. Log in again

---

