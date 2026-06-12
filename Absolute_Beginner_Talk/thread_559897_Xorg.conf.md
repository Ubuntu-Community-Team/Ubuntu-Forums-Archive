---
title: "Xorg.conf"
date: 2007-09-25
forum: Absolute Beginner Talk
---

### Post by aheicher on 2007-09-25
my xorg.conf file is screwed up, here's what is says:
/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw 0 0
um...help!!!!

---

### Post by CaptainInsaneO on 2007-09-25
Your post is very vague. What exactly do you want us to do to help you? Fix it? Write a new xorg.conf for you? Put a band-aid on it and kiss it?

What did you do before your xorg looked like this? Did you do a clean install and this is what it spit out? Are you sure that's a xorg.conf? Doesn't even look remotely close to one to me. Which would make you correct, that thing IS screwed up. :lolflag:

Basically, tell us what you were doing when this happened, how you figured out that it's screwed up, and we can go from there.

---

### Post by aheicher on 2007-09-25
i know, my bad-
when i start up i get no graphic logon
Windows XP, intel i8XX graphics card, dual boot with external HD, 80 GB
Ubuntu 7.0.4
i need it fixed so i can boot graphically, is there any way of doing that?

---

### Post by overdrank on 2007-09-25
> **aheicher said:**
> i know, my bad-
when i start up i get no graphic logon
Windows XP, intel i8XX graphics card, dual boot with external HD, 80 GB
Ubuntu 7.0.4
i need it fixed so i can boot graphically, is there any way of doing that?

Hi I can offer this 
Boot in Recovery Mode (select it from the GRUB menu)
type:


```
sudo dpkg-reconfigure xserver-xorg
```

select the "vesa" driver and press ENTER whenever you don't know the answer to a question.

then type:

```
reboot
```

and boot as usual
Hopefully this will get you to the desktop 

Good luck!

---

### Post by CaptainInsaneO on 2007-09-25
What overdrank is good advice. However, if you have an nVidia card, you could try using nv instead of vesa. I'd suggest what overdrank said.

---

### Post by RomeReactor on 2007-09-25
Hi. I would also recommend you do what overdrank said, but you might want to select the **intel** or **i810** driver.

---

### Post by overdrank on 2007-09-25
> **CaptainInsaneO said:**
> What overdrank is good advice. However, if you have an nVidia card, you could try using nv instead of vesa. I'd suggest what overdrank said.

I would agree Captain and it is a intel, I was just trying to get the op to the desktop.
And I  agree with RomeReactor

---

### Post by CaptainInsaneO on 2007-09-25
> **overdrank said:**
> I would agree Captain and it is a intel, I was just trying to get the op to the desktop.
And I  agree with RomeReactor

I understand completely... if you're just trying to get him to a desktop environment then the intel drivers would be a good choice. :popcorn:

I didn't see that he had posted it was an intel. My fault.

---

### Post by aheicher on 2007-09-25
thanks so much guys, go it

---

### Post by overdrank on 2007-09-25
> **aheicher said:**
> thanks so much guys, go it

8-[\\:D/

---

### Post by andrew.46 on 2007-09-29
Hi,

Saw your discussion:

> **RomeReactor said:**
> Hi. I would also recommend you do what overdrank said, but you might want to select the **intel** or **i810** driver.

 Just to move a little sideways of this discussion: I have an 82865G Integrated Graphics Controller and I have noticed that the i810 driver produces significantly better results than the intel driver. This is with Gutsy Gibbon beta.

 Is this a common finding?

             Andrew

---

### Post by overdrank on 2007-09-29
> **andrew.46 said:**
> Hi,

Saw your discussion:



 Just to move a little sideways of this discussion: I have an 82865G Integrated Graphics Controller and I have noticed that the i810 driver produces significantly better results than the intel driver. This is with Gutsy Gibbon beta.

 Is this a common finding?

             Andrew

I don't know if it is a common thing since gusty has not reach its final release. :guitar:

---

### Post by andrew.46 on 2007-09-29
Hi,

 Thanks for your response:

> **overdrank said:**
> I don't know if it is a common thing since gusty has not reach its final release. :guitar:

 I am currently beating myself around the head for the stuoidity of my question. I guess the beta has only been out for 3 days now :-) Doh!!!

             Andrew

---

### Post by overdrank on 2007-09-29
> **andrew.46 said:**
> Hi,

 Thanks for your response:



 I am currently beating myself around the head for the stuoidity of my question. I guess the beta has only been out for 3 days now :-) Doh!!!

             Andrew

Hi and I will post as before
 please ask Gusty question here you will get better support
[http://ubuntuforums.org/forumdisplay.php?f=238](http://ubuntuforums.org/forumdisplay.php?f=238)

---

