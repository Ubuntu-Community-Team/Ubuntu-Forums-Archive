---
title: "Installing Skype"
date: 2006-09-18
forum: Assistive Technology &amp; Accessibility
---

### Post by pilarp on 2006-09-18
Hi,

does anyone know which version of Skype one should use for kbuntu? Does rpm work in kbuntu? Or is it tar.gz?

---

### Post by ajgreeny on 2006-09-18
You need the .deb version, available if you add the following repo to your sources.list file.  The version is now a beta 1.3.0.30_API, but it works very well.  Give it a try.
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

Alternatively you can just download the debian package from the skype website and install it with a double click, I think, or in a terminal type:-

cd /folder_where_you_downloaded_debfile
sudo dpkg-install xxxx.xxx.xx.deb

(the xxxx.xxx.xx.deb is the name of the package you downloaded

---

### Post by jtibau on 2006-09-22
I've found useful to also install the "alsa-oss" package through apt-get:
Type "sudo apt-get install alsa-oss" in a shell.
Skype uses oss, which is old and doesn't support multichannels or something. I read this somewhere.
The alsa-oss package is a wrapper that makes skype work with alsa.
So after installing both the Skype 1.3b (even though it's beta works way better than the older stable one) and alsa-oss.. Type in a console:
aoss skype
to run skype.
Alternatively, using alacarte you can modify the link on the applications>internet menu. On the "command" box type "aoss skype" instead of just skype.
Good luck

---

### Post by Rastareefer on 2006-09-23
I was using the beta deb version in Kubuntu 6.06 LTS which worked great until a few days ago when I did an adept update which seems to have screwed it up so that I try to run skype and it just spins its wheels till it stops abruptly without opening.:sad:

---

