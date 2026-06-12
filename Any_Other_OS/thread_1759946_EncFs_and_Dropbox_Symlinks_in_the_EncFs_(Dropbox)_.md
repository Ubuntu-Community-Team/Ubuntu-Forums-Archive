---
title: "EncFs and Dropbox: Symlinks in the EncFs (Dropbox) folder"
date: 2011-05-16
forum: Any Other OS
---

### Post by Herbivore on 2011-05-16
It is recommended that to be able to continue to use Dropbox for sensitive files, it is better to encrypt them before they get sent to the Dropbox server. There are tuts on using encfs to make this automatic. (see [https://pragmattica.wordpress.com/2009/05/10/encrypting-your-dropbox-seamlessly-and-automatically/](https://pragmattica.wordpress.com/2009/05/10/encrypting-your-dropbox-seamlessly-and-automatically/))

I rather not put my files and folders in the Dropbox folder so I have been putting symlinks instead. Will putting symlinks in the encrypted Dropbox folder work if the Dropbox folder is encrypted as per the link above? (I could just try it, but with my slow connection, deleting everything in Dropbox just to try this would take days.)

Sysinfo: Kernel 2.6.35-22-generic i686 (32 bit), Linux Mint 10 Julia (Ubuntu 10.10 Maverick Meerkat) on dual core Intel Core2 Duo E7400 desktop.

---

### Post by Triggonaut on 2012-12-09
Hello Herbivore, this answer comes over a year too late and despite your slow connection, I assume you have already tested it. ;-)

I'm currently trying this thing out. EncFS-Folder in my Dropbox, and I have just moved some Symlinks from another Dropbox folder into the EncFS-Folder.

Unfortunately this does not work: Right in the moment you move the symlinks, Dropbox thinks you have deleted the files/folders and wipes the content out of the cloud. Sure in the meanwhile, the new EncFS-symlinks will be written into the Dropbox, but the Dropbox is unable to follow the links sind they're encrypted. Everything you have now in your Dropbox is the symlink itself; unable to do a file synch between two devices that share a EncFS-folder in the dropbox.

I'll do some meditation and hopefully will find another way for symlinks in an encrypted Dropbox... :-)

---

