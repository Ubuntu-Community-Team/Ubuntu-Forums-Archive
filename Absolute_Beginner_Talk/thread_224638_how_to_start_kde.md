---
title: "how to start kde"
date: 2006-07-28
forum: Absolute Beginner Talk
---

### Post by deputyemail on 2006-07-28
I all I am new to linux
and have installed ubuntu for the first time
How does one start the kde from the command line

Thanks
:-( :-( :?:

---

### Post by T700 on 2006-07-28
By default, an Ubuntu installation installs Gnome, but not KDE.  Did you install Kubuntu (Kubuntu installs KDE, but not Gnome.)
[B]
After the installation, are left with a black and white screen--the command line? [/B] Did you perhaps install the Server version instead of the Desktop version?  If so, I'd suggest downloading the Desktop version and reinstalling.  There are ways around the problem if you can not, but that is the best solution, in my opinion.

Paul

---

### Post by deputyemail on 2006-07-28
Thanks 
when I was looking at the downloads I thought
the desktop was for a user desktop as offered by centos
So I will download the desktop version


Thanks very much

---

### Post by T700 on 2006-07-28
Glad to help.  It isn't very clear on the download site.

Paul

---

### Post by Exodus Naixus on 2007-12-29
Thank you very much for not posting a reply on how to start KDE from command line. It would be great if people would just reply there answer but with the actual solution. Thank you very much, not to be rude, but I will have to continue to go to google.com to find a different solution for "how to start kde" BECAUSE EVERYONE continue to give solution other to than what was expected. Please stop post other solution than the command line answer if you don'r know it. Thank you. 

--- A new guy to Ubuntu.

---

### Post by elithrar on 2007-12-30
You've already had your question answered, in a way: **install Kubuntu**. KDE is installed by default with Kubuntu.

---

### Post by bwtranch on 2007-12-30
You can run KDE with Ubuntu if you want, you don't have to boot Kubuntu separate. Nice thing about it is having all that software to play around with ! The options are endless, you can install many K programs with aptitude or apt, Synamptic will install the K desktop that can be run side by side or just pick K programs that you like and use Gnome. I don't know why people want to separate this like it is windows and Mac. It's all Linux folks! You know you can even strip out of bash and just use sh? Happy bashing. Long live Unix. :)

---

### Post by zinya on 2008-03-22
I too would like to know how to start KDE from the command line.

I'm running Ubuntu 7.10, i installed kde, and can get it to load it from the login screen.

**However**, i like to boot into a cli. I have just set it up so that i can, but when i type 'startx' i get thrown into fugly gnome. Does anyone know how to get startx to load kdm? As debian doesn't seem to have a xwmconfig. (Would be very useful, silly debian)

---

### Post by Bachstelze on 2008-03-22
> **zinya said:**
>  I have just set it up so that i can, but when i type 'startx' i get thrown into fugly gnome.

```
cp ~/.xinitrc ~/.xinitrc.old
echo "exec startkde" > ~/.xinitrc
```

---

