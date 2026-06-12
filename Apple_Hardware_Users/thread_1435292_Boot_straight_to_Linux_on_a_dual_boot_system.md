---
title: "Boot straight to Linux on a dual boot system"
date: 2010-03-21
forum: Apple Hardware Users
---

### Post by migel_wimtore on 2010-03-21
Hi. I would like my system to boot straight into Linux, as i very rarely use my OSX partition and can just hold down option on the rare occasions i do boot into it. 
Iv managed to reduce the time lapse until yaboot defaults into booting Linux, but i would like it so that the yaboot screen doesnt even come up at all

Is this possible?

---

### Post by tyre_ on 2010-03-21
I'm definitely not an expert, but you could try deleting yaboot and then in Mac OSX go to utilities>startup disk and set it to boot to Linux.  Might work.

---

### Post by linuxopjemac on 2010-03-21
forget the last option...This won't work for sure.

In yaboot.conf you might want to play with the following:
> 
Use Set delay= (in seconds) to determine how long the multiboot OS menu should wait before booting the default OS. timeout= (in tenths of seconds) to set how long yaboot should wait at the boot: prompt for you to choose a kernel image before booting the first image in the file or the default= image. 

To have no yaboot menu at all, is impossible I think.

---

### Post by migel_wimtore on 2010-03-21
Deleting yaboot (as far as i know) would leave me unable to boot into Linux. And also, in my experience, OSX Disk Utility wont display a Linux partition as a possible startup disk.

Thanks (as ever) to linuxopjemac. Though i had already played with the timeout variable. I didnt have a delay option, and though i created it and set it to 0 it didnt seem to make a difference, as for me the timeout option determined both stages. 
Yet, the yaboot dialogues still pop up, albeit not for long, and i was hoping to find a way to set yaboot to default instantly into Linux. Just to make the boot time a fraction quicker and somewhat tidier. 
But, as there doesnt seem to be simple solution (CORRECT ME IF IM WRONG) i suppose its not that important.

Thanks anyway guys.

---

### Post by oswaldkelso on 2010-03-22
Just edit if needed and re-bless yaboot. If an osx update broke the boot order zap the pram and it will reset it. Search for "ybin -v and holy penguin pee" and you'll find lots of info

[http://ubuntuforums.org/showthread.php?t=480972&](http://ubuntuforums.org/showthread.php?t=480972&)

---

### Post by migel_wimtore on 2010-03-24
Yeh, iv blessed the boot partition with holy penguin pee and all that, but the menus still pop up on the screen for an instant, when iv set timeout and delay to zero. 

I was wondering if there was a way to instruct yaboot to default load Linux and not even run the yaboot boot menu at all. So the laptop would boot straight to the ubuntu splash, as in single boot. 
I dont like that the disk "spins-up" (you know, when it sounds like it might take of momentarily) for yaboot and then spins-up again for ubuntu, my computers old man, i dont want to wear her out any more than is necessary.

Cheers though.

---

### Post by oswaldkelso on 2010-03-24
> **migel_wimtore said:**
> 

I was wondering if there was a way to instruct yaboot to default load Linux and not even run the yaboot boot menu at all. 

Cheers though.
No. I don't think there is. You can skip OSX by removing it from the yaboot menu. Then start OSX with the ALT/OPT key. But yaboot is a hack into the apple boot. I don't think you can remove it, just speed it up.

---

### Post by migel_wimtore on 2010-03-24
Right. Cheers for the info. Im scared of deleting osx  from the yaboot.conf, as i had tried such things (perhaps even that) in the past and got totally locked out of linux on a number of occasions. It was nano to the rescue. 

Are you saying just delete the last line of the following?:

boot=/dev/hda2
device=/pci@f4000000/ata-6@d/disk@0:
partition=3
root=/dev/hda3
timeout=5
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot
macosx=/dev/hda4 

Thanks.

---

### Post by linuxopjemac on 2010-03-25
after editing that file, you have to:
```
sudo ybin -v
```

otherwise these options won't work

---

