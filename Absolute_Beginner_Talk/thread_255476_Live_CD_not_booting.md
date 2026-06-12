---
title: "Live CD not booting"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by df` on 2006-09-11
Hi, I'm a lifelong Windows user looking to move on, unfortunately my first attempt has been met with frustrating failure ](*,) 

I downloaded the Ubuntu 6.06.1 desktop iso for AMD64. I burned it and it gave me the menu, from which I opted to load the OS from the CD. Everything seemed to load okay but after the loading screen disappeared the screen stayed black, and the monitor reported signal lost. After a few minutes of waiting the only option was to hard reset and come crawling back to Windows.

I've tried a few things. I tried the VGA connector on my video card (which is a Radeon X800 Pro) instead of the usual DVI, and I checked the md5sum which matches the one from the download page. The CD-R I used is a little scratched (unfortunately the only blank one I have at the moment) but the CD checker from the boot menu checked out fine, so I doubt that's a problem.

I searched for this and found a few long since buried topics of a similar nature, but I thought I'd make a new topic to see if anyone had any new insights.

My system is an Athlon 64 3500+ on a MSI K8N Neo2 Platinum with 1GB of DDR and the video card mentioned above. More detailed specs can be provided if needed.

---

### Post by meng on 2006-09-11
If you don't have any spare CD-R's then your options are limited. Otherwise I'd advise downloading and burning the "alternate" ISO.

---

### Post by Najand on 2006-09-11
What about when you push ALT+CTRL+F1 after your monitor reports signal lost?

---

### Post by BillA1016 on 2006-09-11
I'm having almost an identical problem booting from a LiveCD on my iMac G3.

---

### Post by Najand on 2006-09-11
Hmm, Does Dapper support Old World PPC Architecture?

---

### Post by BillA1016 on 2006-09-11
The CD-ROM says that it will work on computers with a G3 processor, which is what I have. I have 6GB Hard drive, 333MHz processor, 128MB memory, slot loading CD/DVD-ROM drive, if that makes a difference.

---

### Post by Metacarpal on 2006-09-11
EDIT: my entire post was pointless, missed the line in the initial post where the MD5sum checked out okay...

---

### Post by BillA1016 on 2006-09-11
I didn't download anything- I got the CD that they mail out to you. Someone on another message board said on his iMac G3, he had to enter a command in the beginning to make it work or an identical problem happened. Do you have any suggestions for what this command may be? He said he'd get back to me but hasn't yet. Thanks.

---

### Post by Metacarpal on 2006-09-11
> **BillA1016 said:**
> I didn't download anything- I got the CD that they mail out to you. Someone on another message board said on his iMac G3, he had to enter a command in the beginning to make it work or an identical problem happened. Do you have any suggestions for what this command may be? He said he'd get back to me but hasn't yet. Thanks.

Hi Bill.  I was actually responding to the original poster, df.  I thought I should respond to his problem, which is why I quoted his post.

---

### Post by BillA1016 on 2006-09-11
Oh sorry- I didn't even look at the quote. Still, any suggestions anyone??

---

### Post by Metacarpal on 2006-09-11
Hi again Bill.  Did some forum searching and discovered that the initial release of 6.06 had some installer problems with a small selection of Macs, and it sounds like yours is one.

Your best bet, if you have the capability, is to [download]("http://www.ubuntu.com/download") an installation CD.  The updated version currently available (6.06.1) has fixed this problem for the installer and should work for you.

If you need assistance burning the iso file to CD, [see this howto]("http://www.psychocats.net/ubuntu/maciso").

---

### Post by BillA1016 on 2006-09-11
Thank you. I'll go bum a CD-R off of someone and do it :)

---

### Post by df` on 2006-09-11
> **Najand said:**
> What about when you push ALT+CTRL+F1 after your monitor reports signal lost?

It worked! After I hit ALT+CTRL+F1 the signal came back, and I got a command prompt.

Unfortunately, at that point I wasn't sure what to do next. I only know a few basic linux commands...any help will be greatly appreciated!

---

### Post by df` on 2006-09-13
Shameless bump.

---

### Post by Borfo on 2007-01-26
For the record, I just tried to install the 64 bit version of Edgy on an athlon 64 4000+ on a K8N Neo2 platinum and the livecd hangs right after the "booting the kernel" message comes up.

I had no problems with the 32 bit version at all, maybe it's something to do with the board.


(I'm quite happy going back to the 32 bit version for now anyhow...  I just thought I'd give the 64 bit version a try.  I'll give 64bit a shot sometime on a future release once it's matured a bit.)

---

### Post by Pobega on 2007-01-26
> **Borfo said:**
> For the record, I just tried to install the 64 bit version of Edgy on an athlon 64 4000+ on a K8N Neo2 platinum and the livecd hangs right after the "booting the kernel" message comes up.

I had no problems with the 32 bit version at all, maybe it's something to do with the board.


(I'm quite happy going back to the 32 bit version for now anyhow...  I just thought I'd give the 64 bit version a try.  I'll give 64bit a shot sometime on a future release once it's matured a bit.)

The 32 bit versions are much more stable than the 64 bits on virtually every platform now, although I'm not sure how Vista's handling 64bit currently.

Also, you *are* aware this is a 5 month old topic, right? :P

---

### Post by Borfo on 2007-01-26
> **Pobega said:**
> The 32 bit versions are much more stable than the 64 bits on virtually every platform now, although I'm not sure how Vista's handling 64bit currently.
I know, I thought I'd give it a shot though.  I'm not going to waste any time trying to get it to work though, I'm reinstalling 32 as we speak/type.

> Also, you *are* aware this is a 5 month old topic, right? :P

Yeah, but the OP has the same motherboard as I do and it looked like he was having the same problem as I had.  I just posted so there was a record of the problem occurring more than once on the forums for future users with the same board and the same problem.

---

