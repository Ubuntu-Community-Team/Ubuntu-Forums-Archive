---
title: "I need an alternative for winzip(windows) in Linux"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by Bahal on 2006-10-11
Hi
I need to pack a file, så I can install in "Login Windows". The file is a splash screen with the format "png".

so...any ideas:confused: ?

thx :)

---

### Post by MWAAAHAAA on 2006-10-11
Use zip, gzip, bzip2, or rzip.

---

### Post by gosh on 2006-10-11
ark for KDE
gzip for Gnome
Xarchiver for XFCE
zip
unzip
tar
p7zip

There all in the repositories

---

### Post by Bahal on 2006-10-11
Thx alot for your help..
have nice day:)

---

### Post by cotcot on 2006-10-11
Maybe I do not understand your question well. Not sure what you mean with pack.
You will not gain a lot with packing an already packed format (png).

In linux you have 'tar.bz2' and "tar.gz' formats which can be extracted with 'tar'.

---

### Post by Delkster on 2006-10-11
> **Bahal said:**
> Thx alot for your help..
have nice day:)

Ubuntu (with the GNOME desktop environment) comes with an archive manager that can be found in Applications > Accessories > Archive Manager. Kubuntu (with the KDE desktop) has an archive manager.

In GNOME you can also just locate the file you want to archive in your file browser, right-click on it and select "Create Archive".

---

### Post by MWAAAHAAA on 2006-10-11
> **cotcot said:**
>  In linux you have 'tar.bz2' and "tar.gz' formats which can be extracted with 'tar'.

Technically not correct. tar.bz2 can be unpacked by filtering through bzip2, and tar.gz by filterting through gzip. These files were first archived with tar, and the archive subsequently packed with either bzip2 or gzip.

---

### Post by SoundFriend on 2007-09-11
However, Winzip has three Encryption options, Zip 2.0 compatible, 128bit and 256bit AES encryption.  

It would be nice to find a native Linux prog to read and write the 256bit AES encrypted archive.

As a workaround I have installed Winzip using Crossover Office and it works ok.

SF

---

