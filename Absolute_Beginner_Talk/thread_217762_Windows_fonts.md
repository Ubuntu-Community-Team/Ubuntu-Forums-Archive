---
title: "Windows fonts"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by Typo on 2006-07-17
CAn anyone give me the url for the truetype windows fonts. I know how to install em I just can't find em. The sites I come across are full of popups and adverts and NOT the downloads.

CHeers,

---

### Post by mgor on 2006-07-17
```
$ sudo apt-cache search msttcorefonts
msttcorefonts - Installer for Microsoft TrueType core fonts
$ sudo apt-get install msttcorefonts
```
?

---

### Post by avtolle on 2006-07-17
I thought I had it; try Google for the URL.

---

### Post by Typo on 2006-07-17
None of that works above I took away $ etc I am not complete noob but no work... and dude, I said I have looked everywhere for em.. I have done google...

I asked for link anyone?

BUMP!

---

### Post by avtolle on 2006-07-17
OK, following site has several archives listed to download the true type fonts:

smorgasboard.net/how_to_install_true_type_fonts_ubuntu_linux

HTH.

---

### Post by Typo on 2006-07-17
THat site is parked :/

---

### Post by qyot27 on 2006-07-17
> **Typo said:**
> None of that works above I took away $ etc I am not complete noob but no work... and dude, I said I have looked everywhere for em.. I have done google...

I asked for link anyone?

BUMP!
You have to enable the multiverse repository first.  That's the only thing that would stand in the way of getting the package.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then run *sudo apt-get update* followed by *sudo apt-get install msttcorefonts*.  That should take care of it.

---

### Post by fatsheep on 2006-07-17
Go to the terminal, type "sudo aptitude install msttcorefonts" without quotes and press enter.  If you are prompted to continue then due so.  Once complete, this command should install all of the microsoft core fonts (arial, georgia, verdana, etc...) to your system.  You will have to restart your machine for them to take effect.

---

### Post by Typo on 2006-07-17
I did that and it said:

> Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for msttcorefonts
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done


Restarted, and still they are not on? :/

---

### Post by fatsheep on 2006-07-17
> **Typo said:**
> I did that and it said:



Restarted, and still they are not on? :/

Are you sure? :confused:  It worked for me.  Try going to system>preferences>fonts and try changing them from there.  You should have arial, arial black, georgia, and the rest of them there.

---

### Post by echo $USER on 2006-07-17
> **qyot27 said:**
> You have to enable the multiverse repository first.  That's the only thing that would stand in the way of getting the package.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

Then run *sudo apt-get update* followed by *sudo apt-get install msttcorefonts*.  That should take care of it.

Do what this guy said!

---

### Post by Typo on 2006-07-17
No I don't have arial or any, I don't understand it :/

---

### Post by Typo on 2006-07-17
ok I will try now :/

---

### Post by fatsheep on 2006-07-17
Ah I didn't realize you had to have multiverse repositories enabled.  I do have them enabled so that's probably why it worked for me.

To enabled multiverse respositories:

Go to System (top menu)>Administration>Software Properties. You'll have to enter your password here. After that then select "Ubuntu 6.06 LTS (source)" from the list (should be the first one), click "Add...", select "community maintained (universe)" and "non-free (multiverse)" by clicking the check box. Click add again.

---

### Post by Typo on 2006-07-17
YEp did that and now it works fine. Thanks to everyone who provided help in anyway.. I apreciate it! You guys helping me is what makes me love ubuntu more :))

Cheers!

---

### Post by fatsheep on 2006-07-17
Great, I'm glad it worked for you.  :p

---

### Post by MellonCollie on 2006-07-17
If you want to make your MS fonts look a bit nicer, head over to this thread: [http://www.ubuntuforums.org/showthread.php?t=208396](http://www.ubuntuforums.org/showthread.php?t=208396)

---

