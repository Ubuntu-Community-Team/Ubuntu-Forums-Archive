---
title: "[SOLVED] Change password on encrypted volume"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by PetePete on 2008-01-15
When using the disk encryption from ubuntu alt install CD, is it possible to change the password for the encrypted partition in the future (.... good security practise would assume it gets changed every 90 days)

90 days is a bit much, (well for me, theres a 2:1 chance i'd forget the password after 3 rotations! then loose all my data :S ) but I wouldn't want the same password for 2 years or if it somehow got compromised id need to change it..

is this possible, or is it by the very nature of the encryption insecure to be able to change the password?! :confused:

---

### Post by bodhi.zazen on 2008-01-15
Changing the password is not so easy,

see this link :

[http://encryptionhowto.sourceforge.net/Encryption-HOWTO-6.html](http://encryptionhowto.sourceforge.net/Encryption-HOWTO-6.html)

See Question #4

---

### Post by PetePete on 2008-01-15
cheers, but now the OS wont boot, I assume its because the UUID has changed of the disk, but I dont know how I would update the /boot partition part to know the new one.. (or for that matter find the disks uuid

err0r: cryptsetup: source device /dev/disk/by-uuid/c9292(some numbers) ... not found
begin: waiting for root file system.... ...


(ps all done in virtualbox test enviroment so no harm done :) )

---

### Post by bodhi.zazen on 2008-01-15
>_<

---

### Post by PetePete on 2008-01-15
well i'll safely assume that install's well and truly f*****! 

found this link
[http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html](http://users.piuha.net/martti/comp/ubuntu/en/cryptolvm.html)

says how to change password but page preceeding it stated that it wont work if using LUKS , does the standard ubuntu disk encryption use LUKS?

---

### Post by bodhi.zazen on 2008-01-15
I believe it does :(

> Technology

The Linux kernel offers dm-crypt for handling encrypted block devices. However, this does not provide any metadata about the underlying partition, such as a UUID, a magic that this is an encrypted partition in the first place, the encryption algorithm used, or a keyring. This kind of metadata is provided by the [WWW] LUKS headers, implemented in our cryptsetup. With this format, we retain the correct handling of such partitions with udev, hal, gnome-mount, etc. 

[https://wiki.ubuntu.com/EncryptedFilesystemsInstaller](https://wiki.ubuntu.com/EncryptedFilesystemsInstaller)

---

### Post by PetePete on 2008-01-18
finally managed to solve this one, (posted a howto on the tutorial board but its still not there though?)

here's what I did...
booted a ubuntu live cd
and ran following code


you will need to change /dev/sda5 to what ever your partition with the encrypted volume is on, a guided encryption setup from the installation cd puts it on sda5 (or hda5 hardware depending). You can always run gparted from the livecd to helo find the correct partition.



```

 sudo aptitude install cryptsetup
sudo modprobe dm_crypt
sudo modprobe sha256
sudo modprobe aes_i586

cryptsetup -y luksAddKey /dev/sda5
--> enter your orig password here..
key slot 0 unlocked
--> enter new password
--> reenter new password
command successful

cryptsetup luksDelKey /dev/sda5 0
-->enter new password
key slot 1 unlocked
Command successful

```

restart computer and it should have changed the password.

Please note, the above worked for me, but obviously take backup precautions before doing anything. last thing you want is to be locked out of all your data for ever!

---

### Post by bddrey on 2008-02-26
Actually you can do the commands in your current running Linux. No need for a live CD boot, or modules loading. Simply do the following.

To create a new password:
cryptsetup -y luksAddKey /dev/sda5

This command will print what key is now 'open' this is to be used in the delete command seen below. Will replace the NUMBER with the printed open key. On your computer the /dev/sda5 may not be the correct device. You might have to change this device to the required one you want to change passwords on.

Reboot the machine.

Then to delete the old one:
cryptsetup luksDelKey /dev/sda5 NUMBER
ie. 'cryptsetup luksDelKey /dev/sda5 0'

&#1042;&#1089;&#1077;&#1075;&#1086; &#1093;&#1086;&#1088;&#1086;&#1096;&#1077;&#1075;&#1086;.

---

