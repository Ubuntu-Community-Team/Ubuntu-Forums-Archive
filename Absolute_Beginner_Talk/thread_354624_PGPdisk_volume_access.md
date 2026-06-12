---
title: "PGPdisk volume access"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by Fenryr on 2007-02-06
G'day, folks...
I have several GB of encrypted files which were created using PGPdisk under WinXP. I would like to save when I make my final migration to Linux. Does anyone know if there is a way to access these files from inside Ubuntu? I'd like to continue using the same encryption, if at all possible. My only other option is to decrypt ALL of them, save them offline as cleartext/image files, and then find a file/disk volume encryption program of comparable strength that will work under Linux.
Any help or advice would be greatly appreciated...

I realize this may not be a strictly 'newbie' sort of question, but I would really like to eliminate MS products from my system, and this is the only remaining roadblock...

---

### Post by Fenryr on 2007-02-07
Hello?? Is there anybody there?
I'd at LEAST have expected to be FLAMED by now, if nothin' else...*LOL*

C'mon, folks, I really need an answer on this soon, I've now got 3 machines here waitin' on a brand new OS...*g*

---

### Post by ludovicc on 2007-02-11
Fenryr, 

I want to do exactly the same stuff as you. So right now i'm trying to prepare an encrypted partition on my Ubuntu box, hopefully this guide ([https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)) should help.

Then I will use Unison to transfer files securely between my Windows box with the PGP disk mounted, to the Ubuntu box.

Good luck, this encryption thing is still very confusing, and I hopet that the next release (Feisty) will make things easier.

Ludovic

---

### Post by ludovicc on 2007-02-11
The following seems to work, but the encryption key is only 128 bits and I don't have a nice graphical way of mounting/unmounting the encrypted disk as I did with PGPDisk.

sudo bash
apt-get install cryptsetup
luksformat -t reiserfs /dev/hda2
mkdir /crypt
chown -R $USER:users /crypt
echo "crypt /dev/hda2	none		luks" >> /etc/crypttab
echo "/dev/mapper/crypt /crypt reiserfs noauto,user 0 0" >> /etc/fstab
exit

To mount:
sudo cryptsetup luksOpen /dev/hda2 crypt
sudo mount /dev/mapper/crypt /crypt
sudo chown -R $USER:users /crypt

To unmount:
sudo umount /crypt
sudo cryptsetup luksClose crypt

---

