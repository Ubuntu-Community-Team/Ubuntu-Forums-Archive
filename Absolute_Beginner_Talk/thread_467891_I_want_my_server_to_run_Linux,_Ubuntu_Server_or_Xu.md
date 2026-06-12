---
title: "I want my server to run Linux, Ubuntu Server or Xubuntu?"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by hobs0n on 2007-06-08
Hey friendly forum! =)

Im gonna try to use Linux for my server instead of Windows 2003 and Longhorn. Im mainly gonna use it as a FTP server, Share internet over the network, DC+ clients, Torrents and as a MediaCenter to watch movies and Tv shows on my TV. I wonder if its best to use the Ubuntu server edition or use Xubuntu? I also wonder if there are GUI versions oft he FTP server, DC+ and Torrent clients? Im not very keen on start to learn to type all ;)

---

### Post by HereInOz on 2007-06-08
You may find this useful:

[http://howtoforge.com/perfect_setup_ubuntu_6.10](http://howtoforge.com/perfect_setup_ubuntu_6.10)

However, if you are wanting a gui, then you can always use Ubuntu desktop, and then install the necessary bits and pieces to allow it to do what you want.

However, I am just guessing but I feel that when you say FTP server,  you are actually meaning setting up peer to peer file sharing, like with Limewire (Windows), or something similar, plus using BitTorrent for file sharing.

If my guess is correct, then you would be better off using Ubuntu Desktop and installing Frostwire for your peer to peer, and BitTorrent for the torrent files.

Hope this helps.

---

### Post by hobs0n on 2007-06-09
Yeah I gotta have a GUI :) Im gonna try the Xubuntu desktop then. I mean to have a FTP server and a Torrent client on the server, got any good Linux Torrent client that is similar to Utorrent on Windows? IIRC the regular BitTorrent client is very basic with almost no features and handles 1 Torrent at a time, I need to handle 10-40 at  the same time.

---

### Post by Rocket2DMn on 2007-06-09
Azureus is a popular java-based torrent program which means it's cross platform!  You can use it on linux/windows/mac or whatever!  It is advanced, so if you know what you're doing, I suggest you give it a try, it's available in the repositories.

---

### Post by hobs0n on 2007-06-10
Yeah I used Azureus before I found Utorrent, IIRC Azureus took heaps and heaps of CPU and memory, is that the same now and in Linux?

---

### Post by Rocket2DMn on 2007-06-10
It shouldn't really used heaps and heaps, but it does use more than a typical program of its functionality because it is run on the java virtual machine.  it's really the biggest failing of azureus, and yet, one of it's best qualities.

---

### Post by Golyadkin on 2007-06-10
If you want to run it as a media center, maybe you can think about Linux MCE? 

These two video's made me very interested about it: 

 (part 1) [http://www.youtube.com/watch?v=QcNwnANrCpw](http://www.youtube.com/watch?v=QcNwnANrCpw)
 (part 2) [http://www.youtube.com/watch?v=tC-YwwQ1Pkk](http://www.youtube.com/watch?v=tC-YwwQ1Pkk)

Check it out : [http://linuxmce.com/](http://linuxmce.com/)

---

### Post by Golyadkin on 2007-06-10
By the way, Linux MCE runs on top of Kubuntu Feisty, so you will have the entire GUI available and you can use your programs in the background (like download stuff)

---

### Post by hobs0n on 2007-06-10
Hm Linux MCE seems very interesting, Ill try that later, Have to get the server up and running and working before. 

On to my next problem... I just burned Xubuntu and tried to install it, after I pressed "install and/or run xubuntu" in the first menu on the bootcd it start complaining about HDD errors, it says "revalidation failed", "buffer I/O error on dev fd0 logical block 0" "ata5.01 failed to set xfermode (err_mask=0x40). After a while it start erroring on ata6 too and then after about 5-10mins the screen goes blank. I got my 4 of my 5 HDDs on the   [Promise Ultra 133TX2](http://www.promise.com/product/product_detail_eng.asp?segment=undefined&product_id=87) PCI IDE controller card and I guess that Ubuntu doesnt like that controller card? The last HDD I have on the built-in IDE controller of the [MSI K9AGM2-FIH](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1165&maincat_no=1&cat2_no=171) Motherboard. Anyone got any idea whats going on??

EDIT: found a thread where Mikeshardlinux said he had the same card as I got and it worked. Why doesnt Linux like me? :(

EDIT2: WTF :((( I disconnected the 4 Promise controler HDDs and only had the HDD on the built-in controller, booted up a xp install cd and deleted the partition and ran the Xubuntu install cd again, same error, tho now it only says "buffer I/O error on dev fd0 logical block 0" i think, I havent watched so long... I bought this HDD 4 days ago, I have a hard time it has just broke when I had windows server 2003 installed on it 2 days ago!

---

