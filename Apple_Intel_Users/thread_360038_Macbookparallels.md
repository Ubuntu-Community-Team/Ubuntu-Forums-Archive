---
title: "Macbook/parallels"
date: 2007-02-12
forum: Apple Intel Users
---

### Post by kaahmfish on 2007-02-12
I'm thinking of installing ubuntu into my Macbook (running on Intel chips).

Is that possible?  Can it run on Parallels?

Thanks.  I'd really like to run linux!

---

### Post by Zuuswa on 2007-02-12
Yes, Linux will work on your macbook!  Although, I am not sure what you mean by 'Parallels' . . .

---

### Post by hajk on 2007-02-13
Yes, Linux runs very well in a Parallels for Mac VM on a MacBook. I find Parallels an ideal way of playing with various flavours of Linux -- right now I have Ubuntu Edgy, Ubuntu Feisty, Debian Etch and Debian Sid installed that way.  Make sure that you have 1GB or more RAM on your MacBook, so that you can allocate at least 512MB to a Parallels VM.

One hint that will save you some grief when booting Linux (any flavour) in a Parallels VM: blacklist the intel-agp kernel module in /etc/modprobe.d/blacklist.

Try Parallels, $$ well spent!

---

### Post by kaahmfish on 2007-02-13
uhm, which version should i use?  the mac one, or the windows one?

---

### Post by hajk on 2007-02-14
Parallels for Mac runs under OSX -- I would assume that this is what you need (you can even run Windows in it, but not the OEM versions that come with many computers like Dell). Parallels Work Station runs under Windows or under Linux, this is probably not what you need on a MacBook, although you could first install Windows or Linux on the MacBook (with Boot Camp, say) and then run Parallels Work Station in that... no, forget I even said that.

---

### Post by NewSpecter on 2007-02-22
> **hajk said:**
> 
Try Parallels, $$ well spent!
I'll second that anyway!! [Parallels Desktop]("http://www.parallels.com") is the great solution! Everything will work at almost native speed under Mac os! Get a trial version first and you'll see!

---

### Post by cbrain on 2007-02-25
I use Parallels and it works like a dream!

---

### Post by zugvogel on 2007-02-26
> **cbrain said:**
> I use Parallels and it works like a dream!

I agree. I set 256MB RAM on my macbook not-pro for ubuntu and it runs fine and quick. And I can suspend and resume the ubuntu emulation unlike I ever could when running ubuntu in the normal way, although this confuses ubuntu's internal clock somewhat... When running "idle" it takes about 15% cpu.

---

### Post by tylerdurden on 2007-02-27
i run edgy eft on 1970 and it works great... i find that if i do a gig of ram, ubuntu wont work... so i keep it limited to 768 (i have 2 gigs of ram on my macbook)... my screen stays black for a little when booting, but eventually the login screen displays...  overall a smooth install... very happy with the results... ask for blacklisting... i didnt blacklist any and it worked great...

---

### Post by bdalzell on 2007-03-28
I just put Ubuntu Edgie Linux into Parallels on a macbook pro. 

I just ran the Edgie Full install CD in Parallels. No problem. However if you are thinking of doing this you might want to leave a second linux partition in the Linux parallels install for experimentation with things. It looks like gparted can edit the partitions but of course not the one you are running from.l 

It is working pretty well. Anyone have an idea how to get it to recognize the USB thumb drive from within Parallels.

The mac recognizes the thumb drive but when i click the little icon in the lower right of the Parallels window to mount the thumb - it comes up checked but when I look in /media in Ubuntu  for the usb thumb it is not there. This thumb mounts properly on my Ubuntu linux Athlon as soon as I plug it in.

---

### Post by Chrisj303 on 2007-03-30
VMware fusion beta is shaping up to be a much better solution than parallels. Already they have released 'Tools for linux' - that allow seamless cursor 'focus' and native resolution.

Parallels don't really seem bothered with linux running on mac, and most people on the forums seem to have jumped ship. Parallels support is really crappy as well, they often don't even bother responding to PAID ($30) per request support.

chrisj303

---

