---
title: "[SOLVED] How Long to Wipe a 250Gb Drive ?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2007-06-07
Anyone any idea how long it will take to wipe a 250 Gb external HDD using the command:

```
sudo dd if=/dev/urandom of=/dev/sdb
```

Last time I tried it ran for four days, then looked as if it had hung.

I had to do a hard reset, which messed up my FF installation.

Thanks in advance.

---

### Post by netwerx on 2007-06-07
Thats way to long, i would get that hard drive tested with a manufacturer diagnostic software.

---

### Post by WorldTripping on 2007-06-07
Hmmm..

Cheers for the reply.

It's a brand new drive butI'll have a look around for a diagnostic tool.

Thanks.

---

### Post by mozetti on 2007-06-07
Why are you using dd to wipe it? Won't fdisk or gparted work?

---

### Post by HereInOz on 2007-06-07
How about Darik's Boot & Nuke, for a total wipe.

---

### Post by WorldTripping on 2007-06-07
I'm intending on having the whole partition encrypted.

According to this thread (and a few others):

*[http://ubuntuforums.org/showthread.php?t=420182]("http://ubuntuforums.org/showthread.php?t=420182")*

> Re: [HOWTO] Encrypt whole Feisty installation without reinstalling 

--------------------------------------------------------------------------------

I think you should replace "dd if=/dev/zero of=/dev/sdaX" with "dd if=/dev/urandom of=/dev/sdaX"

because I noticed a potential security flaw in your implementation. 

If someone has physical access to the hardrive, they can do a bit dump of the encrypted partitions to determine where the data is physically located. (It might not help them now, but it will make it easier for them later.)

That is why it is better to write the partitions with "if=/dev/urandom" instead of "if=/dev/zero".

I'm planning on then encrypting it using LUKS.

(Hence my post yesterday, where I was going through this, and had to hard-reset my Ubuntu, and ended up with fsck stalling at boot problems.)

That problem still exists.

I'm booting from the live CD

I'm going to encrypt the external HDD.

Move the data from the Ubuntu stalling laptop to the encrypted external HDD.

Then re-install Ubuntu FF (encrypting as we go).

Hope that is an understandable explanation / reason.

---

### Post by WorldTripping on 2007-06-07
> **HereInOz said:**
> How about Darik's Boot & Nuke, for a total wipe.

Ooh..that looks good, I'll have to check out whether it'll work on an external drive, or just a bootable one.

Cheers for the link.

;)

---

### Post by bodycoach2 on 2007-06-07
> **HereInOz said:**
> How about Darik's Boot & Nuke, for a total wipe.

I second the use of DBAN (Dariks Boot & Nuke). We're working to create a Free Geek of Central Florida, and we use dban to wipe drives on a daily bases. With dban, a 250 GB drive will take 2 hours, maybe 3 if the drive is a 5400rpm.

We've actually created a specific dban machine. We use the floppy drive, and can wipe 4 drives at once. Got the idea from Free Geek Vancouver.

---

### Post by WorldTripping on 2007-06-07
@ HereInOz
@ bodycoach2

Thanks for the tip.

I've just downloaded it, and am busily reading how to use it.

Cheers.

---

### Post by samuriCat on 2007-06-07
> **WorldTripping said:**
> I'm intending on having the whole partition encrypted.

According to this thread (and a few others):

