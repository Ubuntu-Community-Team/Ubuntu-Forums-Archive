---
title: "xmcm-0.1.5 .deb"
date: 2006-07-14
forum: Assistive Technology &amp; Accessibility
---

### Post by jasongrieves on 2006-07-14
Hi everyone,

Got the deb rolling today.  I tested it on a friend's clean install of dapper.  

1) depends on lesstif1 and libxcomposite1

```
sudo apt-get install lesstif1 libxcomposite1
```

2) make sure your driver supports composite (ati, fglrx, nivida, DO but vesa does not!).  You will need to enable composite

sudo gedit /etc/X11/xorg.conf

```

Section "Extensions"
    Option "Composite" "true"
EndSection

```

3) download/install the deb

[http://filebox.vt.edu/users/jgrieves/html/xmcm_0.1.5-0ubuntu1_i386.deb](http://filebox.vt.edu/users/jgrieves/html/xmcm_0.1.5-0ubuntu1_i386.deb)

navigate to downloaded files (typically desktop)

```

Navigate to Applications > Accessories > Terminal
cd Desktop
```

```
 sudo dpkg -i xmcm_0.1.5-0ubuntu1_i386.deb
```

comments and coding of XMCM are welcome!  We are currently trying to fix the bug that renders the magnifier kinda useless.  The upgrade to X11R7 killed the magnifier.  

Email contacts
main developer [email]gk4@us.ibm.com[/email]
me : [email]jasongrieves@gmail.com[/email]

---

### Post by Henrik on 2006-07-14
The deb installs and runs fine. The magnifier has poor performance though, which I guess it the problem you are refering to. I have composite enanabled, but I'm not running XGL or AIGLX.

---

### Post by jasongrieves on 2006-07-14
> **Henrik said:**
> The deb installs and runs fine. The magnifier has poor performance though, which I guess it the problem you are refering to. I have composite enanabled, but I'm not running XGL or AIGLX.

Yeah if you look at the bug list you can see this listed.  George Kraft believes this can be fixed in time, as he really hasn't tried to optimize or even improve performance.  Having XGL or AIGLX should not boost performance, as far as I know...unless xgl somehow improves the compositing?  I do not know how those two subsystems interact.

---

### Post by RKCole on 2006-07-14
This is pretty neat.  I actually configured everything correctly and received a very jumpy magnifier, but this looks very promising.

I know that this is going to be a stupid question (still new to Ubuntu (Dapper)), but where would I need to go to set the configuration (i.e. docked top, line, etc)?

I wish that I could be of more assistance to you guys on all of these assistive technology projects, but my programming experience is very limited, and I'm still quite new to Linux. But I will help any way that I can.

Thanks for all of the hard work you all are putting into making Ubuntu and Linux accessible.

---

### Post by Henrik on 2006-07-15
> **RKCole said:**
> I wish that I could be of more assistance to you guys on all of these assistive technology projects, but my programming experience is very limited, and I'm still quite new to Linux. But I will help any way that I can.

There is actually an area where you can be of great help to us without being able to program: **testing**. 

There are likely lots of bugs floating around in standard distro applications that need reporting and follow-up. Here is a recent example: [https://launchpad.net/products/update-notifier/+bug/53091](https://launchpad.net/products/update-notifier/+bug/53091)

The accessibility applications themselves are getting a fair bit of attention now, but there are literally thousands of regular applications that need to learn to play better with the access tools. Some careful testing of these would be great help!

---

### Post by RKCole on 2006-07-16
I would be very glad to be of assistance in testing.  Where should I go and how should I get started?

I want to do all that I can to help in accessibility development for Linux as I am a partially blind user with very limited income.  I'm tired of Windows...and (as soon as my upgrades stop on my sponsorship for my ZoomText Magnifier) I will not be able to afford the near $500 price for ZoomText v10.0 when it arrives.  I've been using Dapper for about a month now, and I'm seriously considering sticking solely with Linux from now on...even if I have a bit to learn.

I'll do whatever I can to help...although I may need a bit of direction...and I apologize for my ignorance in these matters.

Please take care.

---

### Post by gigait on 2006-07-19
I am new to Linux and have just installed Fedora Core 5. Is it worth me trying to get the magnifier working? Or should I choose another Unix/Linux dstrobution?

I'm happy to help with testing coz I REALLY need a screen magnigier!!!

Please let me know what I need to do.
:-k

---

### Post by yellowband on 2006-07-19
in my experience, the default magnifier (gnopernicus) is pretty craptastic on both distros.  That said, i had better luck with getting it running in ubuntu than in fedora core.  It was totally unusable in fedora core (i was using version 3 at the time), but i did get it working right off the bat in ubuntu 6.06.

---

### Post by gigait on 2006-07-19
have you tried this xmcm magnifier?

---

### Post by RKCole on 2006-07-19
I apologize if this is off of the subject of the thread itself...

gigait:  I began using Fedora Core while in a Linux class a couple of months ago.  Gnopernicus was very horrible to configure and work with in Fedora.  I switched to Ubuntu 5.10 and had problems with Gnopernicus as well (mainly because of my video card settings back then...and my lacking of experience), but it works very well in Ubuntu Dapper Drake (v6.06 LTS).

XMCM seems to be a very promising entry in the field of Linux accessibility.  I am looking forward to seeing what it has to offer in the long run as it seems like it has many of (if not more) the capabilities of ZoomText for Windows.  At this point, though, I have read (and personally experienced) that the magnifier does not work so well.  But as I said, this is a very promising project and I am sure that it will be a great asset in Ubuntu and Linux accessibility in the near future.

For the time being, I am primarily using Gnopernicus with the gnome-mag screen magnifier.  I saw another post which said that there is a newer version of gnome-mag available, so I am waiting/looking forward to new deb packages so I can test it out.

To sum it all up, though, Gnopernicus seems to work MUCH better in Ubuntu Dapper than in Fedora from my experience as well as that of others.

If you need any help with anything, please feel free to private message or e-mail me and I will help as best as I can.

Take care.

---

