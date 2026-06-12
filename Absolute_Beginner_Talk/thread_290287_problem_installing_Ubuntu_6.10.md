---
title: "problem installing Ubuntu 6.10"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by ecoli0157h7 on 2006-11-01
hi there!

I am having problem installing 6.10 on my laptop. there is always an error appearing after choosing the install option. 

Here is how it goes:

"There was an error starting the GNOME Settings Daemon.

Some things, such as themes, sounds, or background settings may not work correctly.

The last error message was:

Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

GNOME will still try to restart the Settings Daemon next time you log in."

There is another error appearing: The panel encountered a problem while loading "OAFID:GNOME_Panel_WirelessApplet".

Furthermore, it takes forever for a thing to happen. 

What's the problem. Obviously, I'm just new in Ubuntu. 

Thanks a lot buddies out there.

---

### Post by pinoyskull on 2006-11-01
have you tried **searching** the forums?

i found a thread similar to this
[http://ubuntuforums.org/showthread.php?t=279186&highlight=There+was+an+error+starting+the+GNOME+Settings+Daemon](http://ubuntuforums.org/showthread.php?t=279186&highlight=There+was+an+error+starting+the+GNOME+Settings+Daemon)

---

### Post by ecoli0157h7 on 2006-11-01
Isn't because my laptop isn't compatible with ubuntu (or linux in general)? I'm using compaq nx4820. I've formatted my hd a lot of times and still got the same error everytime I tried to run live CD to install ubuntu 6.10. The liveCD mode is very slow.

---

### Post by EriktheUnready on 2006-11-01
hahaha, I had the same problem.
Try using a different cdrom drive. (you are somehow getting a cd read error)
It had me on the ropes too...
:-D

---

### Post by ecoli0157h7 on 2006-11-01
ok. i'll try. thank you very much. I can't wait to see my laptop on Ubuntu 6.10. I'm promoting OpenOffice as well!.

---

### Post by seshomaru samma on 2006-11-01
Did you try the solutions advised by pinoyskull?
Like using this command in the terminal:
```
sudo aptitude update && sudo aptitude install -f
```
or
```
sudo /etc/init.d/dbus restart
```

---

### Post by Abhi Kalyan on 2006-11-01
> **ecoli0157h7 said:**
> ok. i'll try. thank you very much. I can't wait to see my laptop on Ubuntu 6.10. I'm promoting OpenOffice as well!.

Great Job Buddy,
This problem could be because of
1. faulty CDROM Drive
2. faulty UBUNTU installation disc ( try installing in some other system)
3. Unsupported or unavailable driver for certain key hardware components. ( Though this is a near impossibility with ubuntu)
Keep Posting would love to look at the situation.
As for promoting Open office, We are involved in shifting and entire organization to UBUNTU and Open Office.
Do post the problems.

---

### Post by ecoli0157h7 on 2006-11-01
I hope the problem is on the CDROM itself. I do encounter errors while loading the liveCD. It somekind of strings of commands of loading errors. Errr. Couldn't understand them though.

---

### Post by ecoli0157h7 on 2006-11-01
I've read another tip. I should have tried burning the image in a much slower speed (about 8x). hmmm. let's see.

---

### Post by ecoli0157h7 on 2006-11-01
The errors keep on appearing. It might be an incompatibility. (Am I reporting here an incompatibility for Ubuntu 6.10). Anybody out there with Compaq nx4820 laptop who is experiencing the same glitches. I've tried almost everything (even accessing the terminal but failed to 'cause the terminal won't open as well) and compared the installation (using the same installer CD) on other units. It worked perfectly and lightning fast but not on my laptop. If I can only have the screenshot of the errors I would supply it here.

---

### Post by _duncan_ on 2006-11-01
this is a long shot, but did you verify the integrity of the iso image using md5 checksum?

EDIT: Ooops! I sent this post before your last comment. It's probably not a checksum problem.

---

### Post by ecoli0157h7 on 2006-11-01
What could this be? Hmmmpp. Could it be that my laptop is *dedicated for MS Windows XP*? Haha. I'm having no problem with XP installation (only with regards to installation procedures). hehehe.

---

### Post by ecoli0157h7 on 2006-11-01
Hey. My processor is Intel Centrino M. Could there be an incompatibility on my laptop's processor? It says, 
> Ubuntu is available in flavours for the i386                         (386/486/Pentium(II/III/IV) and Athlon/Duron/Sempron                         processors) Does Centrino belong to the same family of processors?

---

### Post by ecoli0157h7 on 2006-11-01
How about Celeron M ?

---

### Post by ecoli0157h7 on 2006-11-01
i keep seeing the *micro code* sort of errors.

---

