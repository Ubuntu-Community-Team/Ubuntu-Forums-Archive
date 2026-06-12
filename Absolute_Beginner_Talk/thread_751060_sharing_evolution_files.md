---
title: "sharing evolution files"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by LPLPACA on 2008-04-10
Simple question, hope the answer is simple too.

I am running a dell D630, dual booting between Vista and ubuntu (hardy heron). I have a 250Gb hard drive, it is partioned as 50gb for vista, 47gb for ubuntu, 3gb swap partition and the rest is an ntfs partition where I keep all shared data, ie downloads, music, video files etc. accessible from both Vista and Ubuntu.

What I want to know is would it be possible to move the ubuntu evolution files to the shared data partition, so that when running in Vista I also use evolution and access the same files - ie I keep the same email folders and address book for both versions of evolution?

And if so, how do I go about it?

thanks in advance

Paul

---

### Post by mikeyphi on 2008-04-10
Hi there and welcome!

I don't expect anyone has tried this! Whilst there is a windows version of Evolution - I think it would be very complicated to 'point' the linux version at a location other than /home where it stores (some) of the files.

Have you considered using webmail? that would allow access on both OSs using a browser.

Most users move to Ubuntu to avoid using windows but often keep windows just for those few special, personal, programs that are not yet available through Ubuntu!

---

### Post by LPLPACA on 2008-04-10
My main private email is GMail, work mail is a 2003 exchang server, so yes accessible by both OS's. I use this method already but prefer to use a client to webmail.

I am just curious, since I swap between both OS's whilst in work, it would be handy to let the mail client access the same set of folders. This is not a problem for exchange as the mailbox is kept on the server and only cached / accessed by the client on the laptop.

GMail on the other hand tends to archive all the messages downloaded to the client, and it would mean updating two sets of address books etc if done by the client.

Just thought it would be handy if one client could access the same set of folders in both OS's

Guess it is time to experiment - :)

Thanks for the reply.

Paul C

---

### Post by stchman on 2008-04-10
> **LPLPACA said:**
> Simple question, hope the answer is simple too.

I am running a dell D630, dual booting between Vista and ubuntu (hardy heron). I have a 250Gb hard drive, it is partioned as 50gb for vista, 47gb for ubuntu, 3gb swap partition and the rest is an ntfs partition where I keep all shared data, ie downloads, music, video files etc. accessible from both Vista and Ubuntu.

What I want to know is would it be possible to move the ubuntu evolution files to the shared data partition, so that when running in Vista I also use evolution and access the same files - ie I keep the same email folders and address book for both versions of evolution?

And if so, how do I go about it?

thanks in advance

Paul

You could try this.  In the users section under System--->Administration you can specify a home folder.  The default is /home/<your user name>.  Lets say you mounted the NTFS drive (using ntfs-3g of course) in /media/windows then just substitute the /media/storage there.

Now Evolution for Ubuntu will store all your email in ~/.evolution where it's Windows counterpart stores email I have no idea.  I would guess that it is C:\Documents and Settings\<your username>\Application Data\Evolution and there would be some folders there.

---

### Post by LPLPACA on 2008-04-10
OK thanks, going to backup my evolution folders first then try experimenting tonight / tomorrow - and yes need to find the evolution folder(s) in visciousta and see if I get access to them without to much admin rights adjusting :-\"

---

### Post by LPLPACA on 2008-04-25
The answer was so obvious it was staring me in the face all the time and I didn't notice - DOH!

Answer = as GMail now does IMAP connections, just deleted both profiles after backing everything up and ran the profile on each OS as an IMAP connection - does not matter which one I log into, they both synch with the server - easy peasy!

rgds

---

