---
title: "Ccrypt"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by topic58 on 2005-12-17
Hi, someone out there who can tell me how ccrypt works in terminal? I have downloaded it from Synaptic. I have a .txt file on my desktop I want to encrypt, but I don't know how to make it work.

---

### Post by bscbrit on 2005-12-17
I have used CCrypt but found that another package called Botan is far more useable, and I have been using that for over a year now.  Botan is not part of the ubuntu system but works very well on it regardless.  
To go back to your question though, are you asking how the cryptographic algorithms work, or how to interface your programs to the CCrypt library?  And, if its the second option, how much programming experience have you in C/C++? (I suppose the library might interface with other languages but I only use C/C++ for my crypto programs.

---

### Post by bscbrit on 2005-12-17
Have you tried

'man ccrypt' 

in a terminal window?  I was assuming you were talking about the library but I see that there is also a stand-alone program of the same name.

---

### Post by topic58 on 2005-12-17
Ops, this seem rather complicated.. :???:  All I want to do is to encrypt some files in Ubuntu. Maybe there are some other ways to make this happen? Hopefully easier ways too. :rolleyes:

---

### Post by bscbrit on 2005-12-17
I assume that you were commenting on my first post - which I admit was probably a little wide of the mark.  Try the 'man ccrypt' page.  Ccrypt seems to do what you want and is fairly straightforward for a commandline function.  Have you looked for alternatives such as gpg and gnupg/KGpg?  Gnupg provides a drag-and-drop interface for encrypting and decrypting files and is secure enough for most purposes.  I would not say it cannot be broken but you would need some serious hardware to do it in a reasonable timescale.

---

### Post by topic58 on 2005-12-17
Is there any simple software to be downloaded that I can use without having to use the terminal? A graphical application I mean. Lots of them in windows, but a lack of them here...

---

### Post by bscbrit on 2005-12-17
Yes, install KGpg frontend (although it is designed for KDE it works fine under Gnome too) and gnupg. That will give you menu items in Gnome for encryption and decryption, and a drag-and-drop capability.  I have used it for several years, the last six months or so on Ubuntu, and I have experienced no problems.

---

### Post by ninotob on 2005-12-17
I haven't used ccrypt but I do use "mcrypt" (in the repositories) often.  It can be simple or you can go into great complexity.  It's as easy as this:

mcrypt filename

It then asks you to enter a password twice, if they match it is encrypted.  The original file is untouched so you have to delete it yourself.

To decrypt the file, use the "-d" option:

mcrypt -d filename

It asks for your password and if correct, decrypts the file.  There are many options if you want to get into that which makes it useful in scripts.  But there is no need to go into those complexities if you don't want to.

---

### Post by bscbrit on 2005-12-17
ninotob, Yes, you are correct but I think that topic58 is looking for something that doesn't require the command line.

---

### Post by topic58 on 2005-12-17
Okay, tested mcrypt and it works nice with a simple .txt file. But I get a message "operation not allowed". Still I get the new file.txt.nc Just have to delete the first file.txt. Do you have the same problem? Nothing big just want to verify. ;)

---

### Post by bscbrit on 2005-12-17
Rather than 'deleting' the file, you might want to consider 'wipe'ing the file.  Wipe will destroy the file contents and then the file name securely so that it cannot be recovered.  I assume that if your data is worth protecting you don't want to leave unencrypted copies of your data on your hard disk?  'wipe' can be downloaded using synaptic or apt-get

---

### Post by ninotob on 2005-12-17
[QUOTE=topic58]Okay, tested mcrypt and it works nice with a simple .txt file. But I get a message "operation not allowed". Still I get the new file.txt.nc Just have to delete the first file.txt. Do you have the same problem? Nothing big just want to verify. ;)[/QUOTE]


No I don't -- do you have permissions on the file to read or the folder to write?

This is what I get:

$ cat test.txt
test test test

$ mcrypt test.txt
Enter the passphrase (maximum of 512 characters)
Please use a combination of upper and lower case letters and numbers.
Enter passphrase:
Enter passphrase:

File test.txt was encrypted.
$ mcrypt -d test.txt.nc
mcrypt: test.txt already exists; do you wish to overwrite (y or n)?y
Enter passphrase:
File test.txt.nc was decrypted.


EDIT:  I realize the original poster wants a gui, but mcrypt is so simple I thought I'd mention it.  Man pages can make "ls" look hard, and mcrypt can come in very useful with backup scripts.

