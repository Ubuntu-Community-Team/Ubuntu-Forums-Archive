---
title: "I made a truecrypt howto - where should I post it?"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by hornetcoach on 2008-01-02
Hi all - after messing around for quite a while with a good "scheme" for using truecrypt, fast easy and secure I came up with this and wrote it down....

Can someone QA it and provide feedback - then post it where it should go?

Here it is...it's pretty long...but easy.

Do you really need to encrypt your data?  I asked myself that question after I had cranked through a mandatory Marine Corps "information security" powerpoint class that had been emailed to everyone, with the usual "do this and tell me when you've done it."  I have been a Marine Officer for a pretty long time and I have emails dating back to 1996...back when we really didn't care if someone's SSN was on a cocktail napkin at the bar.  Things are different now and I started thinking - there is probably some sensitive information buried in all those emails, and maybe I should have some better security.  Now you might be thinking - the Marine Corps...they must have some heavy duty encryption schemes for their people!  Well, we do - on the computers that are owned by the Marine Corps.  But...it's the Marine Corps...and the USMC is the cheapest service out there.  The saying goes - We have done so much with so little for so long, we now think we can do anything forever with nothing.  This means I use my own personal laptop for just about everything that is not "classified".  And the USMC gives me nothing to help secure this laptop, I am exactly like every other person out there...only if my laptop was stolen, you might hear about it on CNN..."Marine Officer loses laptop - unknown amount of information lost" etc...

I decided to write my technique for securing my data after switching to Linux and screwing with some different applications.  I spent a fair bit of time setting this up so it is easy to use and easy to backup.  I am a complete Linux newbie, so these instructions should not be too much of a stretch for anyone who can read and type.

Enough of the long story - 

Super tough encryption program:  Truecrypt  ([www.truecrypt.org](www.truecrypt.org))
	Truecrypt has a nice GUI in Windows.  In Linux it uses the command line.  This is a good thing.  Command line combined with a keyfile makes the Linux version easier to use than Windows.  It just takes a little bit more setup time.  Once setup it is dead simple and fast.  Stick in USB stick, double click on an icon and your secure "locker" door is open for you to use.  There is a ton of information out there for Truecrypt.  It is extremely powerful and can do a lot of really clever things.  My use is pretty straightforward...if some steals my laptop or backup drive I don't want them to get to my stuff for millions of years.  I don't care if they can tell it's encrypted, I just want it to be "uncrackable".
	One cool thing with Truecrypt is it makes backup a snap.  The file you set up to store all your stuff in is just one huge file...to backup, just drag and drop onto your backup drive and you have a secure backup of your data.

CAVEATS AND DISCLAIMERS:
USE AT YOUR OWN RISK.  TRUECRYPT RECOMMENDS LONG HARD PASSWORDS.  THERE ARE SOME VERY CLEVER PEOPLE WHO HAVE WRITTEN GUI'S FOR TRUECRYPT IN LINUX - THEY ARE FANTASTIC - THIS IS AN ALTERNATE METHOD USING SIMPLE DESKTOP SCRIPTS.  IF YOU LOOSE YOUR KEYFILE OR PASSWORD YOU WILL NEVER GET YOUR DATA BACK.  IF YOU DELETE THE ONE BIG "FILE" THAT IS YOUR ENCRYPTED CONTAINER, IT IS GONE IN ONE FELL SWOOP.  THIS WHOLE THING IS TECHNIQUE ONLY - DON'T USE IT TO VIOLATE ANY LAWS, COMPANY POLICIES ETC...

OK - so here is what I did - I recommend trying this on a test file first.

1.  **Install Truecrypt.** I am using Ubuntu and I ran Synaptic Package Manager to get it.

2.  **Make a partition for data on your hard drive.**  I used NTFS for portability.  I would avoid FAT32 because the maximum file size in FAT32 is 4 GB.  Your new encrypted vault will likely be much larger than that.  (Mine is 25 GB...it includes everything except media files).

3.  **Create keyfile.**  This will be the no-kidding "key" to your data.  It is like a super long password that would take every computer in the world working at full speed for millions of years to "crack".  To keep this key secure it will NOT be stored on the computer.  This is where your memory stick comes in.  A CD or floppy would work fine too.  The keyfile is stored offboard on the memory device of your choice.
 
	a.  Insert memory stick
	b.  Find path to memory stick...it should be something like /media/disk (right click "properties" works to find path)
	c.  Open terminal
	d.  type: truecrypt --keyfile-create /media/disk/mynewkey
	e.  (You can name the key whatever you want.)
	f.  The 320 random characters are used to "seed" the encryption algorithm...the characters you type are not part of the keyfile they are used for the initial generation of the keyfile.  If you are super paranoid, use the root, mouse enable deal it mentions.

