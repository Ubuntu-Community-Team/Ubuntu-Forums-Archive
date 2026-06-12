---
title: "Storing Sensitive Data - How?"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-29
I noticed that Gnupg is a standard package in Dapper.

On windows I used to use PGP Desktop to secure files and folders containing sensitive data. Is Gnupg similar to PGP Desktop?

How do I do this in Dapper?

For example, if I would like to store wifi access data in a word file from OpenOffice how would I encrypt it?

Or..

How can I encrypt a folder and all of its contents?

Thank you in advance.

---

### Post by mblinux on 2006-11-29
On windows I have always used Truecrypt, I've heard that Truecrypt [http://www.truecrypt.org/](http://www.truecrypt.org/) is also a really valid solution on linux too. I intend to try it these days. So, I think that you could try truecrypt. You can create encrypted volumes on you hard disk and store there all your sensitive data.

---

### Post by PartisanEntity on 2006-11-29
Thanks for the info, for now I would like to learn and use the tools that come as standard packages in Ubuntu, then ill give other tools a go.

Again, thank you in advance.

---

### Post by scc4fun on 2006-11-29
> **PartisanEntity said:**
> I noticed that Gnupg is a standard package in Dapper.

On windows I used to use PGP Desktop to secure files and folders containing sensitive data. Is Gnupg similar to PGP Desktop?

How do I do this in Dapper?

For example, if I would like to store wifi access data in a word file from OpenOffice how would I encrypt it?

Or..

How can I encrypt a folder and all of its contents?

Thank you in advance.

I haven't used GnuPG in quite a while (and then only in Windows), but you are able to encrypt a file from the command line using

```
gpg -e filename
```

You can find more information about GnuPG (GPG) at [www.gnupg.org]("http://www.gnupg.org").

---

### Post by compmodder26 on 2006-11-29
I use encfs.  It is in the repos.

---

### Post by steve.horsley on 2006-11-29
The command man gpg will give you info about the gpg command - it's very similar to PGP I think.

It is also possible to create encrypted partitions (or files) that you can mount into the file system. All the software required is part of standard Ubuntu. See this howto
[http://encryptionhowto.sourceforge.net/Encryption-HOWTO-4.html](http://encryptionhowto.sourceforge.net/Encryption-HOWTO-4.html) - you only need from section 4.3 onwards - ignore the preamble about patching the kernel etc - that's already done in Ubuntu.

I tried it for myself, and in summary, these are the commands I used:

Make a 100M file that will be mounted as though it were a 100M disk partition. You could presumably use a partition, e.g. /dev/hda9 instead. But I used a file in my home folder - the name is .crypto so it is a hidden file:
> steve@StevesPC:~$ dd if=/dev/urandom of=/home/steve/.crypto bs=1M count=100
100+0 records in
100+0 records out
104857600 bytes (105 MB) copied, 21.7532 seconds, 4.8 MB/s

This looks odd, but it primes sudo so that it doesn't ask for your login password at the next step.
> steve@StevesPC:~$ sudo pwd
/home/steve
This connects the partition/file to a loop device and sets up the encryption. The Password prompt is not the sudo prompt for your user password (the step above got rid of that) - it's for the crypto access password:
> steve@StevesPC:~$ sudo losetup -e blowfish /dev/loop0 /home/steve/.crypto 
Password: 

Now create a file system on the device:
> steve@StevesPC:~$ sudo mkfs.ext3 /dev/loop0
mke2fs 1.39 (29-May-2006)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
25688 inodes, 102400 blocks
5120 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=67371008
13 block groups
8192 blocks per group, 8192 fragments per group
1976 inodes per group
Superblock backups stored on blocks: 
        8193, 24577, 40961, 57345, 73729

Writing inode tables: done                            
Creating journal (4096 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 25 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.

Make the directory to mount to. The name is crypto (not hidden, don't confuse with the .crypto file):
> steve@StevesPC:~$ mkdir /home/steve/crypto

Mount the crypto partition and assign ownership of the folder to the user:
> steve@StevesPC:~$ sudo mount -t ext3  /dev/loop0 /home/steve/crypto
steve@StevesPC:~$ sudo chown -R steve:steve /home/steve/crypto

Now unmount again and disconnect from the loop0 device:
> steve@StevesPC:~$ sudo umount /dev/loop0
steve@StevesPC:~$ sudo losetup -d /dev/loop0

Now edit /etc/fstab and add this line:
```
/home/steve/.crypto /home/steve/crypto ext3 noauto,loop,encryption=blowfish,user  0   0
```
Now I can mount and unmount the crypto partition as a user:
> steve@StevesPC:~$ mount ~/crypto
Password: 


I found that cipher aes-256 as suggested by the page I linked didn't work, but that blowfish did. I don't know what other ciphers are available in Ubuntu.

---

### Post by steve.horsley on 2006-11-29
encfs that compmodder26 wrote about sounds interesting, so I tried but can't make it work. Any ideas whta I'm doing wrong?

> steve@StevesPC:~$ encfs ~/.crypt ~/crypt
EncFS Password: 
fuse: failed to exec fusermount: Permission denied
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message
steve@StevesPC:~$ sudo modprobe fuse
Password:
steve@StevesPC:~$ encfs ~/.crypt ~/crypt
EncFS Password: 
fuse: failed to exec fusermount: Permission denied
fuse failed.  Common problems:
 - fuse kernel module not installed (modprobe fuse)
 - invalid options -- see usage message
steve@StevesPC:~$ 


---

### Post by PartisanEntity on 2006-11-29
is there a gui for gnupg?

---

### Post by John.Michael.Kane on 2006-11-29
Heres a list of  gui frontends [http://www.gnupg.org/(en)/related_software/frontends.html](http://www.gnupg.org/(en)/related_software/frontends.html)

---

### Post by compmodder26 on 2006-11-29
> **steve.horsley said:**
> encfs that compmodder26 wrote about sounds interesting, so I tried but can't make it work. Any ideas whta I'm doing wrong?

Been a while since I set it up so I can't remember if I had to do this or not.  But I found this thread from the archives:

[http://ubuntuforums.org/archive/index.php/t-76693.html]("http://ubuntuforums.org/archive/index.php/t-76693.html")

They talk about either changing the permission on the fusermount to o+x or adding yourself to the fuse group.

I'm not at home right now to check so I can't tell you what I did.

---

### Post by compmodder26 on 2006-11-29
Just installed and tried it on a testing server at my work and adding my user to the fuse group did the trick.

---

### Post by PartisanEntity on 2006-11-29
I have installed Seahorse from the repository, its a gui for gnupg, how do I launch it? I entered 'searhorse' into the terminal and got an error message about a daemon that supposedly wasnt running.

---

### Post by BigLebowski on 2006-11-30
Use truecrypt.


-It has many and great encryption techniques
-Developers that jump onto the forum and help answer questions
-Very in depth documentation to help you out if ever in need.
-The truecrypt Partition or file can be made on either Windows or Linux and easily accessed via both, no need to make one for W and L.
-Its open source.

---

### Post by PartisanEntity on 2006-11-30
Thanks for the tip, I will try out the suggestions made in here.

But does anyone know how to launch Seahorse?

---

### Post by John.Michael.Kane on 2006-11-30
Click on Applications--->Accessories---->Encryption keys this will bring up seahorse

Or

From the Terminal Type seahorse

---

