---
title: "encrypted roofilesystem"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by Explode2 on 2007-05-07
Hi everybody :)
I am using Kubuntu and I am an "little bit" expierenced ubuntu user (I also used this distro)
Now, I want to make an encrypted rootfilesystem(one of my 4 hda's), I found some Instructions with google but they have not worked...(or maybe I just dont get on it)
but anyway, have anybody got some manual for absolute beginners(like me)?
I searched the ubuntu forums but I havent found a manual either ....
I would be very happy If some had an manual for me :) 
(which is not so hard , but understandable ;)  )

greetings Explode2

---

### Post by quark_77 on 2007-05-10
Hi Explode2,

I think this is probably the best one I've come across: [http://ubuntuforums.org/showthread.php?t=420182](http://ubuntuforums.org/showthread.php?t=420182). The rest seem to be a little outdated/complex.

Hope this helps, be warned, it was a little complex!!

Just a quick note - on Feisty, if I plug in all my usb devices (having turned off the quiet option and splash option for kernel boot) the "Enter LUKS Passphrase" gets a little lost in all the kernel messages - if you wait for the kernel to finish then type your password and hit enter it works OK!

Quark_77

---

### Post by Explode2 on 2007-05-11
okay thanks a lot ;)
I will try this one now :)

Regards Explode2

---

### Post by hyper_ch on 2007-05-11
Wouldn't it be enough to just encrypt /home?

---

### Post by quark_77 on 2007-05-11
> **hyper_ch said:**
> Wouldn't it be enough to just encrypt /home?

Hi hyper_ch,

In theory yes, however, having a whole encrypted file system makes it more difficult for an attacker to insert keystroke loggers -- any LiveCD can mount XFS, Reiser, ext3, JFS and more... you'd only have to replace the cryptsetup modules from the LiveCD and wait for the entered password...

With whole-disk encryption, your only chance is to attack the ramdisk, or the kernel itself and logging keys from the tty at this stage would be much harder, albeit not impossible.

I run a laptop, so an encrypted hard disk is just another security feature aka stops it being read if stolen.

Finally, there's protection of data that might be stored in /var (although you could just encrypt this too).

It all depends on how paranoid you are!! I asked around before I bothered to make sure there'd be no noticeable impact on speed otherwise I might just have encrypted home too.

Any luck explode2?

Quark_77

---

### Post by hyper_ch on 2007-05-11
You could encrypt your swap also :)

---

### Post by Explode2 on 2007-05-23
Sorry Quark I was not around in the forum for a while.. :(
I tried it sereval times, I encrypted my harddisk ( I got one harddrive in my laptop) and I made some partiotion, now the encryption was successfully, but then I didnt get on that thing with grub...
I dont understand what in the turtorial they mean with the UID(I followed the instructions in the german turtorial)
and also Grub says to but hda(0.5) and not hda(0.0)...thats the problem where I am now,...I tried this for nearly 2 days but always it was not working, so anyway I decided , to make "first" now a piece of my harddrive encrypted with truecrypt...but I think this is not safety because of the swap partition, that one is unencrypted...But I want to completely have an encrypted system..but I dont get on that thing with grub thats the problem,... :(
When I am editing in the /etc/fstab the uid , this UID is also in the menu list from grub, but in the turtorial, there is no UID...so I am a little bit *confused*
But next week I got holidays, so maybe than I give it a try again ;)
But I would be very happy if anyone understand my question with grub what I meant(If you understand my question((I hope))) and would me explaining that ...thx for the postings :)

regards Explode2

---

