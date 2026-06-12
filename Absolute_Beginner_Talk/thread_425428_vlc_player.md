---
title: "vlc player"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Franswa_CS on 2007-04-27
can any one tell all the packages that i need to download it to install vlc player
(note: i don't have a network connection from ubuntu so i can't use add/remove program)

thanks

---

### Post by Kobalt on 2007-04-27
You can find it on [http://packages.ubuntu.com](http://packages.ubuntu.com)
Search for VLC, all the dependencies are listed.

---

### Post by Franswa_CS on 2007-04-27
i have done this and i have downloaded all dependencies but there are some files requires another and so on and i'm tired from downloading the files one each time.
i want there names to download theme at once

---

### Post by toddward on 2007-04-27
[http://freshmeat.net/depends/download-all/36873/]("http://freshmeat.net/depends/download-all/36873/")

---

### Post by NewbieNik on 2007-04-27
Handy Hint:
There is a great (If slightly cheating for the purists) package call Automatix2
download the appropriate version from:-
[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)
and run it.

Pick the apps you want, but please do read the terms and conditions to make sure you are keeping everyone happy!

Baest of Luck

---

### Post by nickpaton on 2007-04-27
To keep it simple I would endorse using Automatix2 as well.

Good luck!

EDIT:  Thanks Trak87 - missed the bit about no network connection.

BTW is there a reason for no connection or is it that you don't have Bband?  Do you have a problem with your connection that we may be able to help you with - it would be easier to download stuff and then install IMHO.

If so may I suggest you make a separate post.

---

### Post by trak87 on 2007-04-27
Hold on a minute. When you install a package via the command line or via  Synaptic, all the dependencies are automatically downloaded and installed for you. You shouldn't need to manually download all the packages separately. Am I missing something?

Just try:

```
sudo apt-get install vlc
```

Oops. Now I see you said you don't have a network connection...

---

### Post by Franswa_CS on 2007-04-28
yes i have problem with my connection as i use dialup modem. i have installed the driver for my modem but it still does not work all what happen is that it dials the number then disconnection immediately.

---

### Post by nickpaton on 2007-04-28
Franswa

May I suggest you post a separate question in Beginners about your modem.

Include information on the modem driver you used, also the chipset used (like connexant or whatever).

You may want to have a look at [this]("http://www.linmodems.org/") from linmodems.org.

A good HOWTO on internal Connexant modems [here]("http://ubuntuforums.org/showthread.php?t=190728").

Great article from the community pages [here]("https://help.ubuntu.com/community/DialupModemHowto").

And finally[ here]("http://ubuntuforums.org/showthread.php?t=171163").

I assume you are posting this from a Windows PC using your dial up which must be working.

I'll look for it there and if I can contribute I will.

Good luck once again and when we get your dial up sorted we can get back to looking at VLC in more detail.

---

### Post by trak87 on 2007-04-28
Try this:

apt-cache showpkg vlc

It will list the dependencies. You can ignore the "reverse dependencies" show as this is a list of programs that would depend on vlc, whereas dependencies is a list of programs vlc depends upon for proper operation.

You might also try: 

apt-cache depends vlc

---

