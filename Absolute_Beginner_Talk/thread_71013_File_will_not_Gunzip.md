---
title: "File will not Gunzip"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by happychap on 2005-10-02
I am unable to get a tar.gz file to unzip.
The file was downloaded/saved in Windows partition which I have mounted to Ubuntu.
I cannot connect to the internet thru Ubuntu until I can setup and configure my DLink 200 Rev B usb modem. The tar file is required to start this process - I am following the instructions in this link:
[http://users.tpg.com.au/johnd/dsl200.html](http://users.tpg.com.au/johnd/dsl200.html)
which is however written for a Fedora distrib. and assumes internet access already available.
By downloading the file in Windows, my intention is/was to access it and untar it instead of 'sucking it down through the CVS repository'.

However, when I issue the tar command:
tar -xvzf /...../"050908 eciadsl-usermode-cvs.tar.gz"
I get this report:
```

gzip: stdin: not in gzip format
tar: child returned status 1
tar: Error exit delayed from previous errors

```

Would this be because I have downloaded/saved the file in Windows? If so, how do I get the file, and the process, operating?

Many thanks

BTW I am using Breezy.

---

### Post by adwait on 2005-10-02
This coulnd't possibly be because you downloaded it in windows, the file seems to be corrupted.......try downloading again....

Also, maybe its not a gz file, anyway, try opening it in the GUI using nautilus......

---

### Post by happychap on 2005-10-02
Thanks, Adwait, for these suggestions.

I've tried them both, but with the same result - no go - same message.

As i've just posted in another thread, I tend to think that I may have some problems in the bootup of Ubuntu - there are 4 processes that come up with 'failed'  in the bootup sequence. They're very hard for me to read, as they scroll through quite quickly, and my screen is quite dark. Looks like I may have to persist though, to find out exactly what they are.

Again, thanks for your help.

---

### Post by happychap on 2005-10-05
Yay,

I found the problem.
The problem is in the browsers. Mostly I use Opera; then tried downloading with Firefox, and finally used Internet Explorer. (all using MS as the OS).

For some reason or other, only IE downloaded the file correctly, retaining the gz format and size. With both the other browsers, the downloaded file had a size of ca. 1200 Kb, instead of its real size - ca. 200 Kb., but still showed the file as being in gz format.

Looks like I will have to stop bad-mouthing IE (but only until I get Linux up and running!!) :p

---

### Post by doclivingston on 2005-10-05
My guess is that (for some reason) the other browsers were gunzipping the file before saving it, so it was really a tar file. One useful tool in these situations is the "file" command.
```
file *filename*
``` will report what kind of file it really is.

---

