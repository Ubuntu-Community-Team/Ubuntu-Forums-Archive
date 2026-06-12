---
title: "[SOLVED] Error while installing software"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by thecoolcat on 2007-11-06
Hello,

I wanted to install softwares after installing gutsy on my PC.

So first thing, I added medibuntu repos using the following commands:

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O  /etc/apt/sources.list.d/medibuntu.list

wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
I didn't get any errors after the above comands. Then I tried to install acroread and w32codecs.

Got same errors for both:

acroread:
 Depends: libstdc++5  but it is not installable

Can someone help me please? Thanks.

---

### Post by ROBarber on 2007-11-06
maybe they are obsolete or not available anymore.

for viewing PDF file you can use:

[http://www.gnome.org/projects/evince]("http://www.gnome.org/projects/evince")

for the codecs, I think we have to wait

---

### Post by volksman on 2007-11-06
Get automatix....It will install both those and more for you with ease...

---

### Post by thecoolcat on 2007-11-06
Thanks for ur reply. Updating many other packages via synaptic package manager results in this error. Is anything corrupted in my installation?

---

### Post by thecoolcat on 2007-11-06
> **volksman said:**
> Get automatix....It will install both those and more for you with ease...

Hi volksman,

How do I get automatix? (Sorry am a noob :( )

---

### Post by overdrank on 2007-11-06
> **thecoolcat said:**
> Thanks for ur reply. Updating many other packages via synaptic package manager results in this error. Is anything corrupted in my installation?

You may want to enable all your repos. You can add repos under system, administration, software sources. The ubuntu software and updates tab. Hope this helps and good luck!

---

### Post by felin on 2007-11-06
> **thecoolcat said:**
> Hi volksman,

How do I get automatix? (Sorry am a noob :( )

It is not recommended on this forum - it can break your system apparently -  I've never used it but you get it from here:

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by thecoolcat on 2007-11-06
> **overdrank said:**
> You may want to enable all your repos. You can add repos under system, administration, software sources. The ubuntu software and updates tab. Hope this helps and good luck!

Thanks. Will try it out and update this thread.

---

### Post by rudeboyskunk on 2007-11-06
Also, if you want to install Adobe Reader, the best place to go is straight to Adobe's website.  They have the Linux version right there (in *.tar.gz, *.deb, *.rpm).

---

### Post by thecoolcat on 2007-11-08
Thanks for all your responses! After enabling all repos, I could add softwares I need.
Will mark this thread closed. :)

---

