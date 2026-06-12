---
title: "Networking with two machines"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by john.burgin on 2007-05-28
I am at my wits end.

I am not a complete newbie to linux, and my computer knowledge is ok.

I have a reasonably decent Dell running Feisty in one room and connecting to a router via a wireless card (that was fun to set-up).

In another room I have an ancient computer running warty and connected to the same router via an ethernet cable.

I have installed samba and both computers are visible.

But Icannot get either of them to talk to one another, let-alone transfer files between them.

I cannot ftp or rlogin - connection is refused each time.

I may be missing something obvious, but can anyone please help?

Many thanks in advance,


John

---

### Post by ggaaron on 2007-05-28
Have you tried ssh?

sudo apt-get install ssh gftp

and transfer files via gftp

---

### Post by john.burgin on 2007-05-28
No, this doesn't work either.

I really am struggling to beleive how unbelievably difficult this is.  I haven't been using linux very long, and I decided to give it a try because I loathe Windows so much.  

I have removed Samba, because I heard that it relates largely to Windows machines, and now neither computer is visible to the other.  They will ping, but not file share AT ALL.

I have read through some tutorials on the web that describe file-sharing via NFS, and I cannot even do this.  Why must it be so God damned difficult to share files with these two machines?  They're both linux, I have an address for both, and I just don't get it.

So please, in fairly plain English, can someone describe;

1. why these two machines will not see one another
2. How to make each of them visible
3. Simply how to exchange files between them

I am not altogether sound in my knowledge of command line, though I am willing to learn.

Apologies for my annoyance, but I fear if I spend any longer trying to do such a simple god damned thing my girlfriend will probably walk out and leave me. ;-)

John

---

### Post by xpod on 2007-05-28
I had the same "plain English" problems as you when first trying to get my head round this stuff but this thread made nfs pretty simple to set up.
[http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto](http://ubuntuforums.org/showthread.php?t=249889&highlight=nfs+howto)

ssh`s really straightforward too mind you
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

the basics at least but nfs is better if it`s two *buntu`s your running i think.
Good luck.

---

### Post by arbulus on 2007-05-28
NFS is your best bet for 2 Ubuntu machines to talk to each other.   Here is a great howto on it:

[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

Samba is great if you're talking to Windows or OS X boxes, but NFS is best for Linux to Linux networking.

I understand your frustration.  I had the same kind of frustration when I first started trying to get my boxes to share directories.  After a bit of cussing and a day or so of just walking away from it, i was finally able to get it up and running well.  Don't give up.  Just take a breath, stay calm, and walk away from if for a little while if you have to.  Don't worry, you'll get it.

Hope this helps.

---

### Post by john.burgin on 2007-05-29
Thanks for all the help - everything is up and running.

Now, though, I have a server machine and a client machine.  Can I set them up so they are both server and client machines, i.e. so I can view files from either, by just using the same process again and mounting the client machine on my server machine?  If that makes sense.

Many Thanks,

John

---

### Post by xpod on 2007-05-29
Hi john,good stuff getting it going:D

I only understand the very basics of this stuff myself i`m afraid so although i reckon you could easily do as you wanted with both as server/client i`m not too sure if it`s a actually good idea or not.

If you have files you want shared between both machines then just make sure the files are in the mounted folder;)
I use ssh for actually "browsing" the other pc`s we have but then i`m only just figuring that out too.

---

