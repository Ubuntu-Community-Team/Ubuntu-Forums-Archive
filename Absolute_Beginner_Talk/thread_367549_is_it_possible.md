---
title: "is it possible?"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by halot on 2007-02-22
Hi I am somewhere between newbie and totally frustrated.  I have been using ubuntu desktop for about a year (and loving it!) but want to run a server with a gui.  I have tried again and again to install ubuntu-desktop on server 6.06 with no success.  So my question is can I just add the lamp apps to desktop ubuntu and be done with it?  This is the first command line issue that I haven't been able to solve.  Just as a note for us beginners it would be good to have the complete walk through, Don't assume we know anything.  As an example I was using aptitude instead of apt-get following following soneones directions to the T.  As a side note I have yet to find a linux distro (redhat, fedora,linspire,frespire, suse,etc.etc.) that has everything working out of the box, like ubuntu.

---

### Post by Ben Sprinkle on 2007-02-22
Try this:
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```
Might have to:
```

sudo apt-get install xorg xserver-xorg

```
In debian I do:
```

sudo apt-get install xorg xserver-xorg gnome

```
Hope that helped.

---

### Post by achill3z on 2007-02-22
So wait....so, this is possible? If it is(please say it is) how glorious! I'm a newb to the core(used ubuntu desktop for a total of about 3 months) but I'm loving it and I love to learn new things and try out new things so I wanted to "dive right in" and install Ubuntu Server...boy did I dive right in. It installed and all I saw was a dark, intimidating black void with nothing but a command-line interface. Needless to say, I wanted to curl up in the fetal position and imagine myself in my comfortable meadow of lush windows and colorful GUIs. But, I would like to re-install and mess around with Ubuntu Server.

---

### Post by Tomosaur on 2007-02-22
Yes, it's possible to install the GUI on top of the server installation, just follow Ben Sprinkle's instructions.

And yes, you can make the ordinary Ubuntu into a server by installing the LAMP apps, that's the beauty of Linux. Versatile :)

---

### Post by Ben Sprinkle on 2007-02-22
[LAMPP?](http://apachefriends.org)

---

### Post by halot on 2007-02-22
Thanks, will try both tonight.  Ubuntu has me doing things I didn't know I could do.

---

### Post by Ben Sprinkle on 2007-02-22
> **halot said:**
> Thanks, will try both tonight.  Ubuntu has me doing things I didn't know I could do.

That's the spirit! :)

---

### Post by achill3z on 2007-02-23
> **Tomosaur said:**
> 
And yes, you can make the ordinary Ubuntu into a server by installing the LAMP apps, that's the beauty of Linux. Versatile :)

So would this way be any less efficient or would it cut out any of the functionality of the full server install? I assume I would just pop in the server disc and then extract the LAMP apps? Any cmmands for doing so?

---

### Post by Ben Sprinkle on 2007-02-23
> **achill3z said:**
> So would this way be any less efficient or would it cut out any of the functionality of the full server install? I assume I would just pop in the server disc and then extract the LAMP apps? Any cmmands for doing so?

Shouldn't be any less effeciant.

---

### Post by Tomosaur on 2007-02-23
> **achill3z said:**
> So would this way be any less efficient or would it cut out any of the functionality of the full server install? I assume I would just pop in the server disc and then extract the LAMP apps? Any cmmands for doing so?

The full server install is actually just a stripped down Ubuntu install. If you want a GUI server, you may aswell just download the ordinary desktop Ubuntu and then download the necessary apps to turn it into a server. The ubuntu-desktop package itself will give you a whole lot more than is necessary though. You should read up on various desktop environments before you commit to anything. Fluxbox may be ideal - it's very lightweight and incredibly customisable. It won't detract too much from your server's resources.

---

