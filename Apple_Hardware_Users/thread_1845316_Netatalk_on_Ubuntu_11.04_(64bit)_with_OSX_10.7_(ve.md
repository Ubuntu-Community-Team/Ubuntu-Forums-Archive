---
title: "Netatalk on Ubuntu 11.04 (64bit) with OSX 10.7 (version problem)"
date: 2011-09-16
forum: Apple Hardware Users
---

### Post by Simi23 on 2011-09-16
I have been struggling with this for few days now, I have tried every howto I could find on this.
After I install Netatalk and Avahi I get message in OSX 10.7 its a wrong version after I put in login info for user. I did tried few different versions for Natatalk but now I'm not even sure which one is installed and if I like to install another version how to completely get rid of the old one since when I install it not from repository but (sudo make install kinda way) I can't seem to unistall it with command sudo apt-get remove netatalk ... then it just says there is no netatalk installed ;-( so Now I'm not sure what to do in this case.

---

### Post by Simi23 on 2011-09-19
ok I guess nobody was really interested to help, but I did find solution in my 64bit system. It seems only version compatible with OSX Lion 10.7 is Netatalk older beta version ([netatalk-2.2-beta4.tar.gz]("http://sourceforge.net/projects/netatalk/files/netatalk/2.2/netatalk-2.2-beta4.tar.gz/download")) after installing this everything worked fine.

I'm still struggling with 32bit Ubuntu 11.04 system, repeating same steps, but still getting version problem on Lion part.

---

### Post by tebrown on 2011-09-22
If you install netatalk 2.2.1 from Jeff Strunk's PPA, it should work fine for OSX Lion.

[https://launchpad.net/~jstrunk-math/+archive/ppa](https://launchpad.net/~jstrunk-math/+archive/ppa)

---

### Post by twoksl2 on 2011-09-25
> **tebrown said:**
> If you install netatalk 2.2.1 from Jeff Strunk's PPA, it should work fine for OSX Lion.

[https://launchpad.net/~jstrunk-math/+archive/ppa](https://launchpad.net/~jstrunk-math/+archive/ppa)

you, sir are awesome. i had been messing with this for way too long, but this took care of it. thank you very much.

---

