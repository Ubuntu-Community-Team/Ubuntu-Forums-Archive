---
title: "[SOLVED] ftp in natalius = secure?"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-12-30
hey, is it ok to do this?

[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-13.png[/IMG]

to ftp inside nataulius? is it ssh or whatever?

i've been using filezilla, this way is so much easier...

sv


and if you have any favorite ftp clients that work great, tell me about it :)

---

### Post by Liolikas on 2007-12-30
nautilus I think...
Yes there is no differece from Filezilla or other client they all do same job,

I use **gftp**

---

### Post by LaRoza on 2007-12-30
ftp isn't secure by nature.

I use Filezilla mostly.

---

### Post by staticvoid on 2007-12-30
ok thanks.

i'll try that other ftp you mentioned. i've used filezilla, its nice


sv

---

### Post by Joeb454 on 2007-12-30
LaRoza: ftp isn't secure by nature, but sftp is a bit more secure, though from what I recall it sends the Username & PW over an unencrypted connection

---

### Post by scorp123 on 2007-12-30
> **Joeb454 said:**
>  sftp is a bit more secure, though from what I recall it sends the Username & PW over an unencrypted connection Nope. SFTP is "FTP over SSH", it sends all its stuff encrypted. 

[http://en.wikipedia.org/wiki/File_Transfer_Protocol#FTP_over_SSH](http://en.wikipedia.org/wiki/File_Transfer_Protocol#FTP_over_SSH)

Quote from there: ".... Other methods of transferring files using SSH that are not related to FTP include SFTP and SCP; in each of these, the entire conversation (credentials and data) is always protected by the SSH protocol."

---