---

### Post by topic58 on 2005-12-17
I even tried to encrypt a folder, but no luck there. Is it even possible?

---

### Post by bscbrit on 2005-12-17
If you want to encrypt a complete directory - but not use it while it is encrypted - you could always pack it into a zip or tar.gz and then encrypt that.  What you are asking for is beyond mcrypt, I think, but it is possible to run encrypted file systems.  That is a major leap from your original idea....

---

### Post by topic58 on 2005-12-17
He he he, okay. Tried tar.gz but it couldn't be fixed back to original with a file of 246 MB. Success with zip though. :o  Very nice. How safe is mcrypt?

---

### Post by bscbrit on 2005-12-17
Thats a difficult question to answer.

If you have a file that has been encrypted using mcrypt on, say, a floppy disk then someone trying to decrypt it has several problems.  Firstly, they have to work out which method of encryption has been used.  I don't just mean which program, but which crypto-algorithm.  If mcrypt uses a distinctive extension for its encrypted files then that alone might be enough to answer both those questions!
Then they still have to discover the password, which is used as a seed to start the encryption/decryption process.  On a disk then they have no idea, but if file is on your computer then they could simply look through your bash log to see what command you used.
And then there is the encryption algorithm itself - how good is it?  A quick search on the web indicates that mcrypt can use a variety of encryption algorithms, many of which are considered 'secure' for normal use. (Given enough time and effort many systems can be broken, but who would want to devote that amount of time and effort?)
In the real world, codes are more likely to be broken by having the password compromised or leaving unencrypted and encrypted files together.  Even when deleted - the data is still written on the disk until something is written over it!  (Hence why I suggested that you use 'wipe')
Protect you password and use common sense and your data will be secure.  Conversely, if you forget your password you can say goodbye to any chance of getting your data back.

---

### Post by topic58 on 2005-12-17
I guess I can feel pretty safe with my information then. And of course sensitive information should not be stored on a computer. ;)  Read an article about that some days ago. They have tested an old harddrive and not surprisingly they found a lot of good information on it. Creditcard numbers and so on. Better then to wipe everything out before selling it or destroying it. Am I being paranoid here or what? But better safe than sorry. Okay then and many thanks for all the help I got in this thread. I will continue using Ubuntu, started out in august, four months now, and still learning the hard way. BUT - I like it a lot. :p

---

### Post by ninotob on 2005-12-17
I don't know how safe it is, and by that I'm guessing you mean "how hard to crack".  The man page for mcrypt is better than most (has examples -- OT: why do so many man pages lack examples??), I'd start there.  After that, just google around.

As for directories, I don't think you can do that directly.  You'd want to tar it first:

tar -czvf [COLOR="DarkRed"]name_of_archive_file.tgz[/COLOR] [COLOR="DarkGreen"]/path/to/folder[/COLOR]

the switches czvf:

