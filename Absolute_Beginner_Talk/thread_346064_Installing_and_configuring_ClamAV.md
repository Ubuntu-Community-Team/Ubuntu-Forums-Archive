---
title: "Installing and configuring ClamAV"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by Nhatz on 2007-01-25
is there an How-To for installing and configure ClamAV... thanks!:guitar:

---

### Post by Josh1 on 2007-01-25
Enable the [universe]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_apt-get_the_easy_way_.28Synaptic.29") then simply type in terminal:
```
sudo aptitude install clamav
```

Simple ;)

---

### Post by RomeReactor on 2007-01-25
Hi. Once you have ClamAV installed, you can get a graphical interface by installing ClamTk; it's in Synaptic. However, if you want to use it from the terminal, try:

```
man clamscan
```

and scroll down to the "EXAMPLES" section to get an idea of how to use it; also look at my post in [this]("http://www.ubuntuforums.org/showthread.php?p=2039075#post2039075") thread for some basic operations.

---

### Post by tr333 on 2007-01-25
a quick search of the [how-to forum]("http://www.ubuntuforums.org/forumdisplay.php?f=100") led me to [this post]("http://www.ubuntuforums.org/showthread.php?t=318091&highlight=clamav").  i have also heard that [Automatix]("http://www.getautomatix.com/") will install clamav for you if you prefer that method.

---

### Post by Nhatz on 2007-01-25
i got this error while installing it.....:( 

Writing extended state information... Done
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe arj 3.10.22-2 [211kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe clamav 0.88.2-1ubuntu1 [65.7kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe unzoo 4.4-4 [19.1kB]
Fetched 296kB in 1m10s (4219B/s)
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = "en_PH:en",
        LC_ALL = (unset),
        LANG = "en_PH.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory

---

### Post by RomeReactor on 2007-01-25
I can't remember if this is in Dapper, but look in "System-->Administration-->Language Support" and change the tab below to "English (Philippines)"; then try installing ClamAV again.

---