4.  **Make a copy of your keyfile and store it somewhere safe**.  Burn a CD and a backup CD and store them in a firesafe, safe deposit box etc...  If the keyfile is lost...you are S.O.L.  Even if the NSA helped you out...the sun would die prior to getting your data unlocked.

Terminal Example of Key Creation
====================================================================================
ara@ara-laptop:~$ truecrypt --keyfile-create /media/disk/mynewkey
TrueCrypt will now collect random data.

To enable mouse movements to be used as a source of random data,
please do one of the following:
- Run TrueCrypt under administrator (root) account.
- Add read permission for your user to device /dev/input/mice.

Please type at least 320 randomly chosen characters and then press Enter:
iouoijrtmoijm,poigjwpioeupvu8yn8ipynipyI&Y&T&^%^%$@#$ETRfchgbvjhbJBMkunbuNLu,jhiuHUIhuyGtyftrfTRFCyrufUTYgiuHuonP<jopjPuioj.poJuhiUHuygytfuyrFtrdTEdred43s32W#2q2!Q@#1#W54dytgUhyu8i()i90I-0o)_oO=-olP{l,p[.>[/[/p[.OPkmIOjUIbuBVytvtrcETxrewXwZw4s$w5$e56R76Y7hjjpiMm<opmIOnyIGtyrFCtedrews$e7687Y89U9kopkOPkmiopjuGHuFy5D64e

Characters remaining: 2
YTFTYFTGuiyhiuojhoijoijo

Keyfile created.
ara@ara-laptop:~$ 
===================================================================================

5.  **Create your encrypted "container" using Truecrypt**.  You need to take a look at all the files you want to put into this vault, to ensure it is big enough.  Like I said in step 2, mine is currently 25GB.

	a.  Open terminal
	b.  type: truecrypt -c
	c.  Truecrypt will prompt you for all the options needed to create your secure container.  The file system inside the container will be FAT32...this has nothing to do with where you will 'store' the container (see the NTFS comment in step 2.)
	d.  Use a clever name for your new vault...something like "locker" or "vault"...if you're paranoid, a name like "trash" might throw off the casual observer.  
	e.  Use the defaults, or any other option for Hash and Encryption algorithm.  Using multiple encryption algorithms will slow down the encrypt/decrypt process, so I don't recommend it (options 7-11).  The U.S. Military uses AES.
	f.  Pick a simple password...we'll use keyfiles (explained later) to make the password inconsequential.  If you don't want to use a keyfile, use a long password.  I used the letter "a" for the password.  YOU MUST REMEMBER THE PASSWORD!
	g.  When prompted for keyfile path, insert your memory stick and use the path to the key generated in step 3.
	h.  The 320 random characters are used to "seed" the encryption algorithm...they are not really used except for the intial generation of the file.  If you are super paranoid, use the root, mouse enable deal it mentions.
NOTE:  I had to do a restart for the file to show up in Nautilus...not sure why and it only happened once.  If you finish this step and don't see the file, try a restart.

Terminal Example of "truecrypt -c"
====================================================
ara@ara-laptop:~$ truecrypt -c
Volume type:
 1) Normal
 2) Hidden
Select [1]: 1

Enter file or device path for new volume: /media/data/locker
Filesystem:
 1) FAT
 2) None
Select [1]: 1

Enter volume size (bytes - size/sizeK/sizeM/sizeG): 2M

Hash algorithm:
 1) RIPEMD-160
 2) SHA-1
 3) Whirlpool
Select [1]: 3

Encryption algorithm:
 1) AES
 2) Blowfish
 3) CAST5
 4) Serpent
 5) Triple DES
 6) Twofish
 7) AES-Twofish
 8) AES-Twofish-Serpent
 9) Serpent-AES
10) Serpent-Twofish-AES
11) Twofish-Serpent
Select [1]: 1

Enter password for new volume '/media/data/locker': 
Re-enter password: 

Enter keyfile path [none]: /media/disk/mynewkey
Enter keyfile path [finish]: 

TrueCrypt will now collect random data.

To enable mouse movements to be used as a source of random data,
please do one of the following:
- Run TrueCrypt under administrator (root) account.
- Add read permission for your user to device /dev/input/mice.

