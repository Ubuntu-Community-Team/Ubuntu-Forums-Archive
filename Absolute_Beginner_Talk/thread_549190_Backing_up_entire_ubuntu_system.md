---
title: "Backing up entire ubuntu system"
date: 2007-09-12
forum: Absolute Beginner Talk
---

### Post by tech9 on 2007-09-12
Hi All....

I have read through the other posts regarding this and decided to try partimage. The problem I get is partimage wants me to unmount /dev/sda1

when I run the umount command... I get errors regarding fstab.
So, the next step I took was to research that on this site. I found that other posts stated to comment out #, the UID under /ect/fstab...
When I did this and ran a umount, the terminal responded as /dev/sda1 is busy:confused:

I am trying to figure out why I cannot unmount the device...

Also, does anyone have any recomendations on free GUI linux backup utilities that are good?

Any help would be appreciated!

Thanks,

T9

---

### Post by ukripper on 2007-09-12
I would rather use Clonezilla.

[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

---

### Post by asmoore82 on 2007-09-12
> **ukripper said:**
> I would rather use Clonezilla.

[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

seconded.

---

### Post by tech9 on 2007-09-12
> **ukripper said:**
> I would rather use Clonezilla.

[http://clonezilla.sourceforge.net/](http://clonezilla.sourceforge.net/)

Thanks, I will check it out.

---

### Post by tech9 on 2007-09-12
> **asmoore82 said:**
> seconded.

Is there a sudo apt-get install command for this in ubuntu?

I don't see any source links to download deb or tar files from the site

---

### Post by tech9 on 2007-09-12
> **tech9 said:**
> Is there a sudo apt-get install command for this in ubuntu?

I don't see any source links to download deb or tar files from the site

nevermind... I found it

it feels like a Monday even though it's Wednesday::wink:

---

### Post by jryprt on 2007-09-12
on the left side it says Download click it

---

### Post by tech9 on 2007-09-12
> **asmoore82 said:**
> seconded.

Thanks to both ukripper and asmoore82!

Take Care,

T9

---

### Post by hyper_ch on 2007-09-12
May I ask why you want to make images and not just backup the files?

---

### Post by CaptainInsaneO on 2007-09-12
Personally, I would rather make an image instead of just backing up files because I spend a lot of time customizing things like compiz fusion and themes and default apps that I don't want to have to do it every time I re-install the greatest operating system in the world.

---

### Post by tech9 on 2007-09-12
> **CaptainInsaneO said:**
> Personally, I would rather make an image instead of just backing up files because I spend a lot of time customizing things like compiz fusion and themes and default apps that I don't want to have to do it every time I re-install the greatest operating system in the world.

CaptainInsaneO pretty much explained it. I have so many customization that I made to the system... It's just faster and easier

---

### Post by hyper_ch on 2007-09-12
not really, all you need to do is save the config files also which are mostly in your /home/USER folder... with rsync and hardlinks I make just every 6h a backup dating back for 90 days...

---

### Post by glupee on 2007-09-12
I love you guys :cry: i've been looking for this.
Now i can tweak to my hearts content!
Thanks.

---

### Post by tech9 on 2007-09-12
> **tech9 said:**
> CaptainInsaneO pretty much explained it. I have so many customization that I made to the system... It's just faster and easier

when you run your commands are you backing it up to a network share, because that's what I am doing. It seems redundant to me to back it up to the local drive and then move it from there.

---

### Post by tech9 on 2007-09-12
> **hyper_ch said:**
> not really, all you need to do is save the config files also which are mostly in your /home/USER folder... with rsync and hardlinks I make just every 6h a backup dating back for 90 days...

when you run your commands are you backing it up to a network share, because that's what I am doing. It seems redundant to me to back it up to the local drive and then move it from there.

---

### Post by hyper_ch on 2007-09-13
well, I backup every 6h to another machine in my lan and once a day to a remote computer at my parents' home. With rSync you can do directly remote synching... for backing up to my parents' home I use rSync over SSH.

---

### Post by ukripper on 2007-09-13
I save energy and my electric bill by creating an image after every 1 month and taking daily local backup of home drive to disk once a week. I tend to keep my lan environment friendly when i am not using 'em I switch other machines off.

---

### Post by tech9 on 2007-09-13
> **ukripper said:**
> I save energy and my electric bill by creating an image after every 1 month and taking daily local backup of home drive to disk once a week. I tend to keep my lan environment friendly when i am not using 'em I switch other machines off.

Good way to save energy ukripper:)

---

### Post by afilonov on 2007-09-13
You can use Mondo. If on Feisty, get fresh packages from Mondo home page. It can create bootable CDs.

Mondo home page: [http://www.mondorescue.org/](http://www.mondorescue.org/)

Look up this thread for more info on Mondo: [http://ubuntuforums.org/showthread.php?t=430866](http://ubuntuforums.org/showthread.php?t=430866)

---

### Post by tech9 on 2007-09-13
> **afilonov said:**
> You can use Mondo. If on Feisty, get fresh packages from Mondo home page. It can create bootable CDs.

Mondo home page: [http://www.mondorescue.org/](http://www.mondorescue.org/)

Look up this thread for more info on Mondo: [http://ubuntuforums.org/showthread.php?t=430866](http://ubuntuforums.org/showthread.php?t=430866)


Thanks afilonov, I'll check it out...

---

### Post by ukripper on 2007-09-13
> **tech9 said:**
> Good way to save energy ukripper:)

Cheers m8..let us know how you getting on with clonezilla.

---

### Post by tech9 on 2007-09-13
> **ukripper said:**
> Cheers m8..let us know how you getting on with clonezilla.

Hi ukripper,

    I am not having any luck with backing up through clonezilla. I have tried several methods...

SSH
Samba
and local dev

when using samba I put in my network credentials, but it keeps telling me that me " /home/partimag is not a mounting point", but no where do I specifiy that is the mounting point.

When I try to save my image to the local dev, I get "no unmounted disks are found".

Could you please tell me your method of backing up?

Thanks!

T9

---

### Post by CaptainInsaneO on 2007-09-13
Right now I'm testing out sbackup on my machine at home (at work right now, as usual) to see if it suits my needs. You could try looking into it, I think it's in the repo's. (Came pre-installed on my Ubuntu Ultimate so I'm not sure).

---

### Post by tech9 on 2007-09-13
> **CaptainInsaneO said:**
> Right now I'm testing out sbackup on my machine at home (at work right now, as usual) to see if it suits my needs. You could try looking into it, I think it's in the repo's. (Came pre-installed on my Ubuntu Ultimate so I'm not sure).

I have tried SBackup, but I was looking for a quick and dirty way to backup

---

### Post by CaptainInsaneO on 2007-09-13
> **tech9 said:**
> I was looking for a quick and dirty way to backup

The connotations of this line are staggering. :lolflag:

---

### Post by tech9 on 2007-09-13
> **CaptainInsaneO said:**
> The connotations of this line are staggering. :lolflag:

I know, know ... linux is always more command line driven, which I have no problem with. Well, at least ubuntu is more stable that any windows products :)

---

### Post by CaptainInsaneO on 2007-09-13
Have you given Partimage a go?

---

### Post by tech9 on 2007-09-13
> **CaptainInsaneO said:**
> Have you given Partimage a go?


I have but, it looks like "tar" is my best bet for now...

until I can figure out clonezilla

Thanks for the suggestions though!

---

