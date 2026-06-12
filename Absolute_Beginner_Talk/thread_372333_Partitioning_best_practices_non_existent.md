---
title: "Partitioning best practices non existent ?"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by GeertPoels on 2007-02-28
Hi all,

I'm looking for documentation describing advice on how to partition my drive.
Which are the major partitions and their recommended size.
Actually, I found no info on this issue. 
Not in the docs, not on the Wikis.

I remember how this was a major topic in old Linux installations.
For reasons of security and logical separation of files, it still seems useful to me.

Did I overlook something or is this indeed not really detailed ?

Thanks,

Geert

---

### Post by xyz on 2007-02-28
Try these:
[GParted]("http://gparted.sourceforge.net/")
[Psychocats]("http://www.psychocats.net/ubuntu/index.php")
[Hermanzone]("http://users.bigpond.net.au/hermanzone/")
You should be able to find out all you need there. Come back for questions if need be!

---

### Post by GeertPoels on 2007-02-28
I looked at all three and a lot of information will come in handy.
Yet, it's not really what I'm looking for.

In 'old times', it was recommended to have separate /tmp /usr /home (even /boot) partitions.
These kind of schemes seems to have completely vanished (maybe because of today's very big HD).
Yet, I find it usefull to have a separate tmp (cannot flood you HD endlessly, you can reformat it, ...) for example.

I'm looking for something like :
[http://pw1.netcom.com/~kmself/Linux/FAQs/partition.html](http://pw1.netcom.com/~kmself/Linux/FAQs/partition.html)
[http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html](http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html)

What are todays size requirements for Ubuntu ?

Is it fe. useful to have multiple swap partitions with todays kernel and fast hardware ?

---

### Post by kidders on 2007-02-28
**Edit:** Sorry... posted this too late.

Hi there,

> **GeertPoels said:**
> Which are the major partitions and their recommended size.It's difficult to make suggestions like that *for* a person ... partitioning decisions are very individual choices.

> **GeertPoels said:**
> I remember how this was a major topic in old Linux installations.I imagine that most Ubuntu users probably throw their entire system onto one filesystem. If you're a long-time Linux user, it would probably be quite difficult to make yourself do that though!

Is your box a general purpose one, or have you specific intentions for it?

As you rightly mentioned, security & logical housekeeping are two good reasons for spreading Linux over multiple partitions. Others include the ability to use more than one filesystem type/configuration on the same OS, selective encryption of certain parts of the OS, dealing with various failure scenarios, sharing files between multiple OSs, persisting data easily between re-installations, and so on.

---

### Post by Tomosaur on 2007-02-28
Well, it's true that you don't 'need' these partitions. Most people follow this scheme:
One partitiion for /
One partition for swap

Some people like to keep their /home dir on a seperate partition, but the only real requirement is a partition for / and a swap partition. Anything more than that is entirely up to preference. The swap partition is generally given twice the RAM available, but that is advice from a while back when there was only little RAM. The maximum you would probably need now is 512mb, but again, it depends on your preference and how you use your machine. If you're going to be using very intensive apps, you may want to extend your swap further.

So to conclude, yes you can have a seperate /tmp partition, and so and so forth, but it's not required unless you prefer it. It won't hurt to have seperate partitions, it's just more work.

---

### Post by xyz on 2007-02-28
[Create a separate /home partition in Ubuntu]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by kidders on 2007-02-28
> **GeertPoels said:**
> In 'old times', it was recommended to have separate /tmp /usr /home (even /boot) partitions.

[LIST]
[*]Personally, I routinely use separate /home partitions ... it just seems "wrong" not to. I tend to be less inclined to separate out /usr though -- it's not something I find practically beneficial.
[*]Separating /boot has, in my opinion, no advantage other than the safety factor. I'm sure you're already familiar with this idea, but by specifying the "noauto" mount option in /etc/fstab, it becomes more difficult to accidentally cause your system to fail to boot. In highly optimisable distros like Gentoo (which I use quite a bit), you would factor in filesystem support issues. For instance, you might format /boot using a filesystem built directly into your kernel, compiling support for others as modules. Ubuntu's design makes distinctions like these fairly irrelevant though.
[*]Quite often, users mount /tmp into RAM, rather than using an actual physical partition, both for performance reasons, and so /tmp doesn't persist between boots. Of course, that would be totally inappropriate for a traditional Linux user, who would be reluctant to reboot his PC any more than twice a year!
[/LIST]

> **GeertPoels said:**
> These kind of schemes seems to have completely vanished (maybe because of today's very big HD).One other reason is that, now that Linux is becoming more mainstream, certain subtleties in system configuration have gone by the wayside.

> **GeertPoels said:**
> Is it fe. useful to have multiple swap partitions with todays kernel and fast hardware ?This is something I would only do on a server box, or on a desktop box with more than one physical disk. I will tend to try to make optimal use of all the hard disks I have, in the belief that encouraging a certain amount of parallel accessing is beneficial, which tends to entail splitting my swap in two.

On server boxes, I have developed a habit of allocating far more swap than necessary, and lowering the priority of some of it, so it's only used in situations where it's really needed. I took this up a few years ago, after a mail server of mine (that I had misconfigured) was subjected to an attack that ate up all my memory, causing Linux to start terminating processes to recover enough RAM to handle all the mail.


I hope you'll excuse all the personal opinion, but I guess my point is that there is still an advantage to be gained by thinking carefully about your partitioning scheme. Having said that, many modern users don't even realise they have the option, and live quite happily with a single partition (even embedding swap in the root filesystem!).

---

### Post by GeertPoels on 2007-02-28
Thanks for the useful suggestions.

I indeed notice a lot of people just define / and swap.
Ought this not to be advised by the installer ?

---

### Post by kpm on 2007-08-30
I have been poking around for too long now looking for a 'best practices' for a LAMP server install.  The canned and claimed 15 minute Ubuntu LAMP server install sounds grand, but, I have been in a Windows world for too long, and when I get to the partitioning questions in the installer, I am stuck.  Sure I could select 'erase entire disk' and plop it all on, but that just seems wrong to me.  I have spent well over those 15 minutes simply trying to find that missing Ubuntu Linux partitioning guide.  I have two hard drives, an 80 gig and 160 gig.  I know on Windows I would separate the tmp and pagefile on one hard drive, install the MySQL data on a separate one, put all the applications on the smaller drive (or even create a smaller partition), and store all the data on the large hard drive, etc.  There are plenty of tutorials and info about installing Ubuntu, but really very little about how best to partition it.
Some claim that partitioning is a very 'personal thing' which is all fine and good, but really, can there be that many different configurations?  Should their not be an 'optimal' partitioning scheme for a run of the mill LAMP server at least?  I'd really love to read it if anyone knows of any links.  
Thanks

---

### Post by rsambuca on 2007-08-30
> **GeertPoels said:**
> Thanks for the useful suggestions.

I indeed notice a lot of people just define / and swap.
Ought this not to be advised by the installer ?

But there really is nothing wrong with this.  It will work fine for most people.

---

### Post by bodhi.zazen on 2007-08-30
> **GeertPoels said:**
> Hi all,

I'm looking for documentation describing advice on how to partition my drive.
Which are the major partitions and their recommended size.
Actually, I found no info on this issue. 
Not in the docs, not on the Wikis.

I remember how this was a major topic in old Linux installations.
For reasons of security and logical separation of files, it still seems useful to me.

Did I overlook something or is this indeed not really detailed ?

Thanks,

Geert

Go for it dude :

See this as a primer to more advanced partitioning: [Linux Partitioning Guide](http://www.overclock.net/linux-unix-mac/11208-linux-partitioning-guide.html).

For a more detailed, "short" review see also: [A Short Guide to Partitioning a Hard Drive for a Linux System](http://www.linuxquestions.org/linux/answers/Hardware/A_Short_Guide_to_Partitioning_a_Hard_Drive_for_a_Linux_System)

You might also like LVM : [http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html](http://www.linuxdevcenter.com/pub/a/linux/2006/04/27/managing-disk-space-with-lvm.html)

---

