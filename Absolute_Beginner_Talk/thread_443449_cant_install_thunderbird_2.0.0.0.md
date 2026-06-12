---
title: "cant install thunderbird 2.0.0.0"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by SnellC on 2007-05-14
Hi

Ive just downloaded thunderbird 2.0.0.0 as it supports hotmail, and now ive extracted the tar.gz i am led to belive i dont have to make the installation as it uses preconfigured binaries.

So now i need to know where to place the thunderbird folder, or do i just run it from my home folder.

I was led to believe that by placing the folder in the /opt directory would make the package available to all users, but i cant copy into this folder.

Any ideas on all of the above.

thanks

---

### Post by kebes on 2007-05-14
In Ubuntu, it's easier to install software using the "Package Manager." You only then need to install things manually if it's not included in the repositories. Luckily, Thunderbird is in the repositories, so installation is simple.

If you want to install via the commandline, just type:
```

sudo aptitude install mozilla-thunderbird

```

If you want to install the GUI way, go Applications > Add/Remove

Then search for "Thunderbird", mark it for installation, and click apply. It will perform all the installation steps automatically for you.


Hope that helps.

---

### Post by crimesaucer on 2007-05-14
I use this guide: [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

It was very easy.

---

### Post by SnellC on 2007-05-14
yeah id figured that out, but for some reason, thunderebird 2.0.0 isnt in the package manager list, its only ver 1.5 which doesnt seem to support the webmail and hotmail add ons.

any idea how i get the package manager to install the newer vrsion?


thanks

---

### Post by kebes on 2007-05-14
Sorry... yes you're right, Thunderbird 2.0 is not in the repositories yet.

You can use this script:
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Install_Official_Mozilla_Build_of_Thunderbird)
to install the latest Thunderbird binary from the mozilla site (mentioned in [this thread]("http://ubuntuforums.org/showthread.php?p=2634731")). Apparently [Automatix]("http://www.getautomatix.com/") can also be used to automatically install the latest Thunderbird (see [this thread]("http://ubuntuforums.org/showthread.php?p=2612071")).

---

### Post by kebes on 2007-05-14
If you want to install it manually, this faq:
[http://www.cyberciti.biz/faq/install-thunderbird-2-in-linux/](http://www.cyberciti.biz/faq/install-thunderbird-2-in-linux/)

Explains that you just have to [download]("http://www.mozilla.com/en-US/thunderbird/") and untar the Linux file somwhere (wherever you want, but in your home directory would be typical).  It looks like you've already done this pat. To run it, then you just activate the "thunderbird" shell file that is in the directory.

However there might be missing shared libraries that you need to manually install using Synaptic...

---

### Post by imdidactic on 2007-05-14
[Automatix]("http://http://www.getautomatix.com/") has an auto installer for Thunderbird 2.0

---

### Post by crimesaucer on 2007-05-14
> **crimesaucer said:**
> I use this guide: [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

It was very easy.

or you could do it the easy way that I linked you to:

```
wget -c http://releases.mozilla.org/pub/mozilla.org/thunderbird/releases/2.0.0.0/linux-i686/en-US/thunderbird-2.0.0.0.tar.gz 


```

```
sudo tar -C /opt -zxvf thunderbird-2.0.0.0.tar.gz 


```

```
sudo dpkg-divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename /usr/bin/mozilla-thunderbird 
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
sudo ln -s /opt/thunderbird/thunderbird /usr/bin/thunderbird


```

now run your new Thunderbird 2.0:

```
thunderbird
```

EDIT- and you will also need to change the launchers from mozilla-thunderbird to just thunderbird. It's all in that ubuntu page.

---

### Post by Derevko on 2007-05-16
You can find a feisty backport in my repository [http://ubuntu.iuculano.it/](http://ubuntu.iuculano.it/)

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

---

### Post by GoneWithTheWind on 2007-05-21
> **crimesaucer said:**
> I use this guide: [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

It was very easy.

Your instructions and the guide helped me to get Thunderbird going right away.

Thanks.  :)

---

### Post by josiah on 2007-05-22
> **Derevko said:**
> You can find a feisty backport in my repository [http://ubuntu.iuculano.it/](http://ubuntu.iuculano.it/)

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

Just installed from your repository, and wanted to let you and everyone else know that it seems to work very well. Thank you!

---

### Post by crimesaucer on 2007-05-22
> **John Rupp said:**
> Your instructions and the guide helped me to get Thunderbird going right away.

Thanks.  :)

No problem, that guide was really easy to follow.

---

### Post by bramvandijk on 2007-05-25
> **Derevko said:**
> You can find a feisty backport in my repository [http://ubuntu.iuculano.it/](http://ubuntu.iuculano.it/)

[http://ubuntu.iuculano.it/dists/feisty/thunderbird/](http://ubuntu.iuculano.it/dists/feisty/thunderbird/)

Thank you very much!

---

