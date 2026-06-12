---
title: "Just a few qustions before attempt #2"
date: 2009-01-24
forum: Arch and derivatives
---

### Post by COLiNx86 on 2009-01-24
So I'm excited to say that I *Almost* got arch fully installed, with only minimal help from the beginners guide  :). 

After I got gnome installed and added everything I needed to rc.conf (hal fam gdm) and rebooted, it wouldn't work, it would *freeze* when ever it said initializing hal. Any idea what I did wrong?

Also when ever i'm installing it and I'm supposed to put my ip address into it, what should I put? leave it default like I did? or change it to something else?

Is there anyway I can install/use ext4 and grub2 (or whatever I need to boot from ext4 or can I even do that?)  during installation?

Thanks.

---

### Post by crimesaucer on 2009-01-24
> **COLiNx86 said:**
> So I'm excited to say that I *Almost* got arch fully installed, with only minimal help from the beginners guide  :). 

After I got gnome installed and added everything I needed to rc.conf (hal fam gdm) and rebooted it wouldn't work, it would *freeze* when ever it said initializing hal or whatever.  Any idea what I did wrong?

Also when ever i'm installing it and I'm supposed to put my ip address into it, what should I put? leave it default like I did? or change it to something else?

Is there anyway I can install/use ext4 and grub2 (or whatever I need to boot from ext4 or can I even do that?)  during installation?

Thanks.

Use DHCP to automatically configure your address.

I'm not sure about your other thing.

---

### Post by COLiNx86 on 2009-01-24
> **crimesaucer said:**
> Use DHCP to automatically configure your address.

I'm not sure about your other thing.

Ok thanks.

---

### Post by crimesaucer on 2009-01-24
> **COLiNx86 said:**
> Ok thanks.

The FTP install method will automatically configure everything if it recognizes your eth0 connection.

---

### Post by COLiNx86 on 2009-01-25
> **crimesaucer said:**
> The FTP install method will automatically configure everything if it recognizes your eth0 connection.

Ok cool that's what I'm using

---

### Post by OutOfReach on 2009-01-25
> **COLiNx86 said:**
> So I'm excited to say that I *Almost* got arch fully installed, with only minimal help from the beginners guide  :). 

After I got gnome installed and added everything I needed to rc.conf (hal fam gdm) and rebooted, it wouldn't work, it would *freeze* when ever it said initializing hal. Any idea what I did wrong?

Also when ever i'm installing it and I'm supposed to put my ip address into it, what should I put? leave it default like I did? or change it to something else?

Is there anyway I can install/use ext4 and grub2 (or whatever I need to boot from ext4 or can I even do that?)  during installation?

Thanks.

Can you show us your MODULES line in your rc.conf?
Remember that the order does matter if one of the daemons depends on other daemons.

Are you using wireless or wired? If wired use dhcpcd, if using wireless try [this]("http://wiki.archlinux.org/index.php/Wireless#Wireless_Quickstart").

EXT4 should be in the next Arch CD (which I think is 2008.12) since it will have the 2.6.28 kernel, which has EXT4 support. I am not sure about Grub2.

Hope that helps.

---

### Post by COLiNx86 on 2009-01-25
> **OutOfReach said:**
> Can you show us your MODULES line in your rc.conf?
Remember that the order does matter if one of the daemons depends on other daemons.

Are you using wireless or wired? If wired use dhcpcd, if using wireless try [this]("http://wiki.archlinux.org/index.php/Wireless#Wireless_Quickstart").

EXT4 should be in the next Arch CD (which I think is 2008.12) since it will have the 2.6.28 kernel, which has EXT4 support. I am not sure about Grub2.

Hope that helps.

I don't have arch installed right now( reinstalled debian so I could get other stuff done) but I know that I put them at the end of the file and I put them hal fam gdm 

Thanks

---

### Post by SnakeHips on 2009-01-25
Hi ,it's nigh-impossible to diagnose fully without more info though I read you now have a working Debian install. 
If you are comfortable with setting-up partitions / Grub  i'd put aside say 10gig for an Arch 'sandbox' ,install there and make it or break it as many times as you like - I didn't arf learn a lot of stuff this way! All with the knowledge you've a working OS to fall back on.

Once you get Arch going as i'm sure you will ,there will be plenty of help available...

Hope it helps.

p.s. it's awesome!
[http://www.archlinux.org/download/](http://www.archlinux.org/download/)
FTP iso
Dhcp
eth0

---

### Post by gjoellee on 2009-01-25
> **COLiNx86 said:**
> 
Is there anyway I can install/use ext4 and grub2 (or whatever I need to boot from ext4 or can I even do that?)  during installation?


you  can convert an existing Ext 3 installation, see this thread: [http://ubuntuforums.org/showthread.php?t=1045349](http://ubuntuforums.org/showthread.php?t=1045349) GRUB2 is not needed because GRUB is patched for Ext4 support.

> **OutOfReach said:**
> 

EXT4 should be in the next Arch CD (which I think is 2008.12) 


I think it would rather be 2009.1

---