c=create
z=gzip compress
v=verbose (tell you what it's doing)
f=means write to a file you name (otherwise the output goes to the screen)

I colored the last two parts.  In red is the filename you want to create.  In green is the directory you want to read and copy into your tar file (in the filename (red) part, I used tgz instead of "tar" because it's gzipped).

if you wanted, you could make a script to do both things at once like this, open your favorite text editor and copy this in (fwiw, I love the cli app "nano" for simple things like this):

#!/bin/bash
NAME=$1
DIR=$2
tar -czvf $NAME $DIR
mcrypt $NAME

Have one blank line under the "mcrypt" line and then save it as "dircrypt", then make it executable (*):
chmod 700 dircrypt

In the location you created the dircrypt script, type:

./dircrypt [COLOR="DarkRed"]file_name.tgz[/COLOR] [COLOR="DarkGreen"]/path/to/folder[/COLOR]

and then it tars it up and asks you to enter a password.
You could do more like add date stamps, or have it get the password from a file (useful for automation purposes).  You could add it to a directory in your path and then you don't have to type "./" -- anyway, mcrypt can be quite useful.

(*) 700 only the owner can execute, read, or write.  Groups and others totally excluded.

Edit:  if you have "wipe" installed (not installed by default), and want to "wipe" the unencrypted *.tgz file, you would simply add a line after the "mcrypt $NAME" part that says "wipe $NAME".  If regular deletion is OK w/ you, modify the mcrypt line so it says "mcrypt -u $NAME" (the "u" stands for "unlink").

Edit 2:  Just so it is clear what is going on in the script, the parts like "NAME=$1" simply assign the arguments you give the script to variable names.  $1 is the first argument, $2 the second.  So when you type out "some_command arg1 arg2", the argument in the first position gets assigned as directed in the script and so on.

---

### Post by poptones on 2005-12-17
If you do not have encrypted swap and /tmp space encryption is pretty much for naught. Boot the system with knoppix, run an fsck recovery on the partition, and there's all your recently used files...

Might I suggest you check the wiki? You can create an encrypted partition (or retroactively encrypt one) very easily.

---

### Post by bscbrit on 2005-12-17
poptones, whilst it is possible that /tmp and /swap _could_ have unencrypted data on them (and note my post on this thread earlier), simply invoking mcrypt does not need either.  /swap will only be used if the kernel has to swap memory to run other jobs at the same time that the encryption program is running.  On my computer with 512MB that doesn't happen very often unless I am running several programs at once, and there is no reason whatsoever for the /tmp directory to be used.  However, there is always this risk that unencrypted data _could_ be on those partitions.  Therefore I do not use mcrypt, but have my own routines based on Botan which I mentioned very early on in this thread.  These routines use secure memory to carry out the various encryption/decryption tasks and the data is not written to disk (ever!) unless it is encrypted in some form or other.  I have carried out reasonably extensive disk analysis using various forensic techniques and I have not found unencrypted data on the disk.  Some data is not encrypted to a very high degree but it is not even recognisable as encrypted data, so I am satisfied the someone whould not know where to begin to decrypt it.  It is also possible to arrange for /swap and /tmp areas to be erased at shutdown.  
However, I feel that we are now digressing from the main reason for this thread.  Let me know if you think I have it wrong because I am currently working on a secure data system and would like to ensure that I have understood the theory correctly.

---

### Post by poptones on 2005-12-17
*These routines use secure memory to carry out the various encryption/decryption tasks and the data is not written to disk (ever!) unless it is encrypted in some form or other.*

That should be interesting if one were opening, say, an iso of a full cd on a machine that had only 512mb of ram.

Making something "wipe" data is closing the barn after the horse has bolted. In the simplest, least invasive case (ie it's not the feds after your data just your spouse or kid) any interruption to the shutdown process doesn't fix anything. Also, those "disk wipe" utilities cannot be trusted pretty much at all. Journaled filesystems may not write immediately or even to the proper sectors, and modern drives may remap sectors if errors are discovered. this latter case won't matter unless there's a forensic analysis of the platters, but it's important to know about these things.

It's **incredibly easy** to encrypt your swap partition - in fact, it makes little sense not to do it. The only case I can think of for not doing it is in a machine  where you use suspend to ram, as that writes the machine state to swap and will cause kernel panics on startup (swap partition key is stored in the encrypted swap partition, how to get it?)

I won't comment much on the "my own routines" part except to say I would personally prefer to use open code that has been well hammered in the community by folks who know a lot more about that shit than me. 

The simplest way to protect "some" data on your drive is just to create an encrypted partition. Ubuntu's mountall script will even create the loopback device and mount it for you if you install cryptsetup and use a file as the source device - it's nearly transparent.

---

### Post by bscbrit on 2005-12-18
Good point about encrypting a CD but the system I am using is not looking at individual chunks of data much larger than about 200K.  These are encrypted on the fly and do not get written to disk until they have been processed.
The reference to my own code is not to the encryption algorithms - only to the code that glues them together.  As I said earlier, I am using the Botan library.  
'wipe' has been tested by (our) appropriate authorities and meets our requirements, but you are correct in saying that it would be better not to have data on the disk in the first instance. :p

Thanks for your comments.

---

### Post by poptones on 2005-12-18
BTW, swap gets used even when your main ram is not "filled." I have seen my system write to swap when I had only 250mb or so out of 512mb in use - swap gets activated for a variety of reasons, time being one of them.

Open a text document in gedit (let's pretend it's encrypted). Minimize the window while you go about doing other stuff. Forget about it an hour or two while you do other stuff - then click on it. See how it takes a couple of seconds to "fill in?" Did you hear your hard drive click? That's because the app had been swapped out as a "low priority" task...

Encrypt your swap space if you use encryption. It's the cheapest insurance you can get.

---