Please type at least 320 randomly chosen characters and then press Enter:
ifut89374j98u*(U89u89tubuytftyftred3w4s32$D%^F&^g786tg76t78Y(*u89uJiom<,P{.p[?p[/P{;.opL0iok(Uj8uyh7yGt6f6rf5eFe43d4wd$#Wd4eFC56rgf7tbh8iJN9uijmn*Uh7yG65tff%$f54f54f6trgvTg5rF4e32S2q12s3wXe4cvtb8uyjn9uJM8uJNyhtg6rf%Ef4ef546FUbhIUnui9m9um8n&bT^v%Rfc54efc6f7tBH8uyj(j*yhg75g6$f54f64fg7g76H78yH7g&6g65rf6rf6gvybh&*Yg7g7g78uh90kjomLKmnlJhkuHiytr64e%$e4tDhgbjkHikhoiyI7t&^4r65#543^rFJHb,jN,n<JbHGVgfCngvGNvchTFRyREy5R7uT

Done: 2.00 MB  Speed: 1.66 MB/s  Left: 0:00:00  
Volume created.
ara@ara-laptop:~$ 
====================================================

6.  **Create an empty folder on the data partition with the similar name as your encrypted container**.  This name will show up on the desktop when you "mount" the container.  I just add the word "crypt" to the file name.
e.g.
/media/data/locker_crypt

7.  **Add a script to run Truecrypt and "mount" your vault.**  Basically, Truecrypt opens a door to your vault.  When the door is open you can come and go as you please.  The name of this door will be "locker_crypt".

	a.  Open text editor
	b.  Enter the command for Truecrypt to "unlock" your locker.

Example:
==========================================================
#!/bin/bash

----------------------------------------------------

# mount your locker

truecrypt -u /media/data/locker /media/data/locker_crypt -k /media/disk/mynewkey
===========================================================

	c.  Save the file on the Desktop, with a name like "mount_locker".
	d.  If you change the location or path of the keyfile, you'll need to update this script to point to the keyfile location.
	e.  Right click on the "mount_locker" script and enable "execute as program" under permissions.

Command Notes:  
*The '-u' mounts the file as FAT - makes it read/writable...this took me a while to figure out.
*/media/data/locker is the location of the encrypted file you made.
*/media/data/locker_crypt is the location of the empty folder...the 'door' to your locker.
*-k /media/disk/mynewkey tells truecrypt to use a keyfile and where it is.

8.  **Try it out! ** 
	a.  Double click on the "mount_locker" on your desktop.
	b.  Click "Run in Terminal"
	c.  You may be prompted to enter your sudo password.
	d.  Enter your easy password "a" in this case.
	e.  An icon should appear on your desktop that looks like a drive and says "locker_crypt".
	f.  You can also get to this 'door' by opening the "locker_crypt" folder in your data partition.
	h.  You need to have the keyfile available.  This is what makes it secure - keep the USB stick on your keychain, or whatever, but separate the keyfile from the computer and this thing is uncrackable.

9.  **Not quite done - you'll want to be able to close the 'door'...another quick script.** 
	a.  Open text editor
	b.  Enter the command for Truecrypt to "close" your locker.

Example:
==========================================================
#!/bin/bash

----------------------------------------------------

# unmount all truecrypt volumes (lockers)

truecrypt -d
===========================================================

	c.  Save the file on the Desktop, with a name like "unmount".
	d.  Right click on the "unmount" script and enable "execute as program" under permissions.
	e.  Double click on it and you should see the 'door' close.  ("locker_crypt" removed from desktop and when you look in the folder, zero items are in it.)

---

### Post by mmb1 on 2008-01-02
You should probably post this in the "tips and tutorials" section of the forums.

---

### Post by hornetcoach on 2008-01-02
Makes sense...how do I move it?

---

### Post by mmb1 on 2008-01-02
You'll either have to repost, or get the attention of a mod, normal users like us lack the ability to move threads.

---

### Post by dada12 on 2008-01-04
Thanks for the post!  Just a quick clarification about FAT vs NTFS:

The 4GB file size limit under FAT refers to the size of **individual files** and not the physical size of a tc volume.  In other words, you can create a tc volume of say, 20GB and have it formatted in FAT.  The only limitation you will have is if you try to store a file that is larger than 4GB in that partition or volume.

The advantage of using FAT vs. NTFS in your tc volume is that secure file deletion is more viable under FAT than under NTFS, which is a journaling file system. 

Should you want to securely delete files within your tc volume, utilities such as **shred** will be more effective under FAT than under NTFS.

Hope this makes sense.

Thanks again for a really helpful howto!

non-windows-user :)

---

### Post by Niniel on 2008-01-04
Oh PLEASE!

> Command line combined with a keyfile makes the Linux version easier to use than Windows.

Keep your personal preferences out of a How To. I am using TC on Windows myself, and that GUI cannot be any easier. Incidentally, I read [somewhere here in the forum]("http://ubuntuforums.org/showthread.php?t=585578&highlight=true+crypt+gui") that some people are developing a TC GUI for Linux/Ubuntu. Don't think it's fully done yet though.

Btw, TC also offers full partition encryption (not sure if that's what you did).

Regarding multiple encryption, my experience is that it does not seem to slow down anything on a modern computer. Copying large amounts of data to your TC container will take a while, but normal operation does not seem to be any slower (I'm using a triple encryption scheme... just because I can).

File system - for such large drives, I don't think FAT would work. I don't see any reason not to use NTFS inside the container. 
Keyfiles - you can also specify files (mp3s, images, almost anything) to be used as keyfiles. Yes, you can specify more than one. 

Btw, for Linux encryption, you may also think about full-disk encryption. You can still put a TC container in there if you feel like it. 
I can recommend the Ubuntu alternate install CD - when it's time to partition, select "use entire disk with LVM encryption" and that's basically it. The only thing unencrypted on your drive will be the /boot partition.

---

### Post by hornetcoach on 2008-01-05
Thanks for the reply.  I'll make the reference to the NTFS vs. FAT clearer..what I meant to say was the date partion was formated to NTFS so it would support the 25GB tc container, then the container itself was formated to FAT...I'll try it with NTFS.   I didn't mean to imply the Windows TC gui was hard to use - I just found I could mount and use the linux version quicker once it was set up.  My comment to the command line interface was intended to demystify it...I am new to the CLI and found it to be a lot easier to use than I thought it might be.  Good to know on the multiple encryption won't slow things down, I'll take that out too.  I am working on downloading the alternate install CD to take a look at the LVM encryption...I only get 150MB a day, so it takes a long time.  d4x has been great for the many day start/stop downloads.  Thanks again for the comments.

---

### Post by Niniel on 2008-01-06
Regarding those encrypted partitions I mentioned earlier - do you know of a way to open them in Linux? 
I have encrypted a partition for use in Windows (/dev/sda5), but it looks like Ubuntu doesn't even see it, probably because it's not formatted in way it knows. 

Oh, and as I was reading through your instructions, I came upon this:

> truecrypt -u /media/data/locker /media/data/locker_crypt -k /media/disk/mynewkey

If I understand this correctly, then that -k switch could be a problem since it points attackers to your key file. Or even tells them that you use one. Or more, if that works with more than 1 file.

---

### Post by BigLebowski on 2008-01-06
The next version of Truecrypt, truecrypt 5.0 will have a Linux GUI. Its coming out this month.

Most likely the reason why the forums are down, probably upgrading to  prepare for the mass of traffic expected. 5.0 will come with Mac/Linux GUI and Full disc encryption ;)

And as was mentioned before the FAT limitations is on individual files. I have a 500GB Fat.

---

### Post by Niniel on 2008-01-06
Oh, that'll be cool.

---

### Post by meho_r on 2008-01-06
> **Niniel said:**
> 
If I understand this correctly, then that -k switch could be a problem since it points attackers to your key file. Or even tells them that you use one. Or more, if that works with more than 1 file.

Agree. And it's recorded in /var/log/auth.log

---

### Post by hornetcoach on 2008-01-08
> **Niniel said:**
> Regarding those encrypted partitions I mentioned earlier - do you know of a way to open them in Linux? 
I have encrypted a partition for use in Windows (/dev/sda5), but it looks like Ubuntu doesn't even see it, probably because it's not formatted in way it knows. 

Oh, and as I was reading through your instructions, I came upon this:



If I understand this correctly, then that -k switch could be a problem since it points attackers to your key file. Or even tells them that you use one. Or more, if that works with more than 1 file.

Yep - the -k does point to the keyfile...so anyone who got my computer would know to look for that file - I think there is a tradeoff between level of security and convenience.  By separating the keyfile (on a usb stick) from the computer, I am comfortable with having a script that points to the off-board keyfile.  If your files need a level of security that requires no one ever know or find a keyfile, or hidden volumes etc... you need to assess your need and take proper precautions.  I like that there is a Linux GUI coming, but have been really impressed with the ease and convenience of TC's CLI interface.

I'm not sure about your sda5 partition, but...
The following thread from rob_jewkes might be what you need:
[http://ubuntuforums.org/showthread.php?t=380469](http://ubuntuforums.org/showthread.php?t=380469)

---

### Post by meho_r on 2008-01-08
> **hornetcoach said:**
> Yep - the -k does point to the keyfile...so anyone who got my computer would know to look for that file - I think there is a tradeoff between level of security and convenience. 

Not necessarily. Look here: [http://ubuntuforums.org/showthread.php?t=585578&page=19](http://ubuntuforums.org/showthread.php?t=585578&page=19) and page 20, same thread. EasyCrypt now doesn't leave any trace about your pass or keyfile

---

### Post by dada12 on 2008-01-08
Niniel, 


Just a quick thought about the "-k" switch.  It does not matter if an attacker notices the path to your key file, as long as your keyfile is on a removable and preferrably, read-only media (CD-R, etc..).

---

### Post by anaconda on 2008-01-08
Thanks for the nice tutorial.. with your script the GUI will be next to useless.. atleast if you use just one TC -file.

Just wanted to mention to the NTFS/FAT32 battle that ext3 is also a good choise..  expecially if you use the TC-container mostly in linux.

---

