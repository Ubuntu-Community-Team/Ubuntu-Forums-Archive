---
title: "Need Program Suggestions"
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by dethredic on 2007-11-30
I am new to Ubuntu, but I would consider myself fairly tech savy, so hopefully will be easy.

I have been a long time windows user, and I need some programs that are the equivalent to what I had on windows. I know there are a bunch of programs that come in the package that are installed, or ready to be installed. If that is the case, just let me know.

- Music / Video Player with iPod Support.
- A program to transfer the songs on my iPod to Ubuntu
- A Pidgin replacement, one with more features. I am mainly looking for a more condensed contact list (no pics is fine), a link that will open my hotmail inbox, an " xxx is typing message" and easy file transfer feature.
- Limewire/frostwire replacement. Can I use these on Linux?
- Is wine the best virtual computer software?

Thanks.

---

### Post by jken146 on 2007-11-30
Check out the package managers Applications > Add/Remove and System > Administration > Synaptic for all your installing needs.


> **dethredic said:**
> 
- Music / Video Player with iPod Support.
- A program to transfer the songs on my iPod to Ubuntu
Rhythmbox (comes installed) has ipod support.  So do many other programs.  EDIT: gtkpod is rumoured to be the best for iPod support.

> - A Pidgin replacement, one with more features. I am mainly looking for a more condensed contact list (no pics is fine), an " xxx is typing message" and easy file transfer feature.
Don't know, I like Pidgin fine, bot have a look in Add/remove or Synaptic.

> - Limewire/frostwire replacement. Can I use these on Linux?
Yes, there are linux versions, in the repositories I believe.

> - Is wine the best virtual computer software?
Wine works well for running some Windows programs (winehq.org has details of what works and what doesn't).  Other programs will work in Cedega (mainly for games, has a price tag) or Crossover Office (price tag too, but 30 day free trial).  Wine is not a virtual machine though.

---

### Post by vikram on 2007-11-30
> 
- Music / Video Player with iPod Support.
- A program to transfer the songs on my iPod to Ubuntu
Try Amarok a very popular music player with iPod support. Also like and use gtkpod to transfer files to and from the ipod.

> 
- A Pidgin replacement, one with more features. I am mainly looking for a more condensed contact list (no pics is fine), an " xxx is typing message" and easy file transfer feature.
Try kopete another multi protocol IM client. One big plus for kopete is web cam support I also like the integration of the contact list with the addressbook

If not already installed, all of them (Amarok, gtkpod and kopete ) are available from the repos. either install them by searching through synaptic or

sudo install amarok gtkpod kopete

---

### Post by dethredic on 2007-11-30
well, I searched add remove programs, and gtkpod was not there, and when I tried via terminal it said it wasn't found or something.

Also, edited my instant messaging program needs - a mail button.

---

### Post by vikram on 2007-11-30
gtkpod 0.99.10-2 is in the universe component of the repository.

check if the universe repos are enabled in synaptic. You may be able to uncomment the universe lines in 
/etc/apt/sources.list
should look somthing like this
## Comment on the 'Universe' repositories
## Comment about the support limitations of Universe & Multiverse
## repositories as well as licence restrictions and update policies.
## Please satisfy yourself as to your rights to use the software.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

see [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) for more details


# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse



not in front of my computer but if since kopete integrates with kaddressbook 
and kaddressbook integrates with kmail you should be able to send mail to contacts. 
IMHO this integration of one program with another increases the usability of KDE apps

---

### Post by atomkarinca on 2007-11-30
> **dethredic said:**
> Also, edited my instant messaging program needs - a mail button.

aMSN has that feature and I guess it works (never tried but my sister uses it so it should be working)

For your iPod you can try amarok, it looks and feels better.

About wine, if you want to play games you may also try [cedega]("http://www.transgaming.com/") but you have to pay for that.

---

### Post by dethredic on 2007-11-30
@vikram 

None of those lines are in mine.

@atomkarinca

Where do I get it? (not in my add/remove programs)

---

### Post by SunnyRabbiera on 2007-11-30
> **dethredic said:**
> 
- Music / Video Player with iPod Support.
- A program to transfer the songs on my iPod to Ubuntu

Amorok and gtkpod are said to do real well in this area from what I heard (dont have an ipod)
and I heard Rhythmbox does fine as well

> 
- A Pidgin replacement, one with more features. I am mainly looking for a more condensed contact list (no pics is fine), a link that will open my hotmail inbox, an " xxx is typing message" and easy file transfer feature.
file transfer is a bit bad on all linux IM apps I am afraid, the issue is not linux but AIM, MSN and YIM hating open source and not allowing decent file transfer apps for linux.
Kopete and amsn are good but really you will have to adjust to certain things

> - Limewire/frostwire replacement. Can I use these on Linux?

yup, both limewire and frostwire are available to us, so no replacements needed

> - Is wine the best virtual computer software?
ehh, this is debatable, and really wine is not a virtual computer software...
but there are ways to get some windows software running on linux, some free and some not free.
wine is getting pretty good I have to admit, another good one is crossover but that is not free.
there are ways to install windows within linux but really virtualization is a risky venture due to its high memory consumption.

---

### Post by atomkarinca on 2007-11-30
> **dethredic said:**
> @atomkarinca

Where do I get it? (not in my add/remove programs)

Well, it should be in add/remove. On the top-right corner you should have "All available applications" selected. And if it's still not here's the [website]("http://www.amsn-project.net/").

---

### Post by vikram on 2007-11-30
this may help

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

---

### Post by SunnyRabbiera on 2007-11-30
also remember that the add/ remove applet is very limited in its options, to get more packages you might want to use synaptic, its under system, in "administration"
Synaptic is a more avdanced package manager then the add/remove app, it might look a little plain to the windows user eyes but it does the trick.
you might want to check out this page:
[here you go]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by dethredic on 2007-11-30
I was using the x64 version of Ubuntu. Would that be the reason that some of the apps weren't under the add/remove programs?

Also, I remember that GAIM was in one of the earlier versions. I am not sure how much I liked it, because it was on a computer with no internet. Is it still available?

---

### Post by dethredic on 2007-12-01
....

---

### Post by atomkarinca on 2007-12-01
> **dethredic said:**
> Also, I remember that GAIM was in one of the earlier versions. I am not sure how much I liked it, because it was on a computer with no internet. Is it still available?

Gaim has changed its name to Pidgin now, it's in the repositories, just type this in the terminal:

```
sudo apt-get install pidgin
```

---

