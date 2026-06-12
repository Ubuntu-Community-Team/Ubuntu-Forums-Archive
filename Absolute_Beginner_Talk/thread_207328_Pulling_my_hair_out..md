---
title: "Pulling my hair out."
date: 2006-07-01
forum: Absolute Beginner Talk
---

### Post by dipswitch on 2006-07-01
I'm this || close to wiping my system clean. I haven't had this much problem with this OS ever.

I can't get universal packages added. Everytime I add it to the repositories then close and open again. Its unchecked. It will not save.

Audio doen't work at all. It used to. But doen't work anymore. When I open volume control it has the right device checked but when I run alsamixer is shows the onboard intel device. ****.

And other things just does not work. I'm so frustrated right now, I need a Valium.
](*,) ](*,) ](*,) ](*,)

---

### Post by aysiu on 2006-07-01
For extra repositories, try this:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by dipswitch on 2006-07-01
I can maunuall edit the sources file but why can't I do it throught Synaptic? That bothers me. It works just fine on my other computers

---

### Post by aysiu on 2006-07-01
I don't know. My philosophy is "Make it work first. Then figure out what was wrong."

---

### Post by Max Luebbe on 2006-07-01
Any chance you have two instances of synaptic running, maybe one on another workspace?

Are you running synaptic with super user permissions?

Those are the two things that come to mind regarding that problem

---

### Post by Jagot on 2006-07-01
[QUOTE=dipswitch]I can maunuall edit the sources file but why can't I do it throught Synaptic? That bothers me. It works just fine on my other computers[/QUOTE]

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by dipswitch on 2006-07-01
I'm positive. Synaptic opens just fine. I even tried sudo synaptic from terminal. Opens fine but it just wont save the settings when I try to add universal. I can put a check in the box but when I close Synaptic and reopen. Universal is unchecked.

Anyways. I think I've had enough. No audio. Can't install UT2004. I have a ut-436 folder on my desktop that WILL NOT DELETE.
```
Cannot move "/home/dips...top/ut-436" to the trash because you do not have permissions to change it or its parent folder.
``` Can't get twinview to work. Still having problems getting NTFS drives to mount. etc etc....

---

### Post by sinack on 2006-07-01
You need to use sudo when running commands in the shell.  sudo gives you root privs.  You might want to readup on it a bit, or setup root's password.  I find that lots of ubuntu users like to type 'sudo [command]', but i prefer to 'su' and run all of my commands.  to make root's password, all you have to do is...

sudo passwd root
[it will prompt you for a password, this should be your login password]
[next it will say that it is changing root's password, type in something different for the root password]

now type 'su' (without the quotes, and enter the password you just entered)

BAM, now you're root, and don't have to type sudo everytime you need root privs.

---

### Post by T700 on 2006-07-01
[quote=sinack]I find that lots of ubuntu users like to type 'sudo [command]', but i prefer to 'su' and run all of my commands.  to make root's password, all you have to do is...[/quote]

You can certainly do this, but doing so removes a very important safety feature.  One of the great positives in Ubuntu, in my opinion, is the lack of a root account by default.  Forcing the user to explicitly invoke root each time it is needed is an excellent way of requiring people to be very careful with powers that can easily render their computer an expensive paperweight.

Paul

---

### Post by raptros-v76 on 2006-07-01
...the problem then is with synaptic itself. probably a bug or something. i dont know. i manually edit my repo's anyway.

---

### Post by Nikusan on 2006-07-01
[QUOTE=dipswitch]
Anyways. I think I've had enough. No audio.[/QUOTE]

Tell us more about your audio hardware. What has changed since audio used to work? Was it a breezy to dapper upgrade?

[QUOTE=dipswitch]Can't install UT2004.[/QUOTE]

There's a whole bunch of UT2004 threads on the forum. Try [this one]("http://ubuntuforums.org/showthread.php?t=33396").

[QUOTE=dipswitch]I have a ut-436 folder on my desktop that WILL NOT DELETE.[/QUOTE]

Try *sudo nautilus* in a terminal and removing it that way.

[QUOTE=dipswitch]Can't get twinview to work.[/QUOTE]

Try reading the [Gentoo wiki entry]("http://gentoo-wiki.com/HOWTO_Dual_Monitors#TwinView"), it's not ubuntu but it should help.

[QUOTE=dipswitch]Still having problems getting NTFS drives to mount. etc etc....[/QUOTE]

[Here's how.]("http://ubuntuguide.org/wiki/Dapper#How_to_mount.2Funmount_Windows_partitions_.28NTFS.29_manually.2C_and_allow_all_users_to_read_only")

---

