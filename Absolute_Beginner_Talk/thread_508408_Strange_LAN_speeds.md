---
title: "Strange LAN speeds"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by jd65pl on 2007-07-24
I have a file server and an apache web server running on the same machine. When I transfer files via http the data rate is good (6000kbs +) however when transfering files through samba the data rate is appalling (90kbs). The same file is transfered in both cases. Both were going slow until I forced the card to 100T full duplex using ethtool.
Anyone know how I can fix this or what is causing the problem?

---

### Post by asmoore82 on 2007-07-25
samba/Windows Share is a horrible protocol for transfer of large files.

many may find this bizarre but the absolute fastest way to **Transfer a File** is the **File Transfer Protocol (FTP)**

running vsftpd and transfering Linux to Linux I've achieved sustained transfer speeds of 97.3 Mbps  (11.6 MB/s) many times.

and Furthermore, using the same 100 Mbit switch, the same ethernet cables, the same vsftpd Linux server and **_Faster_** Windows machines as the client; I've never come close to the same speed as plain old FTP Linux to Linux 1.3GHz CPUs

---

### Post by jd65pl on 2007-07-25
Thanks,

I still require the use of samba, improved speed would be good if at all possible.

---

### Post by Mornedhel on 2007-07-25
> **asmoore82 said:**
> many may find this bizarre but the absolute fastest way to **Transfer a File** is the **File Transfer Protocol (FTP)**

I don't see why that's bizarre. FTP has got to be one of the most error-prone protocols : poor checks, errors are not corrected unless you implement some sort of checksum on both sides (which would not be part of the FTP protocol anyway). Thus the speed. That it's the fastest way doesn't mean it's the better. I don't recommend transferring high-quality music samples (think FLAC encoded) over a wireless FTP. The result may be horrible.

As for the problem at hand, I am interested by the solution as well.

---

### Post by asmoore82 on 2007-07-25
actually FTP is theoretically error proof as well; it uses TCP connections for control and data flow
so each piece of data is properly paritied. One of many things that same vsftpd Linux server did was an archlinux package mirror so multiple computers pulled packages from it at MAX SPEED and checksummed the data and NEVER had an error.

YOUR Mileage WILL vary when Non-*NIX (inferrior) machines are involved!!!

P.S. that bizarre comment was tongue-in-cheek...
if the best way to **transfer a file** was _NOT_ the **File Transfer Protocol**,
I would have given up on computers long ago. Ergo, I _DID_ give up on PC's with Winders _long_ ago.

---

### Post by Mornedhel on 2007-07-25
You have to manually compare file sizes on both sides to know if a transfer was interrupted or if it ended properly. And the TCP checksum is weak. (It is.) Any ameliorations are made on the client side, * after * the FTP layer.

FTP is not encrypted. FTP does not preserve timestamps.

OK, edited out the part about the "bizarre comment".

But what if I require Samba for, uh, I dunno, compatibility reasons (compatibility with pointy-haired bosses, that is) ?

Edition : Please note that a little personal war is going on between asmoore82 and me (nothing serious, eh). I'll be editing this post with the results, if there ever are any.

---

### Post by jd65pl on 2007-07-25
Again: ftp is not an option.

The machine serves files to windows machine which are opened using software on the client machine and saved back to the server, there should not be a requirement for the user to do anything other than open the file as they would a file located on a local drive.

---

### Post by asmoore82 on 2007-07-25
> **Mornedhel said:**
> You have to manually compare file sizes on both sides to know if a transfer was interrupted or if it ended properly.
That sounds like a serious design flaw **of the FTP *client* you are using**.
Please note that Windows Explorer/Internet Explorer/Firefox are _NOT_ proper ftp clients.. see gftp, filezilla
 
> **Mornedhel said:**
> And the TCP checksum is weak. (It is.)
FTP is not encrypted.
FTP does not preserve timestamps.
1. It is a 16 bit check which I would not even call a checksum. I would say it is a 16 bit wide collapsed parity, which, in truth, cannot be a 100% substitute for good checksum practices.
But, _nothing_ can be a sub for good checksum practices, this is why checksums exist.

2. This is an arbitrary fact of little value. If someone specifally requested a secure transfer, I would not even bring up FTP. Furthermore, not being encrypted would not even be an issue on a small office or home LAN setup.

3. Again, an arbitrary fact of little value. A remote transfer that goes out of its way to preserve timestamps is perverting the timestamp concept itself. You want the timestamp *on the local machine* to give you info *about the local machine*; a timestamp of a file *on a local machine* that gives you info about a file *on some server somwhere* is a timestamp that does not serve its purpose. (Just curious, but why would you want to preserve timestamps keeping in mind that UNIX machines do _not_ store file creation time?)

> **Mornedhel said:**
> But what if I require Samba for, uh, I dunno, compatibility reasons (compatibility with pointy-haired bosses, that is) ?
Indeed, getting back to the topic at hand....
Sorry, but I can't help with that specific problem.
But one must understand as they search for a solution that one is trying to use a superior system (Linux server) to preform an inferior task (Windows Netowrk Share). Therefore, there may not be a workable Samba solution.

Sorry, I do wish I *could* help.

Edit: TCP does "collapse" the parity by adding the 16 bit values; hence the name "check**sum**."
however, upon further reflection it still cannot be called "weak." You can call a 16-bit encryption "weak" in comparision to a 128-bit encryption, but this TCP thing is a different sitution... the 16-bit checksum of TCP packets garantees beyond doubt that every single bit (literally) of data is accounted for and correct. From that point on, It is the responsibility of your software and Operating System to reliably save the data. Ergo, I'll wager anything that widespread FTP errors on Windows have nothing to do with FTP.

The point of this rambling is this: TCP checksum is NOT weak.
A 16-bit checksum garantees all bits are correct.
A 256-bit checksum garantees all bits are correct.

ALSO, do not forget that TCP is the protocol used for almost all IP connections: FTP, HTTP, SSH, AND EVEN SAMBA.
Ergo, calling FTP unreliable because of a "weak" TCP checksum invalidates all these other protocols.

---

### Post by jd65pl on 2007-08-05
Bump

---

### Post by splintercellguy on 2007-08-05
Just curious but what are the NICs you have on both client/server?

---

### Post by Nythain on 2007-08-05
that has to be one of the most useless non to the point threads i've read on here in a while... only one poster even attempted to offer an option before it turned into two peoples debates over a protocall that the original poster has stated isnt an option.

i to am having this problem, and seeing as how i serve media files and other stuff to a large home network, ftp just isnt an option... my problem started recently... and samba was working fine untill recently, but now i get inconsistant rates fluctuating between 0-500k, often times hanging at 0 till the windows machines involved time out, or causing horrible choppiness or lag and unsync in any media file being played.

i understand i can switch to ftp, but it makes no sense for me to keep a bunch of stuff on a server (mostly media files) and have everyone else have to download them onto thier computers to listen to or watch them...  they could just download them themselves and waste thier limited hard drive space if that were the case...

---

### Post by jd65pl on 2007-08-06
Lol I wasn't so happy with the thread being hijacked like that, it has been somewhat unproductive.

I think this thread might be a bit out of scope for the beginners forum so I have posted it in networking. [Link]("http://ubuntuforums.org/showthread.php?p=3142846")

---

