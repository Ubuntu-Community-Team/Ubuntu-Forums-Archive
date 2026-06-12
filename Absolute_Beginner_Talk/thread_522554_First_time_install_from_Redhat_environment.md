---
title: "First time install from Redhat environment"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by Paliswan on 2007-08-10
I have Redhat on my system and have no iidea how to install Ubuntu.  I know Redhat very poorly (which is part of reason I want to switch to Ubuntu).  I have Ubuntu disk.  When I fire up the computer it doesn't detect the Ubuntu install disk.  When I try to install from the loaded Redhat environment, I don't know which file to click on to get the installation started.  Everytime I click on a .exe, redhat tells me that it can't run .exe!  Very frustrating!

It took me a while to figure out that I need to do some special steps to "unbundle" the CD drive.  I did that, and I can see the CD contents, but nothing gets me to where I want to go.  It is 7.04.

How do I start Ubuntu?

Hopefully this does not involve going to roots and GUI's and dos.  These are  very foreign terms to me.  But, hey maybe I can learn from the experience.

---

### Post by zvacet on 2007-08-10
Of course you put your computer to boot from CD.If you can boot other Cd-s it is somethimg with blank Cd or with iso you downloaded.You have to burn it as iso not as data(you know that but just to be sure).Did you try to burn it on other CD?If download is bad you can fix it like this:
Download with torrent and direct download to the folder where your iso is.Torrent will just chek iso and if it is something corrupted torrent will replace it.After that burn it.

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by Paliswan on 2007-08-10
There are no instructions for coming from Redhat.  Only from MS or Ubuntu environments.

Any special information coming from Redhat environment?

---

### Post by zvacet on 2007-08-10
I belive you have CD/DVD burner in your Redhet distro.Just burn it as iso not as data and you should be good.

---

### Post by bodhi.zazen on 2007-08-10
No special instructions for Ubuntu, you can follow the guide zvacet posted.

How did you burn the iso ? the way you use .exe it sounds as if you are coming from Microsoft.

The iso is burned to cd, not as a data disk, but as an image.

See here : [http://www.petri.co.il/how_to_write_iso_files_to_cd.htm](http://www.petri.co.il/how_to_write_iso_files_to_cd.htm)

---

### Post by Paliswan on 2007-08-10
I don't understand, but thanks for trying to help.  I have Ubuntu disk from the snail mail.  I don't understand about iso's.  I tried the burning cd and it crashed (it said there was a fatal error).  So, it looks like I can't use the install disk I received in the mail?  The instructions about creating an iso talked about what to do if you have MS Operating system, but nothing about coming from Redhat.  Is it possible just to delete and turn off Redhat to start with blank hard drive?

I don't understand a lot of this.  I can do some stuff, but not too fancy of stuff.

---

### Post by bodhi.zazen on 2007-08-10
Well you have to boot the CD

Set your BIOS to boot to the CD first, then hard drive ;)

---

### Post by heinig on 2007-08-10
Are you sure that your computer is set up to boot from the CD?
It sounds that our computer is booting your HD (with Redhat) and your are trying to install Ubuntu from there (what I don't think is possible....but I dont know much either... :-))

PS: only now I saw bodhi.zazen post and I have the same impression here...

---

### Post by Paliswan on 2007-08-10
How do I set the BIOS?  I'll google that.

---

### Post by annda on 2007-08-10
most likely F2, F12 or DEL on boot. watch the screen closely when your computer boots

---

### Post by Tyke91 on 2007-08-10
When you restart your computer, it should tell you the name of your computer manufacturer (Dell, Compaq, whatever) and in the bottom right it should say "Press XXXX for setup"

just press whatever button it is, go to the "Boot order" page, and select boot from CD drive as first.



about not running .exe files:  

No linux distro will do that. RedHat will run .rpm files and ubuntu will run .deb files like exes.  exe is only for windows.

---

### Post by Paliswan on 2007-08-10
Thank you very much everyone.  I went to the Safe mode and booted straight from the CD.  It worked great!

---

### Post by bwtranch on 2007-08-10
Yeah, just look at the screen when your computer boots and look for "boot menu" or options whatever. You may not get it on that go around, but on the next keep tapping that key. It will then give you a boot menu and you of course select CD. Re-start and it will try to boot from the CD, if it doesn't then there is something wrong with the CD or the drive. Also, make sure that you have burned an IMAGE (iso) not just copied files to disk. By the way, not meaning to be mean, but if you can't get past this, stay with windoze.:)

---

### Post by bwtranch on 2007-08-10
Sorry, I take it back. Forgot that you had redhat. Glad you got it going.

---

