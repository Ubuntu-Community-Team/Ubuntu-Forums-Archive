---
title: "[SOLVED] Installing FirstClass client..."
date: 2007-08-07
forum: Absolute Beginner Talk
---

### Post by slappy19 on 2007-08-07
If an install is made for:  (from the site: [http://www.softarc.com/clientdownloads/FC83LinuxDownloadPage](http://www.softarc.com/clientdownloads/FC83LinuxDownloadPage))

To download the Linux Fedora Core 5 version click here.
To download the Linux SuSE Intel version click here.
To download the Linux Debian Intel version click here.
To download the Linux Generic Intel version click here.

Can I use any of these Linux downloads for Ubuntu even if their isn't a specific Ubuntu link?  Thanks in advance.  (I tried the Generic, but it was just files and I couldn't get it to install or load).  I am VERY new to Linux, but trying...

---

### Post by Dr Small on 2007-08-07
Download the debian version, then either double click on it and it will open it with the package manager, or run the command in the terminal to install it:
```
sudo dpkg -i installsdebpackage.deb
```

Dr Small

---

### Post by slappy19 on 2007-08-07
> **Dr Small said:**
> Download the debian version, then either double click on it and it will open it with the package manager, or run the command in the terminal to install it:
```
sudo dpkg -i installsdebpackage.deb
```

Dr Small

Worked like a charm!  Thanks a ton!   I didn't even have to use the terminal...

---

### Post by Shibby73 on 2007-10-06
The company that manages my Firstclass Server has this site:

[http://www.aptiris.com/ClientDownloads/8.3/FCC8315Linux](http://www.aptiris.com/ClientDownloads/8.3/FCC8315Linux)

I followed the directions here and had no problems.

I also have used beta clients on Linux without too many problems.

-Steve (Shibby73)
My Firstclass Server:
[www.stansgnosticus.net](www.stansgnosticus.net)


:guitar:

---

