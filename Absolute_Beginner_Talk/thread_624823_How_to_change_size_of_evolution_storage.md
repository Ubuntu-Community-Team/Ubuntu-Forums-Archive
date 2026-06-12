---
title: "How to change size of evolution storage"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by linuxneeewb on 2007-11-27
I have a gmail account with about 3 GB of storage space. Yesterday I was downloading most of my emails via POP3 in Evolution. But it suddenly stopped and kept giving me the message below. 

Error while Opening folder mbox: /home/user/.evolution/mail/local#Inbox

I would greatly appreciate if you could tell me how to make my evolution storage space much higher so that I can download all of my emails. 

Thanks

:guitar:

---

### Post by Nano Geek on 2007-11-27
I don't think Evolution has a size limitation on your Inbox.
Perhaps you hard-drive if full.

---

### Post by stchman on 2007-11-27
> **linuxneeewb said:**
> I have a gmail account with about 3 GB of storage space. Yesterday I was downloading most of my emails via POP3 in Evolution. But it suddenly stopped and kept giving me the message below. 

Error while Opening folder mbox: /home/user/.evolution/mail/local#Inbox

I would greatly appreciate if you could tell me how to make my evolution storage space much higher so that I can download all of my emails. 

Thanks

:guitar:

I agree with poster #2.  My .evolution folder is over 350MB.  You are limited by the size of your hdd.

---

### Post by linuxneeewb on 2007-11-27
I know that it is not an issue with my harddrive. My harddrive is 320 GB and I have over 280GB of free space.

:lolflag:

---

### Post by Nano Geek on 2007-11-27
Can you tell us what the permissions are for that file?

---

### Post by Arthur Archnix on 2007-11-27
First, confirm that you have it setup correctly:
[http://www.go-evolution.org/FAQ#How_can_I_access_my_GMail_POP_account.3F](http://www.go-evolution.org/FAQ#How_can_I_access_my_GMail_POP_account.3F)

Second, try downloading only 100 messages or so at a time. I had errors using thunderbird, and I just had to slow it down and let TB digest the stuff. Don't try and do it at one go.

I can't find any report, bug, complaint or any other reference to a file size limit, though one person on #evolution said that its possible to force a limit when compiling. So, theoretically at  least, Ubuntu could have compiled in a limit on the file size, but its doubtful.

---

### Post by linuxneeewb on 2007-11-27
I am sure that my setup was correct.

:popcorn:

---

### Post by Nano Geek on 2007-11-27
Did you try everything suggested here? I can't imagine that it's not one of those.

---

### Post by djcrash1981 on 2008-02-11
Hi to all.

I'm having the same problem here.

I've look everywhere to find an answer and nothing.

What i've see is that is not a matter of free space on the hard drive, is more related to de file size of your inbox.

Checking the size of my inbox is about 2 gb long and the error it gives me, is that can't write because the size is too big for the filetype.

Now can anyone help me to recover some of my mails????

Help!!!!!!!!!

---

### Post by djcrash1981 on 2008-02-13
> **djcrash1981 said:**
> Hi to all.

I'm having the same problem here.

I've look everywhere to find an answer and nothing.

What i've see is that is not a matter of free space on the hard drive, is more related to de file size of your inbox.

Checking the size of my inbox is about 2 gb long and the error it gives me, is that can't write because the size is too big for the filetype.

Now can anyone help me to recover some of my mails????

Help!!!!!!!!!

Ok,I've resolve this.

The problem was that for the mbox filetype can't exceed the 2 Gb limit. ](*,) :twisted:

So what i did was use the [archivemail tool]("http://archivemail.sourceforge.net/"), with this I cleaned up the file and it reduce drastically. The tool create a new file with all the old mails found so I didn't loose a thing.
\\:D/

I hope this help someone. :lol:

Thanks.

---

