---
title: "GPG error! Problem with Update Manager"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Floren on 2006-09-10
Hi,

From one day to the next without (apparently) touching any system files I get this problem: When I try to run the Update Manager and click on check I get:

[PHP]W: GPG error: http://us.archive.ubuntu.com dapper Release: Unknown error executing gpgv 
W: GPG error: http://us.archive.ubuntu.com dapper-updates Release: Unknown error executing gpgv 
W: GPG error: http://us.archive.ubuntu.com dapper-backports Release: Unknown error executing gpgv 
W: GPG error: http://archive.canonical.com dapper-commercial Release: Unknown error executing gpgv 
W: GPG error: http://security.ubuntu.com dapper-security Release: Unknown error executing gpgv[/PHP]  

If I try 'sudo apt-get update' from the console, I get the same answer. And I also noticed that all software that I try to install with Synaptic appears as 'Not authenticated'.

Any idea what's wrong?

Thanks,
Floren

---

### Post by FakeOutdoorsman on 2006-09-10
Is your clock time correct?  You may get this problem if your clock is set to the wrong year.

---

### Post by Floren on 2006-09-10
Yes, the year, month and time seem to be right... Thanks for your answer anyway. Any other suggestion?

   Floren

---

### Post by FakeOutdoorsman on 2006-09-10
The very last section of this site has good instructions on how to fix GPG signature error (which I assume is what you're getting):
[URL="http://www.psychocats.net/linux/sources.php"]
http://www.psychocats.net/linux/sources.php[/URL]

---

### Post by Floren on 2006-09-10
Gaack! I tried that and it didn't work either. It looked like a good approach :(

Thanks again,

    Floren

---

### Post by FakeOutdoorsman on 2006-09-11
Try this:

[Apt GPG Error]("http://www.de-brauwer.be/wiki/wikka.php?wakka=AptGPG")

and make sure your BIOS clock is correct too.  If that doesn't work, then have a shot of whisky.

---

### Post by FakeOutdoorsman on 2006-09-11
While searching for the answer I saw you [solved the problem]("http://ubuntuforums.org/showpost.php?p=1485648&postcount=3") already.  Now for that shot...

---

### Post by Najand on 2006-09-11
When a repository in this list has a GPG key, you may need to add that to the APT trusted keys. You can do this with the following commands (replace KEY with the key ID)

      gpg --keyserver subkeys.pgp.net --recv KEY
      gpg --export --armor KEY | sudo apt-key add -

Key IDs:
Ubuntu supported packages           GPG Key: 437D05B5
Seveas' packages                    GPG Key: 1135D466
Cipherfunk multimedia packages      GPG Key: 33BAC1B3
kubuntu.org packages for the latest 
KDE version                         GPG Key: DD4D5088
Bazaar-NG development               GPG Key: 1F44842D

---

