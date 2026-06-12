---
title: "Opera for ubuntu"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by Sbarton on 2006-02-02
As I have had no luck getting Firefox to load I have downloaded Opera for Linux (Ubuntu - Breezy) onto my windows pc. I can save this file into a removeable pen drive so that it is recognised by Ubuntu when connected to it. Is it possible to install it in Ubuntu and - how?
Thanks



*[size=1]Locked due to triple posting - Artificial Intelligence*[/size]

---

### Post by MartinG on 2006-02-02
Yes. Either copy it across to your machine, or mount the drive, and from the directory it is in run:```
sudo dpkg -i <package_name>
```This assumes it is indeed a deb.

Alternatively, you could use [Automatix]("http://ubuntuforums.org/showthread.php?t=66563")

---

### Post by ferebee on 2006-02-02
There are detailed instructions for installation and configuring Opera here:
[https://wiki.ubuntu.com/OperaBrowser]("https://wiki.ubuntu.com/OperaBrowser")

Hope this helps!

---

### Post by Sbarton on 2006-02-03
Thanks for replies, however, none actually were successful. Following the suggestions I followed the Wiki Opera Browser setup, got to the very last instruction, saved the file only to be told that a error saving to a file Blah! blah!blah! (deep breath, deep breath) s**t. How can any software be so difficult to install? Give me a .exe file please!(deep breath - try again) OK! I am not going to quit! So I have the file on my disk waiting to install-HELP!

---

### Post by Sbarton on 2006-02-03
[QUOTE=Sbarton]Thanks for replies, however, none actually were successful. Following the suggestions I followed the Wiki Opera Browser setup, got to the very last instruction, saved the file only to be told that a error saving to a file Blah! blah!blah! (deep breath, deep breath) s**t. How can any software be so difficult to install? Give me a .exe file please!(deep breath - try again) OK! I am not going to quit! So I have the file on my disk waiting to install-HELP![/QUOTE]

Tried installing 'Automatix' only to be told that could not resolve Http:// beerorkid (etc) Geez! How simple this should be!! Forgive me I am having a moment! OK! any suggestions anyone! Helpful ones:D 
Thanks

---

### Post by MartinG on 2006-02-03
No luck with Firefox before that, and not resolving beerorkid etc.  Tough :(  It begins to seem as if there's a problem with networking somewhere? Or in the installation process?  Sorry, that sounds a bit gloomy, but I'm not sure what else to suggest.  Anyone else?

---

### Post by aysiu on 2006-02-03
Don't download the **Ubuntu** .deb (I know this goes against all human logic and intuition). Download the **other/static** .deb to your desktop. Then ```
cd Desktop
sudo dpkg -i opera*.deb
```

---