*[http://ubuntuforums.org/showthread.php?t=420182]("http://ubuntuforums.org/showthread.php?t=420182")*



I'm planning on then encrypting it using LUKS.

(Hence my post yesterday, where I was going through this, and had to hard-reset my Ubuntu, and ended up with fsck stalling at boot problems.)

That problem still exists.

I'm booting from the live CD

I'm going to encrypt the external HDD.

Move the data from the Ubuntu stalling laptop to the encrypted external HDD.

Then re-install Ubuntu FF (encrypting as we go).

Hope that is an understandable explanation / reason.

Sorry to double-post this question, but why would this kind of encryption be necessary?

---

### Post by WorldTripping on 2007-06-07
Essentially I want encrypted data as I am security conscious.

Some of the client data on my laptop is sensitive.

My data on my laptop is sensitive (passwords, bank account details etc.

I want an encryped filesystem to provide another level of annoyance in case it ever goes missing.

A couple of other opinions..

From *[http://luks.endorphin.org/about]("http://luks.endorphin.org/about")*

> LUKS is the upcoming standard for Linux hard disk encryption. By providing a standard on-disk-format, it does not only facilitate compatibility among distributions, but also provide secure management of multiple user passwords. In contrast to existing solution, LUKS stores all setup necessary setup information in the partition header, enabling the user to transport or migrate his data seamlessly.

From *[http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS]("http://www.saout.de/tikiwiki/tiki-index.php?page=EncryptedDeviceUsingLUKS")*

> In simple terms, it's better encryption, but more importantly to the end user, it allows you to change the password for your disk, without requiring a very slow re-encode of the whole disk. You also have the option of having several different passwords for the same data.


From *[http://www.teaparty.net/technotes/crypto-fs.html]("http://www.teaparty.net/technotes/crypto-fs.html")*

> It's occurred to me before that I should have an encrypted file system on my laptop. I often leave it lying around at client sites, or I might leave it on the train, or something. Hell, even Her Majesty's spies occasionally lose laptops. Yes, mine is configured so that the screensaver will be running when it's resuscitated. But if blackhats rebooted it, or even worse, removed the HDD and plugged it into another device, my home directory would be exposed to the world. 

Cheers.

---

### Post by samuriCat on 2007-06-07
> **WorldTripping said:**
> Essentially I want encrypted data as I am security conscious.

Some of the client data on my laptop is sensitive.

My data on my laptop is sensitive (passwords, bank account details etc.

I want an encryped filesystem to provide another level of annoyance in case it ever goes missing.

...(snip)

Cheers.

Oh, I see. Is this something everyone should do? For example, while I never keep my online banking passwords in an electronic file (a notebook is just fine), could it still be pulled out through, for example, an open port or something? Say I'm using a torrent, for example--am I still vulnerable?

Thanks for you expertise, btw

---

### Post by WorldTripping on 2007-06-07
This type of encryption is to provide a level of security against someone gaining *physical* access to your data.

e.g. If a laptop or external HDD is stolen etc.
(Or in your case, if someone stole your notebook.)

i.e. the data will be physically unaccessable until the correct password has been supplied to unlock it.

Internet security, i.e. securing your data over a network is a completely different kettle of fish.

For someone to gain access to your data over the Net, your machine would either; have to be compromised, with a virus, keylogger etc.; or  someone would have to have access to your network (username and password).

As far as I know Ubuntu has a good track record of not catching viruses.

So as long as you keep your network secure you should be OK.

BTW: I'm no network genius, so you might like to ask someone else.

---

### Post by Sencer on 2007-06-08
> **WorldTripping said:**
> Anyone any idea how long it will take to wipe a 250 Gb external HDD using the command:

```
sudo dd if=/dev/urandom of=/dev/sdb
```

Open another terminal window and type sudo pkill -USR1 dd. This will send a USR1-signal to the dd process which will make it dump the currently written amount of data and the current speed to the prompt on the window where that command was running.

urandom is relatively fast compared to real random, but it is painfully slow comapred to /dev/zero. On my notebok I get a speed of 19MB/s (zero) and 3 MB (urandom). THe former is limited by the write speed of your hdd, the latter by the cpu-power (it gets slower, when I "speedstep" the cpu).

An alternative might be to use (from the dm-crypt wiki):
```
/sbin/badblocks -c 10240 -svw -t random /dev/sdb
```

This will also use a pseudorandm pattern and it may or may not be faster, I haven't tried it (but from what I hear it is supposed to be faster, and also limited by hdd-write speed rather than cpu).

---

