---
title: "GUI for Samba"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by rtcary on 2006-06-23
Is there a GUI interface for Samba?  RedHat does have a GUI interface.

Thank you

---

### Post by patsissons on 2006-06-24
[QUOTE=rtcary]Is there a GUI interface for Samba?  RedHat does have a GUI interface.

Thank you[/QUOTE]
I know that in KDE you can use konqueror or krusader to browse a samba network graphically.  However, I don't think either apps allow you to browse shares on the entire network.  I haven't really ever tried to do that before.  But if that is what you are looking to do, there is a simple CLI command to do the same.   I know it is not a GUI, but it just tells you what is out there and then you can use whichever GUI app to  interact with the share.  Not sure which GUI app is out there for Gnome, but I'm sure that there is one.
```

smbtree -N           # browse the network as a guest
smbtree -U=username  # browse the network as a specific user (will ask for password)

```
I use either of those commands to check out what shares are available, it should be pretty reliable since it probes the samba network at your request instead of using cached entries (*cough* windows *cough*).  Hope that helps.

---

### Post by aysiu on 2006-06-24
Isn't *smb4k* a GUI for Samba?

---

### Post by rtcary on 2006-06-24
[QUOTE=patsissons]I know that in KDE you can use konqueror or krusader to browse a samba network graphically.  However, I don't think either apps allow you to browse shares on the entire network.  I haven't really ever tried to do that before.  But if that is what you are looking to do, there is a simple CLI command to do the same.   I know it is not a GUI, but it just tells you what is out there and then you can use whichever GUI app to  interact with the share.  Not sure which GUI app is out there for Gnome, but I'm sure that there is one.
```

smbtree -N           # browse the network as a guest
smbtree -U=username  # browse the network as a specific user (will ask for password)

```
I use either of those commands to check out what shares are available, it should be pretty reliable since it probes the samba network at your request instead of using cached entries (*cough* windows *cough*).  Hope that helps.[/QUOTE]

Can you point me to a place where I can get instructions on how to install Samba on my Ubunta Desktop?  With RedHat, it is automatically installed and there is a GUI configuration.

Thank you...

---

### Post by Stormbringer on 2006-06-24
I just wrote an HOWTO on this matter ... take a look at the link in my signature.

Feel free to ask for any help.

As for the "GUI" - if you are talking about the configuration GUI called SWAT:

Inside a terminal type:
# sudo apt-get install swat

Upon installation it's accessible through your brower ([http://localhost:901/](http://localhost:901/))

---

### Post by rtcary on 2006-06-24
[QUOTE=Stormbringer]I just wrote an HOWTO on this matter ... take a look at the link in my signature.

Feel free to ask for any help.

As for the "GUI" - if you are talking about the configuration GUI called SWAT:

Inside a terminal type:
# sudo apt-get install swat

Upon installation it's accessible through your brower ([http://localhost:901/](http://localhost:901/))[/QUOTE]

Many thanks for writing the very detailed HOWTO!  Fortunately, I was able to go to my RedHat Linux box and copy smb.conf to my Ubuntu DeskTop and everything worked perfectly.  What I did not know how to do was the installation of Samba *and* that you helped with.

Is there a place where one can share their enthusiasm about Ubuntu.  Though I am a software developer (Windows), I am *not* a systems guru and I am finding Ubuntu to be a very well put put together package of Linux.  Yes, the Linux gurus my be offended when I say Ubuntu has the Mac polish, but that is what the average user wants/needs.  Yet, under the hood is a powerful and stable OS.

Todd

---

### Post by Stormbringer on 2006-06-24
> **rtcary]Is there a place where one can share their enthusiasm about Ubuntu.[/QUOTE]

You're already at the right place where you can share your enthusiasm ...

However, there's always the [Ubuntu Cafe]("http://ubuntuforums.org/forumdisplay.php?f=11") or [Ubuntu Testimonial]("http://ubuntuforums.org/forumdisplay.php?f=103") Section where you can express yourself.

And you are right about the "polish" --- Dapper just looks great (even without all the Compiz/XGL eyecandy) said:**
> Many thanks for writing the very detailed HOWTO! Fortunately, I was able to go to my RedHat Linux box and copy smb.conf to my Ubuntu DeskTop and everything worked perfectly.

Thanks for the cheers.

The way you managed to solve things is just another approach (taking a working config from another system). Glad you've been able to work it out.

---

