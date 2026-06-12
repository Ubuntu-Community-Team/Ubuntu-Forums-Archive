---
title: "DVD-R Burning - DVD Keeps Being Ejected"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-30
I am trying to copy 4 folders, each containing a video file to a DVD-R on Dapper using CD/DVD Creator.

After selecting the content, and choosing a volume name and writing speed and clicking 'Write'  it creates the image to be written, then as it is writing it ejects the DVD-R.

Are DVD-R's not supported?

Has anyone else experienced this behaviour?

Any other software I should be using?

Thanks.

p.s. this is the first time I try to burn a DVD in Ubuntu.

---

### Post by divague on 2006-11-30
why don't you try installing gnomebaker or k3b

---

### Post by deadgobby on 2006-11-30
> **PartisanEntity said:**
> I am trying to copy 4 folders, each containing a video file to a DVD-R on Dapper using CD/DVD Creator.

After selecting the content, and choosing a volume name and writing speed and clicking 'Write'  it creates the image to be written, then as it is writing it ejects the DVD-R.

Are DVD-R's not supported?

Has anyone else experienced this behaviour?

Any other software I should be using?

Thanks.

p.s. this is the first time I try to burn a DVD in Ubuntu.
What program are you using to copy or burn DVD's. Did you load up the CODECS?

---

### Post by wpshooter on 2006-11-30
> **divague said:**
> why don't you try installing gnomebaker or k3b

Install K3b.  Both CD/DVD creator and Gnomebaker are junk as far as I am concerned !!!

---

### Post by PartisanEntity on 2006-11-30
@ deadgobby: which CODECS ? I am using CD/DVD Creator (comes standard in Dapper).

@ wpshooter: It seems I already have K3B installed, ill give it a try.

---

### Post by deadgobby on 2006-11-30
To burn a DVD you need to install restricted formats. Perhaps install 
Automatix, Right now the server is down for that. So go to ubies Wiki 
[https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=restricted+formats&titlesearch=Titles](https://wiki.ubuntu.com/Home?action=fullsearch&context=180&value=restricted+formats&titlesearch=Titles)
Sorry to tell you that. But you most like need to install the format. Becuase even with K3B or GNOME Baker. You'll be stopped dead cold
Gobby

---

### Post by PartisanEntity on 2006-11-30
@ deadgobby: I have Automatix and I have already installed the codecs.

@ wpshooter: I just tried K3B, it worked, then after about 65% it ejected the DVD claiming success, when I pop the DVD back in, it is empty.

[IMG]http://i16.tinypic.com/29ckk6d.jpg[/IMG]

---

### Post by deadgobby on 2006-11-30
MMM did you try a program called DVD Rip?

---

### Post by PartisanEntity on 2006-12-01
Anyone know why I am having errors in K3B  & CD/DVD Creator?

---

### Post by PartisanEntity on 2006-12-01
I tried GnomeBaker, it started the writing process then ran into errors:

```
Executing 'mkisofs -gui -V GnomeBaker data disk -A GnomeBaker -p A -iso-level 3 -l -r -hide-rr-moved -J -joliet-long -graft-points --path-list /tmp/GnomeBaker-amr/gnomebaker-MqLBjS | builtin_dd of=/dev/hdc obs=32k seek=0'
INFO:	UTF-8 character encoding detected by locale settings.
	Assuming UTF-8 encoded filenames on source filesystem,
	use -input-charset to override.
/dev/hdc: "Current Write Speed" is 8.2x1385KBps.
:-( unable to WRITE@LBA=ee0h: Input/output error
:-( write failed: Input/output error
/dev/hdc: flushing cache
/dev/hdc: updating RMA
:-[ CLOSE TRACK failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
/dev/hdc: closing disc
:-[ CLOSE DISC failed with SK=5h/ASC=30h/ACQ=05h]: Wrong medium type
```

The DVD's I am trying to use are:

Brand: Platinum
DVD-R
8x

Is this the wrong kind of DVD to make a data DVD?

---

### Post by PartisanEntity on 2006-12-01
For anyone else having this problem here some of my experiences.

It seems the format DVD-R is not supported by Linux (or Ubuntu) burning software.

I tried CD/DVD Creator, K3B and GnomeBaker using DVD-R to make a data DVD, in all cases the writting session failed. The error messages were not very helpful for a newb, only GnomeBaker informed me that something wasn't right with the 'medium'.

So I went out and bought DVD+R and DVD+RW. 

I tested the DVD+R with K3B and it worked, I was able to make the data DVD without any errors.

CD/DVD Creator also worked using DVD+R.

It is safe to assume that GnomeBaker will also work with DVD+R.

I have not tested the DVD+RW yet.

**On a final note, if any experienced users know how to get DVD-R's to work with Ubuntu burning software please let me know, since DVD-R's are much cheaper than the other types** :)

---

