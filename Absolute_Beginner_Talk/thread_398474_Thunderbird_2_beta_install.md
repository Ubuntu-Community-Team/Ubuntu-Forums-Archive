---
title: "Thunderbird 2 beta install"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by psyphen on 2007-04-01
The Thunderbird 2 beta isn't in any of the repositories, and I'm itching to install it. How would I go about doing that? I googled around, and I didn't see any deb packages that anyone made off-hand.

Thanks
~psyphen

---

### Post by ajmorris on 2007-04-01
go here: 
[http://www.mozilla.com/en-US/thunderbird/releases/2.0b1.html#downloadandinstall](http://www.mozilla.com/en-US/thunderbird/releases/2.0b1.html#downloadandinstall)

the source code for linux is there.

---

### Post by psyphen on 2007-04-01
but how would i get that to replace the thunderbird 1.5 I installed with apt-get (i.e. keep the shortcuts, etc?)

---

### Post by ajmorris on 2007-04-01
> **psyphen said:**
> but how would i get that to replace the thunderbird 1.5 I installed with apt-get (i.e. keep the shortcuts, etc?)

unless you convert it to a .deb file to be installed through dpkg, you can't use it to replace your 1.5 version.

---

### Post by zeddock on 2007-04-12
How can one convert it to a .deb file?

Thanx!

zeddock

---

### Post by Andrew1234 on 2007-04-12
Don't know if this is much help but on the [www.showmedo.com](www.showmedo.com) site there is a tutorial on making .deb's.
[showmedo tutorial]("http://www.showmedo.com/videos/video?name=linuxJensMakingDeb&fromSeriesID=37")

---

### Post by nexu56 on 2007-04-21
Here's how I did it (without converting to .deb)

1. [Download Thunderbird 2.0 for Linux]("http://getthunderbird.com")

2. Extract it the tarball, rename it and put it somewhere (I put it in /opt)

```
tar xvf thunderbird-2.0.0.0.tar.gz
mv thunderbird thunderbird2
sudo mv thunderbird2 /opt
```

3. Start Thunderbird 2

```
/opt/thunderbird2/thunderbird
```

4. Go through the wizard and enter your email settings as usual

5. Go to menu **Edit -> Accounts**

6. Select **Server Settings**

7. On the field Local Directory hit the Browse button, and then navigate to your existing mozilla thunderbird folder, it will be under mozilla-thunderbird in your home directory. For instance mine was /home/nexu56/.mozilla-thunderbird/cz0kpya6.default/Mail/mail.nexu56.com

8. Close  thunderbird 2, start it up again as in step 3, and your email should now be there.

You will also need to update whatever link/launcher you use to point to** /opt/thunderbird2/thunderbird** instead of **mozilla-thunderbird**. I'm sure there's a tutorial somewhere on how to do that ;-)

---

### Post by kittyhawk63 on 2007-05-01
Best instructions I've found so far. Thanks.
kh

---

