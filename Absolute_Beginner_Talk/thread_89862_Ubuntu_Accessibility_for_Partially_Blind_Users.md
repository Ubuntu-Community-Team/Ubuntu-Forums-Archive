---
title: "Ubuntu Accessibility for Partially Blind Users?"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by RKCole on 2005-11-13
Hello, everyone.

I am going to be receiving (hopefully in a few days) a CD for Ubuntu Linux.  I am very new to Linux (I've only worked with the command-line side in college, via a telnet connection), so I just have a few questions.  Firstly, though, I am very much looking forward to working with and learning Linux.  I chose Ubuntu because their standards and mission are very inspiring, and because I cannot afford blank CDs or to purchase other distress.  Ubuntu just seems like the one for me to use...
I am legally, partially blind.  I use a program called [ZoomText]("http://www.aisquared.com/") for Windows (it is a screen magnifier/reader; however I only use the screen magnification feature.

I was wondering if anyone knew of any flexible magnification applications that I could use on Ubuntu?  I have seen a few while doing online searches, such as Kmag, Xzoom, and others.  Is any one familiar with any of these, or would anyone have a better recommendation?

I am taking programming courses at the college which I attend, and once I have enough skill in the field I am hoping to begin designing a magnification program for Linux that is like ZoomText...unless there is something already available.

Thanks for any help and advice provided.

Take care, everyone.

---

### Post by Qrk on 2005-11-13
Yes. Gnome has high accesibility themes available for download via synaptic. After you install ubuntu, you can easily download them with the simple command

```
sudo apt-get install gnome-accessibility-themes
```

which you can put into a terminal from Applications->Accessories->Terminal

or by opening up synaptic via System->Administration->Synaptic Package Manager, and searching for gnome-accessibility-themes.

Once you install them, you can select them via System-->Preferences-->Themes

Unfortunatly, they are not installed by default, which means you'll have to use the default themes to find them. These are themes that have larger text and icons or high contrast. 

Gnome also comes with a screen magnifier, called gnome-mag, which can be installed in the same manner as the gnome-accessibility-themes,

```
sudo apt-get install gnome-mag
```

I have not tried any of the other magnifiers, but they can also be found in synaptic, although some need the universe repositories. (You'll find a ton of information on those in these forums) You are, of course, free to choose any you like.

---

### Post by Lambert on 2005-11-13
[SIZE=4]I have no experience with this but gnome is set up to use an assitive program for you. You will have to install a program called [/SIZE][SIZE=4][COLOR=Sienna]gnopernicus. [COLOR=Black]Here are notes about it.

> Screen reader for GNOME 2
Gnopernicus is designed to allow users with limited or no vision to
access GNOME applications.  It provides a number of features, including
magnification, focus tracking, braille output, and more.

Warning: Gnopernicus is still experimental; there is no official release
yet.  This package is provided as a convenience for interested Debian users
to try out Gnopernicus.

To enable the magnification feature you must also install the optional
component gnome-mag. 
Maybe you can contact the developers of this project and assist them in the project.

[http://www.baum.ro/gnopernicus.html](http://www.baum.ro/gnopernicus.html)
[/COLOR][/COLOR][/SIZE]

---

### Post by linbetwin on 2005-11-13
[quote=RKCole]Hello, everyone.

I am going to be receiving (hopefully in a few days) a CD for Ubuntu Linux. I am very new to Linux (I've only worked with the command-line side in college, via a telnet connection), so I just have a few questions. Firstly, though, I am very much looking forward to working with and learning Linux. I chose Ubuntu because their standards and mission are very inspiring, and because I cannot afford blank CDs or to purchase other distress. Ubuntu just seems like the one for me to use...
I am legally, partially blind.  I use a program called [ZoomText]("http://www.aisquared.com/") for Windows (it is a screen magnifier/reader; however I only use the screen magnification feature.

I was wondering if anyone knew of any flexible magnification applications that I could use on Ubuntu? I have seen a few while doing online searches, such as Kmag, Xzoom, and others. Is any one familiar with any of these, or would anyone have a better recommendation?

I am taking programming courses at the college which I attend, and once I have enough skill in the field I am hoping to begin designing a magnification program for Linux that is like ZoomText...unless there is something already available.

Thanks for any help and advice provided.

Take care, everyone.[/quote] 
Hello RKCole,

I am also partially blind and I use the Magnifier utility in Windows.

I've tried several Linux distros (Mandrake 10.1, SUSE 10.0 and Ubuntu 5.04 and 5.10) and there is no difference between them in terms of accessibility.

There are two magnifiers you can use in Linux: KMag and Gnopernicus. KMag doesn't follow text editing, Gnopernicus does, but only in very few applications (Terminal, gedit.. and not much else) and even there very poorly. Another problem of Gnopernicus is that if you move your mouse a little faster than very slow you will see black "rectangles" in the magnification area, or even portions of previously closed windows, as if the magnifier cannot render the images fast enough. The magnifier process uses 140-150 MB of RAM and CPU usage soars to 100% when you move your mouse.

KMag also uses a lot of CPU, but it renders images very fast and with no problems. Yet it doesn't follow text editing in any application. I've written to the maintainers of the project and they've informed me text editing focus is a feature scheduled for KDE 4.0.

I don't want to discourage you (I know I'm not discouraged!). Good luck with the programming! Maybe a partially blind developper can come up with a more useful magnifier. I would have done it myself but I am literally illiterate in programming and the way i figure it, if developing a good magnifier would be easy, someone would have done it by now.

---

### Post by RKCole on 2005-11-13
Thanks for the replies, Lambert, Qrk, and linbetwin.

I will take a look at the links you all gave me when I finally get to install the OS.  I really appreciate the help and advice.

linbetwin, I've been doing a lot of checking around, and I have found a few magnifiers...The only problem is that I will not be able to test them out until I receive my Ubuntu CD and install Linux.

I've used Windows Magnifier for quite awhile, but it has some problems.  I was fortunate enough to have a copy of Ai Squared's ZoomText purchased for me, but the makers of it do not support Linux.  It is a lot more flexible and efficient than Magnifier, but it has a few issues...as almost all software does.

So the magnifiers take up a lot of CPU usage?  I only have about 256MB of RAM, and when I install Ubuntu, I ma planning on allocating it maybe 20-30GB of space on my hard drive (I have an 80GB hard drive currently...); would this cause a problem?

I have read that the screen resolution/color contrast can be changed for larger icons and wording in many places, including a previous reply to this thread.  Would this also have an effect on CPU Usage?  Also, my processor is a Pentium 4 2.8GHz if that would make much of a difference.

I've wanted to start Linux for years, but I was always afraid to because I was not sure how accommodating it is.

When I get enough programming experience, I hope to create (although I am not sure how difficult it would be) a program similar to ZoomText that would run on Linux, without the $500 price tag...

I'm definitely not discouraged from using Linux, and it is really nice to see that there are other people out here on the Internet with visual disabilities. (You're actually the first person, linbetwin, who I have come across.)  I've been a Windows user from the beginning, and I always wanted something else.  I always wanted to get into Linux, but I was discouraged by many people.  I figure I'm just going to jump in and give it a try, and who knows...one of these days I'll be developing accessibility software for the platform.  I'm a strong believer in the open source community and free software...Without help I never could have afforded ZoomText.  Only reason the price is so high is because it is specific to blind users...I suppose.

Thanks again, everyone.  I'll post back later on if I find anything more on this subject, or to reply to further posts.

linbetwin, if you ever need someone to relate to concerning the disability, feel free to e-mail me.  I have some resources that may be of some help to you for using your PC.  I saw a really promising magnifier app awhile back that was much more powerful than Windows magnifier...If I find it I'll post the link here.

Everyone please take care.

---

### Post by redbone on 2006-03-31
Hello, 
first of all sorry for my bad english, I am a Windows user and I also have vision problem, I can't use Linux because I don't find a software like M$ Windows Magnifier. If I have well understood there are only KMag and Gnopernicus but they  have some problems ? it's true ?

---

### Post by RKCole on 2006-03-31
[SIZE="4"]Hello there, redbone.

I just began taking a Linux class at my college this past week.  Unfortunately, I have not been able to get hold of a second hard drive to install Ubuntu on (I had very excessive failures trying to dual boot on the same drive).  The class works with Fedora Core 2 (I like Ubuntu much better), and the instructor for the class has never worked with any assistive technologies for Linux.

I spent a little time yesterday trying to configure Gnopernicus (it was a much older version), and it worked pretty well.  I have a feeling it will work much better on an Ubuntu system.  It took a little while to get used to and to configure, but by the time I was finished I had it docked at the top of the screen like Windows Magnifier.

One thing which I must point out is that (at least for the older version of Gnopernicus that I used) the magnifier cannot be resized by using sizers as it can on Windows.  You must manually set the properties and tell the program how many pixels from the top, bottom, left, and right it must be.  It was a hassle at first, but I found it to be much better than Windows Magnifier.

I have a link at this moment for you for GNOME Accessibility.  Developers are currently working on a GNOME Accessibility project which will be for users with assistive needs.  The link (below) is to a guide to the GNOME Accessibility features.  Hopefully this will be of some help to you.

[http://delysid.org/gnome.html](http://delysid.org/gnome.html)

There was also a program called Gmag (gnome-mag) available, but I am having a bit of trouble finding information on it at this time.  I have not yet been able to test it, so I cannot give any input on it.  However, Gnopernicus (when configured to your liking) is not too bad of a program.  It worked well for me.

If I can be of any further help, please let me know.  Just don't be discouraged.  Linux is growing very quickly, and it has a lot to offer.

If it would be of any help, I w9ill try to write a short tutorial so that you can configure Gnopernicus.  It is not too difficult, though.

Take care.

[/SIZE]

---

### Post by redbone on 2006-04-03
Ok thank you very much **RKCole** for your reply. Now I have see that exist also the italian support forum for Ubuntu and I have asked the same question in the italian Forum.
I'll try to install Ubuntu in dual boot I ask to my friend to install it with Gnopernicus and I hope to became an Ubuntu user soonh. Thank you again.
Take care too

---

### Post by redbone on 2006-04-04
I have another question , **RKCole**,
in italian Forum have suggested me to try Ubuntu Live CD before install it in my Hard disk to test my harsware configuration but they don't know if Gnopernicus is in Live CD.
Do you know if Gnopernicus is in the Live CD Distribution ?
If the answer is "yes" you can suggest me a fast way to run it ? I don't know very much about Linux in this moment.
If not I'll try to install Ubuntu on my machine. I have see also that is possible to use Wine to run an windows application like magnifier.exe. 
Thank you again.
Ciao

---

### Post by Henrik on 2006-04-25
The latest dapper Live CD now have the magnifier installed: [http://releases.ubuntu.com/6.06/](http://releases.ubuntu.com/6.06/) 

Perhaps someone who lives close to these guys (US and Italy I guess) could burn and send out a copy? :)

---

